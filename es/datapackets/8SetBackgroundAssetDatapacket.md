# SetBackgroundAsset Datapacket
Este datapacket es solo de servidor, se envia justo despues de SetAmbient Datapacket si mando false o después de SetBackgroundColor Datapacket, simplemente establece el fondo de un recurso registrado.
| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x08 | ID | unsigned short | 67 | ID de recurso tipo Fondo |
