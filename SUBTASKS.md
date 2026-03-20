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

#### Funcionales

- Implementar el endpoint de registro de usuario
- Validar `nombre de usuario` y `contraseña` como obligatorios
- Validar exclusividad (no repetición) de `nombre de usuario`
- Persistir el usuario
- Retornar error por campos vacíos
- Retornar error por nombre de usuario ya existente

---

## HDU_2: Iniciar sesión

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir flujos de "happy path" (credenciales correctas) y flujos negativos (usuario inexistente, contraseña errónea).
- **Validación de API**: Automatizar pruebas para verificar códigos de respuesta: 200 OK (éxito con entrega de Token), 401 Unauthorized (credenciales inválidas) y 400 Bad Request (campos vacíos).
- **Pruebas de UI**: Verificar el redireccionamiento exitoso a la página principal y el resaltado visual de campos obligatorios cuando están vacíos.

#### No funcionales
- **Seguridad (Autenticación)**: Validar que tras un inicio de sesión exitoso, el sistema genere y almacene un token de sesión seguro y no exponga la contraseña en la URL o en logs
- **Usabilidad de Errores**: Comprobar que el mensaje de error para credenciales inválidas sea genérico (ej: "Usuario o contraseña incorrectos") para no dar pistas sobre qué dato falló específicamente.

#### Funcionales

- Implementar el endpoint de inicio de sesión
- Validar nombre de usuario y contraseña como obligatorios
- Validar credenciales contra usuarios registrados
- Retornar acceso exitoso.
- Retornar error por credenciales inválidas

---

## HDU_3: Crear nuevo curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir flujos para nombres de cursos con caracteres especiales, longitudes máximas y espacios en blanco al inicio/final
- **Validación de API**: Automatizar pruebas para los métodos POST (crear) y PUT (editar), verificando respuestas 201 Created (éxito), 409 Conflict (duplicado) y 400 Bad Request (título vacío)
- **Pruebas de UI**: Verificar que tras la creación exitosa, el usuario sea redirigido a la vista del nuevo curso o que este aparezca inmediatamente en el listado de la página principal

#### No funcionales
- **Consistencia en Modificación**: Validar que al editar el título de un curso, todos los estudiantes y grupos previamente asignados mantengan su vínculo correctamente

#### Funcionales

- Implementar el endpoint de creación de curso
- Validar la no repetición del título del curso
- Persistir el curso
- Implementar la actualización del título del curso
- Retornar el curso creado o actualizado

---

## HDU_4: Consultar curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba**: Definir escenarios para cursos con muchos estudiantes, cursos vacíos y estudiantes sin notas (promedio 0).
- **Validación de API**: Automatizar pruebas para el endpoint GET /courses/{id} verificando la estructura del JSON y códigos 200 OK o 404 Not Found
- **Pruebas de UI**: Verificar que la tabla de estudiantes muestre correctamente las columnas de nombre completo, grupo, instancias evaluatorias y promedios, asegurando que el diseño sea legible.

#### No funcionales
- **Rendimiento**: Validar el tiempo de carga de la pantalla de detalle cuando el curso tiene un volumen alto de estudiantes (ej: +50 registros)
- **Consistencia de Datos**: Realizar pruebas E2E para confirmar que el promedio visualizado en la pantalla coincida exactamente con el cálculo interno de la base de datos.

#### Funcionales

- Implementar búsqueda de estudiante por ID
- Implementar alta on-the-fly para estudiantes nuevos
- Validar ID, Nombre completo y Correo como obligatorios
- Persistir el estudiante nuevo
- Asociar el estudiante al curso
- Retornar datos autocompletados cuando el ID ya exista

---

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

## HDU_13: Actualizar instancia de evaluacion del programa del cursoo

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Escenarios de edición de nombres, pesos válidos e inválidos (0, negativos, >100%)
- **Validación de API**: Automatizar pruebas para el endpoint PUT, verificando que el servidor bloquee duplicado de nombres y sumas != 100% 
- **Pruebas de UI**: Verificar que el sistema resalte visualmente los campos con error (vacíos o duplicados) antes de permitir el envío al backend

#### No funcionales
- **Prueba de Integridad (Recálculo)**: Validar que tras cambiar una ponderación (ej: de 20% a 30%), las notas de todos los estudiantes se actualicen
- **Prueba de estres del rendimiento**: Simular la actualización de pesos en un curso con 100 estudiantes y 10 instancias evaluatorias para asegurar que el recálculo no bloquee la base de datos o cause un timeout
- **Atomicidad**: Confirmar que si el recálculo de promedios falla a mitad del proceso, el sistema haga un rollback y mantenga los pesos anteriores

## HDU_14: registrar nota de una instancia de evaluacion del programa a un estudiante del curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de matriz de datos de calificación**: Definir casos para notas enteras, decimales, notas extremadamente altas (límite de capacidad del campo) y el valor exacto 0
- **Validación de la "Regla de Oro"**: Crear un escenario donde un estudiante tenga 50% de sus notas vacías y verificar que el promedio baje proporcionalmente (confirmando que se tratan como 0)
- **Automatización de API**: Validar que el endpoint de calificación rechace strings, símbolos y valores negativos (400 Bad Request), y acepte null transformándolo internamente
- **Pruebas de UI**: Verificar que el resaltado de notas nulas sea visualmente distinto para alertar al docente

#### No funcionales
- **Precisión Matemática**: Validar que el recálculo del Promedio Ponderado y General ocurra en tiempo real (o tras el guardado) sin errores de redondeo
- **Atomicidad**: Confirmar que si el recálculo de promedios falla a mitad del procesoo, el sistema haga un rollback y mantenga los pesos anteriores

