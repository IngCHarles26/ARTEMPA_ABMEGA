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
- pdfDriveId **string** id del archivo pdf en google drive
- xmlDriveId **string** id del archivo xml en google drive
- cdrDriveId **string** id del archivo cdr en google drive
- hash **string** hash de la factura retorno de la api de facturacion
- xmlLink **string** enlace del xml de la api de facturacion
- xmlCdr **string** enlace del cdre de la api de facturacion
- comment **string** comentarios adicionales de la factura (control interno)

- serialId ***relation_103*** uno a muchos (que numero de serie es la factura)
- detractionId **relation_111** uno a muchos (que tipo de detraccion es)
- currencyId ***relation_001*** uno a muchos (que tipo de moneda es)
- entityId ***relation_201*** uno a muchos (a que cliente pertenece) 
- companyId ***relation_101*** uno a muchos (que empresa abm-mega emitio la factura)
- serviceId ***relation_207*** muchos a muchos (a que OTs pertenece la factura)


### Funciones
- En las observaciones se debe agregar automaticamente el numero de guias de recojo, entrega, orden de compra y conformidad de servicio si es que estan existen al momento de generar la factura
- Si la 