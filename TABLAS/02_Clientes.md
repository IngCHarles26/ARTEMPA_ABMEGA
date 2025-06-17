# Clientes
## Columnas
- ruc: **number** RUC del cliente (id del cliente)
- name: **string** Razon social del cliente
- address: **string** Direccion de facturacion del cliente
- isABM: **bool** Cliente habilitado para ABM
- isMega: **bool** Cliente habilitado para Megaman

# Contactos de cliente
## Columnas
- id: **number** Identificador unico del contacto
- name: **string** Nombre y apellido del contacto
- email: **string** Correo del cliente
- phone: **number** Numero de contacto 
- rol: **string** Cargo en la empresa del cliente
- toSendInvoice: **bool** Contacto a enviar facturas, guias y notas de credito
- toSendPres: **bool** Contacto a enviar presupuestos
- clientRUC: **relation** Relacion uno a muchos (varios contactos a un cliente)
