
# Items Ventas - invoice_items
### Columnas
- id **number** identificador unico del item de factura
- order **number** numero de orden de aparicion en la factura
- quantity **number** cantidad del item
- description **string** descripcion del item 
- unitPrice **number** valor unitario del item

- invoiceId ***relation_210*** uno a muchos (a que factura pertenece el item) 
- measurementUnitId ***relation_108*** uno a muchos (que unidad de medida se utiliza)
- itemInvoiceCodeId ***relation_113*** uno a muchos (que codigo de item de factura es)