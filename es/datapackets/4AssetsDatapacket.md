# Assets Datapacket
Este datapacket lo envía el servidor justo después de LoginDatapacket para avisar que recursos necesita por url.
Las URL deben ser compatibles con http y https y con verificación por CRC32
| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Url Base | String | "`www.asset.com/`" | La URL base sin Protocolo para descargar assets |
| 0x04 | Cantidad | short | 55 | Cantidad de assets que tiene el datapacket |
|  | Recursos | asset[] | asset[...] | Un array de assets según la cantidad |

La URL se formularia así:

`protocolo://urlBase/b/id.png` para bloques

`protocolo://urlBase/e/id.png` para entidades

`protocolo://urlBase/a/id.ogg` para audios

`protocolo://urlBase/i/id.png` para ítems

`protocolo://urlBase/f/id.png` para fondos del mundo

Los siguientes urls no necesitan ID así que el ID se ignora puedes poner cualquier valor.

`protocolo://urlBase/sun.png` para el Sol

`protocolo://urlBase/moon.png` para la Luna

`protocolo://urlBase/click.ogg` para sonido de Click

`protocolo://urlBase/daycloud.png` para Nube de Día

`protocolo://urlBase/nightcloud.png` para Nube de Noche

`protocolo://urlBase/raincloud.png` para nube de Lluvia

`protocolo://urlBase/raindrop.png` para gota de Lluvia

Ejemplo:

`https://www.asset.com/i/55.png`

## Asset
este es el contenido de un asset en el array del datapacket:
| **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- |
| ID | short | 1 | ID del Recurso para llamarlo en el juego (no puedes usar 0x00 ya que está en uso para vacío, en caso de audio es sonido click) |
| Versión | byte | 0x01 | Versión del recurso para procesar la caché en el juego si la versión no coincide se descarga de nuevo el recurso |
| Tipo | byte | 0x01 | Tipo de recurso que es |
| Verificación | int | 5 | Verificación de 4 bytes tipo CRC32 del recurso |

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
