# Login
Este se usa para obtener un token de inicio de sesión para generar Tickets de cuenta.

Usa una petición a: ``

Tipo POST en `application/octet-stream`

Escribe el código de verificación de 6 dígitos en bytes que se obtiene de la forma de inicio de sesión.

La respuesta es unsigned byte para la longitud del nombre del jugador en bytes, nombre del jugador en bytes, y un token de 32 bytes (**NUNCA DEBE COMPARTIRSE EL TOKEN**).