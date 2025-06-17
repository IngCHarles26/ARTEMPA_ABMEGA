# USUARIOS
## Tipos | .env
0. Admin
1. Office
1. Operator
1. Acountant
1. Client

## Columnas | Pendiente
- id: **number** Identificador unico del usuario
- userName: **string** Nombre de usuario para el ingreso a la aplicacion
- password: **string_hashed** Contraseña del usuario para el ingreso a la aplicacion
- name: **string** Nombre del usuario
- lastName **string** Apellido del usuario
- rol **string** Tipo de usuario
- active **bool** Configurar si el usuario esta activo
- phone **number** Telefono de contacto (whatsapp, telegram)
- address **string** Direccion de residencia del usuario
- dni **number** Documento nacional de identificacion

## Funciones
- Login o logout: Todos
- Creacion de Usuarios: Admin

## Consideraciones
- Limite de 3 sessiones por usuario
- 