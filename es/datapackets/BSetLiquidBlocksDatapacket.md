# SetLiquidBlocks Datapacket
Este datapacket es solo de servidor, se envia justo después de Assets Datapacket y se usa para definir los bloques líquidos por ID.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x0B | Cantidad | unsigned short | 55 | Cantidad de bloques líquidos que tiene el datapacket |
|  | Bloques Líquidos | unsigned short[] | unsigned short[...] | IDs de los bloques que son Líquidos |
