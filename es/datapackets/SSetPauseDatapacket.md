# SetPause Datapacket
Este datapacket lo envía el cliente, se usa para avisar que el jugador entro en pausa, se usa principalmente para optimizar la red, si está en pausa solo envía Ping Datapacket para mantener viva la conexión, si pasan más de 5 minutos en pausa el servidor debe desconectar del cliente por falta de actividad.
Al volver al juego solo se mandan los datos actuales del juego y no todas las actividades del tiempo.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x1C | Pausa | boolean | true | Si el jugador está en pausa o no |
