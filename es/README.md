# Especificación del Protocolo CreadorCraft 2D

Bienvenido a la especificación y documentación oficial del protocolo de red de **CreadorCraft 2D**. Este protocolo está diseñado desde cero para ofrecer una eficiencia extrema, un consumo mínimo de memoria y una latencia ultra baja, lo que lo hace perfectamente adaptado para funcionar sin problemas incluso en entornos retro como **J2ME (Java ME)** y dispositivos modernos de recursos limitados como **Android**.

Al eliminar la pesada sobrecarga de serialización (como JSON o XML) y cambiar a flujos binarios estrictos, el tamaño de los paquetes se reduce a unos pocos bytes, evitando los temidos tirones del Recolector de Basura (*Garbage Collector*) en hardware heredado.

## 🔒 Requisitos de Cifrado y Seguridad de Red (TLS)

Para garantizar la compatibilidad con dispositivos retro (como J2ME que carecen de soporte nativo para TLS 1.3) y a la vez mantener altos estándares de seguridad modernos, toda la infraestructura de **CreadorCraft 2D** opera bajo estrictas normativas criptográficas:

*   **Conexiones de Servidores de Juego (WSS):** Deben establecerse obligatoriamente mediante **WebSocket Seguro (WSS)** utilizando **exactamente TLS 1.2** (o superior compatible). Es un requisito indispensable para que las implementaciones de sockets en Java ME puedan completar el apretón de manos (*handshake*) cifrado sin arrojar errores de versión de protocolo.
*   **API Backend de Autenticación (HTTPS):** Los endpoints HTTP (`/wakeup`, `/get-ticket`, `/verify-ticket`) operan sobre HTTPS soportando **TLS 1.2 y/o TLS 1.3**, permitiendo conexiones fluidas desde clientes modernos (Android, PC, Web) y retro por igual.

## 📋 Tipos de Datos Primitivos y Binarios

Todos los paquetes y campos de datos se leen y escriben en orden de bytes **Big-Endian**. El protocolo se basa en los siguientes tipos de datos primitivos:

* **`byte`**: Entero con signo de 8 bits (`int8`, rango de `-128` a `127`).

* **`unsigned byte`**: Entero sin signo de 8 bits (`uint8`, rango de `0` a `255`).

* **`short`**: Entero con signo de 16 bits (`int16`, rango de `-32,768` a `32,767`).

* **`unsigned short`**: Entero sin signo de 16 bits (`uint16`, rango de `0` a `65,535`).

* **`boolean`**: Indicador booleano de 1 byte (`0x01` para verdadero, `0x00` para falso).

* **`String` (Cadena de Texto)**: Campo de texto de longitud variable que consiste en un `unsigned short` inicial que indica la longitud exacta de la cadena en bytes, seguido inmediatamente por los bytes en bruto de la cadena codificados en UTF-8 o ASCII.

## 🤝 Handshake y Flujo de Conexión Recomendado

El ciclo de vida de la conexión y la secuencia de sincronización inicial entre el Cliente y el Servidor sigue este orden estricto:

1. **Autenticación y Login**: Al abrir la conexión, el cliente envía el paquete **`LoginDatapacket`** (`0x01`) con su plataforma, idioma, versión de protocolo y el ticket de autenticación. Si la validación falla o las versiones no coinciden, el servidor responde con un **`DisconnectDatapacket`** (`0x03`) y cierra el enlace.

2. **Configuración de Entorno y Recursos (Servidor $\rightarrow$ Cliente)**:

   * El servidor declara el manifiesto de recursos y la URL base mediante **`AssetsDatapacket`** (`0x04`).

   * Define los bloques líquidos (`0x0B`) y los bloques vacíos sin colisión (`0x0C`).

   * Transmite la matriz de bloques del mundo con **`LevelDatapacket`** (`0x05`).

   * Configura los ajustes ambientales (`SetAmbient` `0x06`, colores de fondo o assets de fondo).

   * Inicializa el inventario del jugador (`0x0D`), la entidad/skin del jugador (`0x0E`) y las coordenadas de reaparición (`0x10`).

3. **Carga Completa**: Una vez que el cliente termina de descargar los recursos y procesar el mundo, envía el paquete **`DoneDatapacket`** (`0x11`) para notificar al servidor que ya ha aparecido completamente en el juego.

4. **Latido (Heartbeat) y Mantenimiento**: Ambos extremos intercambian periódicamente el paquete **`PingDatapacket`** (`0x02`) cada 15 segundos. Si transcurren 120 segundos sin recibir datos ni ping, la conexión expira por tiempo de espera (*Time-out*).

## 📦 Índice Completo de DataPackets (OpCodes)

