# SW603 – PRIMERA PRÁCTICA CALIFICADA

## INSTRUCCIONES

- Los grupos serán los mismos que se indican en el directorio del curso. Cada grupo deberá trabajar sobre el repositorio asignado en la organización del curso en Github.

- La PC1 es una **consolidación de las actividades previas realizadas en clase**. El informe debe integrar, de forma coherente y unificada, los entregables trabajados en cada actividad. Se ha cargado el índice de tópicos en cada repositorio grupal.

- El alcance del informe cubre **todas las secciones del índice**, hasta el bosquejo de Documentación de Arquitectura (C4), pasando por las decisiones de diseño. Adicionalmente, cada integrante desarrollará un tema asignado, como parte del componente individual.

- El uso de IA está permitido siempre que sirva para amplificar la capacidad y el criterio del equipo, nunca como sustituto del esfuerzo propio. Si se detectan secciones que los integrantes no están en capacidad de sustentar ni defender, se aplicarán penalidades sobre la calificación y, en casos graves, se anulará la práctica.

- Los entregables son los siguientes:
    - **Informe:** Consideren sus cambios en formato markdown en su repositorio de Github, siguiendo el índice propuesto.

    - **Documentación de Soporte:** Todos los documentos que sustenten su informe deben ser presentados: diapositivas de presentación, documentación del proceso, artefactos intermedios y referencias bibliográficas. Colóquenlos en una carpeta `docs` dentro de su repositorio (no incluya links, ni use herramientas como Google Drive) y referéncienlos como links en la sección correspondiente del informe.

    - **Componente Individual:** El tema elegido previamente debe ser sustentado en su informe. Además, cada integrante presenta **dos videos** antes del vencimiento del entregable: uno del tema individual y otro de su aporte al proyecto grupal (ver la sección 9).

- La calificación final tendrá en cuenta los siguientes aspectos:

    - Calidad del informe grupal presentado (10 puntos).
    - Calidad de la temática desarrollada por el alumno en su componente individual: Módulo desarrollado + tema individual (7 puntos).
    - Participación del estudiante en la clase y en actividades individuales: Casos prácticos, ejercicios (3 puntos).

- Para la exposición, el docente descargará previamente los repositorios de todos los grupos en la máquina principal. No está permitido el uso de material adicional ni abrir cuentas personales (por ejemplo, Google Drive): toda la información necesaria —diagramas, prototipos, documentación, ADRs, etc.— debe estar accesible desde el repositorio del grupo. No es necesario que presenten una diapositiva, el formato será de preguntas y respuestas.

- La fecha límite del entregable es el día **martes 29 de setiembre (Semana 5)** a las 16:00. Este vencimiento incluye tanto al informe, como el desarrollo del tema individual, incluyendo los dos videos. No se considerarán entregas posteriores a esa hora.

- Se revisarán los trabajos y se dará retroalimentación a cada grupo. En función a ello, el grupo podrá presentar una versión mejorada de su informe hasta el día **sábado 3 de octubre a las 23:59**. En función a las mejoras presentadas, podrán tener una bonificación en el componente grupal de la calificación.

- **Motivos de anulación de la evaluación (calificación de cero):**
  - **Trabajo grupal incompleto:** todo el grupo recibe calificación de cero.
  - **Módulo incompleto o trabajo individual incompleto:** el integrante responsable recibe calificación de cero.
  - **Inasistencia a la exposición:** el estudiante no se presentó en el horario asignado.
  - **Videos individuales no presentados o fuera de fecha:** aplica si falta cualquiera de los dos, si no están en YouTube o si no son públicos. Incluye entregas claramente improvisadas o de calidad muy baja.
  - **Falta de participación en el trabajo:** cuando la contribución del estudiante es nula o poco relevante. Ejemplos:
    - No presenta commits en el repositorio o su aporte es mínimo.
    - No mantiene comunicación con el grupo y entrega contenido improvisado muy cerca de la exposición.
    - El grupo reporta ausencia total de participación de un integrante.

- **Retroalimentación de Proyectos:**

    Cada estudiante podrá interactuar con los grupos que exponen realizando preguntas durante sus presentaciones y registrando comentarios a través de un formulario, disponible únicamente durante la etapa de preguntas de cada grupo. Se recomienda participar activamente en esta etapa, ya que mejora la experiencia de aprendizaje y suma puntaje en el componente de participación.

---

## ALCANCE DEL INFORME

El informe debe cubrir las siguientes secciones. Cada sección corresponde a una consolidación de los entregables trabajados en actividades previas.

### 1. Caso de Negocio y Descripción del Proceso

Presentación del proceso elegido por el grupo: contexto, propósito, alcance, actores, reglas de negocio, problemas actuales y oportunidades de mejora. Incluye el listado consolidado de actores y roles, y la estructura del equipo.

### 2. Diagramación del Proceso

Representación gráfica del flujo del proceso (BPMN o diagrama de flujo) en su modelo TO-BE, tabla de descripción de actividades y glosario de términos del dominio.

### 3. Requisitos Funcionales

Identificación de módulos (uno por integrante) y especificación de los requisitos funcionales asociados a cada módulo, utilizando casos de uso o historias de usuario de forma consistente. Se debe incluir el listado consolidado del sistema.

### 4. Requisitos de Atributos de Calidad

