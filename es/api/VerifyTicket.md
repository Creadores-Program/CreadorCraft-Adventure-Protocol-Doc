# Verify Ticket
Este se usa para verificar el ticket del jugador y saber que no es invalido

Usa una petición a: ``

Tipo POST en `application/octet-stream`

Escribe el Ticket, longitud de tu dirección de tu servidor en unsigned byte y la dirección de tu servidor en bytes.

Si la respuesta es 200 OK
Te retornará la información del jugador en `application/octet-stream`

Lee un Long para el ID de discord, unsigned byte para la longitud del nombre, lee los bytes de la longitud para el Nombre y convierte a String.

El ticket es válido solo una vez y solo por 12 segundos.
