# Sub Servicios - sub_services
### Columnas
- id **number** identificador unico del sub servicio
- subOt **number** numero de sub ot del servicio
- power **number** potencia del equipo (hp, kw, )
- plateData **string** descripcion de datos de placa
- price **number** costo sin igv por el sub servicio
- clientComments **string** indicaciones del cliente para con este sub servicio (control interno) 
- startDate **bigInt** fecha de inicio de servicio
- finishDate **bigInt** fecha de finalizacion del servicio (si esta vacia se considera aun)

- serviceId ***relation_207*** uno a muchos (a que OT pertenece el sub servicio)
- serviceTypeId ***relation_102*** uno a muchos (que tipo de servicio)
- machineBrandId ***relation_107*** uno a muchos (que marca es el equipo)
- machineTypeId ***relation_106*** uno a muchos (que tipo de equipo es)
- powerUnityId ***relation_003*** uno a muchos (que unidad de medida es la potencia del equipo)
- supplyTypeId ***relation_004*** uno a muchos (tipo de alimentacion del equipo)
- userId ***relation_200*** uno a muchos (tecnico a cargo del sub servicio)
- schemeId ***relation_115*** uno a muchos (esquema de conexion)


## Funciones