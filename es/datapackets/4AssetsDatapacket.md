# Assets Datapacket
Este datapacket lo envía el servidor justo después de LoginDatapacket para avisar que recursos necesita por url.
Las URL deben ser compatibles con https.
| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Url Base | String | "`www.asset.com/`" | La URL base sin Protocolo para descargar assets |
| 0x04 | Cantidad | unsigned short | 55 | Cantidad de assets que tiene el datapacket |
|  | Recursos | asset[] | asset[...] | Un array de assets según la cantidad |

La URL se formularia así:

`https://urlBase/b/id.png` para bloques

`https://urlBase/e/id.png` para entidades

`https://urlBase/a/id.ogg` para audios

`https://urlBase/i/id.png` para ítems

`https://urlBase/f/id.png` para fondos del mundo

Los siguientes urls no necesitan ID así que el ID se ignora puedes poner cualquier valor.

`https://urlBase/sun.png` para el Sol

`https://urlBase/moon.png` para la Luna

`https://urlBase/click.ogg` para sonido de Click

`https://urlBase/daycloud.png` para Nube de Día

`https://urlBase/nightcloud.png` para Nube de Noche

`https://urlBase/raincloud.png` para nube de Lluvia

`https://urlBase/raindrop.png` para gota de Lluvia

`https://urlBase/ruby.png` para Rubí

Ejemplo:

`https://www.asset.com/i/55.png`

## Asset
este es el contenido de un asset en el array del datapacket:
| **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- |
| ID | unsigned short | 1 | ID del Recurso para llamarlo en el juego (no puedes usar 0x00 ya que está en uso para vacío, en caso de audio es sonido click) |
| Versión | unsigned byte | 0x01 | Versión del recurso para procesar la caché en el juego si la versión no coincide se descarga de nuevo el recurso |
| Tipo | unsigned byte | 0x01 | Tipo de recurso que es |

### Tipos de Recursos
- 0x01 Bloque
- 0x02 Entidad
- 0x03 Audio
- 0x04 Ítem
- 0x05 Sol
- 0x06 Luna
- 0x07 Sonido de Click
- 0x08 Nube de Día
- 0x09 Nube de Noche
- 0x10 Nube de Lluvia
- 0x11 Gota de Lluvia
- 0x12 Fondo
- 0x13 Rubí
