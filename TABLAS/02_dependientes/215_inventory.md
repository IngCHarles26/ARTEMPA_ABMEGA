# Inventario - inventory
### Columnas
- id **number** identificador unico del item de inventario
- code **string** nombre del elemento del inventario (6204, 6205)
- description **string** descripcion del elemento del inventario
- quantity **number** cantidad en posecion
- buyPrice **number** precion en soles de compra (el mas alto)
- salePrice **number** precion en soles de venta (el mas alto)

- spareTypeId ***relation_110*** uno a muchos (que tipo de repuesto es)
- spareBrandId ***relation_109*** uno a muchos (de que marca es el repuesto)