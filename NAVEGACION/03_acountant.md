# Opciones de Menu
## Estados de cuenta
  > accountant/bank-states
  ### Funciones
  - Visualizar y descargar la lista de estados de cuenta de *companies*
    - Los enlaces de descarga llevan al enlace de Google Drive.
  - Ordenar por fecha y filtrar por *company* 
  ### Visual
  - Muestra una tabla con las columnas: mes, año, pdf y company

  ### Peticiones
  ```js
  //GET /bank-states
    return {
      success: true/false,
      data : {
        company: {
          id: name,
          ...
        },
        data: [
          {id,month,year,pdfDriveId,companyId},
          ...
        ]
      }
    }
  ```

## Ventas
  > accountant/sales

  > accountant/sales/:invoiceId
  ### Funciones
  - Mostrar la lista de facturas de ventas
    - Hay un formulario para extraer las facturas segun el periodo, cliente, vencimiento y company;
    - Dependiendo de la opcion elegida, se deben llenar los inputs para que se habilite el boton de buscar (comun para todos los tipos de busqueda)
    - Se puede ordenar por cliente, fecha, estado, por defecto se ordenan de la mas reciente a la mas antigua
  - Marcar el pago de facturas y el pago de detraccion (operacion y fecha)
    - Los cambios de estado de facturas se debe reflejar en el store.
  - Diferenciar las facturas pagadas, vencidas y pendientes
  ### Visual
  - Muestra un formulario en la parte superior para hacer la busqueda de facturas
    - Slider busqueda: periodo, cliente, vencidas y factura
    - Input de fecha, mes, cliente, serie, numero y company
    - Boton de buscar
    - El formulario queda fijo arriba asi como las cabeceras de la tabla
    - Muestra una paginacion en base al tamaño de la pantalla y la cantidad de facturas que entran (pacgina actual, ultima pagina como texto, boton de siguiente y anterior pagina)
  - Muestra una tabla con la lista de facturas (serie, numero, fecha, cliente, importe, pdf,*detail*,estado)
    - Al hacer click en *detail* lleva al componente detail de factura con la informacion completa
    - Dependiendo del estado (pendiente, pagada, vencida) se pinta de un color determinado
  - Detail Factura: muestra un pop-up con la informacino completa de las facturas y
    - Input para agregar datos de pago (numero de operacion y fecha) y pago de detraccion (numero de operacion y fecha).

  ### Peticiones
  ```javascript
  //GET /all-companies
    return {
      success: true/false,
      data: [
        {id,shortName},...
      ]
    }
  //GET /all-clients/:companyId
    return {
      success: true/false,
      data: [
        {
          id,shortName
        }
      ]
    }
  //POST /invoices
    body = {
      month, year, clientId, state,companyId
    }
    return {
      success: true/false,
      data: [
        {id, serie, numero, fecha, cliente, importe, pdf, paid, credit,},
        ...
      ]
    }
  //GET /invoice/:id
    return {
      success: true/false,
      data: {
        allInvoiceInformation...
      }
    }
  //UPDATE /invoice/:invoiceId
    // Puedo actualizar cualquier valor de la factura menos, (number, date,igv)
    body = {
      payDate,detractionPayDate,payOperation,detractionPayOperation
    }    return {
      success: true/false,
    }
  ```


aqui

## Compras
  > accountant/purchases
  ### Visual
  - Muestra un form para ingresar: company, mes y año; además de un boton para solicitar la informacion
  - Similar al componente de ventas pero solo se puede seleccionar el periodo de compras (dejando de lado la seleccion por proveedor)
  - Muestra una tabla con la informacion de las facturas (serie, numero, shortName, dia, total, paid )
  - Al hacer click en la una fila nos lleva al detalle de la compra, dando la opcion para editar la informacion
  - El funcionamiento de la paginacion es exactamente igual al de las ventas
  - El filtrado debe ser por proveedor (puediendo seleccionar multiples proveedores en el filtrado), el ordenamiento es por la factura mas reciente
  - 
  ### Funcionamiento
  - Por defecto al entrar al componente se cargan las compras y ventas del mes y el año actuales
  - Toda la informacion se guarda en el store
  - En la pagina solo se mostraran 25 facturas, pero las peticiones se haran por todas las facturas de los periodos.
  - 
  ### Peticiones
  >GET /purchases?month=&year=
  ```javascript
    return {
      success: true/false,
      data: [
        {id,date,number,serialId,entityId,}
      ]
    }
  ```
  >UPDATE /purchase/:purchaseId
  ```javascript
    body = {
      keysAeditar
    }
    return {
      success: true/false,
    }
  ```

## Notas de credito
  > accountant/credit-notes
  ### Visual
  - Similar a todo lo anterior, con la diferencia que trae todas las notas de credito, el unico input es company
  - El componente de detalles persiste, con la diferencia que la informacion no se puede editar
  - Se puede filtrar por cliente y ordenar por fecha
  ### Funcionamiento
  - Las peticiones para todos los componentes anteriores pueden ser las mismas, solo variando el input y el objeto return
  - 
  ### Peticiones
  >GET /credit-notes
  ```javascript
    return {
      success: true/false,
      data: [
        {creditNoteKeys}
      ]
    }
## Resultados
  > accountant/results
  ### Visual
  - Muestra un form con input de company, mes y año, además de un boton para generar el input (opciones desplegables para evitar fechas futuras o muy antiguas)
  - En la parte derecha muestra el total de ventas seguido de el % de venta por cliente
  - En la parte izquierda muestra el total de compras seguido del % de compra por proveedor
  - 
  ### Funcionamiento
  - En el backend se debe guardar el inicio de la fecha para los estados
  - Verifica si se tiene la informacion del periodo seleccionado antes de hacer la peticion al servidor
  ### Peticiones
  >GET /results?month=&year=
  ```javascript
    return {
      success: true/false,
      data:{
        sales: {
          total:,
          percent:[{entityId, val},...]
        },
        purchases: {
          total:,
          percent:[{entityId, val},...]
        },
      }
    }
  ```