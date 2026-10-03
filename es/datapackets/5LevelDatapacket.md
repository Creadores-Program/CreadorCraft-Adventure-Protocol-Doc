# Level Datapacket
Este datapacket solo es de Servidor, se envia justo después de Assets Datapacket para construir el mundo 2D o al cambiar de mundo.

El mundo tiene un Y único de 100 bloques y un X configurable de mínimo de 50 y máximo de 500 bloques

La fórmula para obtener el Bloque exacto por coordenadas es:

```java
int index = y + (x * maxY);
```

Y la fórmula para tener el length máximo del array es:

```java
int length = maxX * maxY;
```

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | MaxX | short | 200 | Cantidad máxima de bloques en el mundo por enviar |
| 0x05 | Bloques | short[] | short[...] | Cantidad exacta de bloques por ID del mundo |
