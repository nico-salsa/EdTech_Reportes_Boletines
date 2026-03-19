# User Stories

A continuación dejamos la constancia de las historias de usuario redactadas para este proyecto.

> [!NOTE]
> Estas historias de usuario están pensadas para principalmente la fase Backend.
>
> `DoR` significa "Definition of Ready"
>
> `DoD` significa "Definition of Done"

---

## 0.1. HDU_T1: Definir base frontend de la historia funcional

| Aspecto | Descripción |
|---------|-------------|
| **Como** | equipo de desarrollo
| **Quiero** | dejar definida la base visual y de interacción de una historia funcional |
| **Para** | poder implementarla en frontend sin ambiguedades |

### Criterios de aceptación

**Criterio 1 - Mockup definido**
- **Dado**: que voy a desarrollar una historia funcional
- **Cuando**: se revisa el alcance del frontend
- **Entonces**: debe existir un mockup, flujo o pantalla base que represente la interacción esperada

**Criterio 2 - Estados de pantalla definidos**
- **Dado**: que la historia que voy a desarrollar tiene interacción con el usuario
- **Cuando**: se revisa su diseño funcional
- **Entonces**: deben estar definidos al menos el estado inicial, el estado exitoso y los estados intermedios definidos por la historia

---

## 0.2. HDU_T2: Definir contrato backend

| Aspecto | Descripción |
|---------|-------------|
| **Como** | equipo de desarrollo
| **Quiero** | dejar definido el contrato backend de una historia funcional |
| **Para** | implementar la historia sin inconsistencias entre frontend, lógica y persistencia de datos |

### Criterios de aceptación

**Criterio 1 - Endpoint definido**
- **Dado**: que una historia requiere backend
- **Cuando**: se revisa el diseño técnico
- **Entonces**: debe quedar definida la ruta del endpoint, su nomenclatura y el llamado (verbo) HTTP correspondiente

**Criterio 2 - Request definido**
- **Dado**: que estoy revisando un endpoint definido
- **Cuando**: se revisa el contrato de entrada
- **Entonces**: debo encontrar definidos los campos de la solicitud, especificando cuáles son obligatorios y cuál es su formato esperado

**Criterio 3 - Response definido**
- **Dado**: que estoy revisando un endpoint ya definido
- **Cuando**: se revisa el contrato de salida
- **Entonces**: debo encontrar definido la estructura de la respuesta exitosa

**Criterio 4 - Errores definidos**
- **Dado**: se contempla fallos de validación y negocio
- **Cuando**: se revisa el contrato backend
- **Entonces**: debo observar que están definidos los códigos de respuesta y la estructura de error para: formularios incompletos y creación de objetos con información duplicada

---

## 1. HDU_1: Registrar usuarios

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente |
| **Quiero** | registrarme con mis credenciales: nombre de usuario y contraseña |
| **Para** | registrarme en el sistema |

### DoR

- Existe la pantalla de registro (mockup)
- El contrato para registrar el usuario con `nombre de usuario` y `contraseña` está definido.
- La respuesta de error para campos vacío está definido
- La respuesta de error para nombre de usuario duplicado está definido

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
- **Entonces**: el sistema debe mostrar un mensaje de error indicando que dicho nombre de usuario ya se encuentra registrado y no finalizar el registro+

### DoD

- Un docente puede registrarse enviando `nombre de usuario` y `contraseña`
- Si `nombre de usuario` o `contraseña` están vacíos, el sistema no registra al docente y muestra qué campo obligatorio falta
- Si `nombre de usuario` ya existe, el sistema no registra al docente y muestra mensaje de usuario ya existente con ese nombre
- El registro exitoso deja al usuario creado en el sistema

---

## 2. HDU_2: Iniciar sesión

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente |
| **Quiero** | iniciar sesión con mis credenciales: nombre de usuario y contraseña |
| **Para** | acceder al sistema |

### DoR

- Existe al menos un usuario registrado para probar el login
- Está definida las respuestas para campos vacíos y credenciales inválidas

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

### DoD

