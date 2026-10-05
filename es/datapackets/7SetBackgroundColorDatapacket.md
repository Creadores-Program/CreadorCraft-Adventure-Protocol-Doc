# SetBackgroundColor Datapacket
Este datapacket es solo de servidor, se envia justo despues de SetAmbient Datapacket si mando false, simplemente establece el color del fondo del mundo en RGB

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Rojo | unsigned byte | 100 | un valor de 0 a 255 para el color rojo |
| 0x07 | Verde | unsigned byte | 100 | un valor de 0 a 255 para el color verde |
|  | Azul | unsigned byte | 100 | un valor de 0 a 255 para el color azul |
