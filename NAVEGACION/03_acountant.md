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
  - Marcar el pago de facturas y el pago de detraccion
  - Diferenciar las facturas pagadas, vencidas y pendientes
  - 
  ### Visual
  - Muestra un formulario en la parte superior
    - Sera el filtro para extraer la informacion de las
  - Muestra una tabla con la lista de facturas
  - Muestra un pop-up con la informacino completa de las facturas y para agregar datos de pago 
   con inputs de mes y año o cliente, el







  - Muetra un nav-bar para mostrar las ventas por periodo y por cliente
  - Muestra un slider para intercambiar entre las companies
  - Muestra un boton para hacer la busqueda en base a a los inputs
  - Muestra un mensaje para indicar al usuario que debe rellenar los inputs antes de ver la informacion.
  - Muestra una tabla con la informacion de las facturas (serie, numero, fecha, cliente, importe, pdf)
  - Las facturas pagadas, vencidas y las demas se pintaran de un color determinado
  - Al hacer click en una fila, nos lleva a la informacion completa de la factura y la opcion para editar la informacion de pago y demas informacion; en este componente debe aparecer la opcion de regresar al home (este componente se va a reutilizar en todos los elementos que den detalles sobre alguna accion)
  - Si las facturas no entran en la pantalla, se el header de la tabla queda fijo y permite hacer scroll
  - Debe mostrar botones para la paginacion, el total de paginas, la pagina actual y un input con boton para ir a una determinada pagina, ademas de un boton para resetear los filtros.
  - Muestra un input para acceder directamente a una factura por serie y numero
  - Mostrar un boton para acceder a un form para ingresar la informacion de pago de la factura (detraccion y restante)
  ### Funcionamiento
  - Al iniciar el componente, todos los inputs estan vacios, el boton para hacer la peticion se encuentra deshabilitado hasta que todos los inputs esten llenos
  - Se puede filtrar las facturas por pendientes, pagadas y vencidas, el numero total de paginas depende de los filtros aplicados
  - Dependiendo de la cantidad de facturas, solo se mostraran 25 por pagina, las peticiones se haran de 25 en 25
  - Al entrar al modal de la factura, hace la peticion por id para mostrar la informacion completa
  - Si se hace un cambio en los inputs del formulario, se borra todos los elementos de la tabla y se reemplazan por los nuevos valores
  - Las facturas se ordenan por defecto de la mas reciente a la mas antigua
  - Al actualizar satisfactoriamente cualquier factura, se hace el cambio de esa informacion en el store
  - Si se accede a una factura por numero y serie, la company debe estar seleccionada para poder hacer la peticion
  - *Idea*: Por defecto puede mostrar las ventas del mes actual de abm y megaman, llenar estos valores en el formulario de solicitud de datos al inicio del componente.
  ### Peticiones
  >GET /all-companies
  ```javascript
    return {
      success: true/false,
      data: [
        {id,shortName},...
      ]
    }
  ```
  >GET /all-clients/:companyId
  ```javascript
    return {
      success: true/false,
      data: [
        {
          id,shortName
        }
      ]
    }
  ```
  >POST /invoices
  ```javascript
    // Se da preferencia al clientId, 
    body = {
      alreadyInvoiceIds: [],
      quantity:25,
      clientId,
      month,
      year,
    }
    return {
      success: true/false,
      data: [
        {id, serie, numero, fecha, cliente, importe, pdf, paid, credit,},
        ...
      ]
    }
  ```
  >GET /invoice/:id
  ```javascript
    return {
      success: true/false,
      data: {
        allInvoiceInformation...
      }
    }
  ```
  >GET /invoice?serial=&number=&company=
  ```javascript
    return {
      success: true/false,
      data: {
        allInvoiceInformation...
      }
    }
  ```
  >UPDATE /invoice/:invoiceId
  ```javascript
    // Puedo actualizar cualquier valor de la factura menos, (number, date,igv)
    body = {
      ?bodyKeys: newData,
      ...
    }
    return {
      success: true/false,
    }
  ```


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