- Si el docente ingresa un `nombre de usuario` y `contraseña` registrados, el sistema permite el aceso a la página principal.
- Si el docente ingresa credenciales no registradas, el sistema deniega el acceso
- Ante campo vacío el sistema no procesa el inicio de sesión y resalta el campo faltante

---

## 3. HDU_3: Crear un nuevo curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente autenticado en el sistema |
| **Quiero** | crear cursos |
| **Para** | gestionar la información de grupos, estudiantes y del programa académico |

### DoR

- La definición del contrato que válida el nombre del curso ya existe y está estandarizada

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

### DoD

- El curso creado o actualizado queda visible en el sistema

---

## 4. HDU_4: Consultar curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente autenticado en el sistema  |
| **Quiero** | consultar mis cursos |
| **Para** | visualizar la información relacionada | 

### DoR

- Existe al menos 1 curso creado
- El detalle del curso muestra una tabla con `nombre completo`, `grupo asignado` y `promedio` de los estudiantes.

### Criterios de aceptación

**Criterio 1 - Visualizar detalle del curso**
- **Dado**: que selecciono un curso existente en la página principal
- **Cuando**: se carga la pantalla del detalle del curso
- **Entonces**: debo de poder visualizar la lista de estudiantes del curso con su nombre completo, su grupo asignado y sus promedios 

### DoD

- Para cada estudiante se muestra la información completa: `nombre completo`, `grupo asignado` y `promedio`

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
- **Entonces**: debo de poder ver al estudiante en la lista de estudiantes del curso
- **Y**: el estudiante debe quedar registrado en el sistema

**Criterio 2 - Agregar estudiante a la lista de estudiantes del curso con campos obligatorios vacíos**
- **Dado**: que me encuentro en la pantalla de gestion de estudiantes
- **Cuando**: ingreso un estudiante con un ID nuevo
- **Y**: relleno la información personal obligatoria del estudiante de forma incompleta (ID, Nombre completo, Correo)
- **Entonces**: el estudiante no se debe agregar a la lista de estudiantes del curso
- **Y** no se procesará la creacion del estudiante en el sistema

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

### Criterios de aceptación

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

### Criterios de aceptación

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

### Criterios de aceptación

**Criterio 1 - definir programa existosamente**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de definir un programa
- **Y**: agrego una lista de instancias evaluatorias
- **Y**: asigno un porcentaje de ponderacion a todas las instancias evaluatorias agregadas
- **Y**: la suma de los porcentajes de ponderacion de todas las instancias evaluatorias coincide con el 100%
- **Y**: confirmo la definicion del programa
- **Entonces**: el sistema debe guardar el programa del curso
- **Y**: las instancias evaluatorias deben verse en la pantalla de detalle del curso

**Criterio 2 - definir programa con instancias de evaluación con nombre vacio**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de definir un programa
- **Y**: agrego una lista de instancias evaluatorias
- **Y**: al menos una instancia evaluatoria no tiene nombre
- **Y**: confirmo la definicion del programa
- **Entonces**: la definicion del programa no se debe procesar
- **Y**: el sistema debe notificar que no se permiten agregar instancias evaluatorias sin nombre
- **Y**: el sistema debe permitir que las actividades evaluatorias con nombre vacío sean completadas

**Criterio 3 - definir programa cuyas instancias de evaluación no sumen un 100%**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de definir un programa
- **Y**: agrego una lista de instancias evaluatorias
- **Y**: asigno un porcentaje de ponderacion a todas las instancias evaluatorias agregadas
- **Y**: la suma de los porcentajes de ponderacion de todas las instancias evaluatorias no coincide con el 100%
- **Y**: confirmo la definicion del programa
- **Entonces**: la definicion del programa no se debe procesar
- **Y**: el sistema debe notificar que la suma de porcentajes de ponderacion de las instancias evaluatorias tienen que sumar un total del 100%
- **Y**: se debe permitir que los porcentajes de ponderación se actualicen para lograr que la suma de estos sea del 100%

