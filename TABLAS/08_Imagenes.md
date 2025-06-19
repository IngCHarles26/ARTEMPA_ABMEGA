# Tipos de Imagenes - image_types
### Columnas
- id **number** identificador unico de tipo de imagen
- name **string** descripcion del tipo de imagen (informe, esquema, cuaderno)


# Imagenes - images
### Columnas
- id **number** identificador unico de imagen
- name **string** descripcion de la imagen
- idDrive **string** id del archivo del google drive

- imageTypeId ***relation*** uno a muchos (que tipo de imagen es)
- subServiceId  ***relation*** uno a muchos (a que sub OT pertenece la imagen)

