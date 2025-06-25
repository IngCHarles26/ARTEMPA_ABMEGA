# Opciones de menu
## Asignaciones
  > operator/assignments                                          
  ### Visual
  - Muestra un nav-bar superior donde se selecciona entre los actuales y los entregados
  - Muestra en la parte central una lista de cards con las sub ots asignadas a el, cada card muestra la OT,subOT, cliente, descripcion, company
  - Al hacer click en un card, nos lleva al detalle del sub servicio
  - En el componente detalles, en un sector muestra los datos del cliente
  - En el componente detalles, en un sector muestra para ingresar la potencia y demas datos de placa del motor, tipo de equipo, marca, alimentacion
  - En el componente detalles, en un sector muestra para ingresar los requerimientos (cantidad, tipo, descripcion)
  - En el componente detalles,, un sector para subir/ver imagenes (cuaderno y proceso), que al entrar abre un modal para subir la informacion, en caso de tener un esquema asignado, mostrara el enlace del esquema
  - Tiene que haber un boton para guardar los datos
  - Debe mostrar los comentarios que ha echo el cliente antes del servicio
  - Tiene que haber un input para que el tecnico deje los comentarios del servicio
  - Una seccion para marcar el inicio y fin del servicio
  ### Funcionamiento
  - La descripcion toma los datos de palca del motor
  - AL cargar el detalle del servicio asignado, se cargan los datos de la base de datos, el tecnico puede editar los requerimientos siempre y cuando no haya serrado la opcion el usuario office
  - La asignacion de esquemas estara en la ruta *esquemas* 
  - Los cards de asignaciones estaran en color claro para los servicios actuales y en una tonalidad oscura para los servicios entregados (este valor sera para los valores marcados como finalizados)
  - Cuando el tecnico marque el inicio del servicio o su finalizacion, tambien se guardara la fecha
  - Al hacer las peticiones de los requerimientos no trae el precio
  ### Peticiones
  >GET operator/assignments/:userId
  ```javascript
    return {
      success: true/false,
      data: [
        {id, ot, subot, client,company, typeService},...
      ]
    }
  ```
  >GET operator/sub-service/:subServiceId
  ```javascript
    return {
      success: true/false,
      data: {
        ...allSubServiceInfo,
      }
    }
  ```
  >POST operator/images
  ```javascript
    body = {
      subServiceId: ,
      images:[
        {type,name,idDrive},...
      ]
    }
    return {
      success: true/false,
    }
  ```
  >POST operator/add/sub-service-items
  ```javascript
    body = {
      subServiceId: ,
      items:[
        {order,quantity,description},...
      ]
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
  - 
  ### Funcionamiento
  - Los requerimientos conforme van siendo comprados se eliminan en tiempo real de la lista (deseable)
  ### Peticiones

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



# Acciones  (mobile)
- Visualizar la lista de sub servicios a su cargo
  - ot
  - cliente
  - compañia
- Al hacer click lo lleva a la informacion completa del sub servicio
  - Marcar la fecha de inicio del sub servicio
  - Marcar como finalizado el servicio
  - subir fotos de recepcion, proceso 
- Solicitar compras de repuestos, insumos o servicios
- Subir fotos de esquema y asociarla a una sub ot
- Asociar un esquema a una sub ot
- Subir las necesidades de la sub ot
