# Entidades - entities
### Columnas
- id **number** identificador unico del cliente
- ruc **number** RUC del cliente (id del cliente)
- name **string** Razon social del cliente
- shortName **string** razon social acortada del cliente
- address **string** Direccion de facturacion del cliente
- folderDriveId **string** 

- companyId ***relation*** muchos a muchos con Empresas (abm, mega, etc)

### Consideraciones
- Se guardan proveedores y clientes, si no tiene relacion es un proveedor
- Se va 

# Contactos de Empresas - entity_contacts
### Columnas
- id **number** Identificador unico del contacto
- name **string** Nombre y apellido del contacto
- email **string** Correo del cliente
- phone **number** Numero de contacto 
- rol **string** Cargo en la empresa del cliente
- toSendInvoice **bool** Contacto a enviar facturas, guias y notas de credito
- toSendPres **bool** Contacto a enviar presupuestos

- entityId ***relation*** uno a muchos (a que entidad pertenece el contacto)