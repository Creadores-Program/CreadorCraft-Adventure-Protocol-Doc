# SetSpawn Datapacket
Este datapacket lo envía el servidor, este se envia justo antes de aparecer en un mundo, es el último datapacket del servidor para spawnear en el mundo.

Las posiciones se multiplican por 100 ejemplo:
```java
short x = 12.60 * 100; //1260
```

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x10 | X | unsigned short | 1450 (14.50) | Posición X del jugador |
|  | Y | unsigned short | 3040 (30.40) | Posición Y del jugador |
