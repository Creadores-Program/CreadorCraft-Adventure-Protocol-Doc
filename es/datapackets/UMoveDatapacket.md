# Move Datapacket
Este es para ambos lados (Servidor y Cliente), se usa para mover entidades o el jugador.

Las posiciones se multiplican por 100 ejemplo:
```java
short x = 12.60 * 100; //1260
```

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | ID Mundial | unsigned short | 5 | ID mundial de la entidad (el jugador actual es 0) |
| 0x1E | X | unsigned short | 1060 (10.60) | Posición X de la entidad |
|  | Y | unsigned short | 1420 (14.20) | Posición Y de la entidad |