Identificación de los atributos de calidad relevantes para el proyecto (con argumentación, riesgos e interacciones) y especificación de escenarios de seis partes por módulo. Se debe incluir el listado consolidado.

### 5. Prototipo de Interfaces

Cada integrante incluye los prototipos de las pantallas de su módulo en la sección que le corresponde, y el grupo presenta además un prototipo navegable unificado del sistema completo. Cada pantalla se debe documentar utilizando un código, captura y notas de rendimiento o carga.

### 6. Decisiones de Diseño

Cada integrante debe identificar y documentar **al menos 10 decisiones de diseño relevantes para su módulo**, distribuidas a través de las siete categorías vistas en clase. Cada decisión se documenta con el formato **ADR** propuesto en la actividad, acompañado de la tabla resumen (ID, título, categoría, estado).

Ninguna categoría debería quedar sin al menos una decisión, salvo que se indique explícitamente por qué no aplica al módulo. Las alternativas planteadas deben ser reales —si solo hay una opción viable, probablemente no es una decisión que valga la pena documentar— y el sustento debe conectarse con los atributos de calidad priorizados en la sección anterior.

### 7. Documentación de Arquitectura (Bosquejo)

Primer bosquejo de la documentación de arquitectura del sistema utilizando los tres primeros niveles del modelo C4:

- Diagrama de Contexto (Nivel 1).
- Diagrama de Contenedores (Nivel 2).
- Diagrama de Componentes (Nivel 3).

Cada uno de los elementos representados (sistema, sistema externo, contenedor y componente) debe contar con documentación de respaldo: la diagramación por sí sola no es suficiente, es necesario describir el propósito y las responsabilidades de cada elemento.

El desarrollo de la arquitectura debe ser unificado a nivel del sistema; sin embargo, es posible que algún módulo se diagrame de forma independiente cuando se anticipe que funcionará como un subsistema completo. La estructura del informe contempla también una diagramación por módulo: ahí cada integrante puede incluir los fragmentos que le corresponden y ampliar el detalle de forma narrativa.

> **Debe existir coherencia entre esta sección y la anterior:** lo decidido en los ADR tiene que reflejarse en los diagramas, y los diagramas no deben introducir elementos que ninguna decisión sustente.

### 8. Tópicos en Diseño de Software (Componente Individual)

Cada integrante desarrollará el tema individual que ya eligió previamente.

Cada integrante deberá elaborar un informe sobre el tema elegido y esta información será colocada como Anexo al informe del grupo. El video correspondiente se rige por lo indicado en la sección 9.

Adicionalmente, el grupo deberá elegir el mejor tema individual, el cual será presentado durante la sesión de clase (5 minutos - breve introducción y directo a la demo).

Cada tema deberá tener, por lo menos, cobertura de los siguientes aspectos:

#### - Desarrollo conceptual

El cual deberá ser independiente de la tecnología / proveedor de servicios de nube.

#### - Consideraciones técnicas

Debería proveerse información suficiente para que sus compañeros puedan involucrarse con el concepto / herramienta / servicio desarrollado. Por ejemplo, si se trata de un patrón de diseño deben tocarse aspectos de aplicación y trade-offs; si es una herramienta o framework, aspectos de instalación y configuración; si es un servicio en la nube, el paso a paso para crear una cuenta y poderlo utilizar.

#### - Demo (Código)

Deben presentar un escenario de aplicación relevante - relacionado con su tema grupal - y realizar una implementación utilizando el tema desarrollado. El código debe estar publicado en el repositorio Github del grupo.

### 9. Videos Individuales

Cada integrante debe presentar **dos videos**, ambos sin límite de tiempo:

1. **Tema individual:** desarrollo integral del tema documentado en la sección anterior, explicando detalladamente todos los aspectos del informe y mostrando el código de demostración.
2. **Aporte al proyecto grupal:** los requisitos, las decisiones de diseño y los diagramas de su módulo, explicando qué construyó y por qué.

Los enlaces de **ambos videos** se colocan en la sección **Temas Individuales - PC 1** que corresponde a cada integrante dentro del informe del grupo.

Tres condiciones, sin excepción:

- **YouTube.** No se aceptan videos en Google Drive, OneDrive ni en ninguna otra herramienta.
- **Públicos.** El video debe estar publicado y accesible sin pedir permisos: un enlace privado o restringido equivale a no haber presentado el video.
- **Cuidado con la longitud.** No hay restricción de duración, pero un video largo demora en subir y procesar. Prevean ese tiempo: la hora de corte no se mueve.

---

## Orden de las Exposiciones

Las exposiciones se realizan en dos sesiones, con 30 minutos por grupo y 5 minutos de receso entre exposiciones. El calendario completo del ciclo está en [Calendario de Exposiciones](../s000-organizacion/calendario-exposiciones.md).

### Martes 29 de setiembre

| **Orden** | **Horario**     | **Grupo** |
|-----------|-----------------|-----------|
| **1** | **16:15 - 16:45** | **Grupo 05** |
| **2** | **16:50 - 17:20** | **Grupo 02** |
| **3** | **17:25 - 17:55** | **Grupo 04** |

### Miércoles 30 de setiembre

| **Orden** | **Horario**     | **Grupo** |
|-----------|-----------------|-----------|
| **1** | **20:15 - 20:45** | **Grupo 06** |
| **2** | **20:50 - 21:20** | **Grupo 01** |
| **3** | **21:25 - 21:55** | **Grupo 03** |
