# SetAmbient Datapacket
Este datapacket es solo del Servidor, se envia justo despues de Level Datapacket para definir si el mundo esta en el exterior (ciclo de dia/noche y clima) o esta en otro mundo/dimension/cueva/instancia/etc. (el mundo se ambienta por SetBackgroundColor y/o SetBackgroundAsset)

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x06 | Ambiente | boolean | true | Habilitar o no el ambiente del mundo |
