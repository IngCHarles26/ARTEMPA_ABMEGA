# Opciones de menu

## Lista de Users
  > admin/list-users
  ### Visual
  - Muestra la lista de usuarios: id, userName, name, role
  ### Funcionamiento
  - Al hacer click en un usuario nos lleva a un modal con la informacion completa del usuario (menos la contraseña)
  - El modal muestra un boton que permite editar la informacion de los usuarios: role, active, dni
  - Se puede filtrar (role, active) y ordenar (lastname, role, active) la lista de usuarios
  ### Peticiones
  >GET /list-users


## Crear Users
  > admin/create-user
  ### Visual
  - Muestra un formulario con inputs: userName, password, role, name, lastName, phone
  ### Funcionamiento
  - Hace la peticion del nuevo usuario y verifica que quien la haga sea el usuario admin
  ### Peticiones

