# LoginDatapacket
Este es el primer Datapacket que debe enviar el Cliente con información Básica de el:

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Plataforma | unsigned byte | 0x01 (Android) | Plataforma del Cliente (más abajo documentación de este campo) |
|  | Idioma | short | 25971 (es) | Idioma tipo ISO-639-1 codificado en 2 bytes |
|  | Versión de Protocolo | unsigned byte | 0x01 | Versión del Protocolo de red |
| 0x01 | Discord ID | long | 293849... | ID de usuario de Discord |
|  | Ticket | byte[6] | [...] | Ticket obtenido por la API de CreadorCraft |
|  | UserName | String | "maxpro" | Nombre de usuario único de Discord |

La respuesta del Servidor puede ser desconexión (si fallo la autenticación) o continuar la conexión.

## Plataformas ID

- 0x00 Unknown
- 0x01 Android
- 0x02 Linux
- 0x03 J2ME
- 0x04 Mac
- 0x05 BSD
- 0x06 Solaris
- 0x07 Raspberry Pi
- 0x08 iOS
- 0x09 Nintendo
- 0x0A PSP
- 0x0B PS Vita
- 0x0C Symbian OS
- 0x0D BlackBerry
- 0x0E Palm OS
- 0x10 Xbox
- 0x11 PlayStation
- 0x12 Web
- 0x13 Windows Phone
- 0x14 Windows
- 0x15 Java
