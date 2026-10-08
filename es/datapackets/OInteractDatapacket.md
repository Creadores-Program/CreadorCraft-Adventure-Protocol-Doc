# Interact Datapacket
Este datapacket lo envía el cliente, se usa para mandar eventos de click del jugador.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Tipo de Click | unsigned byte | 0x01 | Tipo de click del jugador |
| 0x18 | Objetivo X | unsigned short | 20 | Posición X del mundo |
|  | Objetivo Y | unsigned short | 10 | Posición Y del mundo |
|  | ID Mundial de Entidad | unsigned short | 3 | ID Mundial de la entidad (0 es ninguna entidad) |

# Tipo de Click
- 0x01 Click/Click Izquierdo
- 0x02 Click prolongado/Derecho