# SetItemHand Datapacket
Este es para ambos lados (Servidor y Cliente), se usa para cambiar el item en mano del jugador.

El index es simplemente la posición del array de 0 a 24 en total de 25 ítems en inventario.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x16 | Index | unsigned byte | 14 | Index del ítem en inventario |