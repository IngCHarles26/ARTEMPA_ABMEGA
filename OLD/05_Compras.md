# Compras - purchases
### Columnas
- id **number** identificador unico de compra
- date **bigInt** fecha de emision de la facrtua en segundos (millis/1000)
- number **number** numero de la factura de compra
- total **number** total del monto facturado
- paid **bool** la compra esta pagada o no
- typePaid **bool** true para efectivo y false para transferencia
- payOperation **number** numero de operacion de pago (si es por transferencia)
- comments **string** comentarios de la factura (control iterno)

- serialId ***relation*** serie de la factura de compra
- entityId ***relation*** uno a muchos (a que proveedor pertenece la compra)
- companyId ***relation*** uno a muchos (que empresa hizo la compra abm o mega)