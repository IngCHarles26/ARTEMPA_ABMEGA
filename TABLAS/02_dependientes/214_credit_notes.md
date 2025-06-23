# Notas de Credito - credit_notes
### Columnas
- id **number** identificador unico de la nota de credito
- number **number** numero de nota de credito
- reason **string** motivo de anulacion
- pdfDriveId **string** id del archivo pdf guardado en google drive
- date **bigInt** fecha de emision de la nota de credito
- 

- serialId ***relation_103*** uno a muchos (que numero de serie utiliza)
- invoiceId ***relation_210*** uno a uno (que factura está anulando)
- invoiceItemId ***relation_211*** muchos a muchos (que items de la factura se están anulando)


### Consideraciones
- Los datos (moneda,) los va a sacar de la relacion con la factura 
```javascript
{
    "documento": "nota_credito",
    "serie": "F001",
    "numero": 1,
    "fecha_de_emision": "2024-09-06",
    "moneda": "PEN",
    "cliente_tipo_de_documento": "6",
    "cliente_numero_de_documento": "20548042535",
    "cliente_denominacion": "INVERSIONES SERVIS S.A.C",
    "cliente_direccion": "AV. DEL PARQUE NORTE NRO. 1126 LIMA - LIMA - SAN BORJA",
    "nota_credito_codigo_tipo": "09",
    "nota_credito_motivo": "Disminución en el valor",
    "documento_afectado": {
        "documento": "factura",
        "serie": "F001",
        "numero": 10
    },
    "items": [
        {
            "unidad_de_medida": "ZZ",
            "descripcion": "PRODUCTO 1 - DESCUENTO POR PROMOCIÓN",
            "cantidad": "1",
            "valor_unitario": "84.75",
            "precio_unitario": "100",
            "porcentaje_igv": "18",
            "codigo_tipo_afectacion_igv": "10"
        }
    ],
    "total_gravada": "84.75",
    "total_igv": "15.25",
    "total": "100"
}
```