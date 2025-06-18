# Moneda - currencies
### Columnas
- id **number** identificador unico de moneda
- name **string** nombre de la moneda
- short **string** abreviacion de la moneda

# Unidad medida - measurment_units
### Columnas
- id **number** identificador unico de moneda
- name **string** unidad de medida

# Codigo Facturas - item_invoice_codes
### Columnas
- id **number** identificador unico de codigo de item de factura
- name **string** item de factura


# Detraccion - detractions
### Columnas
- id **number** identificador unico de tipo de detraccion
- name **string** Descripcion del tipo de detraccion
- number **number** % de detraccion aplicable segun el tipo

# Seriales - serial
- id **number** identificador unico de la serial de comprobantes
- name **string** descripcion de la serie de comprobantes

# Ventas - invoices
### Columnas
- id **number** Identificador unico de factura de venta
- number **number** Numero de la factura
- date **bigInt** Fecha de emision de la factura en segundos (millis/1000)
- credit **number** dias de credito de la factura
- typePay **bool** true para contado y false para credito (escrito en la seccion tipo de transaccion)
- obs **string** Observaciones en la factura
- total **number** total del monto facturado sin igv
- igv **number** % de igv de la factura
- paid **bool** indica si la factura esta pagada o no
- payDate **bigInt** fecha de pago en segundos (millis/1000)
- payOperation **number** numero de operacion del pago de la factura
- pdfIdDrive **string** id del archivo pdf en google drive
- xmlIdDrive **string** id del archivo xml en google drive
- cdrIdDrive **string** id del archivo cdr en google drive
- comment **string** comentarios adicionales de la factura (control interno)

- serialId ***relation*** uno a muchos (que numero de serie es la factura)
- detractionId **relation** uno a muchos (que tipo de detraccion es)
- currencyId **relation** uno a muchos (que tipo de moneda es)
- entityId ***relation*** uno a muchos (a que cliente pertenece) 
- companyId ***relation*** uno a muchos (que empresa abm-mega emitio la factura)
- serviceId ***relation*** muchos a muchos (a que OTs pertenece la factura)


### Funciones
- En las observaciones se debe agregar automaticamente el numero de guias de recojo, entrega, orden de compra y conformidad de servicio si es que estan existen al momento de generar la factura
- Si la 


# Items Ventas - invoice_items
### Columnas
- id **number** identificador unico del item de factura
- order **number** numero de orden de aparicion en la factura
- quantity **number** cantidad del item
- description **string** descripcion del item 
- unitPrice **number** valor unitario del item

- invoiceId ***relation*** uno a muchos (a que factura pertenece el item) 
- measurementUnitId ***relation*** uno a muchos (que unidad de medida se utiliza)
- itemInvoiceCodeId ***relation*** uno a muchos (que codigo de item de factura es)