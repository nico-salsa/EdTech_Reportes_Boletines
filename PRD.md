# Product Requirement Document (PRD) - EdTech

> **Contexto del producto**
> Entre las labores cotidianas de un docente se evidencia la gran carga de trabajo que tienen los profesores al momento de calcular los promedios de sus estudiantes y generar boletines académicos.
>
> Esta solución se enfoca en una herramienta para centralizar la generación y el cálculo de promedios de los estudiantes para cada uno de sus cursos.
>
> Los boletines se pueden exportar en formato `.pdf`, `.html`, `.xlsx`.

---

## 1. Visión y Objetivos

!!! note
    Esta solución está pensada como una app de ejecución local, no como un aplicación web.

El desarrollo de esta solución involucra 4 pantallas principales:
1. *Login* de profesores
2. *Dashboard* principal
3. Creación de curso
4. Detalle curso creado

**EdTech** se visualiza como una herramienta que simplifica y acelera las labores diarias y repetitivas que tiene un docente durante la ejecución de un curso. A continuación se desglosa los objetivos de la aplicación y de cada una de sus pantallas:

### *Login* de profesores

Para mantener la privacidad y seguridad de la información de cada persona involucrada en un curso se diseña un sistema de login con acceso exclusivo a administradores de la aplicación y usuarios registrados. Estos últimos pueden ser profesores o auxiliares de docente autorizados por dicho docente.

### *Dashboard* principal

En esta pantalla está el resumen de los cursos creados por el usuario. Por *default* se encontrarán los cursos activos y dentro de la misma pantalla estará el grupo "finalizados" en un toggle list que por defecto necesita interaccionarse con él para visualizar dichos cursos.

Esto es con el fin de mantener una interfaz limpia y ordenada en todo momento.
También es posible crear cursos o modificarlos con el objetivo de tener un gestor centralizado para el usuario y sus pendientes.