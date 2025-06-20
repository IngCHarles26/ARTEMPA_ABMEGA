
# Elementos de guia - delivery_note_items
### Columnas
- id **number** identificador unico del item de guia
- order **number** numero de orden de aparicion en la guia
- quantity **number** cantidad de items
- description **string** descripcion de los items

- deliveryNoteId **relation_212** uno a muchos (a que guia pertenece el item)
- measurementUnitId **relation_108** uno a muchos (cual es la unidad de medida del item)
- itemDeliveryNoteCodeId **relation_114** uno a muchos (codigo del tipo de elemento a transportar)