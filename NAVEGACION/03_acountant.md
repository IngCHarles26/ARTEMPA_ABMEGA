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
  - Mostrar la lista de facturas de ventas segun la company y: periodo, cliente y vencidas en forma de tabla
    - Datos a ver: dia, mes, año, serie, numero, cliente, monto, pdf, xml, estado (color)
  - Editar la informacion de la factura (fecha pago, numero de operacion, fecha de pago de detraccion y numero de operacion de detraccion); accediento al detail por boton
  - Ordenar las facturas por cliente y fecha
  - Diferenciar por color de fondo las facturas pagadas, vencidas y pendientes.
  ### Visual
  - Muestra un formulario en la parte superior para hacer la busqueda de facturas
  - Mostrar un navbar para la paginacion y ordenar los valores de la tabla
  - Muestra una tabla con la lista de facturas
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
  ### Funcionamiento
  - Mostrar la lista de compras segun el periodo y la company
    - Datos a ver: dia, mes, año, serie, numero, ruc, proveedor, inStorage, edit
  - Agregar comentarios a la factura y si esta en posecion
    - Abre un pop-up que muestra el comentario que tiene, edita el comentario y agrega uno nuevo
  - Guardar todos los cambios 
  - Ordenar por provedor, inStorage
  ### Visual
  - Muestra un formulario en la parte superior para hacer la busqueda de facturas
  - Mostrar un navBar para la paginacion, ordenar los valores de la tabla y guardar los cambios
  - Mostrar una tabla de las facturas con un checkbox para *inStorage* y boton para comentarios
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