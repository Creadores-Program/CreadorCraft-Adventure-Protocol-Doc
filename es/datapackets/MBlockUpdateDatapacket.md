# BlockUpdate Datapacket
Este datapacket lo envía el servidor, se usa para actualizar bloques en el mundo de forma limitada (un bloque por datapacket) si quieres actualizar más de 3 bloques o de forma masiva usa BulkUpdate Datapacket.

La fórmula para obtener el Bloque Index exacto por coordenadas es:

```java
int index = y + (x * maxY);
```

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x16 | Index | unsigned short | 50 | Index del bloque en el mundo a cambiar |
|  | ID | unsigned short | 3 | ID del bloque |