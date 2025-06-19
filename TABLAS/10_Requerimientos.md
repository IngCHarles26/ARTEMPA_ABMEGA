# Tipos de requerimientos - requirement_types

### Columnas
- id **number** identificador unico del tipo de requerimiento
- name **strung** descripcion del requerimiento de la compra
- quantity **number** cantidad solicitada
- done **bool** indica si ya fue comprado\
- date **bigInt** fecha en segundos en la que se solicito la compra
- buyDate **bigInt** fecha en segundos en la que se realizo la compra

- userId ***relation*** uno a muchos (que usuario esta solicitando la compra)
- spareTypeId ***relation*** uno a muchos (que tipo de repuesto es)
- measurementUnityId ***relation*** uno a muchos (que unidad de medida de la cantidad solicitada)