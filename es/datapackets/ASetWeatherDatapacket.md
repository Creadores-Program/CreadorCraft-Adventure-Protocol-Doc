# SetWeather Datapacket
Este datapacket es solo de servidor, se envia en cualquier momento para cambiar el clima si el ambiente está activo.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x0A | Clima ID | unsigned byte | 0x01 | Tipo de clima del mundo |

## Clima IDs
- 0x01 Despejado
- 0x02 Lluvia
- 0x03 Nevado
