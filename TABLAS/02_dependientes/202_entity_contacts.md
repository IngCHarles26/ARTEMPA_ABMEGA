# Contactos de Empresas - entity_contacts
### Columnas
- id **number** Identificador unico del contacto
- name **string** Nombre y apellido del contacto
- email **string** Correo del cliente
- phone **number** Numero de contacto 
- rol **string** Cargo en la empresa del cliente
- toSendInvoice **bool** Contacto a enviar facturas, guias y notas de credito
- toSendPres **bool** Contacto a enviar presupuestos

- entityId ***relation_201*** uno a muchos (a que entidad pertenece el contacto)