**Criterio 4 - definir programa mediante el uso de la ponderación equitativa**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de definir un programa
- **Y**: agrego una lista de instancias evaluatorias
- **Y**: selecciono la opcion de ponderar equitativamente
- **Y**: confirmo la definicion del programa
- **Entonces**: el sistema debe guardar el programa del curso
- **Y**: las instancias evaluatorias deben verse en la pantalla de detalle del curso

**Criterio 5 - definir programa con instancias de evaluación con peso cero**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de definir un programa
- **Y**: agrego una lista de instancias evaluatorias
- **Y**: al menos una instancia evaluatoria no tiene un porcentaje de ponderacion o su porcentaje es igual a 0
- **Y**: confirmo la definicion del programa
- **Entonces**: la definicion del programa no se debe procesar
- **Y**: el sistema debe notificar que cada instancia debe tener una ponderación mayor al 0%
- **Y**: el sistema debe permitir que las actividades evaluatorias sin ponderación sean completadas

**Criterio 6 - definir programa con instancias de evaluación con porcentaje de ponderación negativo**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de definir un programa
- **Y**: agrego una lista de instancias evaluatorias
- **Y**: al menos una instancia evaluatoria tiene un porcentaje de ponderacion negativo
- **Y**: confirmo la definicion del programa
- **Entonces**: la definicion del programa no se debe procesar
- **Y**: el sistema debe notificar que cada instancia debe tener una ponderación mayor al 0%
- **Y**: el sistema debe permitir que las actividades evaluatorias con ponderación negativa sean editadas

**Criterio 7 - definir programa con instancias de evaluación con nombre duplicado**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de definir un programa
- **Y**: agrego una lista de instancias evaluatorias
- **Y**: al menos dos instancias evaluatorias tienen el mismo nombre
- **Y**: confirmo la definicion del programa
- **Entonces**: la definicion del programa **no** se debe procesar
- **Y**: el sistema debe notificar que las instancias definidas no deben contener nombres duplicados

## 12. HDU_12: Eliminar instancia de evaluacion del programa del curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de detalle del curso |
| **Quiero** | editar el programa del curso |
| **Para** | eliminar instancias evaluatorias del curso | 

### Criterios de aceptación

**Criterio 1 - eliminar instancia evaluatoria exitosamente**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de editar el programa
- **Y**: elimino una instancia de evaluacion de la lista de instancias del programa
- **Y**: actualizo los porcentajes de ponderacion de las instancias del programa
- **Y**: la suma de los porcentajes de ponderacion de todas las instancias evaluatorias coincide con el 100%
- **Y**: confirmo la edición del programa
- **Entonces**: la edicion del programa se debe de procesar
- **Y**: la instancia eliminada ya no debe aparecer en la pantalla de detalle

**Criterio 2 - eliminar instancia evaluatoria y la suma de los porcentajes de ponderación no es exactamente del 100%**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de editar el programa
- **Y**: elimino una instancia de evaluacion de la lista de instancias del programa
- **Y**: la suma de los porcentajes de ponderacion de todas las instancias evaluatorias no coincide exactamente con el 100%
- **Y**: confirmo la edición del programa
- **Entonces**: la edicion del programa **no** se debe de procesar
- **Y**: el sistema debe notificar que la suma de porcentajes de ponderacion de las instancias evaluatorias tienen que sumar un total del 100%

## 13. HDU_13: Actualizar instancia de evaluacion del programa del curso
> [!IMPORTANT]
> Integridad de Datos: Al confirmar una actualización de ponderación en un programa que ya posee notas registradas, el sistema debe recalcular automáticamente todos los promedios (ponderados y generales) de los estudiantes del curso para reflejar los nuevos pesos.

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de detalle del curso |
| **Quiero** | editar el programa del curso |
| **Para** | actualizar instancias evaluatorias del curso | 

### Criterios de aceptación

**Criterio 1 - actualizar los porcentajes de ponderacion de las instancias de evaluacion del curso exitosamente**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de editar el programa
- **Y**: edito la ponderación de una instancia de evaluacion de la lista de instancias del programa
- **Y**: la suma de los porcentajes de ponderacion de todas las instancias evaluatorias coincide exactamente con el 100%
- **Y**: confirmo la edición del programa
- **Entonces**: la edicion del programa se debe de procesar
- **Y**: la modificación debe reflejarse en la pantalla de detalle

