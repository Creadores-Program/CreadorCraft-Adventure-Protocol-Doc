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

Se escribe el UI ID en byte igual como si fuera un datapacket seguido de sus datos.

## ModalUI
Este se usa para confirmaciones o por ejemplo pantalla de muerte.

| **UI ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Titulo | String | "Comprar" | Titulo del UI |
| 0x01 | Contenido | String | "Seguro que Quieres Comprar?" | Contenido del UI |
|  | Botón Negativo | String | "No" | Contenido del Botón Negativo |
|  | Botón Positivo | String | "Si" | Contenido del Botón Positivo |

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

Si no se proporcina ningún botón se añade automaticamente el botón Enviar

| **UI ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Titulo | String | "Ajustes" | Tituto del UI |
| 0x03 | Cantidad de Elementos | unsigned byte | 4 | Cantidad de Elementos a mostrar |
|  | Elementos | UI Elements[] | UI Elements[...] | Elementos a mostrar |

# UI Elements

Se escribe el Element ID en byte igual como si fuera un datapacket seguido de sus datos.

## Button Element
Este elemento es un botón presionable, en SimpleUI se ignora el Element ID ya que en el solo accepta este elemento

| **Element ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x01 | ID de Imagen Asset | unsigned short | 6 | La imagén del botón por id de asset tipo Bloque usa 0 para ninguna |
|  | Contenido | String | "El Mejor" | Texto del Botón |

## Text Element
Este elemento añade texto al UI.

| **Element ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x02 | Texto | String | "Hola Buenas!" | Texto a añadir |

## Image Element
Este elemento añade una imagen de assets tipo Bloque al UI.

| **Element ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x03 | ID de Imagen Asset | unsigned short | 6 | La imagén del botón por id de asset tipo Bloque |

## Check Element
Este elemento tiene varias opciones para elegir, se puede hacer unico o varias opciones.

| **Element ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Solo una opción | boolean | true | Puede o no el jugador seleccionar más de una opción |
| 0x04 | Cantidad de Opciones | unsigned byte | 4 | Cantidad de opciones a elegir |
|  | Opciones | String[] | String[...] | Opciones a mostrar |
|  | Opción por defecto | unsigned byte | 1 | la opción por defecto en index, este solamente se añade si es de una sola opción |

## Input Element
Este elemento añade una entrada de texto.

| **Element ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Texto | String | "Nombre" | Texto antes de la entrada |
| 0x05 | Placeholder | String | "Maxi" | Texto si no hay nada en la entrada |
|  | Texto por defecto | String | "Pepe" | Texto por defecto en la entrada |

# UI Responses
Se escribe el UI Response ID en byte igual como si fuera un datapacket seguido de sus datos.

## ModalUI Response
Esta respuesta se usa para saber si el jugador acepto o no el UIModal

| **UI Response ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x01 | Respuesta | boolean | true | Si la respuesta fue positiva o no |

## SimpleUI Response
Esta respuesta se usa para saber que Botón presionó el jugador en SimpleUI

| **UI Response ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x02 | Botón | String | "Comprar" | Texto del botón presionado (Close significa que no eligio ningunó) |

## CustomUI Response
Esta respuesta se usa para la respuesta del CustomUI.

| **UI Response ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
|  | Cantidad de Check's | unsigned byte | 4 | Cantidad de elementos Check con respuesta |
|  | Respuestas Check | Check Response[] | Check Response[...] | Respuestas de Check Element's |
| 0x03 | Cantidad de Input's | unsigned byte | 3 | Cantidad de elementos Input con respuesta |
|  | Respuestas Input | Input Response[] | Input Response[...] | Respuestas de Input Element's |
|  | Botón Presionado | String | "Enviar" | Texto del Botón Presionado |

### Elements Response's
Este no necesita id porque CustomUI Response separa los elementos

#### Input Response
Este se usa para dar una respuesta de lo que escribio el jugador.

| **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- |
| Texto | String | "Nombre" | Texto antes de la entrada del elemento Input |
| Texto del Input | String | "Maxi" | Texto que escribio el jugador en la entrada |

#### Check Response
Este se usa para dar una respuesta de lo que eligio el jugador.

| **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- |
| Cantidad | unsigned byte | 3 | Cantidad de opciones que eligio el jugador (si es de una sola opción simpre es 1) |
| Opciones | String[] | String[...] | Opciones que eligio el jugador (si es de una sola opción solo es un String) |