# User Stories
A continuación dejamos la constancia de las historias de usuario redactadas para este proyecto.
## 1. HDU_1: Registrar usuarios
`Como` docente

`Quiero` registrarme con mis credenciales: nombre de usuario y contraseña

`Para` registrarme en el sistema

### Criterios de aceptación
#### Criterio 1 - Registro exitoso
`Dado` que un docente ingresa su usuario y contraseña

`Cuando` este confirme la información

`Entonces` el sistema lo guardará en el sistema

#### Criterio 2 - Registro fallido
`Dado` que el docente deja campos vacíos en el formulario de registro

`Cuando` este confirme la información

`Entonces` el sistema debe mostrar un error indicando los campos vacíos que son obligatorios y no finalizar el registro

#### Criterio 3 - Registro duplicado
`Dado` que el docente ingresa un usuario ya registrado

`Cuando` este confirme la información

`Entonces` el sistema debe mostrar un error indicando que dicho nombre de usuario ya se encuentra registrado y no finalizar el registro

---

## 2. HDU_2: Iniciar sesión
`Como` docente

`Quiero` iniciar sesión con mis credenciales: nombre de usuario y contraseña

`Para` acceder al sistema

#### Criterio 1 - Inicio de sesión válido
`Dado` que un docente ingresa su usuario y contraseña

`Cuando` este confirme la información

`Y` las credenciales coinciden con algún usuario registrado

`Entonces` el sistema permitirá el acceso al usuario

#### Criterio 2 - Inicio de sesión con credenciales inválidas
`Dado` que un docente ingresa su usuario y contraseña

`Cuando` este confirme la información

`Y` las credenciales no coinciden con ningún usuario registrado

`Entonces` el sistema denegará el acceso al usuario

#### Criterio 3 - Inicio de sesión inválido con campos vacíos
`Dado` que un docente no completa un campo obligatorio

`Cuando` este confirme la información

`Entonces` el sistema debe resaltar el campo faltante y no procesar el inicio de sesión

---

## 3. HDU_3: Crear un nuevo curso
`Como` docente autenticado en el sistema

`Quiero` crear cursos

`Para` gestionar la información de grupos, estudiantes y del programa académico

#### Criterio 1 - Crear curso exitosamente
`Dado` que un docente autenticado ingresa el título del curso

`Cuando` este confirma la información

`Y` el nombre del curso no exista en el sistema

`Entonces` el sistema creará el curso en la página principal

#### Criterio 2 - Crear curso duplicado
`Dado` que un docente autenticado ingresa el título del curso

`Cuando` este confirma la información

`Y` el nombre del curso ya existe en el sistema

`Entonces` el sistema debe mostrar un error indicando que ese curso ya existe y no procesará la creación de uno nuevo

#### Criterio 3 - Modificar curso
`Dado` que un docente edita el título de un curso

`Cuando` este confirma la información

`Y` el título no coincida con un curso ya creado

`Entonces` el sistema debe cambiar el título del curso


## 3. HDU_4: Consultar curso
`Como` 

`Quiero` 

`Para` 