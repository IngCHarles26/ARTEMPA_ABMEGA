# Guias - delivery_notes
### Columnas
- id **number** identificador unico de guias
- number **number** numero de guia de remision
- issueDate **bigInt** Fecha de emision de la guia en segundos (millis/1000)
- transferDate **bigInt** Fecha de traslado de la guia en segundos (millis/1000)
- transferDescription **string** descripcion del traslado (en caso se selecciona otros en los motivos)
- privateTransport **bool** true si el transporte es privado
- kg **number** peso total de la mercancia transportada
- obs **string** observaciones de la factura
- pdfDriveId ***string** id del archivo pdf en drive
- lumps **number** numero de bultos

- transfeReasonId ***relation_112*** uno a muchos (cual es el motivo del trasladp)
- entityId ***relation_201*** uno a muchos (a que cliente se le esta entregando )
- serviceId ***relation_207*** muchos a muchos (que ots se estan entregando con la guia)
- serialId ***relation_103*** uno a muchos (a que numero de serie pertenece)
- companyId ***relation_101*** uno a muchos (que empresa esta entregando el servicio abm-mega)
-              


### Consideraciones
- Si el transporte es privado, se agregan los datos de vehiculos y choferes
```javascript
  // modelo del body
{
    "documento": "guia_remision_remitente",
    "serie": "T001",
    "numero": 1,
    "fecha_de_emision": "2024-10-10",
    "hora_de_emision": "15:12",
    "modalidad_de_transporte": "02",
    "motivo_de_traslado": "01",
    "fecha_inicio_de_traslado": "2024-10-01",
    "punto_de_partida_ubigeo": "150110",
    "punto_de_partida_direccion": "CHACRA CERRO NRO. 103 INT. B-2",
    "punto_de_llegada_ubigeo": "150135",
    "punto_de_llegada_direccion": "AV. A MZ A LT. 12 URB. PRO INDUSTRIAL",
    "numero_de_bultos": 3,
    "peso_bruto_unidad_de_medida": "KGM",
    "peso_bruto_total": "3180.000",
    "observaciones": "Primera entrega",
    "cliente_tipo_de_documento": "6",
    "cliente_numero_de_documento": "20557361384",
    "cliente_denominacion": "EMPRESA DE SERVICIOS SAC",
    "cliente_direccion": "JR. OCOÑA 160 PISO 6 CERCADO DE LIMA"
    "transportista": {
        "numero_de_documento": "20100686814",
        "denominacion": "OLVA COURIER S.A.C",
        "numero_de_registro_mtc": ""
    },
    "conductores": [
        {
            "conductor": "principal",
            "tipo_de_documento": "1",
            "numero_de_documento": "72533576",
            "nombres": "OSCAR DANIEL",
            "apellidos": "FERNANDEZ JIMENEZ"
            "numero_licencia_conducir": "Q72533576"
        },
        {
            "conductor": "secundario",
            "tipo_de_documento": "1",
            "numero_de_documento": "72533576",
            "nombres": "OSCAR DANIEL",
            "apellidos": "FERNANDEZ JIMENEZ"
            "numero_licencia_conducir": "Q72533576"
        },
        {
            "conductor": "secundario",
            "tipo_de_documento": "1",
            "numero_de_documento": "72533576",
            "nombres": "OSCAR DANIEL",
            "apellidos": "FERNANDEZ JIMENEZ"
            "numero_licencia_conducir": "Q72533576"
        }
    ],
    "vehiculos": [
        {
            "vehiculo": "principal",
            "numero_de_placa": "",
            "tarjeta_unica_de_cirulacion": "",
            "numero_de_autorizacion": "",
            "codigo_entidad_autorizadora": ""
        }
    ],
    "items": [
        {
            "cantidad": "3",
            "unidad_de_medida": "TE",
            "descripcion": "LEJIA 8% - TOTEM 1000 KG (UN1791 CLASE 8)",
            "codigo_interno": "0206LGL8002",
            "codigo_producto_sunat": "47131807"
            "codigo_GTIN": "",
            "tipo_estructura_GTIN": ""
        }
    ],
    "documento_relacionados": [
        {
            "documento": "factura",
            "serie": "F001",
            "numero": "1",
            "ruc_emisor": "20123456890"
        }
    ]
}
```