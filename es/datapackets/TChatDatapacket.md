# Chat Datapacket
Este es para ambos lados (Servidor y Cliente), se usa para mandar mensajes en el juego.

En caso del servidor al enviar el cliente muestra el mensaje en el cajón de chat.

En caso del cliente solamente lo envía al servidor, el servidor debe responder con el mensaje formateado por ejemplo:
```
Max: Hola!
```


| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x1D | Texto | String | "Hola!" | Mensaje a enviar/mostrar |
