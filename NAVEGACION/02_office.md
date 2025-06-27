# Opciones de menu
## Servicios
  > office/services
  ### Visual
  - 
  ### Funcionamiento
  ### peticiones

## Requerimientos tecnicos
  > office/requirements
  ### Funcionamiento
  - Visualiza los requerimientos solicitados por los operadores, marcados como no comprados
  - Marca los requerimientos adquiridos
  - Las casillas marcadas deben ser persistentes y guardadas en local storage
  ### Visual
  - Muestra una tabla con las peticiones de los tecnicos pendientes de compra (quantity, descripcion, measurementUnityId, itemInvoiceCode,  )
  - Cada fila tiene una casilla que se puede marcar
  - Presenta un boton para marcar como comprados los items 
  ### Peticiones
  >GET office/requirements
  ```javascript
    return {
      success: true/false,
      data:[
        {id,quantity,name,userId,itemInvoiceCodeId,mesaruementUnityId,subServiceId},...
      ]
    }
  ```
  >POST office/mark-requirements
  ```javascript
    body = {
      data: [...requirementId]
    }
    return {
      succes: true/false
    }
  ```

## Presupuesto

## Compras
  > office/purchases

  > office/purchases/:purchaseId
  ### Funciones
  - Seleccionar el año, mes y company en un form y un boton para traer los datos, o tambien seleccionar las compras por cliente, cuando cambias los valores de los inputs se resetea la lista de de facturas mostradas, tambien debe haber un boton para subir los cambios, que solo se debe mostrar o habilitar cuando se detecte un cambio.
  - Se visualiza una tabla con los datos de las facturas segun el form, teniendo la opcion de ver en una aruta toda la informacion de la compra, con la opcion de editar los valores. Conforme se vayan editando las facturas, se va agregando los cambios segun el id de compra efectuado, cuando se da al boton de subir, se guardan todos los cambios en la base de datos
  - Se puede ordenar por fecha, proveedor y estado de pago 
  ### Visual
  - Muestra un form en la parte superior con los inputs y botones 
  - Muestra una tabla con los datos de las facturas (dia, serial, number, shortName, total), tambien un boton en cada fila donde se accede a los detalles del componente
  - Muetra un boton para guardar los cambios
  ### Peticiones
  >GET office/purchases?month&year
  ```javascript
    return {
      succes: true/false,
      data: [
        {...allPurchasesIds},...
      ]
    }
  ```
  >POST office/purchases
  ```javascript
    body = [
      {...onlyKeysChanged},...
    ]
  ```

## Facturas
  > office/invoices
  > office/invoices/:invoiceId
  ### Funciones
  - Se selecciona el (año, mes), (vencidas), (cliente) y company; además de un boton para solicitar los datos, 
  - Se suben los cambios realizados en las facturas
  - Se puede editar 
  ### Visual
  ### Peticiones

## Estados de cuenta
  > office/bank-statements
  ### Funcionamiento
  - Ver los estados de cuenta por enlace de drive
  - Ver la lista de estados de cuenta desde el inicio
  - Seleccionar la company de la cual se va a solicitar los estados de cuenta
  - Agregar un estado de cuenta


## Guias
  ### Funciones
  - 

## Notas de Credito

## Inventario

## Esquemas

## Otros (entidades, companies, serials, cars, drives, machineTypes, machineBrands, measurementUnits, spareBrands,spareTypes,detractions,transferReasons,itemInvoiceCodes,itemDeliveryNotesCodes)



# Acciones (desktop - mobile)
- Intercambiar entre la lista de compañias
- Crear ots y sub ots
- Visualizar la lista de OTS
  - ot
  - fecha
  - cliente
  - descripcion
- Al hacer click en una ot nos muiiestra la informacion completa del servicio y se puede editar
  - lista de sub ots (muestra un )
    - sub ot
    - encargado
    - tipo de servicio
    - requerimientos del encargado
  - Acciones de presupuesto
    - enviar por correo
    - editar
    - visualizar
  - Emitir facturas, guias y notas de credito y asociarla a una o varias ots
- Las mismas acciones que el contador, solo que dando la opcion de ver el detalle de cada item
- Crear entidades y personas de contacto
- Subir informacion de compras 
- Editar la informacion de las companies
- Ver todas las base de datos para editar la informacion (seriales, carros, drivers, etc etc)
- COnsultar datos de ruc
- Consultar validez de una factura
- Anular un comprobante (maximo 2 dias despues)
 