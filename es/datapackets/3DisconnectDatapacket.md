# Disconnect Datapacket
Este datapacket existe en ambos lados (Cliente y Servidor)

Este se envia si fallo en Login, No es compatible con el cliente, fue baneado, kickeado, el servidor está en lista blanca o cualquier otra razón

En caso del cliente si el cliente se desconecto o no es compatible con el servidor.

| **Packet ID** | **Nombre** | **Tipo** | **Ejemplo** | **Notas** |
| :--- | :--- | :--- | :--- | :--- |
| 0x03 | Razón | String | "Cliente Desactualizado" | Razón de Desconexión |
