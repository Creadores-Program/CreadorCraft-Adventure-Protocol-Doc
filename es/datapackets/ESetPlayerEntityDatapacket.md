# SetPlayerEntity Datapacket
Este datapacket lo envía el servidor, se usa para establecer la entidad del jugador por ID, se manda antes del primer SetSpawn o cualquier momento despues de SetSpawn.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x0E | Entidad ID | unsigned short | 1 | Entidad/Skin con el cual se muestra el Jugador |
