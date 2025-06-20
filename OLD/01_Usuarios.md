# Empresa - companies (ABM o MEGA)
### Columnas
- id **number** identificador unico de la empresa
- ruc **number** RUC de la empresa
- name **string** Razon social de la empresa
- address **string** Direccion de la empresa
- bcpCCT **string** numero de cuenta corriente bcp
- bcpCCI **string** numero de cuenta interbancario
- spot **number** numero de cuenta para detracciones




# USUARIOS - users
## Tipos | .env
0. Admin
1. Office
1. Operator
1. Acountant
1. Client

### Columnas | Pendiente
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

### Funciones
- Login o logout: Todos
- Creacion de Usuarios: Admin

### Consideraciones
- Limite de 3 sessiones por usuario
- 

# Sesiones - sessions
### Columnas
- id **string** identificador unico de la sesion del usuario
- expireDate **bigInt** fecha en segundos del limite de sesion del usuario

- userId ***relation*** uno a muchos (a que usuario pertenece la sesion) 


### Consideraciones
- Maximo 3 sesiones por usuario




# NOTAS MIDU
- hashear el password con bcrypt
- id-username-password
- validar username y password (requerimientos en el nombre del usuario) - se requiere definir las condiciones
- validar que el user name sea unico
- usa bcryupt para comparar el passwword ingresado con el hash