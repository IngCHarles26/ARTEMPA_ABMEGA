# Opciones de menu

## Lista de Users
  > admin/users-list
  > admin/user-list/:userId
  ### Funciones
  - Ver la lista de usuarios de la página
  - Editar la informacion de los usuarios
  ### Visual
  - Muestra la tabla con la lista de usuraios: id, userName, name, lastName, role, active
    - Se puede filtrar por role y active; y ordenar por lastName y role
    - En cada fila hay un boton para editar la informacion del usuario que al presionar nos lleva al componente detail
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

