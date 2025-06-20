# Notas de Credito - credit_notes
### Columnas
- id **number** identificador unico de la nota de credito
- number **number** numero de nota de credito
- reason **string** motivo de anulacion

- serialId ***relation*** uno a muchos (que numero de serie utiliza)
- invoiceId ***relation*** uno a uno (que factura está anulando)
- invoiceItemId ***relation*** muchos a muchos (que items de la factura se están anulando)