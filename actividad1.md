# Actividad: Elección de Tema

## Contexto

El punto de partida para cualquier proyecto de diseño de software es la **especificación de requisitos**. Es necesario entender con claridad **qué problema se quiere resolver** y **cómo funciona el proceso que se desea apoyar con tecnología**.

Antes de iniciar con el desarrollo de su proyecto del curso deben **elegir un problema o proceso de negocio dentro de la Facultad** que el grupo desee analizar, documentar y optimizar mediante el diseño de un software.

---

## Criterios para la elección del tema

No todos los procesos son igualmente adecuados para este proyecto. Al momento de evaluar alternativas, el grupo debe tener en cuenta los siguientes criterios:

- **Cobertura transaccional**: El proceso elegido debe generar un volumen suficiente de transacciones y entidades como para que **cada integrante del grupo pueda asumir, por lo menos, la responsabilidad de un módulo independiente**. Un proceso con pocas entidades o transacciones resultará en un trabajo desbalanceado o poco rico en términos de diseño.

- **Relevancia y oportunidad de mejora**: Debe existir una problemática real o una oportunidad concreta de optimización. Procesos que actualmente se gestionan con formularios físicos, hojas de cálculo o de manera informal son candidatos especialmente interesantes. Sin embargo, este tipo de trabajos necesitarán un mayor trabajo de campo. Por esta razón, estamos centrando el foco en mejoras dentro de la facultad.

- **Acceso a información**: El grupo debe poder obtener información suficiente del proceso, ya sea a través de entrevistas con personas involucradas, observación directa, documentos internos o fuentes equivalentes.

### Ejemplos de procesos dentro de la Facultad

A modo orientativo, algunos procesos que suelen reunir los criterios anteriores:

- Gestión de trámites de grado y titulación.
- Registro y seguimiento de prácticas preprofesionales.
- Gestión de reservas de laboratorios y equipos.
- Proceso de matrícula y gestión de ampliaciones.
- Gestión de proyectos de investigación y docentes.
- Proceso de selección y seguimiento de docentes.
- Gestión de biblioteca: préstamos, reservas y devoluciones.
- Gestión del departamento médico: atenciones, medicamentos y servicios.
- Proceso de evaluación y acreditación de cursos (por ejemplo: ABET).

> **Nota:** Esta lista es referencial. El grupo puede proponer un proceso diferente, siempre que cumpla con los criterios descritos.

---

## Estructura del entregable

Una vez elegido el tema, el grupo debe elaborar un documento que cubra las siguientes secciones. Estas secciones son pre-requisito para el inicio de su proyecto y constituyen la base sobre la cual se construirán todos los entregables posteriores.

---

### 1. Descripción del Proceso

El objetivo de esta sección es presentar el proceso elegido de forma clara y estructurada, de modo que cualquier persona pueda comprender su funcionamiento sin necesidad de conocer la institución en detalle.

Para ello, el grupo debe:

- Describir el **contexto** en el que opera el proceso: área, unidad orgánica o dependencia responsable, y su rol dentro de la Facultad.
- Definir el **propósito** del proceso: qué problema resuelve y qué valor genera para los usuarios o la institución.
- Delimitar el **alcance**: punto de inicio, punto de fin, y qué queda fuera del proceso (límites explícitos).
- Identificar las **entradas y salidas**: qué información o recursos se requieren para iniciar el proceso y qué productos o resultados genera.
- Listar los **actores o roles involucrados**: personas, áreas o sistemas que participan en la ejecución del proceso.
- Documentar las **reglas de negocio clave**: condiciones, restricciones o políticas que rigen el proceso (por ejemplo: *"un alumno puede matricularse en un máximo de X créditos"*).
- Identificar los **problemas actuales**: ineficiencias, cuellos de botella, inconsistencias de datos o tareas manuales susceptibles de automatización.
- Incluir **indicadores o KPIs relevantes**, si los hay (por ejemplo: tiempo promedio de atención, tasa de solicitudes rechazadas, volumen mensual de transacciones).

#### Qué incluir en esta sección

