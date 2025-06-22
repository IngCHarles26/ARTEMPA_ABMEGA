# Requerimientos de sub ot - operator_sub_service_requirements
### Columnas
- id **number** identificador unico del requerimiento del operador
- order **number** numero de orden de aparicion
- quantity **number** cantidad solicitada
- comments **string** detalles de lo solicitado

- subServiceId ***relation_208*** uno a muchos (requerimientos del encargado)