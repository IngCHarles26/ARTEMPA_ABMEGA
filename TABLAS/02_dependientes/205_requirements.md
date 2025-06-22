# Requerimientos - requirements
### Columnas
- id **number** identificador unico del tipo de requerimiento
- name **strung** descripcion del requerimiento de la compra
- quantity **number** cantidad solicitada
- done **bool** indica si ya fue comprado\
- date **bigInt** fecha en segundos en la que se solicito la compra
- buyDate **bigInt** fecha en segundos en la que se realizo la compra

- userId ***relation_200*** uno a muchos (que usuario esta solicitando la compra)
- itemInvoiceCodeId ***relation_113*** uno a muchos (repuesto, insumo, servicio)
- measurementUnityId ***relation_108*** uno a muchos (que unidad de medida de la cantidad solicitada)

