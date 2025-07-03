# Opciones de menu
## Servicios Terminados
  > operator/finished-services
  ### Funcionamiento
  - Mostrar los servicios antiguos para consulta
  - 
  ### Visual
  ### Peticiones

## Asignaciones
  > operator/assignments  

  > operator/assignments/:subServiceId
  ### Funcionamiento
  - Mostrar los sub-servicios asignados al operador en forma de cards
    - Datos a ver: company, cliente, descripcion, servicio, boton detail
    - Solo se muestran los activos y se pintan del color de la empresa
    - Se muestran todos los servicios activos
  - Editar informacion de sub-servicios (detail)
    - Datos a editar: potencia, datos de placa, fecha de inicio y fin, comentarios
    - Datos a agregar: requerimientos correctivos  
    - Los datos solo se editan si el office ha cerrado el servicio
    - Asociar un esquema o crear uno nuevo y asignarlo               
  ### Visual
  - Mostrar un navbar para la paginacion
  - Lista de cards con los servicios
  - 
  
  
  
  - Muestra un nav-bar superior donde se selecciona entre los actuales y los entregados
  - Muestra en la parte central una lista de cards con las sub ots asignadas a el, cada card muestra la OT,subOT, cliente, descripcion, company
  - Al hacer click en un card, nos lleva al detalle del sub servicio
  - En el componente detalles, en un sector muestra los datos del cliente
  - En el componente detalles, en un sector muestra para ingresar la potencia y demas datos de placa del motor, tipo de equipo, marca, alimentacion
  - En el componente detalles, en un sector muestra para ingresar los requerimientos (cantidad, tipo, descripcion)
  - En el componente detalles,, un sector para subir/ver imagenes (cuaderno y proceso), que al entrar abre un modal para subir la informacion, en caso de tener un esquema asignado, mostrara el enlace del esquema
  - Tiene que haber un boton para guardar los datos
  - Debe mostrar los comentarios que ha echo el cliente antes del servicio (subido por el creador de la sub-ot/OT)
  - Tiene que haber un input para que el tecnico deje los comentarios del servicio
  - Una seccion para marcar el inicio y fin del servicio
  - Tiene que haber la opcion para editar los datos de la sub ot (solo lo correspondiente al tecnico)
  - Tiene que haber una opcion para mostrar los enlaces de las imagenes asociadas al sub servicio
  ### Peticiones
  ```javascript
  //GET operator/assignments/:userId
    return {
      success: true/false,
      data: [
        {id, ot, subot, client,company, typeService},...
      ]
    }
  //GET operator/sub-service/:subServiceId
    return {
      success: true/false,
      data: {
        ...allSubServiceInfo,
      }
    }
  //POST operator/images
    body = {
      subServiceId: ,
      images:[
        {type,name,idDrive},...
      ]
    }
    return {
      success: true/false,
    }
  //GET operator/images/:subServiceId
    return {
      success: true/false,
      data: [
        {id,name,idDrive,typeImage},...
      ]
    }
  //POST operator/add/sub-service-items
    body = {
      subServiceId: ,
      items:[
        {order,quantity,description},...
      ]
    }
    return {
      success: true/false,
    }
  //UPDATE operator/sub-services
    body = {
      power,plateData,startDate,FinishDate,operatorComments
    }
    return {
      success: true/false,
    }
  ```



## Requerimientos
  > operator/requirements
  ### Visual
  - Muestra un listado de requerimientos solicitados por el usuario (no comprados)
  - Muestra un formulario para agregar mas solicitudes de compra (cantidad, descripcion)
  ### Funcionamiento
  - Los requerimientos conforme van siendo comprados se eliminan en tiempo real de la lista (deseable)
  ### Peticiones
  >POST operator/add-requirements
  ```javascript
    body = [
      {name,quantity,userId,subServiceId,measurementeUnityId,itemInvoiceCodeId},...
    ]
    return {
      succes: true/false,
    }
  ```
  >GET operator/requirements/:userId
  ```javascript
  // solo pendientes
    return {
      success: true/false,
      data: [
        {id,quantity,itemInvoiceCodeId,measurementUnityId,subServiceId},...
      ]
    }
  ```

## Esquemas
  > operator/schemes
  ### Visual
  - Muestra un formulario para realizar la busqueda por grupos y polos
  - En la parte central muestra la lista de coincidencias (id, enlace)
  - En cada lista habra un boton para asociar el esquema con una sub ot
  - Muestra un boton para subir un esquema, el cual abre un modal para subir la imagen del esquema y la demas informaicon de la tabla
  - 
  ### Funcionamiento
  - Todos los enlaces redirijen a un arhivo google drive
  ### Peticiones
  >GET operator/scheme?groups=&poles=
  ```javascript
    return {
      success: true/false,
      data: [
        {id,imageDriveId,details},...
      ]
    }
  ```
  >UPDATE operator/scheme-sub-service
  ```javascript
    body = { subServiceId, schemeId }
    return {
      success
    }
  ```
  >POST operator/scheme
  ```javascript
    body = {groups,poles,imageDriveId,details}
    return {
      success: true/false,
    }
  ```

