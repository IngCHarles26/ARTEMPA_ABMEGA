# Tipos repuesto - spare_types
### Columnas
- id **number** identificador unico del tipo de activo (rodamiento, sello, reten, cable vulcanizado, etc)

# Marcas repuesto - spare_brands
### Columnas
- id **number** identificador unico de marca
- name **string** nombre de la marca

# Inventario - inventory
### Columnas
- id **number** identificador unico del item de inventario
- code **string** nombre del elemento del inventario (6204, 6205)
- description **string** descripcion del elemento del inventario
- quantity **number** cantidad en posecion
- buyPrice **number** precion en soles de compra (el mas alto)
- salePrice **number** precion en soles de venta (el mas alto)

- spareTypeId ***relation*** uno a muchos (que tipo de repuesto es)
- spareBrandId ***relation*** uno a muchos (de que marca es el repuesto)

# Historial consumos - usage_history
### Columnas
- id **number** identificador unico del historial
- quantity **number** cantidad de repuestos retirados
- lastStock **number** stock de recepcion antes del consumo

- subServiceId ***relation*** uno a muchos (en que sub servicio se uso el repuesto)
- userId ***relation*** uno a muchos (que usuario retiro el repuesto)
- inventoryId ***relation*** uno a muchos (que tipo de repuesto se consumio)