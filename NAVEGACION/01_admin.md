# Opciones de Menu

## Lista de Users
  > admin/users-list
  
  > admin/user-list/:userId
  ### Funciones
  - Ver la lista de usuarios de la página en forma de tabla
  - Editar la informacion de los usuarios
    - Al hacer click en el usuario
  ### Visual
  - Muestra la tabla con la lista de usuraios: id, userName, name, lastName, role, active y un boton de editar
  - En el detail de user, se muestra la informacion del usuario y los editables como inputs (role, active, dni)
  ### Peticiones
  ```js
  //GET /list-usres
    return {
      success: true/false,
      data: [
        {id,userName,name,lastName,active,role},...
      ]
    }

  //POST /edit-user
    body = {id,?role,?active,?dni}
    return {
      success: true/false
    }
  ```


## Crear Users
  > admin/create-user
  ### Funciones
  - Crear nuevos usuarios
  ### Visual
  - Muestra un formulario con inputs: userName, password, role, name, lastName, phone
  ### Peticiones
  ```js
  //POST /create-user
    body = {
      userName = '',
      password = '',
      role = '',
      name = '',
      lastname = '',
      phone = '',
    }
    return {
      success: true/false,
    }
  ```