| OpCode | Nombre del Paquete | Dirección | Descripción | 
| ----- | ----- | ----- | ----- | 
| **`0x01`** | **`LoginDatapacket`** | Cliente $\rightarrow$ Servidor | Envía la plataforma, idioma, versión de protocolo y ticket del cliente. | 
| **`0x02`** | **`PingDatapacket`** | Bidireccional | Paquete de latido enviado cada 15s para mantener la sesión activa. | 
| **`0x03`** | **`DisconnectDatapacket`** | Bidireccional | Termina la conexión, llevando un motivo en formato `String`. | 
| **`0x04`** | **`AssetsDatapacket`** | Servidor $\rightarrow$ Cliente | Declara la URL base de recursos y el array del manifiesto. | 
| **`0x05`** | **`LevelDatapacket`** | Servidor $\rightarrow$ Cliente | Transmite las dimensiones del mundo (`maxX`, `maxY`) y la matriz de bloques. | 
| **`0x06`** | **`SetAmbientDatapacket`** | Servidor $\rightarrow$ Cliente | Activa o desactiva el ambiente exterior (ciclo día/noche y clima). | 
| **`0x07`** | **`SetBackgroundColorDatapacket`** | Servidor $\rightarrow$ Cliente | Establece un color RGB sólido de fondo si el ambiente está desactivado. | 
| **`0x08`** | **`SetBackgroundAssetDatapacket`** | Servidor $\rightarrow$ Cliente | Establece un asset gráfico de fondo si el ambiente está desactivado. | 
| **`0x09`** | **`SetTimeDatapacket`** | Servidor $\rightarrow$ Cliente | Actualiza el tiempo del mundo en ticks del juego (`0` a `24000`). | 
| **`0x0A`** | **`SetWeatherDatapacket`** | Servidor $\rightarrow$ Cliente | Modifica el tipo de clima activo (Despejado, Lluvia, Nieve). | 
| **`0x0B`** | **`SetLiquidBlocksDatapacket`** | Servidor $\rightarrow$ Cliente | Define los IDs de bloques que actúan como líquidos. | 
| **`0x0C`** | **`SetVoidBlocksDatapacket`** | Servidor $\rightarrow$ Cliente | Define los IDs de bloques que no tienen colisión física. | 
| **`0x0D`** | **`SetInventoryDatapacket`** | Servidor $\rightarrow$ Cliente | Puebla el inventario de 25 espacios de ítems del jugador. | 
| **`0x0E`** | **`SetPlayerEntityDatapacket`** | Servidor $\rightarrow$ Cliente | Asigna la entidad o skin visual del jugador local. | 
| **`0x0F`** | **`SpawnEntityDatapacket`** | Servidor $\rightarrow$ Cliente | Spawnea entidades o jugadores secundarios con coordenadas escaladas (`pos * 100`). | 
| **`0x10`** | **`SetSpawnDatapacket`** | Servidor $\rightarrow$ Cliente | Establece las coordenadas iniciales de aparición del jugador en el mundo. | 
| **`0x11`** | **`DoneDatapacket`** | Cliente $\rightarrow$ Servidor | Confirma que el cliente terminó de cargar y apareció exitosamente. | 
| **`0x12`** | **`SetRubiesDatapacket`** | Servidor $\rightarrow$ Cliente | Actualiza la cantidad de rubíes del jugador. | 
| **`0x13`** | **`SetXPDatapacket`** | Servidor $\rightarrow$ Cliente | Actualiza el nivel de experiencia y el porcentaje de progreso del jugador. | 
| **`0x14`** | **`RemoveEntityDatapacket`** | Servidor $\rightarrow$ Cliente | Elimina o despawnea una entidad del mundo según su ID mundial. | 
| **`0x15`** | **`BulkBlockUpdateDatapacket`** | Servidor $\rightarrow$ Cliente | Actualiza múltiples bloques de forma masiva mediante índices e IDs. | 
| **`0x16`** | **`BlockUpdateDatapacket`** | Servidor $\rightarrow$ Cliente | Actualiza un solo bloque en el mundo por su índice. | 
| **`0x16`** | **`SetItemHandDatapacket`** | Bidireccional | Cambia el índice activo (0–24) del ítem sostenido en la mano. | 
| **`0x17`** | **`SetItemByIndexDatapacket`** | Servidor $\rightarrow$ Cliente | Reemplaza una ranura de inventario específica por índice e ID de ítem. | 
| **`0x18`** | **`InteractDatapacket`** | Cliente $\rightarrow$ Servidor | Transmite acciones de clic (Izquierdo/Derecho) sobre coordenadas del mundo o entidades. | 
| **`0x19`** | **`SetSpeedDatapacket`** | Servidor $\rightarrow$ Cliente | Configura el multiplicador de velocidad de movimiento (`velocidad * 100`). | 
| **`0x1A`** | **`SetHealthDatapacket`** | Servidor $\rightarrow$ Cliente | Actualiza la vida del jugador (`-1` para inmortal, hasta `100`). | 
| **`0x1B`** | **`SetGravityDatapacket`** | Servidor $\rightarrow$ Cliente | Activa o desactiva la predicción de gravedad (habilita/deshabilita el vuelo). | 
| **`0x1C`** | **`SetPauseDatapacket`** | Cliente $\rightarrow$ Servidor | Notifica el estado de pausa para reducir el tráfico de red solo a latidos. | 
| **`0x1D`** | **`ChatDatapacket`** | Bidireccional | Envía o transmite mensajes de texto dentro del chat del juego. | 
| **`0x1E`** | **`MoveDatapacket`** | Bidireccional | Sincroniza las posiciones de movimiento de entidades o jugadores (`pos * 100`). | 
| **`0x1F`** | **`UIDatapacket`** | Bidireccional | Renderiza o responde a interfaces de usuario modulares (`ModalUI`, `SimpleUI`, `CustomUI`). | 
