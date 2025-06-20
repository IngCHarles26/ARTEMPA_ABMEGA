# Notas de Credito - credit_notes
### Columnas
- id **number** identificador unico de la nota de credito
- number **number** numero de nota de credito
- reason **string** motivo de anulacion

- serialId ***relation_103*** uno a muchos (que numero de serie utiliza)
- invoiceId ***relation_210*** uno a uno (que factura está anulando)
- invoiceItemId ***relation_211*** muchos a muchos (que items de la factura se están anulando)