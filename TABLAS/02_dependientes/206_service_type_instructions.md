
# Descripcion del tipo de servicio - service_type_instructions
### Columnas
- id **number** identificador de la descripcion del tipo de servicio
- order **number** numero de orden del proceso
- name **string** descripcion paso del procedimiento (desmontaje, barnizado, tratamiento termico al horno)

- serviceTypeId ***relation_102*** uno a muchos (a que tipo de servicio corresponde la descripcion)