# Unidades de potencia - power_unities
### Columnas
- id **number** identificador unico de la unidad de medida
- name **string** unidad de medida (cv, hp, kva, va, kw, w)
- factor **number** factor de convercion hacia hp

# Tipos de maquina - machine_types
### Columnas
- id **number** identificador unico de los tipos de maquinas
- name **string** tipo de equipos (bomba, compresor, motoreductor, etc etc)

# Marcas de maquinas - machine_brands
### Columnas 
- id **number** identificador unico de las marcas de maquinas
- name **string** marca de la maquina (siemens, aeg, weg, delcrosa, etc, etc)

# Servicios - services
## Columnas
- id: **number** identificador unico para el servicio
- notificationDate **bigInt** fecha en segundos de la solicitud de servicio
- receptionDate **bigInt** fecha en segundos de recepcion del servicio (si esta vacio es solo presupuesto)
- receptionDocument **string** numero de documento de recepcion
- description **string** descripcion general del alcance del servicio
- price **number** monto total del servicio
- serviceOrder **string** orden de compra del servicio
- serviceCompliance **string** conformidad del servicio
- dispatchDate **bigInt** fecha en segundos de despacho del servicio (en caso que no se entregue con una guia de remision)
- budgetVersions **number** numero de versiones de presupuestos
- 
 
- companyId ***relation*** uno a muchos (que empresa realiza el servicio abm o mega)
- entityId ***relation*** uno a muchos (cliente se realiza el servicio)
- entityContactId ***relation*** uno a muchos (persona de contacto del cliente)
- userId ***relation*** uno a muchos (tecnico a cargo del servicio)
- invoiceId ***relation*** muchos a muchos (cual es la factura del servicio)
- deliveryNoteId ***relation*** muchos a muchos (cual es la guia de despacho de los servicios)


## Funciones



# Sub Servicios - sub_services
## Columnas
- id **number**

## Funciones



# Items Sub Servicios - sub_service_items
## Columnas
- id **number** Identificador unico del item del presupuesto
- order **number** Numero de orden de apareicion en el presupuesto
- quantity **number** Cantidad de items del presupuesto
- description **number** Descripcion del presupuesto
- price **number** Precio unbitario del presupuesto
- subServiceID **relation** Relacion con SUB OT


## Funciones
- 

# Tipos Servicios - service_types
### Columnas
- id **number**
- name **string** Descripcion del servicio (rebobinado motor, rebobinado transformador, rebobinado compresor, mantenimiento, fabricacion, balanceo, venta, alineamiento, recladmo, parada, etc)

## Funciones
-

# Descripcion del tipo de servicio
### Columnas
- id **number** identificador de la descripcion del tipo de servicio
- order **number** numero de orden del proceso
- name **string** descripcion paso del procedimiento (desmontaje, barnizado, tratamiento termico al horno)

- serviceTypeId ***relation*** uno a muchos (a que tipo de servicio corresponde la descripcion)