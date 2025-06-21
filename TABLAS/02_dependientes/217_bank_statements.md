# Estados de cuenta - bank_statements
### Columnas
- id **number** identificador unico del estado de cuenta
- month **number** mes del estado de cuenta
- year **string** año del estado de cuennta
- pdfDriveId **string** id del archivo pdf 

- companyId  ***relation_101*** uno a muchos (a que empresa pertenece el estado de cuenta abm, mega, etc)

### Consideraciones
- Se guardan proveedores y clientes, si no tiene relacion es un proveedor
- Se va 