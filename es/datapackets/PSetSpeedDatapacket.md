# SetSpeed Datapacket

Este datapacket lo envía el servidor, se usa para establecer la velocidad del jugador por ticks por defecto es 0.20 bloques por tick.

La valocidad se multiplica por 100 ejemplo:
```java
short x = 0.20 * 100; //20
```

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x19 | Velocidad | unsigned short | 20 (0.20) | Velocidad del jugador cada 1 tick avanza 0.20 bloques |