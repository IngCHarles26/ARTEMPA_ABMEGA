# Servicios - services
### Columnas
- id **number** identificador unico para el servicio
- ot **number** numero de OT del servicio
- notificationDate **bigInt** fecha en segundos de la solicitud de servicio
- receptionDate **bigInt** fecha en segundos de recepcion del servicio (si esta vacio es solo presupuesto)
- receptionDocument **string** numero de documento de recepcion
- description **string** descripcion general del alcance del servicio
- price **number** monto total del servicio sin igv
- serviceOrder **string** orden de compra del servicio
- serviceCompliance **string** conformidad del servicio
- dispatchDate **bigInt** fecha en segundos de despacho del servicio (en caso que no se entregue con una guia de remision)
- proformVersions **number** numero de versiones del presupuesto
- proformClientDescription **string** descripcion del cliente en la guia de remision o informacion de recepcion
- proformDate **bigInt** fecha en segudos de la emision del presupuesto
- proformDaysCredit **number** dias de credito por el servicio
- proformDaysDelivery **number** dias habiles de entrega del servicio
- proformDaysWarrantyl **number** dias de garantia por el servicio
- proformDaysValidate **number** dias de validez del presupuesto
- proformPlaceDispatch **string** lugar de entrega del servicio
 
- companyId ***relation_101*** uno a muchos (que empresa realiza el servicio abm o mega)
- entityId ***relation_201*** uno a muchos (cliente se realiza el servicio)
- entityContactId ***relation_202*** uno a muchos (persona de contacto del cliente)
- userId ***relation_100*** uno a muchos (tecnico a cargo del servicio)
- invoiceId ***relation_210*** muchos a muchos (cual es la factura del servicio)
- deliveryNoteId ***relation_212*** muchos a muchos (cual es la guia de despacho de los servicios)


### Funciones

### Consideraciones
- El titulo de presupuesto (1961-05ABM25) se genera con la ot y la fecha de notificacion
- El tipo de servicio va a ser independiente por cada sub OT
- La descripcion es la misma que la que se va a colocar en el presupuesto
- Si los dias de credito son 0 se escribe contado

