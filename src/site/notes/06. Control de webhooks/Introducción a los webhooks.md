---
{"dg-publish":true,"permalink":"/06-control-de-webhooks/introduccion-a-los-webhooks/","dgPassFrontmatter":true}
---


Los **webhooks de Iris** permiten notificar a sistemas externos sobre eventos relevantes que ocurren dentro de la plataforma, en tiempo real.  Gracias a ellos, puedes mantener sincronizados otros sistemas, desencadenar flujos automáticos, registrar eventos o auditar la actividad del usuario sin necesidad de hacer consultas activas a Iris.

### ¿Cómo funcionan?

Cuando se produce un evento en Iris (como la creación de una interacción, un cambio de estado, o la recepción de una respuesta del usuario), se envía una **petición HTTP POST** al endpoint configurado por el cliente.

Esta petición incluye un cuerpo JSON con información estructurada del evento y su contexto (tipo, fecha, payload, etc.).

#### Ejemplo de llamada webhook

```json
{
  "Event": "INTERACTION_OUT_CREATED_EVT",
  "Created": "2025-06-25T12:09:31.8490000Z",
  "Payload": {
    "...": "contenido relacionado con el evento"
  }
}
```

---

### 🧾 Eventos soportados

Iris emite diferentes tipos de eventos según el contexto. Algunos de los más habituales son:

| Evento                                  | Descripción                                                                 |
| --------------------------------------- | --------------------------------------------------------------------------- |
| [[06. Control de webhooks/Eventos/INTERACTION_IN_CREATED_EVT\|INTERACTION_IN_CREATED_EVT]]          | Un usuario final ha enviado una nueva interacción al sistema.               |
| [[06. Control de webhooks/Eventos/INTERACTION_OUT_CREATED_EVT\|INTERACTION_OUT_CREATED_EVT]]         | Se ha creado una interacción de salida (mensaje generado por Iris).         |
| [[06. Control de webhooks/Eventos/INTERACTION_STATUSCHANGED_EVT\|INTERACTION_STATUSCHANGED_EVT]]       | La interacción ha cambiado de estado (por ejemplo, de enviada a entregada). |
| [[06. Control de webhooks/Eventos/INTERACTION_CUSTOMSTATUSCHANGED_EVT\|INTERACTION_CUSTOMSTATUSCHANGED_EVT]] | Cambio en un subestado (customStatus) específico del proveedor.             |

Puedes consultar el contenido exacto del `Payload` en la sección [[07. Integraciones/Introducción al envío de interacciones#Response\|Introducción al envío de interacciones#Response]].

### ⚙️ Configuración

Los webhooks se configuran por por integración, y pueden incluir opciones como:

- URL del endpoint receptor.
- Filtros por tipo de evento.


Para configurar los webhooks de tu tenant, contacta con tu administrador de la plataforma o revisa la sección [[Configuración de Webhooks\|Configuración de Webhooks]] si está habilitada en tu entorno.