**Criterio 2 - actualizar los porcentajes de ponderacion de las instancias de evaluacion del curso cuya suma no es exactamente del 100%**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de editar el programa
- **Y**: edito la ponderación de una instancia de evaluacion de la lista de instancias del programa
- **Y**: la suma de los porcentajes de ponderacion de todas las instancias evaluatorias **no es** exactamente del 100%
- **Y**: confirmo la edición del programa
- **Entonces**: la edicion del programa **no** se debe de procesar
- **Y**: el sistema debe notificar que la suma de porcentajes de ponderacion de las instancias evaluatorias tienen que sumar un total del 100%

**Criterio 3 - actualizar los porcentajes de ponderacion de las instancias de evaluacion con ponderación negativa o '0%'**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de editar el programa
- **Y**: edito la ponderación de una instancia de evaluacion de la lista de instancias del programa con ponderacion menor o igual a 0
- **Y**: confirmo la edición del programa
- **Entonces**: la edicion del programa **no** se debe de procesar
- **Y**: el sistema debe notificar que cada instancia debe de tener una ponderación mayor al 0%

**Criterio 4 - actualizar el nombre de las instancias de evaluacion del curso exitosamente**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de editar el programa
- **Y**: edito el nombre de una instancia de evaluacion de la lista de instancias del programa
- **Y**: el nuevo nombre **no** se encuentra vacío
- **Y**: confirmo la edición del programa
- **Entonces**: la edicion del programa se debe de procesar
- **Y**: las instancias evaluatorias editadas deben verse en la pantalla de detalle del curso

**Criterio 5 - actualizar el nombre de las instancias de evaluacion del curso con campo vacío**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de editar el programa
- **Y**: edito el nombre de una instancia de evaluacion de la lista de instancias del programa
- **Y**: el nuevo nombre **se encuentra vacío**
- **Y**: confirmo la edición del programa
- **Entonces**: la edicion del programa **no** se debe de procesar
- **Y**: el sistema debe resaltar los nombres vacíos

**Criterio 6 - actualizar el nombre de las instancias de evaluacion con nombre duplicado**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opcion de editar el programa
- **Y**: edito el nombre de una instancia de evaluacion de la lista de instancias del programa
- **Y**: el nuevo nombre ya se encuentra en la lista de instancias de evaluacion del programa
- **Y**: confirmo la edición del programa
- **Entonces**: la edicion del programa **no** se debe de procesar
- **Y**: el sistema debe resaltar los nombres repetidos

## 14. HDU_14: registrar nota de una instancia de evaluacion del programa a un estudiante del curso
> [!NOTE]
> Diseño de Calificación Abierto: Se ha optado por no imponer un límite superior en la escala de notas para garantizar que el sistema sea compatible con diversos modelos académicos (escalas 1-10, 1-12, 1-100, etc.). La única restricción técnica es que el valor debe ser numérico y mayor o igual a 0. 

> [!TIP]
> Regla de oro: las notas 'nulas' o 'vacías' equivalen a una nota de 0 para el cálculo de los promedios de los estudiantes

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de detalle del curso |
| **Quiero** | registrar la nota de una instancia de evaluacion de un estudiante |
| **Para** | llevar un registro de las notas del estudiante y su promedio | 

### Criterios de aceptación

**Criterio 1 - registrar una nota de una instancia de evaluacion del estudiante exitosamente**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opción de registrar nota de una instancia de evaluacion a un estudiante
- **Y**: ingreso una nota mayor o igual a '0' (tenga o no una nota previa)
- **Entonces**: el sistema debe guardar la nota del estudiante en la instancia seleccionada
- **Y**: la nueva nota del estudiante debe verse reflejada en la pantalla de detalle del curso
- **Y**: el promedio ponderado del estudiante debe actualizarse automáticamente en la pantalla de detalle.
- **Y**: el promedio general del estudiante debe actualizarse automáticamente en la pantalla de detalle.

