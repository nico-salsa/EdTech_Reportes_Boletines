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
- **Dado**: que edito el título de un curso
- **Cuando**: confirmo la información y el título no coincide con un curso ya creado
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
- **Entonces**: debo de poder visualizar la lista de estudiantes del curso con su nombre completo, su grupo asignado y sus promedios 

## 5. HDU_5: Agregar estudiantes a la lista de estudiantes de un curso
> [!NOTE]
> Esta historia de usuario tiene 2 responsabilidades que fueron contempladas como necesarias para la HU, ya que el registro de los estudiantes al sistema ocurre utilizando un metodo *"on-the-fly"* con la finalidad de aportar mejor experiencia de usuario para los docentes que utilicen la herramienta.

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de gestión de estudiantes de un curso |
| **Quiero** | agregar estudiantes al curso |
| **Para** | gestionar sus notas y entregables en el curso | 

### Criterios de aceptación

**Criterio 1 - Agregar estudiante a la lista de estudiantes del curso**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes
- **Cuando**: ingreso un estudiante con un ID nuevo
- **Y**: relleno la información personal obligatoria del estudiante (ID, Nombre completo, Correo)
- **Entonces**: debo de poder ver al estudiante en la lista de estudiantes del curso, y el estudiante debe quedar registrado en el sistema

**Criterio 2 - Agregar estudiante a la lista de estudiantes del curso con campos obligatorios vacíos**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes
- **Cuando**: ingreso un estudiante con un ID nuevo
- **Y**: relleno la información personal obligatoria del estudiante de forma incompleta (ID, Nombre completo, Correo)
- **Entonces**: el estudiante no se debe agregar a la lista de estudiantes del curso, y no se procesará la creacion del estudiante en el sistema

**Criterio 3 - Agregar estudiante existente a la lista de estudiantes del curso**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes
- **Cuando**: ingreso un estudiante con un ID existente
- **Entonces**: debo de poder ver al estudiante en la lista de estudiantes del curso, con su información personal autocompletada

## 6. HDU_6: Agregar grupos a un curso creado

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de gestión de grupos de un curso |
| **Quiero** | agregar grupos al curso |
| **Para** | gestionar diferentes estudiantes con horarios distintos en grupos separados | 

### Criterios de aceptación

**Criterio 1 - Agregar grupo a la lista de grupos del curso**
- **Dado**: que me encuentro en la pantalla de gestion de grupos
- **Cuando**: selecciono crear nuevo grupo
- **Y**: asigno un nombre al grupo
- **Entonces**: debo de poder ver el grupo en la lista de grupos del curso

**Criterio 2 - Agregar grupo a la lista de grupos del curso con campos obligatorios vacíos**
- **Dado**: que me encuentro en la pantalla de gestion de grupos
- **Cuando**: selecciono crear nuevo grupo
- **Y**: dejo vacío el nombre del grupo
- **Entonces**: el sistema debe resaltar el campo faltante y no crear el nuevo grupo

**Criterio 3 - Agregar grupo con nombre ya existente en la lista de grupos**
- **Dado**: que me encuentro en la pantalla de gestion de grupos
- **Cuando**: selecciono crear nuevo grupo
- **Y**: asigno un nombre al grupo
- **Y**: el nombre del grupo que ingresé coincide con alguno que ya existe en la lista de grupos del curso
- **Entonces**: el sistema debe mostrar un mensaje de error indicando que ese grupo ya existe en el curso y no procesará la creación de uno nuevo


## 7. HDU_7: Asignar estudiante a un grupo dentro de un curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de gestión de estudiantes de un curso |
| **Quiero** | asignar un estudiante de la lista de estudiantes del curso a un grupo especifico |
| **Para** | separar los estudiantes de un curso en distintos grupos | 

### Criterios de aceptación

**Criterio 1 - asignar estudiante a un grupo**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes
- **Cuando**: asigno un estudiante del curso a un grupo especifico
- **Entonces**: debo de poder ver al estudiante en la lista de estudiantes del grupo que corresponde al curso

**Criterio 2 - asignar estudiante repetido a un grupo**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes
- **Cuando**: asigno un estudiante del curso a un grupo especifico en el cual ya se encuentra
- **Entonces**: el sistema debe mostrar un mensaje de error indicando que ese estudiante ya forma parte del grupo y no procesará la asignacion al grupo

**Criterio 3 - asignar estudiante que ya pertenece a un grupo a un grupo nuevo**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes
- **Cuando**: asigno un estudiante del curso a un grupo especifico
- **Y**: el estudiante ya forma parte de otro grupo del curso
- **Entonces**: el sistema debe mostrar un mensaje de error indicando que ese estudiante ya forma parte de otro grupo dentro del curso y no procesará la asignacion
---

## 8. HDU_8: Desasignar estudiante de un grupo dentro del curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de gestión de estudiantes de un curso |
| **Quiero** | desasignar a un estudiante de la lista de estudiantes de un grupo del curso |
| **Para** | gestionar a los estudiantes que pertenecen al grupo | 

### Criterios de aceptación

