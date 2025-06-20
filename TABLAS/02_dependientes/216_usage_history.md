# Historial consumos - usage_history
### Columnas
- id **number** identificador unico del historial
- quantity **number** cantidad de repuestos retirados
- lastStock **number** stock de recepcion antes del consumo

- subServiceId ***relation_208*** uno a muchos (en que sub servicio se uso el repuesto)
- userId ***relation_100*** uno a muchos (que usuario retiro el repuesto)
- inventoryId ***relation_215*** uno a muchos (que tipo de repuesto se consumio)