**Criterio 2 - registrar una nota **negativa** de una instancia de evaluacion del estudiante**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opción de registrar nota de una instancia de evaluacion a un estudiante
- **Y**: ingreso una nota menor a '0' (tenga o no una nota previa)
- **Entonces**: la nota no se debe guardar
- **Y**: el sistema debe notificar que no se permiten registrar notas negativas

**Criterio 3 - registrar una nota vacía de una instancia de evaluacion del estudiante**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opción de registrar nota de una instancia de evaluacion a un estudiante
- **Y**: Ingreso una nota **nula** (tenga o no una nota previa)
- **Entonces**: el sistema debe guardar la nota del estudiante en la instancia seleccionada
- **Y**: el sistema debe resaltar que la nota es nula
- **Y**: el promedio ponderado del estudiante debe actualizarse automáticamente en la pantalla de detalle, considerando las notas **nulas** como '0' para la suma del promedio.
- **Y**: el promedio general del estudiante debe actualizarse automáticamente en la pantalla de detalle, considerando las notas **nulas** como '0' para la suma del promedio.

**Criterio 4 - registrar una nota con caracteres no numéricos de una instancia de evaluacion del estudiante**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opción de registrar nota de una instancia de evaluacion a un estudiante
- **Y**: ingreso una nota con un valor alfanumérico o con símbolos 
- **Entonces**: la nota no se debe guardar
- **Y**: el sistema debe mostrar un error de formato

## 15. HDU_15: generar boletín del estudiante de un curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de detalle del curso |
| **Quiero** | generar un boletín reflejando las notas y promedio de un estudiante del curso |
| **Para** | descargar los boletines academicos de los estudiantes en distintos formatos | 

### Criterios de aceptación

**Criterio 1 - generar boletín de un estudiante del curso**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opción de generar boletin de un estudiante del curso
- **Y**: selecciono uno de los formatos disponibles
- **Entonces**: el sistema debe descargar el boletín con la información completa del estudiante, y la información de sus notas y promedios del curso en el formato seleccionado

**Criterio 2 - generar boletín de un estudiante del curso con al menos una instancia de evaluación vacía**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Cuando**: selecciono la opción de generar boletin de un estudiante del curso
- **Y**: el estudiante tiene una nota **vacía** en al menos una instancia de evaluación
- **Y**: el sistema informa sobre la existencia de notas **vacías** en las instancias de evaluación
- **Y**: confirmo la generación del boletin
- **Y**: selecciono uno de los formatos disponibles
- **Entonces**: el sistema debe descargar el boletín con la información completa del estudiante, y la información de sus notas y promedios del curso en el formato seleccionado

## 16. HDU_16: generar reporte de calificaciones de todos los estudiantes de un curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de detalle del curso |
| **Quiero** | generar un reporte consolidado de calificaciones de todos los estudiantes |
| **Para** | analizar el rendimiento grupal y descargar el acta de notas final | 

### Criterios de aceptación

**Criterio 1 - generar reporte consolidado exitosamente**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Y**: que el curso tiene estudiantes registrados y un programa definido.
- **Cuando**: selecciono la opción de generar reporte grupal
- **Y**: selecciono uno de los formatos disponibles
- **Entonces**: el sistema debe descargar un archivo que contenga la lista de todos los estudiantes en filas, con sus respectivas notas en columnas y sus promedios finales en el formato seleccionado

**Criterio 2 - advertencia de registros incompletos**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Y**: que el curso tiene estudiantes registrados y un programa definido
- **Cuando**: selecciono la opción de generar reporte grupal
- **Y**: selecciono uno de los formatos disponibles
- **Y**: existen estudiantes con instancias de evaluación sin calificar (notas nulas)
- **Entonces**: el sistema debe advertir que el reporte se generará con notas incompletas antes de iniciar la descarga
- **Y**: el sistema debe descargar un archivo que contenga la lista de todos los estudiantes en filas, con sus respectivas notas en columnas y sus promedios finales en el formato seleccionado

