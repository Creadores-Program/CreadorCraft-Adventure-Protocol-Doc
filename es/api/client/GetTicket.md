# GetTicket
Este se usa para generar tickets para entrar a servidores de 6 bytes de unico uso y solo valido 10 segundos se hace justo antes de conectar a un servidor.

Usa una petición a: ``

Tipo POST en `application/octet-stream`

Escribe el token de 32 bytes de la cuenta y la longitud de direccion del servidor a entrar sin protocolo (wss://) y el string en bytes.

La respuesta serán 6 bytes que son el ticket para usar en el Login Datapacket.