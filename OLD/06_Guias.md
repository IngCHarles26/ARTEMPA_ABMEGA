# Motivos Traslado - transfer_reasons
### Columnas
- id **number** identificador unico del motivo de traslado
- name **string** nombre del motivo de traslado

# Conductores - drivers
### Columnas
- id **number** identificador unico del chofer
- name **string** nombre del conductor
- licence **string** numero de licencia de conducir 
- pdfIdDrive **string** id del archivo pdf de la licencia
- extern **bool** true si es un chofer externo a abm o megaman


# Vehiculos - cars
### Columnas
- id **number** identificador unico del vehiculo
- name **string** nombre del vehiculo
- plate **string** numero de placa del vehiculo
- soatExp **bigInt** fecha de vencimiento de soat
- techRevExp **bigInt** fecha de vencimiento de revision tecnica
- soatPdfIdDrive **string** id del archivo pdf del soat
- revPdfIdDrive **string** id del archivo pdf de la revision tecnica


# Codigo Guias - item_delivery_note_codes
### Columnas
- id **number** identificador unico de codigo
- name **string** nombre de el codigo del equipo a trasladar

# Guias - delivery_notes
### Columnas
- id **number** identificador unico de guias
- number **number** numero de guia de remision
- pdfIdDrive ***string** id del archivo pdf en drive
- issueDate **bigInt** Fecha de emision de la guia en segundos (millis/1000)
- transferDate **bigInt** Fecha de traslado de la guia en segundos (millis/1000)
- transferDescription **string** descripcion del traslado (en caso se selecciona otros en los motivos)
- privateTransport **bool** true si el transporte es privado
- kg **number** peso total de la mercancia transportada
- obs **string** observaciones de la factura

- transfeReasonId ***relation*** uno a muchos (cual es el motivo del trasladp)
- entityId ***relation*** uno a muchos (a que cliente se le esta entregando )
- serviceId ***relation*** muchos a muchos (que ots se estan entregando con la guia)
- serialId ***relation*** uno a muchos (a que numero de serie pertenece)
- companyId ***relation*** uno a muchos (que empresa esta entregando el servicio abm-mega)


### Consideraciones
- Si el transporte es privado, se agregan los datos de vehiculos y choferes


# Elementos de guia - delivery_note_items
### Columnas
- id **number** identificador unico del item de guia
- order **number** numero de orden de aparicion en la guia
- quantity **number** cantidad de items
- description **string** descripcion de los items

- deliveryNoteId **relation** uno a muchos (a que guia pertenece el item)
- measurementUnitId **relation** uno a muchos (cual es la unidad de medida del item)
- itemDeliveryNoteCodeId **relation** uno a muchos (codigo del tipo de elemento a transportar)