## HDU_15: generar boletín del estudiante de un curso

### Tareas de Calidad (QA)

#### Funcionales
- **Validación de Formatos**: Probar la descarga y apertura correcta en los formatos definidos
- **Prueba de "Notas Vacías"**: Verificar que el flujo de advertencia se dispare correctamente y que el archivo final muestre la nota como "0" o "N/A" según el diseño, manteniendo el promedio coherente
- **Integridad de Datos en el Documento**: Asegurar que el Nombre, ID, Notas por Instancia y Promedios en el boletín coincidan al 100% con la base de datos
- **Pruebas de UI**: Comprobar que el selector de formatos sea intuitivo y que el mensaje de advertencia de notas vacías no bloquee la descarga si el docente decide continuar

#### No funcionales
- **Diseño y Layout**: Asegurar que en formatos como PDF el contenido no se "corte" si el nombre del estudiante es muy largo o si hay muchas instancias evaluatorias
- **Rendimiento de Generación**: Medir el tiempo de respuesta desde el "clic" hasta que inicia la descarga (especialmente en formatos pesados como PDF)

## HDU_16: generar reporte de calificaciones de todos los estudiantes de un curso

### Tareas de Calidad (QA)

#### Funcionales
- **Validación de Estructura de Matriz**: Verificar que las columnas correspondan exactamente a las instancias del programa definido y las filas a la lista completa de estudiantes (sin omisiones)
- **Prueba de Flujo de Advertencia**: Confirmar que si falta una sola nota en todo el curso, el sistema dispare la alerta de "Registros Incompletos"
- **Verificación de Cálculos**: Cruzar los promedios finales que aparecen en el reporte grupal contra los promedios individuales de la HDU_15 para asegurar total paridad
- **Validación de Formatos**: Probar la descarga en PDF (lectura visual), JSON (integridad de datos) y HTML y otros formatos en caso de ser necesario

#### No funcionales
- **Prueba de estrés**: Validar la generación del reporte en un curso muchos estudiantes (100 por ejemplo) y muchas instancias evaluatorias (10 por ejemplo) para evitar errores de memoria o timeouts
- **Usabilidad del Layout**: En el formato PDF, verificar que el reporte sea legible si hay muchas columnas
- **Seguridad de Datos**: Asegurar que el reporte solo incluya estudiantes activos del curso y no filtre datos de otros cursos

## HDU_17: dar de baja a un estudiante del curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba**: Escenarios de baja para estudiantes con 0 notas, con algunas notas y con todas las notas completas.
- **Validación de API**: Automatizar pruebas para el endpoint de desvinculación DELETE, verificando que el código 200 OK o 204 No Content se reciba tras confirmar
- **Pruebas de UI**: Confirmar que tras la baja, el estudiante desaparece inmediatamente de la lista del curso y de los selectores de grupos
- **Verificación de Persistencia Global**: Validar que el estudiante siga siendo consultable en el sistema general (por ejemplo, para inscribirlo en otro curso)

#### No funcionales
- **PIntegridad de Datos**: Validar directamente en la base de datos que los registros de notas asociados a ese estudiante en ese curso hayan sido eliminados físicamente o marcados como borrados
- **Consistencia de Reportes**: Verificar que, tras la baja, el reporte grupal (HDU_16) ya no incluya al estudiante, recalculando correctamente cualquier métrica grupal si existiera
- **Seguridad de Operación**: Asegurar que aparezca un modal de confirmación para evitar bajas accidentales

## HDU_18: actualizar información personal de un estudiante

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba**: Definir flujos de edición simple (nombre) y edición crítica (cambio de ID o Correo).
- **Prueba de Propagación**: Inscribir un estudiante en dos cursos diferentes, editar su nombre en el directorio y verificar que el cambio sea visible en ambos cursos sin intervención adicional
- **Validación de API**: Automatizar pruebas para el endpoint PUT, verificando respuestas 200 OK, 409 Conflict (ID duplicado) y 400 Bad Request (campos vacíos)
- **Validación de UI**: Verificar que el formulario de edición cargue los datos actuales correctamente y que los mensajes de error sean claros

#### No funcionales
- **Integridad Referencial (ID)**: Si el ID es la clave primaria, validar que el cambio de ID en la tabla de Estudiantes actualice correctamente todas las llaves foráneas en las tablas de Notas y Grupos (Update en cascada)
- **Consistencia de Cache**: Asegurar que el Frontend no muestre información desactualizada tras la edición 

## HDU_19: eliminar estudiante del sistema (global)

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba**: Escenarios de eliminación de un estudiante con notas en múltiples cursos vs. un estudiante sin actividad
- **Validación de API**: Automatizar pruebas para el endpoint DELETE, verificando que devuelva 200 OK tras la confirmación y 404 Not Found si se intenta borrar dos veces
- **Prueba de Flujo de Interrupción**: Verificar que al "Cancelar", no se ejecute ninguna petición al backend y el estado de la UI permanezca intacto
- **Verificación de Desaparición Global**: Validar que el estudiante ya no aparezca en: el Directorio, las listas de Cursos, los Grupos y los Reportes Consolidados

#### No funcionales
- **Integridad de Datos**: Validar en base de datos que se hayan eliminado los registros relacionados al estudiante para evitar "registros huérfanos"
- **Seguridad**: Comprobar que el modal de advertencia sea lo suficientemente disruptivo (ej: color rojo, mensaje claro) para evitar errores humanos fatales