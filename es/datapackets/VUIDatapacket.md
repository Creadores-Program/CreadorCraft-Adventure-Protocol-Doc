# UI Datapacket
Este es para ambos lados (Servidor y Cliente), se usa para hacer interfaces de usuario o responderlas.

En caso de cliente se Responde segun el tipo de UI

En caso de servidor se Envian los datos de la Interfaz

## Servidor Datapacket:
| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x1F | Tipo de UI | unsigned byte | 0x01 (ModalUI) | Tipo de UI a mostrar |
|  | UI | UI | ModalUI | Un UI igual al Tipo de UI del datapacket |

## Cliente Datapacket:
| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x1F | Respuesta UI | UI Response | ModalUI Response | Respuesta del UI |

# UI's

## ModalUI

Este se usa para confirmaciones o por ejemplo pantalla de muerte.

| **UI ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Titulo | String | "Comprar" | Titulo del UI |
| 0x01 | Contenido | String | "Seguro que Quieres Comprar?" | Contenido del UI |
|  | Botón Negativo | String | "No" | Contenido del Botón Negativo |
|  | Botón Positivo | String | "Si" | Contenido del Boton Positivo |

## SimpleUI

Este se usa para interfaces simples.

| **UI ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Titulo | String | "Comprar" | Titulo del UI |
| 0x02 | Contenido | String | "Compra lo que quieras!" | Contenido del UI |
|  | Cantidad de Botones | unsigned byte | 5 | Cantidad de Botones a mostrar |
|  | Botones | Button Element[] | Button Element[...] | Botones a mostrar |

## CustomUI

Este se usa para interfaces complejas.

| **UI ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Titulo | String | "Ajustes" | Tituto del UI |
| 0x03 | Cantidad de Elementos | unsigned byte | 4 | Cantidad de Elementos a mostrar |
|  | Elementos | UI Elements[] | UI Elements[...] | Elementos a mostrar |

# UI Elements

## Button Element

# UI Responses