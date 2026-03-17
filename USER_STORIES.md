# User Stories

A continuación dejamos la constancia de las historias de usuario redactadas para este proyecto.

---

## 1. HDU_1: Registrar usuarios

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente |
| **Quiero** | registrarme con mis credenciales: nombre de usuario y contraseña |
| **Para** | registrarme en el sistema |

### Criterios de aceptación

**Criterio 1 - Registro exitoso**
- **Dado**: que ingreso un nombre de usuario y una contraseña
- **Cuando**: confirmo la información
- **Entonces**: el sistema debe registrarme

**Criterio 2 - Registro fallido**
- **Dado**: que ingreso mi información con campos vacíos en el formulario de registro
- **Cuando**: confirmo la información
- **Entonces**: el sistema debe mostrar un mensaje de error indicando los campos vacíos que son obligatorios y no finalizar el registro

**Criterio 3 - Registro duplicado**
- **Dado**: que ingreso un nombre de usuario ya registrado
- **Cuando**: confirmo la información
- **Entonces**: el sistema debe mostrar un mensaje de error indicando que dicho nombre de usuario ya se encuentra registrado y no finalizar el registro

---

## 2. HDU_2: Iniciar sesión

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente |
| **Quiero** | iniciar sesión con mis credenciales: nombre de usuario y contraseña |
| **Para** | acceder al sistema |

### Criterios de aceptación

**Criterio 1 - Inicio de sesión válido**
- **Dado**: que ingreso un nombre de usuario y contraseña
- **Cuando**: confirmo la información y las credenciales coinciden con algún usuario registrado
- **Entonces**: el sistema permitirá el acceso a la pagina principal

**Criterio 2 - Inicio de sesión con credenciales inválidas**
- **Dado**: que ingreso un nombre de usuario y contraseña
- **Cuando**: confirmo la información y las credenciales no coinciden con ningún usuario registrado
- **Entonces**: el sistema denegará el acceso

**Criterio 3 - Inicio de sesión inválido con campos vacíos**
- **Dado**: que relleno el formulario de inicio de sesión con un campo obligatorio vacío
- **Cuando**: confirmo la información
- **Entonces**: el sistema debe resaltar el campo faltante y no procesar el inicio de sesión

---

## 3. HDU_3: Crear un nuevo curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente autenticado en el sistema |
| **Quiero** | crear cursos |
| **Para** | gestionar la información de grupos, estudiantes y del programa académico |

### Criterios de aceptación

**Criterio 1 - Crear curso exitosamente**
- **Dado**: que ingreso el título del curso
- **Cuando**: confirmo la información y el nombre del curso no existe en el sistema
- **Entonces**: el sistema creará el curso

**Criterio 2 - Crear curso duplicado**
- **Dado**: que ingreso el título del curso
- **Cuando**: confirmo la información
- **y**: el nombre del curso ya existe en el sistema
- **Entonces**: el sistema debe mostrar un mensaje de error indicando que ese curso ya existe y no procesará la creación de uno nuevo

**Criterio 3 - Modificar curso**
- **Dado**: un docente edita el título de un curso
- **Cuando**: este confirma la información y el título no coincida con un curso ya creado
- **Entonces**: el sistema debe cambiar el título del curso

---

## 4. HDU_4: Consultar curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente autenticado en el sistema  |
| **Quiero** | consultar mis cursos |
| **Para** | visualizar la información relacionada | 

### Criterios de aceptación

**Criterio 1 - Visualizar detalle del curso**
- **Dado**: que selecciono un curso existente en la página principal
- **Cuando**: se carga la pantalla del detalle del curso
- **Entonces**: debo de poder visualizar los detalles del curso