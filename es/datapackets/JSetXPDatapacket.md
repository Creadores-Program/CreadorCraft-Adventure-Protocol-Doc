# SetXP Datapacket
Este datapacket lo envía el servidor, este se puede enviar en cualquier momento para establecer el xp del Jugador.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x13 | Nivel de xp | unsigned short | 6 | Nivel Actual del Jugador |
|  | Porcentaje XP | unsigned byte | 50 | XP Actual del nivel (de 0% a 100%) |
