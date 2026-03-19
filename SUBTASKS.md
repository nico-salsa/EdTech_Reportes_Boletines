# SubTasks

A continuación dejamos la constancia de las subtasks redactadas para este proyecto.

---

## HDU_1: Registrar usuarios

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba:** Definir flujos para la validación de contraseñas (longitud mínima, caracteres permitidos) y duplicidad de nombres de usuario.
- **Validación de API:** Automatizar pruebas para las respuestas `201 Created` y `400 Bad Request` (campos vacíos) y `409 Conflict` (usuario duplicado).
- **Pruebas de UI:** Verificar que los mensajes de error sean visibles y que el botón de registro permanezca inactivo mientras haya campos obligatorios vacíos.

#### No funcionales
- **Verificación de seguridad:** Comprobar directamente en base de datos que la contraseña no se almacene en texto plano (hashing)

### Tareas de Desarrollo (Dev)

## HDU_2: Iniciar sesión

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir flujos de "happy path" (credenciales correctas) y flujos negativos (usuario inexistente, contraseña errónea).
- **Validación de API**: Automatizar pruebas para verificar códigos de respuesta: 200 OK (éxito con entrega de Token), 401 Unauthorized (credenciales inválidas) y 400 Bad Request (campos vacíos).
- **Pruebas de UI**: Verificar el redireccionamiento exitoso a la página principal y el resaltado visual de campos obligatorios cuando están vacíos.

#### No funcionales
- **Seguridad (Autenticación)**: Validar que tras un inicio de sesión exitoso, el sistema genere y almacene un token de sesión seguro y no exponga la contraseña en la URL o en logs
- **Usabilidad de Errores**: Comprobar que el mensaje de error para credenciales inválidas sea genérico (ej: "Usuario o contraseña incorrectos") para no dar pistas sobre qué dato falló específicamente.

## HDU_3: Crear nuevo curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir flujos para nombres de cursos con caracteres especiales, longitudes máximas y espacios en blanco al inicio/final
- **Validación de API**: Automatizar pruebas para los métodos POST (crear) y PUT (editar), verificando respuestas 201 Created (éxito), 409 Conflict (duplicado) y 400 Bad Request (título vacío)
- **Pruebas de UI**: Verificar que tras la creación exitosa, el usuario sea redirigido a la vista del nuevo curso o que este aparezca inmediatamente en el listado de la página principal

#### No funcionales
- **Consistencia en Modificación**: Validar que al editar el título de un curso, todos los estudiantes y grupos previamente asignados mantengan su vínculo correctamente

## HDU_4: Consultar curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba**: Definir escenarios para cursos con muchos estudiantes, cursos vacíos y estudiantes sin notas (promedio 0).
- **Validación de API**: Automatizar pruebas para el endpoint GET /courses/{id} verificando la estructura del JSON y códigos 200 OK o 404 Not Found
- **Pruebas de UI**: Verificar que la tabla de estudiantes muestre correctamente las columnas de nombre completo, grupo, instancias evaluatorias y promedios, asegurando que el diseño sea legible.

#### No funcionales
- **Rendimiento**: Validar el tiempo de carga de la pantalla de detalle cuando el curso tiene un volumen alto de estudiantes (ej: +50 registros)
- **Consistencia de Datos**: Realizar pruebas E2E para confirmar que el promedio visualizado en la pantalla coincida exactamente con el cálculo interno de la base de datos.

## HDU_5: Agregar estudiantes a la lista de estudiantes de un curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba**: Definir escenarios de "Primer Registro" (ID nuevo) y "Registro con ID existente" (el estudiante ya se encuentra en el sistema)
- **Validación de API**: Automatizar pruebas para el endpoint de inscripción, verificando que un POST con ID nuevo devuelva 201 Created y uno con ID existente devuelva el objeto ya persistido
- **Pruebas de UI**: Verificar que la tabla de estudiantes muestre correctamente la lista de estudiantes con nombre completo asegurando que el diseño sea legible.

#### No funcionales
- **Integridad**: Validar que si la inscripción al curso falla (ej: por error de red) el estudiante no quede registrado a medias en el sistema global.

## HDU_6: Agregar grupos a un curso creado

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir casos para nombres de grupos cortos (1 caracter), largos y con caracteres especiales (como "G-01")
- **Validación de API**: Automatizar pruebas para el endpoint POST /courses/{id}/groups, verificando respuestas 201 Created y 409 Conflict cuando el nombre ya existe dentro de ese mismo curso
- **Pruebas de UI**: Verificar que tras crear el grupo, la lista de grupos se actualice sin necesidad de recargar la página

#### No funcionales
- **Integridad**: Validar que el nuevo grupo quede correctamente vinculado al ID del curso padre en la base de datos
- **Usabilidad**: Comprobar que el resaltado de campos vacíos sea accesible y desaparezca inmediatamente al empezar a escribir

