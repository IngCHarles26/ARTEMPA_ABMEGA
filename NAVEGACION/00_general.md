# Rutas generales

## JWT
El json web token tendra la siguiente estructura, el cual se va a guardar en una cookie de solo acceso por https
```javascript
  {
    id: 1290,
    role: 'admin',
    userName: 'usuario login',
    name: 'nombre del usuario',
    limitTime: '00:00 del dia siguiente'
  }
```
## Consideraciones aplicables a todo el proyecto
- Se tendra un slice con la lista de peticiones realizadas y otro slice con los datos de esas peticiones, por lo que al hacer una peticion primero se revisa en el store si estas existen, luego se suministra la informacion primero del store y luego de la peticion del backend.
- Las tablas simples que solo tienen las columnas id-name (102, 103, 106,107, 108, 109, 110, 112, 113, 114) compartiran el mismo endpoint para el manejo de sus datos.
- Las tablas 0 (se guardan por codigo), tambien van a almacenar variables generales de todo el archivo que no implican seguridad 
  - Mes y año limites, para los inputs que son para periodos mensuales.
- Tanto en el back como en el front, se va a realizar el filtrado de los tipos de role, para proteger las rutas y las peticiones.
- Cuando se refrezca la pagina, se revisa el local storage para ver los datos el: id, name y role; si los datos existen, se redirige al menu principal, por el contrario se redirige al componente login. 
- En las peticiones al back, se va a tener una palabra secreta como variable de entorno, que va al inicio de cada peticion para proteger las rutas del servido
- Para todas las tablas, cuando el mouse pasa por una fila, la fila cambia de color o una tonalidad mas oscura respecto al fondo.

## Login
  > /login
  ### Funciones
  - Loguear al usuario
    - Envia al usuario logueado al componente *home*
  - Guardar el JWT sobre los datos de sesion del usuario 
    - Guarda el JWT en una cookie http only y en local-storage {id,name,role}
    - Si en local storage no existe {id,name,role}, se realiza una peticion con el JWT para reconstruir esa informacion.

  ### Visual
  - Formulario con input de user y password, además de un boton para inicio de sesion
  - Mensaje de respuesta por un mal login
  ### Peticiones
  ```js
    //GET /login=userName&password
    return {
      msg: 'guelcom'
      token: 'jwt',
    }
  ```

## Logout
  > /logout
  ### Funciones
  - Desloguear al usuario
    - Envia el JWT por HTTP para validar que el usuario sea el que verdaderamente esta queriendo desloguearse
    - Borra el JWT de la cookie y los datos de local-storage
  ### Visual
    - Boton con icono en el aside izquierdo de todos los menus de usuarios
  ### Peticiones
  ```js
    //POST /logout
    body = {
      token: JWT
    }
    return {
      msg: 'bye',
    }
  ```

## Componente *home*
  > user-type/home
  ### Funciones
  - Mostrar las acciones que puede realizar un usuario
  - Navegar entre funciones 
  - Log out del usuario
  - Mostrar un mensaje de bienvenida
    - Aparece despues de loguearnos o cuando se refrezca la pagina y se pierden los valores del local-storage
  ### Visual
  - Lista de opciones en un aside con un color de fondo diferente
  - El aside consta de imagen texto, que al mover el mouse se agranda ligeramente y al estar seleccionada su color de fondo es mas oscuro que el de los demas además de cambiar el color del texto, en mobile tiene un boton para ocultar el aside, tambien debe tener un boton para hacer log-out, en la parte super muestra la informacion del usuario logeado y al hacer click lleva al componetne *user-info*.
  - En mobile se tiene un boton que muestra el aside y el boton se oculta cuando no hay movimiento o acciones en el sitio.




## Componente *user-info*
  > user-type/user-info
  ### Funciones
  - Visualizar los datos del usuario
  - Editar userName y password
    - Al hacer un cambio de estos, se hace un log-out del usuario
  - Editar la informacion del usuario (name, lastName, phone, address)
    - Al presionar el boton de editar se convierten en inputs los lugares seleccionados y si se hace un cambio en el valor se guardan los nuevos datos para la peticion.
    - Los nuevos datos se envian por peticion pero se usara la informacion local para mostrar los valores, 
    - Puede editar todas o solo algunas
  ### Visual
  - Muestra la informacion completa del usuario 
  - Muestra un boton de edit y save
  ### Peticiones
  ```js
    //POST /edit-user-info
    body = {?name,?lastName,?phone,?address}
    return {
      succes: true/false
    }

    //POST /edit-user-access
    body = {newUserName,newPassword}
    return {
      success: true/false,
      resetCookie
    }
  ```
