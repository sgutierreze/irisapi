---
{"dg-publish":true,"permalink":"/05-interacciones/estados-de-las-interacciones/","dgPassFrontmatter":true}
---


Cada interacción en Iris atraviesa una serie de estados a lo largo de su ciclo de vida. Estos estados permiten conocer en qué punto del proceso se encuentra una interacción, desde que se registra hasta que se completa, o si se ha producido algún error.

El campo `status` refleja este estado general y es común a todos los canales. A través de él, es posible hacer seguimiento operativo, detectar fallos, o controlar flujos automatizados según el avance de cada interacción.

A continuación, se describen los posibles valores que puede tomar este campo:

| Estado                   | Descripción                                                                                                                              |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `VALIDATION_PENDING`     | La interacción ha sido registrada y está pendiente de validación. Todavía no ha comenzado el proceso de envío.                           |
| `VALIDATION_ERROR`       | La validación de la interacción ha fallado. Puede deberse a errores en el contenido, destinos inválidos o problemas en la configuración. |
| `DISPATCH_PENDING`       | La interacción ha sido validada correctamente y está encolada para su envío al proveedor correspondiente.                                |
| `SENT`                   | La interacción ha sido enviada al proveedor. No implica necesariamente que haya sido entregada al usuario final.                         |
| `PROVIDER_SENDING_ERROR` | Se produjo un error al intentar enviar la interacción al proveedor (por ejemplo, error de red o rechazo del proveedor).                  |
| `PROCESS_ERROR`          | Ocurrió un error interno durante el procesamiento de la interacción. Normalmente el proveedor devolvió error.                            |
| `COMPLETED`              | La interacción ha sido completamente procesada y finalizada. Dependiendo del canal, puede implicar confirmación de entrega o lectura.    |
| `RECEIVED`               | En interacciones de entrada, indica que el mensaje fue recibido desde el canal externo y registrado correctamente en el sistema.         |
