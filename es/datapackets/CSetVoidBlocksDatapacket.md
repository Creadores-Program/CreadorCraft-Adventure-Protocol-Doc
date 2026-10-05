# SetVoidBlocks Datapacket
Este datapacket es solo de servidor, se envia justo después de SetLiquidBlocks Datapacket y se usa para definir los bloques sin colisión por ID.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x0C | Cantidad | unsigned short | 55 | Cantidad de bloques vacíos que tiene el datapacket |
|  | Bloques Vacíos | unsigned short[] | unsigned short[...] | IDs de los bloques que son Vacíos |
