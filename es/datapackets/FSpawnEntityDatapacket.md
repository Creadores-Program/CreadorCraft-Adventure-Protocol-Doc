# SpawnEntity Datapacket
Este datapacket lo envía el servidor, se usa para spawnear entidades o jugadores que no son el jugador actual en el mundo con 2 IDs, un id de entidad definida en Assets Datapacket y otro id de entidad del mundo

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Entidad ID | unsigned short | 1 | Entidad/Skin con el cual se muestra la Entidad |
|  | ID Mundial | unsigned short | 5 | Id unico de la entidad que diferencia de las demas en el mundo |
| 0x0F | X | float | 10.6 | Posición X de la entidad |
|  | Y | float | 14.2 | Posición Y de la entidad |
|  | Nombre | String | "Max" | Nombre de la entidad (se puede dejar vacio) |
