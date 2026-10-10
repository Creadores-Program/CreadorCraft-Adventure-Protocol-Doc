# WakeUp
Este se usa para despertar el backend para iniciar sesión, se usa justo al entrar a la interfaz de inicio de sesión.

Se hace una petición POST en `application/octet-stream` a `` con un byte 0x00 y se ignora la respuesta (puede ser error).