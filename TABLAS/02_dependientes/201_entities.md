# Entidades - entities
### Columnas
- id **number** identificador unico del cliente
- ruc **number** RUC del cliente (id del cliente)
- name **string** Razon social del cliente
- shortName **string** razon social acortada del cliente
- address **string** Direccion de facturacion del cliente
- folderDriveId **string** 

- companyId  ***relation_101*** muchos a muchos con Empresas (abm, mega, etc)

### Consideraciones
- Se guardan proveedores y clientes, si no tiene relacion es un proveedor
- Se va 