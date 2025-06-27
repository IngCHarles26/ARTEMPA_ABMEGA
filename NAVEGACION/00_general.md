# Rutas generales

## JWT
El json web token tendra la siguiente estructura
```javascript
  {
    id: 1290,
    role: 'admin',
    userName: 'usuario login',
    name: 'nombre del usuario',
    limitTime: '00:00 del dia siguiente'
  }
```
## Peticiones
- Toda la informacion que sea enviada del servidor, se va a guardar en el store para futuras consultas y evitar peticiones repetidas
- Las tablas que solo son id-name, tendran el mismo endpoint devolviendo un objeto [id]:name
- Las peticiones se guardan en el local storage, para cuando se haga la misma, no se vuelva a repetir la misma peticion
- En los forms que tengan un input de mes y año, se deben tener un minimo de fecha para no pedir fechas futuras y o muy antiguas

## Acceso general
- Se utilizara el local storage (id, name y role) para decirle al front los componentes a mostrar, el usuario que esta realizando las acciones y el nombre del usuario; las acciones que el usuario haga se validan contrastando la informacion del local storage y el JWT generado en el login, además de guardar el role, id y nombre en el store.
- Si existe local storage y JWT, el usuario navega libremente en las opciones disponibles, actualizando los estados en el store.
- Si no existe JWT, el navegador debe llevar al usuario al componente login
- Si no existe local storage pero si existe JWT, el navegador debe actualizar la informacion del local storage con una peticion al servidor.
- Al hacer log out, se elimina la informacion del local storage y el JWT con la peticion al servidor.

### Peticiones
>GET /validate-user
```javascript
  return {
    success: true/false,
    data  = {
      id: 0,
      name: '',
      userName: '',
      role: '',
    }
  }
```
>GET /user-logout
```javascript
  return {
    success: true/false,
  }
```
## Componente Login
> /login
### Visual
- Muestra un formulario para el inicio de sesion con input para userName y password
- En la parte inferior izquierda  muestra pop-ups con los mensajes de respuesta que manda el servidor
### Funcionamiento
- Al hacer login se guarda en una cookie el JWT con la informacion de la sesion y guarda en local storage el id, name y role del usuario logueado.
- Cuando la sesion es exitosa manda al componente *home* y el servidor retorna el JWT de la sesion que dura hasta las 00:00 del dia siguiente
### Peticiones
>POST /user-login
```javascript
  // sin JWT
  body = {
    userName: '',
    password: ''
  }
  return {
    data:{
      id: 0,
      name: '',
      userName: '',
      role: '',
    },
    token: '',
  }
```


## Componente Home
> 'typeUser'/home

### Visual
- Muestra un aside en la izquierda con las opciones de menu dependiendo del tipo de usuario.
- En la parte derecha ocupando la mayor parte del espacio, se muestra el body con contenido del componente dependiendo de la opcion del menu seleccionada.
- Al iniciar sesion y no se tiene una opcion del menu seleccionada muestra un mensaje de bienvenida al usuario en body.
- Las opciones de menu constan de un icono y un nombre, los iconos al estar ocultos y pasar el mouse sobre ellos se muestra el nombre del componente como comentario.
- Debe resaltar la opcion seleccionada en el aside.
- En mobile se tiene un boton que muestra el aside de lado izquierdo sobre el contenido del componente principal, este boton desaparece si el usuario no hace acciones por uno determinado tiempo, cuando vuelve a interactuar aparece nuevamente el boton.
- En mobile el boton de menu se muestra en la parte inferior izquierda, cuando se muestra el menu, el boton se oculta
- En el aside debe haber la opcion para esconder el menu, en desktop muestra solo los iconos de los menus y en mobile oculta completamente el componente
- En la parte inferior del aside, debe haber un boton para hacer log-out con confirmacion de accion.
- En la parte superior del aside, muestra un logo del usuario, el nombre y el role; al hacer click nos lleva a la informacion del usuario

### Funcionamiento
- Al dar click en cada opcion nos lleva a la ruta del componente




## Componente user-info
> 'typeUser'/user-info

### Visual
- Muestra la informacion completa del usuario
- Muestra un boton para editar usuario y contraseña, no necesariamente las dos
- Muestra un boton para editar informacion general (name, lastName, phone, address), puede enviar todas o solo algunas; si la respuesta es positiva se actualizan los datos cambiados en el store


### Funcionamiento
- Al hacer un cambio de usuario o contraseña, se elimina la sesion en el front.
- Esta opcion esta disponible para todos los tipos de usuarios excepto (por definir) admin y client

### Peticiones
>POST /edit-user-info
```javascript
  body = {
    userInfo:{
      name: '',
      lastName: '',
      phone: '',
      address: '',
    },
  }
  return {
    success: true/false,
  }
```
>POST /edit-user-access
```javascript
  body = {
    userInfo: {
      userName: '',
      password: '',
    },
  }
  return {
    success: true/false,
  }
```