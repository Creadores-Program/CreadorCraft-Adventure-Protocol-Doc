# SetItemByIndex Datapacket
Este datapacket lo envía el servidor, se usa para actualizar ítems del jugador de forma limitada (1 por datapacket) si quieres reemplazar el inventario usa SetInventory Datapacket.

El index es simplemente la posición del array de 0 a 24 en total de 25 ítems en inventario.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x17 | Index | unsigned byte | 14 | Index del ítem a cambiar |
|  | ID | unsigned short | 3 | ID del ítem |