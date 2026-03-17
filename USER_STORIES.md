# User Stories
A continuación dejamos la constancia de las historias de usuario redactadas para este proyecto.
## 1. HDU_1: Registrar usuarios
`Como` docente
`Quiero` registrarme con mis credenciales: nombre de usuario y contraseña
`Para` acceder al sistema

### Criterios de aceptación
#### Criterio 1 - Registro exitoso
`Dado` que un docente ingresa su usuario y contraseña
`Cuando` cuando este confirme la información
`Entonces` el sistema lo guardará en el sistema

#### Criterio 2 - Registro fallido
`Dado` que el docente deja campos vacíos en el formulario de registro
`Cuando` cuando este confirme la información
`Entonces` el sistema debe mostrar un error indicando los campos vacíos que son obligatorios y no finalizar el registro

#### Criterio 3 - Registro duplicado
`Dado` que el docente ingresa un usuario ya registrado
`Cuando` cuando este confirme la información
`Entonces` el sistema debe mostrar un error indicando que dicho nombre de usuario ya se encuentra registrado y no finalizar el registro