- Descripción narrativa del proceso (puede apoyarse en una tabla resumen).
- Listado de actores y sus roles.
- Listado de reglas de negocio.
- Identificación de problemas actuales y oportunidades de mejora.

---

### 2. Diagramación del Proceso

El objetivo de esta sección es **representar gráficamente el flujo del proceso**, de manera que la secuencia de actividades, las decisiones y los actores involucrados sean fácilmente comprensibles.

Para ello, el grupo debe:

- Construir un **diagrama BPMN** o un **diagrama de flujo** que represente el proceso seleccionado. Se recomienda el uso de BPMN por su precisión para representar roles y flujos de información. Herramientas sugeridas: [Bizagi Modeler](https://www.bizagi.com/), [diagrams.net](https://app.diagrams.net/).
- Enfocarse en el modelo **TO-BE**: el proceso tal como debería funcionar con el sistema de información propuesto, incorporando las mejoras identificadas. Si resulta útil como punto de comparación, puede incluirse también el modelo **AS-IS** (situación actual).
- Para cada actividad del diagrama, documentar:
  - **Número y nombre** de la actividad.
  - **Descripción breve**: qué se hace, para qué y cómo.
  - **Responsable**.
  - **Entradas necesarias** y **salidas generadas**.
  - **Reglas de negocio** asociadas.
  - **Sistemas implicados** (si aplica).

- Elaborar un **glosario de términos** del dominio, con las definiciones necesarias para facilitar la comprensión del proceso por parte de lectores externos.

#### Qué incluir en esta sección

- Diagrama del proceso (BPMN o diagrama de flujo).
- Tabla de descripción de actividades.
- Glosario de términos del dominio.

---

### 3. Especificación de Requisitos Funcionales

El objetivo de esta sección es **describir con precisión qué debe hacer el sistema** para dar soporte al proceso de negocio seleccionado. Los requisitos funcionales definen el comportamiento esperado del sistema desde la perspectiva del usuario.

Para ello, el grupo debe:

- Identificar los **módulos o subsistemas** necesarios para cubrir el proceso completo. Cada módulo agrupará un conjunto de funcionalidades relacionadas y será responsabilidad de un integrante del grupo.
- Especificar los requisitos de cada módulo utilizando **casos de uso** o **historias de usuario** (el grupo debe optar por uno de los dos formatos y aplicarlo de manera consistente).

#### Si se documentan como casos de uso

Para cada caso de uso:

- **Nombre**: identificación única y descriptiva.
- **Actor(es) involucrado(s)**: usuario, sistema u otros actores externos.
- **Objetivo**: qué busca lograr el actor.
- **Precondiciones**: estado necesario antes de iniciar.
- **Disparador o evento inicial**: acción que inicia la ejecución.
- **Flujo principal**: secuencia de pasos del escenario exitoso.
- **Flujos alternativos**: variaciones o caminos alternativos.
- **Postcondiciones**: estado final esperado.
- **Excepciones**: situaciones de error o casos especiales.

#### Si se documentan como historias de usuario

Para cada historia:

- **Título**.
- **Narrativa**: *"Como [rol], quiero [funcionalidad] para [beneficio esperado]."*
- **Criterios de aceptación**: condiciones que determinan cuándo la historia está completa.
- **Descripción narrativa adicional**: detalle de lo que debe ocurrir en el sistema.

#### Qué incluir en esta sección

- Identificación de módulos y asignación de integrantes.
- Especificación de requisitos funcionales (casos de uso o historias de usuario) por módulo.

---

### 4. Especificación de Requisitos No Funcionales

El objetivo de esta sección es **documentar los atributos de calidad** que el sistema debe cumplir. Estos requisitos definen *cómo* debe comportarse el sistema, no *qué* hace. Dos sistemas pueden ofrecer la misma funcionalidad pero diferenciarse significativamente en rendimiento, seguridad o disponibilidad.

Para cada atributo, el grupo debe describir **qué se espera** y, en la medida de lo posible, establecer **criterios medibles o umbrales concretos**.

Los atributos principales a considerar son:

- **Rendimiento**: tiempos de respuesta aceptables y volumen máximo de datos que se procesará.
  *Ejemplo: "La consulta de historial de trámites debe mostrar resultados en menos de 2 segundos para un máximo de 10,000 registros."*

- **Disponibilidad**: nivel de tiempo en línea esperado y horarios críticos de operación.
  *Ejemplo: "El módulo de matrícula debe estar disponible el 99.5% del tiempo durante el período de inscripción, entre las 08:00 y las 22:00 horas."*

- **Escalabilidad**: capacidad de soportar crecimiento en usuarios, datos o transacciones.
  *Ejemplo: "El sistema debe poder atender hasta 300 usuarios concurrentes en el pico del período de matrícula sin superar un tiempo de respuesta de 4 segundos."*

- **Seguridad**: autenticación, autorización, manejo de datos sensibles y auditoría.
  *Ejemplo: "El acceso al módulo de gestión de notas debe requerir autenticación de dos factores y registrar cada operación en un log de auditoría."*

- **Usabilidad**: facilidad de uso e intuitividad para los diferentes perfiles de usuario.
  *Ejemplo: "Un estudiante sin experiencia previa debe poder completar una solicitud de trámite en no más de 3 pasos."*

Adicionalmente, si el grupo identifica **restricciones técnicas o normativas** relevantes (por ejemplo, integración obligatoria con sistemas existentes de la institución, normativas de protección de datos personales, limitaciones de infraestructura), deben documentarlas en esta sección. Documentarlas no implica que necesariamente deban aplicarse en su totalidad, pero es importante dejar registro de su existencia.

#### Qué incluir en esta sección

- Especificación de atributos de calidad con criterios medibles.
- Listado de restricciones técnicas, normativas o de negocio identificadas.

---

### 5. Prototipo de Interfaces

El objetivo de esta sección es **diseñar las pantallas y flujos de navegación del sistema**, de manera que sea posible visualizar cómo interactuarán los usuarios con el sistema antes de comenzar el diseño y la implementación.

El prototipo no necesita ser funcional, pero sí debe ser lo suficientemente detallado como para representar la lógica de navegación y los datos que se capturan o presentan en cada pantalla.

Para ello, el grupo debe:

- Diseñar las pantallas correspondientes a **cada módulo** del sistema. Cada integrante es responsable del prototipo del módulo que tiene asignado.
- Construir un **prototipo unificado y navegable** del sistema completo, que permita recorrer el flujo de pantallas en la misma secuencia que seguiría un usuario real. El grupo debe compartir un único enlace para visualizar el sistema completo.
- Para cada pantalla, documentar:
  - **Código** de la pantalla.
  - **Imagen o captura** del diseño.
  - **Notas de rendimiento o carga**: identificar si la pantalla implica consultas potencialmente costosas o si existirán necesidades especiales de optimización.

#### Herramientas recomendadas

- [Figma](https://www.figma.com/)
- [Marvel App](https://marvelapp.com/)
- [Balsamiq Wireframes](https://balsamiq.com/wireframes/)
- Está permitido experimentar con herramientas de IA, pero el grupo debe estar en capacidad de sustentar todas sus decisiones. Un ejemplo interesante es [Google Stitch](https://stitch.withgoogle.com/).

#### Qué incluir en esta sección

- Prototipos de pantallas por módulo (imagen + código + notas).
- Enlace al prototipo navegable unificado del sistema completo.

---

## Consideraciones generales

- El tema elegido debe permitir que **cada integrante desarrolle un módulo propio** con suficiente profundidad. Si el proceso elegido no genera la cobertura necesaria, evalúen ampliarlo o consideren un proceso diferente antes de avanzar.
- Toda la documentación debe redactarse con **terminología consistente**: los nombres de procesos, actividades, actores y datos deben mantenerse iguales en todas las secciones.
- Si existe documentación previa sobre el proceso (informes, trabajos de tesis, manuales de procedimientos), inclúyanla como referencia y cítenla adecuadamente.
- Esta primera entrega establece la base de todos los entregables posteriores. Un buen entendimiento del proceso y una especificación clara de requisitos facilitarán significativamente el trabajo de diseño.