**Criterio 1 - desasignar estudiante de un grupo**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes
- **Cuando**: desasigno a un estudiante de un grupo
- **Entonces**: el estudiante que fue desasignado no deberia de aparecer en la lista de estudiantes del grupo
- **Y** el estudiante deberia de permanecer en la lista general de estudiantes del curso

## 9. HDU_9: Eliminar grupo dentro de un curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de gestión de estudiantes de un curso |
| **Quiero** | eliminar un grupo dentro del curso |
| **Para** | gestionar los grupos que tiene el curso | 

**Criterio 1 - eliminar grupo vacío**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes de un curso
- **Cuando**: elimino un grupo dentro del curso
- **Y**: la lista de estudiantes del grupo está vacía
- **Entonces**: el grupo eliminado no se debería de ver en la lista de grupos del curso

**Criterio 2 - eliminar grupo con estudiantes de manera exitosa**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes de un curso
- **Cuando**: elimino un grupo dentro del curso
- **Y**: hay estudiantes dentro de la lista de estudiantes del grupo
- **Y**: confirmo la eliminación del grupo
- **Entonces**: el grupo eliminado no se debería de ver en la lista de grupos del curso
- **Y**: los estudiantes pertenecientes al grupo eliminado deberían permanecer en la lista general de estudiantes del curso

**Criterio 3 - eliminar grupo con estudiantes de manera fallida**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes de un curso
- **Cuando**: elimino un grupo dentro del curso
- **Y**: hay estudiantes dentro de la lista de estudiantes del grupo
- **Y**: cancelo la eliminación del grupo
- **Entonces**: el grupo debe de permanecer en la lista de grupos del curso
- **Y**: los estudiantes pertenecientes al grupo deben permanecer en la lista de estudiantes del grupo

## 10. HDU_10: Actualizar título de un grupo dentro del curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de gestión de estudiantes de un curso |
| **Quiero** | actualizar el nombre de un grupo dentro del curso |
| **Para** | gestionar los grupos que tiene el curso | 

**Criterio 1 - actualizar título de un grupo de manera exitosa**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes de un curso
- **Cuando**: actualizo el titulo de un grupo dentro del curso
- **Y**: el nuevo titulo del grupo no coincide con otro titulo existente
- **Entonces**: el cambio de titulo debe verse reflejado en la lista de grupos del curso

**Criterio 2 - actualizar título de un grupo con titulo duplicado**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes de un curso
- **Cuando**: actualizo el titulo de un grupo dentro del curso
- **Y**: el nuevo titulo del grupo coincide con otro titulo existente
- **Entonces**: el sistema no debería de guardar el cambio
- **Y**: el sistema debe mostrar un mensaje de error indicando que el titulo ya está en uso

**Criterio 3 - actualizar título de un grupo con titulo vacío**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes de un curso
- **Cuando**: actualizo el titulo de un grupo dentro del curso
- **Y**: el nuevo titulo del grupo está vacío
- **Entonces**: el sistema no debería de guardar el cambio
- **Y**: el sistema debe mostrar un mensaje de error indicando que el nuevo título está vacío

## 11. HDU_11: Definir programa del curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de detalle del curso |
| **Quiero** | definir un programa dentro del curso |
| **Para** | agregar instancias evaluatorias con un porcentaje de ponderacion determinado | 

**Criterio 1 - definir programa existosamente**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: defino un programa
- **Y**: agrego {cantidad} de instancias evaluatorias
- **Y**: asigno un porcentaje de ponderacion a todas las instancias evaluatorias agregadas
- **Y**: la suma de los porcentajes de ponderacion de todas las instancias evaluatorias coincide con el 100%
- **Y**: confirmo la definicion del programa
- **Entonces**: el sistema debe guardar el programa del curso
- **Y**: las instancias evaluatorias deben verse en la pantalla de detalle del curso

**Criterio 2 - definir programa con instancias de evaluación vacías**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: defino un programa
- **Y**: agrego {cantidad} de instancias evaluatorias
- **Y**: al menos una instancia evaluatoria no tiene nombre
- **Y**: confirmo la definicion del programa
- **Entonces**: la definicion del curso no se debe procesar
- **Y**: el sistema debe notificar que no se permiten agregar instancias evaluatorias sin nombre
- **Y**: se debe permitir que las actividades evaluatorias con titulo vacío sean completadas

**Criterio 3 - definir programa cuyas instancias de evaluación no sumen un 100%**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: defino un programa
- **Y**: agrego {cantidad} de instancias evaluatorias
- **Y**: asigno un porcentaje de ponderacion a todas las instancias evaluatorias agregadas
- **Y**: la suma de los porcentajes de ponderacion de todas las instancias evaluatorias no coincide con el 100%
- **Y**: confirmo la definicion del programa
- **Entonces**: la definicion del curso no se debe procesar
- **Y**: el sistema debe notificar que la suma de porcentajes de ponderacion de las instancias evaluatorias tienen que sumar un total del 100%
- **Y**: se debe permitir que los porcentajes de ponderación se actualicen para lograr que la suma de estos sea del 100%