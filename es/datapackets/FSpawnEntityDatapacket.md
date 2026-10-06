# SpawnEntity Datapacket
Este datapacket lo envía el servidor, se usa para spawnear entidades o jugadores que no son el jugador actual en el mundo con 2 IDs, un id de entidad definida en Assets Datapacket y otro id de entidad del mundo

Las posiciones se multiplican entre 100 ejemplo:
´´´java
short x = 12.60 * 100; //1260
´´´

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Entidad ID | unsigned short | 1 | Entidad/Skin con el cual se muestra la Entidad |
|  | ID Mundial | unsigned short | 5 | Id unico de la entidad que diferencia de las demas en el mundo |
| 0x0F | X | unsigned short | 1060 (10.60) | Posición X de la entidad |
|  | Y | unsigned short | 1420 (14.20) | Posición Y de la entidad |
|  | Nombre | String | "Max" | Nombre de la entidad (se puede dejar vacio) |
