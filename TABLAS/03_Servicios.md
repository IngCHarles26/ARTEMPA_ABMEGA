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
### Columnas
- id **number** identificador unico para el servicio
- ot **number** numero de OT del servicio
- notificationDate **bigInt** fecha en segundos de la solicitud de servicio
- receptionDate **bigInt** fecha en segundos de recepcion del servicio (si esta vacio es solo presupuesto)
- receptionDocument **string** numero de documento de recepcion
- description **string** descripcion general del alcance del servicio
- price **number** monto total del servicio sin igv
- serviceOrder **string** orden de compra del servicio
- serviceCompliance **string** conformidad del servicio
- dispatchDate **bigInt** fecha en segundos de despacho del servicio (en caso que no se entregue con una guia de remision)
- proformVersions **number** numero de versiones del presupuesto
- proformClientDescription **string** descripcion del cliente en la guia de remision o informacion de recepcion
- proformDate **bigInt** fecha en segudos de la emision del presupuesto
- proformDaysCredit **number** dias de credito por el servicio
- proformDaysDelivery **number** dias habiles de entrega del servicio
- proformDaysWarrantyl **number** dias de garantia por el servicio
- proformDaysValidate **number** dias de validez del presupuesto
- proformPlaceDispatch **string** lugar de entrega del servicio
 
- companyId ***relation*** uno a muchos (que empresa realiza el servicio abm o mega)
- entityId ***relation*** uno a muchos (cliente se realiza el servicio)
- entityContactId ***relation*** uno a muchos (persona de contacto del cliente)
- userId ***relation*** uno a muchos (tecnico a cargo del servicio)
- invoiceId ***relation*** muchos a muchos (cual es la factura del servicio)
- deliveryNoteId ***relation*** muchos a muchos (cual es la guia de despacho de los servicios)


### Funciones

### Consideraciones
- El titulo de presupuesto (1961-05ABM25) se genera con la ot y la fecha de notificacion
- El tipo de servicio va a ser independiente por cada sub OT
- La descripcion es la misma que la que se va a colocar en el presupuesto
- Si los dias de credito son 0 se escribe contado



# Sub Servicios - sub_services
### Columnas
- id **number** identificador unico del sub servicio
- subOt **number** numero de sub ot del servicio
- power **number** potencia del equipo (hp, kw, )
- plateData **string** descripcion de datos de placa
- price **number** costo sin igv por el sub servicio
- clientComments **string** indicaciones del cliente para con este sub servicio (control interno) 

- serviceId ***relation*** uno a muchos (a que OT pertenece el sub servicio)
- serviceTypeId ***relation*** uno a muchos (que tipo de servicio)
- machineBrandId ***relation*** uno a muchos (que marca es el equipo)
- machineTypeId ***relation*** uno a muchos (que tipo de equipo es)
- powerUnityId ***relation*** uno a muchos (que unidad de medida es la potencia del equipo)
- supplyTypeId ***relation*** uno a muchos (tipo de alimentacion del equipo)

## Funciones



# Items Sub Servicios - sub_service_items
## Columnas
- id **number** Identificador unico del item del presupuesto
- order **number** Numero de orden de aparicion en el presupuesto
- quantity **number** Cantidad de items del presupuesto
- description **number** Descripcion del item del presupuesto
- price **number** Precio unitario del item del presupuesto

- subServiceId **relation** Relacion con SUB OT


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

# Tipos de alimentacion - supply_types
### Columnas
- id **number** identificador unico del tipo de alimentacion
- name **string** descripcion del tipo de alimentacion (mono, trifa, dc, no aplica, etc, etc)

