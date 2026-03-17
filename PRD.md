# Product Requirement Document (PRD) - EdTech

> **Contexto del producto**
> Entre las labores cotidianas de un docente se evidencia la gran carga de trabajo que tienen los profesores al momento de calcular los promedios de sus estudiantes y generar boletines académicos.
>
> Esta solución se enfoca en una herramienta para centralizar la generación y el cálculo de promedios de los estudiantes para cada uno de sus cursos.
>
> Los boletines se pueden exportar en formato `.pdf`, `.html`, `.json`.

---

## 1. Visión y Objetivos

> [!NOTE]
> Esta solución está pensada como una app de ejecución local, no como un aplicación web.

El desarrollo de esta solución involucra 4 pantallas principales:
<details>
  <summary><strong><em>Login</em> de profesores</strong></summary>

Para mantener la privacidad y seguridad de la información de cada persona involucrada en un curso se diseña un sistema de login con acceso exclusivo a administradores de la aplicación y usuarios registrados. Estos últimos pueden ser profesores o auxiliares de docente autorizados por dicho docente.
</details>

<details>
  <summary><strong><em>Dashboard</em> principal</strong></summary>

En esta pantalla está el resumen de los cursos creados por el usuario. Por *default* se encontrarán los cursos activos y dentro de la misma pantalla estará el grupo "finalizados" en un toggle list que por defecto necesita interaccionarse con él para visualizar dichos cursos.

Esto es con el fin de mantener una interfaz limpia y ordenada en todo momento.
También es posible crear cursos o modificarlos con el objetivo de tener un gestor centralizado para el usuario y sus pendientes.
</details>

<details>
  <summary><strong><em>Creación</em> de curso</strong></summary>

Cada curso debe definirse un nombre y dentro del mismo la cuando el usuario entra por primera vez encontrará una lista vacía para agregar estudiantes.

El usuario podrá ingresar manualmente la información de sus estudiantes. Para poder guardar la información de un estudiante; el profesor debe adjuntar el número de identificación único del estudiante en el campo `ID`, utilizando su Cédula de Ciudadanía (por ejemplo).

Una vez un estudiante se guarde por primera vez en el sistema, esta información podrá utilizarse de forma transversal para cualquier curso o profesor en búsquedas siguientes.

Si un estudiante ya está en la base de datos de la aplicación, cuando el usuario ingrese su `ID` el resto de su información de autocompletará.

> Cómo visión futura se estima el poder importar lista de estudiantes en un curso. Si desea importarlos puede elegir:
> 1. Importar de otro curso
> 2. Importar desde un .csv
</details>

<details>
  <summary><strong><em>Detalle</em> curso creado</strong></summary>

En esta pantalla está la lsita de estudiantes inscritos al curso. Cada estudiante está situado en la fila de una tabla de puntajes o notas.

Esta tabla de notas debe especificarse la primera vez que se entra al curso; estableciendo la cantidad de entregables y sus porcentajes de la nota final del curso.

>[!WARNING]
Los entregables deben sumar exactamente 100% para poder guardar la tabla. No se aceptaran cambios que no cumplan esa norma en ningún momento.

Una vez creada la tabla, cada estudiante tendra su fila con las siguientes columnas:
- Nombre del estudiante
- Nombre de entregable y su porcentaje (`n` columnas creadas por el usuario)
- Promedio
- Promedio ponderado
</details>

**EdTech** se visualiza como una herramienta que simplifica y acelera las labores diarias y repetitivas que tiene un docente durante la ejecución de un curso. A continuación se desglosa los objetivos de la aplicación y de cada una de sus pantallas:

---

## 2. Alcance del MVP

#### IN

- Autenticación básica: Ingreso para los docentes
- Gestión de entidades: (cursos, grupos, estudiantes)
- Definir programa: agregar actividades evaluatorias a los cursos con un porcentaje de ponderación, donde la suma de ellas equivale al 100% del curso
- Motor de calculo: Lógica para procesar las notas de los estudiantes de manera automática segun el programa definido, asignandole un promedio general y un promedio ponderado.
- Exportación: Exportar boletines en formato <.PDF> <.HTML> <.JSON>

#### OUT

- Carga Masiva: Importación de estudiantes mediante archivos CSV
- Acceso a estudiantes: Portal estudiantil donde los estudiantes puedan ver sus notas y promedios
- Gráficos estadísticos: Representaciones visuales avanzadas del rendimiendo general de los estudiantes de un curso o grupo


## 3. Riesgos

#### Del negocio:

- Curva de aprendizaje elevada: Riesgo de que alguna interfaz sea tan complicada que el docente prefiera métodos tradicionales como Excel, haciendo que el producto pierda su propósito

- Duplicidad de datos: Registrar 2 veces a un mismo estudiante en un mismo grupo

- Manejo de datos sensibles: Manejo inadecuado de las calificaciones de los estudiantes

#### Técnicos

- Inconsistencia en la exportación de promedios/boletines

- Precisión inconstante en el cálculo de los promedios de los estudiantes

- Que el sistema guarde un programa en donde la suma de los porcentajes de ponderación de las actividades evaluatorias definidas no sumen un 100% del curso.

- Corrupcion de archivos (que el archivo PDF, HTML o JSON se genere incompleto o con errores)
