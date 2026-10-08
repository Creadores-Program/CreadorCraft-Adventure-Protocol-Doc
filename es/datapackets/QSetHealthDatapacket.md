# SetHealth Datapacket
Este datapacket lo envía el servidor, se usa para actualizar la vida del jugador, por defecto es -1 (inmortal), el daño o regeneración el servidor debe enviar este datapacket para aplicarlo, si es 0 el servidor debe mostrar un UI de muerte y hacer la lógica que quiera que pase usa UI Datapacket para la interfaz de muerte.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x1A | Vida | byte | 98 | La vida del jugador de -1 a 100, -1 es inmortal |
