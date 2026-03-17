# Product Requirement Document (PRD) - EdTech

> **Contexto del producto**
> Entre las labores cotidianas de un docente se evidencia la gran carga de trabajo que tienen los profesores al momento de calcular los promedios de sus estudiantes y generar boletines académicos.
> En esta solución se enfoca en una herramienta para centralizar la generación y el cálculo de promedios de los estudiantes para cada uno de sus cursos.
>
> Los boletines se pueden exportar en formato `.pdf`, `.html`, `.xlsx`.

---

### Alcance del MVP

#### IN

- Autenticación básica: Ingreso para los docentes
- Gestión de entidades: (cursos, grupos, estudiantes)
- Definir programa: agregar actividades evaluatorias a los cursos con un porcentaje de ponderación, donde la suma de ellas equivale al 100% del curso
- Motor de calculo: Lógica para procesar las notas de los estudiantes de manera automática segun el programa definido, asignandole un promedio general y un promedio ponderado.
- Exportación: Exportar boletines en formato <.PDF> <.HTML> <.XLSX>

#### OUT

- Carga Masiva: Importación de estudiantes mediante archivos CSV
- Acceso a estudiantes: Portal estudiantil donde los estudiantes puedan ver sus notas y promedios
- Gráficos estadísticos: Representaciones visuales avanzadas del rendimiendo general de los estudiantes de un curso o grupo

---