## HDU_7: Asignar estudiante a un grupo dentro de un curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir flujos para asignación simple, re-asignación fallida (mismo grupo) y conflicto de pertenencia (otro grupo)
- **Validación de API**: Automatizar pruebas para el endpoint de vinculación, verificando respuestas 200 OK (éxito) y 409 Conflict cuando se violan las reglas de exclusivida
- **Pruebas de UI**: Verificar que los grupos se actualicen correctamente luego de una asignación, y que los mensajes de error sean claros para el docente

#### No funcionales
- **Usabilidad**: Comprobar que en la vista de "Estudiantes por Grupo", solo aparezcan aquellos que fueron asignados realmente, sin de datos de otros grupos

## HDU_8: Desasignar estudiante de un grupo dentro del curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Validar desasignación de un estudiante único, desasignación masiva y el estado de la lista del grupo tras la acción (debe quedar vacía si era el último por ejemplo)
- **Validación de API**: Automatizar pruebas para el endpoint DELETE o de desvinculación, verificando código 200 OK o 204 No Content
- **Pruebas de UI**: Confirmar que el estudiante desaparece de la vista filtrada por grupo pero se mantiene visible en la vista "Todos los estudiantes" del curso

#### No funcionales
- **Integridad de Datos**: Validar en base de datos que el campo grupo_id del estudiante pase a NULL sin afectar sus notas o asistencia registradas en el curso

## HDU_9: Eliminar grupo dentro de un curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir flujos para eliminación de grupo vacío, eliminación con confirmación y cancelación del proceso 
- **Validación de API**: Automatizar pruebas para el endpoint DELETE, verificando que el código 200 OK o 204 No Content se reciba tras la confirmación
- **Pruebas de UI**: Verificar que el modal de advertencia aparezca solo cuando el grupo tiene estudiantes y que la lista de grupos se actualice visualmente tras la eliminación.

#### No funcionales
- **Integridad de Datos**: Validar en base de datos que al borrar el grupo, los registros de los estudiantes pasen a grupo_id = NULL automáticamente, que no se borren de la tabla Estudiantes y que los estudiantes mantengan su vínculo con el curso

## HDU_10: Actualizar título de un grupo dentro del curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir casos para edicion sin cambios (guardar el mismo nombre), cambio exitoso y duplicidad de nombres
- **Validación de API**: Automatizar pruebas para el endpoint PUT, verificando respuestas 200 OK, 409 Conflict (duplicado) y 400 Bad Request
- **Pruebas de UI**: Verificar que luego de la edición, todos los componentes que muestran el nombre del grupo se actualicen en tiempo real

#### No funcionales
- **Integridad de Referencia**: Confirmar que al cambiar el nombre del grupo, los estudiantes asignados a él sigan vinculados al ID interno del grupo

## HDU_11: Definir programa del curso

### Tareas de Calidad (QA)

#### Funcionales

- **Analisis de valores límite**: Crear casos para el anális de valores límite, para sumas exactas (100%), por debajo (99.9%) y por encima (100.1%)
- **Validación de Algoritmo Equitativo**: Probar la división de los porcentajes con números impares (ej: 3 instancias = 33.33%, 33.33%, 33.34%) para verificar cómo el sistema maneja estos casos
- **Automatización de API**: Validar que el método POST rechace payloads con nombres duplicados, pesos menores o iguales a 0, nombres vacíos o campos con datos inválidos (como alfanuméricos en los porcentajes de ponderacion por ejemplo)
- **Pruebas de UI**: Verificar que los mensajes de error sean específicos y no bloqueen la edición (que se permita al usuario corregir los datos erróneos)

#### No funcionales
- **Usabilidad de la Ponderación automática**: Comprobar que al activar la "Ponderación Equitativa", los campos de entrada se deshabiliten o se actualicen visualmente de forma inmediata para dar feedback al docente
- **Precisión Aritmética**: Validar que el sistema use tipos de datos decimales de alta precisión (como BigDecimal en Java) para evitar errores de redondeo acumulados en los promedios ponderados

## HDU_12: Eliminar instancia de evaluacion del programa del curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Escenarios donde se elimina una instancia y se redistribuye el peso manualmente vs. uso de la función equitativa
- **Validación de API**: Automatizar pruebas para el endpoint PUT o PATCH del programa, verificando que el servidor rechace la solicitud si la llamada resultante no suma exactamente 100%
- **Pruebas de UI**: Verificar que al eliminar la instancia, la interfaz notifique visualmente el "deficit" de porcentaje pendiente por asignar para alcanzar el 100%

#### No funcionales
- **Integridad de Datos**: Validar que las notas ya registradas de los estudiantes en esa instancia sean eliminadas en la BD
- **Consistencia de Calculos**: Verificar que el Promedio de los estudiantes se actualice inmediatamente en toda la plataforma tras confirmar la eliminación y redistribución de pesos