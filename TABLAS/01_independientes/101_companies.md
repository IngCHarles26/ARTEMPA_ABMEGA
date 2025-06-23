# Empresa - companies (ABM o MEGA)
### Columnas
- id **number** identificador unico de la empresa
- ruc **number** RUC de la empresa
- name **string** Razon social de la empresa
- shortname **string** Nombre comercial de la empresa
- address **string** Direccion de la empresa
- bcpCC **string** numero de cuenta corriente bcp
- bcpCCI **string** numero de cuenta interbancario
- spot **number** numero de cuenta para detracciones

### Informacion inicial
|id|ruc|name|shorName|address|bcpCC|bcpCCI|spot|
|:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |
|1|20456335943|ABM ELECTRIC S.R.L.|ABM|MZA. F LOTE. 10 ARTEMPA (FTE. LOCAL DE ARTEMPA) AREQUIPA - AREQUIPA - CERRO COLORADO|215-1976560-0-68|002-215-001976560068-29|101263444
|1|20456335943|MEGA OPERACIONES EN MANTENIMIENTO S.R.L.|MEGA|CAL.7 MZA. F LOTE. 11 URB. ARTEMPA AREQUIPA - AREQUIPA - CERRO COLORADO|215-2172830-0-93|002-215-002172830093-26|101406636

### Peticiones
- Extraer la lista total: id, shorName 
- Editar la informacion por ID: solo se ingresan las props que se van a editar
- Extraer la informacino por ID
- Visualizar la informacino por ID


### Consideraciones
- Si se agrega una compañia nueva, se hará directamente en la base de datos
