# Ping Datapacket
Este datapacket se empieza a envíar justo después de LoginDatapacket para mantener la conexión de preferentemente cada 15 segundos este es para ambos lados (Servidor y Cliente)

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x02 |  |  |  | Solamente es el ID |

Si no se recibe respuesta es 120 segundos en uno de los 2 lados debe cerrar la conexión por Time out