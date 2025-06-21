# Guias - delivery_notes
### Columnas
- id **number** identificador unico de guias
- number **number** numero de guia de remision
- issueDate **bigInt** Fecha de emision de la guia en segundos (millis/1000)
- transferDate **bigInt** Fecha de traslado de la guia en segundos (millis/1000)
- transferDescription **string** descripcion del traslado (en caso se selecciona otros en los motivos)
- privateTransport **bool** true si el transporte es privado
- kg **number** peso total de la mercancia transportada
- obs **string** observaciones de la factura
- pdfDriveId ***string** id del archivo pdf en drive

- transfeReasonId ***relation_112*** uno a muchos (cual es el motivo del trasladp)
- entityId ***relation_201*** uno a muchos (a que cliente se le esta entregando )
- serviceId ***relation_207*** muchos a muchos (que ots se estan entregando con la guia)
- serialId ***relation_103*** uno a muchos (a que numero de serie pertenece)
- companyId ***relation_101*** uno a muchos (que empresa esta entregando el servicio abm-mega)


### Consideraciones
- Si el transporte es privado, se agregan los datos de vehiculos y choferes