## 17. HDU_17: dar de baja a un estudiante del curso

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo la pantalla de detalle del curso |
| **Quiero** | dar de baja a un estudiante del curso |
| **Para** | gestionar la lista de estudiantes del curso | 

### Criterios de aceptación

**Criterio 1 - dar de baja a un estudiante del curso sin notas registradas**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Y**: que el curso tiene estudiantes registrados
- **Cuando**: selecciono la opción de dar de baja a un estudiante
- **Y**: confirmo la baja del estudiante
- **Entonces**: el sistema debe de dar de baja al estudiante del curso
- **Y**: el estudiante que se dió de baja debe permanecer en el sistema

**Criterio 2 - dar de baja a un estudiante del curso con notas registradas**
- **Dado**: que me encuentro en la pantalla de detalle del curso
- **Y**: que el curso tiene estudiantes registrados
- **Cuando**: selecciono la opción de dar de baja a un estudiante
- **Y**: confirmo la baja del estudiante
- **Entonces**: el sistema debe de dar de baja al estudiante del curso
- **Y**: eliminar sus notas de las instancias evaluatorias del curso
- **Y**: el estudiante que se dió de baja debe permanecer en el sistema

## 18. HDU_18: actualizar información personal de un estudiante

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo el directorio de estudiantes |
| **Quiero** | editar la información personal de un estudiante registrado |
| **Para** | corregir errores de registro de forma centralizada | 

### Criterios de aceptación

**Criterio 1 - actualización exitosa del estudiante**
- **Dado**: que me encuentro en el directorio de estudiantes
- **Cuando**: selecciono la opción de editar un estudiante
- **Y**: modifico su Nombre, ID o Correo con formatos válidos
- **Y**: confirmo los cambios
- **Entonces**: el sistema debe actualizar la información del estudiante globalmente
- **Y**: los cambios deben verse reflejados automáticamente en todos los cursos donde el estudiante esté inscrito

**Criterio 2 - actualización con ID duplicado**
- **Dado**: que me encuentro en el directorio de estudiantes
- **Cuando**: selecciono la opción de editar un estudiante
- **Y**: modifico su ID por uno que ya existe en el sistema
- **Entonces**: el sistema debe mostrar un mensaje de error indicando que el ID ya está en uso
- **Y**: el sistema no debe proceder con el guardado los cambios

**Criterio 3 - actualización con campo obligatorio vacío**
- **Dado**: que me encuentro en el directorio de estudiantes
- **Cuando**: selecciono la opción de editar un estudiante
- **Y**: modifico su Nombre, ID o Correo dejando el campo vacío
- **Entonces**: el sistema debe mostrar un mensaje de error indicando los campos vacíos
- **Y**: el sistema no debe proceder con el guardado los cambios

## 19. HDU_19: eliminar estudiante del sistema (global)

| Aspecto | Descripción |
|---------|-------------|
| **Como** | docente viendo el directorio de estudiantes |
| **Quiero** | eliminar definitivamente a un estudiante del sistema |
| **Para** | limpiar la base de datos de registros erróneos o duplicados |

### Criterios de aceptación

**Criterio 1 - eliminación definitiva exitosa**
- **Dado**: que me encuentro en el directorio de estudiantes
- **Cuando**: selecciono la opción de eliminar a un estudiante
- **Y**: el sistema muestra una advertencia indicando que se perderán sus notas de todos los cursos
- **Y**: confirmo la eliminación
- **Entonces**: el sistema debe borrar el registro del estudiante globalmente
- **Y**: el estudiante debe desaparecer de todas las listas de cursos donde figuraba previamente

**Criterio 2 - cancelación de la eliminación**
- **Dado**: que me encuentro en el directorio de estudiantes
- **Cuando**: selecciono la opción de eliminar a un estudiante
- **Y**: el sistema muestra una advertencia indicando que se perderán sus notas de todos los cursos
- **Y**: selecciono la opción de cancelar
- **Entonces**: el sistema no debe realizar ningún cambio
- **Y**: el registro del estudiante debe permanecer intacto en el directorio y en sus respectivos cursos