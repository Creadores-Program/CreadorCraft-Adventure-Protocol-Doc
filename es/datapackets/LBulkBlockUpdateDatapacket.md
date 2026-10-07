# BulkBlockUpdate Datapacket
Este datapacket lo envía el servidor, se usa para actualizar bloques en el mundo de forma masiva pero no total de el.

La fórmula para obtener el Bloque Index exacto por coordenadas es:

```java
int index = y + (x * maxY);
```

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Cantidad | unsigned short | 100 | Cantidad de bloques a actualizar |
| 0x15 | Index's de los bloques a cambiar | unsigned short[] | unsigned short [50, ...] | Index's de los bloques a actualizar usando la misma poción del ID del bloque en el array |
|  | IDs de los bloques a cambiar | unsigned short[] | unsigned short [3, ...] | IDs de los bloques a actualizar usando la misma posición del array anterior |

El primer bloque del ejemplo anterior reemplaza el index 50 del mundo por el bloque ID 3.
