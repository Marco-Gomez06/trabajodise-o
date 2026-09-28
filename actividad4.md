# Actividad: Documentación de Arquitectura (Bosquejo)

## Contexto

Una arquitectura de software bien diseñada pierde gran parte de su valor si no se comunica de forma efectiva. La documentación de arquitectura permite que todos los involucrados —desarrolladores, arquitectos, stakeholders y equipos futuros— compartan una misma comprensión del sistema: qué existe, cómo se estructura y por qué se tomaron ciertas decisiones.

En esta actividad trabajaremos con el **modelo C4**, que nos permitirá representar visualmente la arquitectura en distintos niveles de abstracción.

---

### ¿Qué es el Modelo C4?

El modelo C4, creado por Simon Brown, es un enfoque para visualizar la arquitectura de software mediante **cuatro niveles jerárquicos de abstracción**. El nombre "C4" proviene de los cuatro niveles: **Context, Containers, Components y Code**. La idea central es que, al igual que un mapa, podemos hacer zoom progresivo: partimos de una vista general del sistema en su entorno y vamos profundizando hasta llegar al detalle de los componentes internos.

Para esta actividad, cada el equipo debe elaborar una primera versión de la documentación de la arquitectura de su módulo utilizando **tres de los cuatro niveles** del modelo C4:

1. Diagrama de Contexto (Nivel 1)
2. Diagrama de Contenedores (Nivel 2)
3. Diagrama de Componentes (Nivel 3)

> **Nota:** El cuarto nivel (Código) no se requiere en esta actividad. Incluso en implementaciones en la industria, se recomienda su generación automática en la mayor parte de los casos.

![Niveles del Modelo C4](https://c4model.com/images/c4-static.png)

---

### Nivel 1: Diagrama de Contexto

El diagrama de contexto es la **vista de más alto nivel**. Muestra el sistema como una caja única y lo sitúa dentro de su entorno, representando quiénes lo usan y con qué otros sistemas interactúa.

**Propósito:** Responder a la pregunta *"¿Qué estamos construyendo y cómo encaja en el entorno que lo rodea?"*

**Elementos que aparecen en este diagrama:**
- **El sistema en desarrollo** (representado como un único recuadro o caja central - asígnenle un nombre a su sistema).
- **Personas/Usuarios** que interactúan directamente con el sistema (por ejemplo: estudiantes, administradores, docentes).
- **Sistemas externos** con los que el sistema se comunica (por ejemplo: sistema de correo electrónico, pasarela de pagos, sistema de autenticación institucional, APIs de terceros).

**Lineamientos y recomendaciones:**
- Definan con claridad quiénes son los usuarios y sistemas externos que interactúan con su sistema. Si tienen módulos totalmente aislados, puede ser relevante hacer más de un diagrama.
- Representen las relaciones a través de líneas simples indicando el tipo de interacción (por ejemplo: "Envía solicitudes", "Consulta estado", "Notifica por correo").
- Mantengan la simplicidad: este diagrama debe ser comprensible para cualquier stakeholder, incluso personas sin conocimiento técnico. Limiten la cantidad de elementos a lo esencial.
- **No incluyan detalles internos** del sistema en este nivel. El sistema es una caja negra.
- Cada relación debe tener una etiqueta descriptiva que indique qué información fluye o qué acción se realiza.

**Errores comunes a evitar:**
- Incluir demasiados detalles técnicos (tecnologías, protocolos).
- Representar componentes internos del sistema en este nivel.
- Omitir sistemas externos relevantes con los que el sistema interactúa.
- No etiquetar las relaciones entre elementos.

*Ejemplo de referencia (fuente: [c4model.com](https://c4model.com)):*

![Diagrama de Contexto - Ejemplo](https://c4model.com/images/examples/SystemContext.png)

---

### Nivel 2: Diagrama de Contenedores

El diagrama de contenedores hace **zoom dentro del sistema** y muestra los principales bloques técnicos que lo componen. Un "contenedor" en el contexto de C4 no se refiere a contenedores Docker, sino a una **unidad de despliegue o ejecución**: una aplicación web, una aplicación móvil, una API, una base de datos, un sistema de archivos, un servicio de mensajería, entre otros.

**Propósito:** Responder a la pregunta *"¿Cuáles son los principales bloques técnicos de nuestro sistema y cómo se comunican entre sí?"*

**Elementos que aparecen en este diagrama:**
- **Contenedores del sistema:** aplicaciones web (frontend), aplicaciones de servidor (backend/API), bases de datos, colas de mensajes, sistemas de archivos, microservicios, entre otros.
- **Personas/Usuarios** (se mantienen del diagrama de contexto para mostrar cómo acceden a los contenedores).
- **Sistemas externos** (se mantienen del diagrama de contexto para mostrar las integraciones). Ahora podremos saber, por ejemplo, qué parte específica de nuestro sistema se integra con la pasarela de pagos.

**Lineamientos y recomendaciones:**
- Enfóquense en mostrar las principales aplicaciones o servicios y cómo interactúan entre sí.
- **Indiquen la tecnología** utilizada en cada contenedor. Por ejemplo: "API REST [Spring Boot / Java]", "Base de Datos Relacional [PostgreSQL]", "Aplicación Web SPA [React]".
- Definan los **límites del sistema** claramente. Los contenedores dentro de la frontera de su sistema deben diferenciarse visualmente de los elementos externos (como se ve en el ejemplo, se suele utilizar colores para esto).
- Representen los **protocolos de comunicación** entre contenedores (HTTP/REST, gRPC, JDBC, AMQP, WebSocket, etc.).
- Si el sistema tiene múltiples subsistemas, representen sus fronteras.

**Errores comunes a evitar:**
- Confundir contenedores con componentes internos (un "Controller" o un "Service" no es un contenedor, es un componente).
- No especificar las tecnologías de cada contenedor.
- Omitir las bases de datos u otros mecanismos de persistencia.
- No representar cómo los usuarios acceden al sistema (¿vía navegador web? ¿aplicación móvil?).

*Ejemplo de referencia (fuente: [c4model.com](https://c4model.com)):*

![Diagrama de Contenedores - Ejemplo](https://c4model.com/images/examples/SystemContext.png)

---

### Nivel 3: Diagrama de Componentes

El diagrama de componentes hace **zoom dentro de un contenedor específico** y muestra los bloques lógicos o módulos internos que lo conforman. Los componentes representan agrupaciones de funcionalidad relacionada encapsulada detrás de una interfaz bien definida. Por lo tanto, vamos a tener múltiples diagramas de componentes en función a la cantidad de contenedores que hayamos definido en el nivel anterior.

**Propósito:** Responder a la pregunta *"¿Cómo está organizado internamente este contenedor y cuáles son sus piezas principales?"*

**Elementos que aparecen en este diagrama:**
- **Componentes del contenedor:** controladores, servicios, repositorios, módulos, librerías internas, handlers, entre otros.
- **Otros contenedores** con los que los componentes interactúan (bases de datos, APIs externas, colas de mensajes). Debe tener consistencia con el nivel anterior.
- **Sistemas externos** relevantes para los componentes mostrados. De la misma forma, debe coincidir con lo especificado para los niveles anteriores.

**Lineamientos y recomendaciones:**
- Dividan los contenedores en sus componentes internos, como controladores, servicios de negocio, repositorios de datos, servicios de seguridad y otros elementos.
- Representen cómo estos componentes interactúan y colaboran dentro del contenedor. Por ejemplo: el controlador de solicitudes invoca al servicio de validación, que a su vez consulta el repositorio de datos.
- **Especifiquen el propósito** de cada componente y cómo se integra con los demás. Cada componente debe tener un nombre descriptivo y una breve indicación de su responsabilidad.
- Indiquen la **tecnología o patrón** utilizado cuando sea relevante (por ejemplo: "Repositorio de Usuarios [Spring Data JPA]", "Servicio de Notificaciones [Patrón Observer]").
- No es necesario hacer un diagrama de componentes para **todos** los contenedores; prioricen los contenedores más complejos o relevantes (típicamente el backend o la API principal).

**Errores comunes a evitar:**
- Llegar a un nivel de detalle excesivo (no es necesario representar cada clase o método).
- No mostrar las interacciones entre componentes.
- Crear componentes que no tienen una responsabilidad clara o que mezclan múltiples responsabilidades.
- Omitir la relación de los componentes con los almacenes de datos o sistemas externos.

*Ejemplo de referencia (fuente: [c4model.com](https://c4model.com)):*

![Diagrama de Componentes - Ejemplo](https://c4model.com/images/examples/Components.png)

---

### Notación y Herramientas

El modelo C4 es **independiente de la notación**. No requiere una herramienta específica ni un formato gráfico obligatorio. Sin embargo, los gráficos que hemos mostrado corresponden a los lineamientos propuestos por sus creadores y han sido extraídos de la web oficial.

**Herramientas sugeridas:**

- **Diagramación visual:**
  - [diagrams.net (draw.io)](https://app.diagrams.net/) — Gratuita, con plantillas C4 disponibles.
  - [Miro](https://miro.com/) — Pizarra colaborativa con soporte para diagramas.
  - [Lucidchart](https://www.lucidchart.com/) — Herramienta de diagramación con plantillas C4.

- **Diagramas como código (recomendado para trazabilidad):**
  - [Mermaid](https://mermaid.js.org/) — Soporta diagramas C4 y se integra con Markdown y GitHub.
  - [Structurizr](https://structurizr.com/) — Herramienta oficial del creador de C4. Permite generar diagramas C4 a partir de un DSL.
  - [PlantUML con C4-PlantUML](https://github.com/plantuml-stdlib/C4-PlantUML) — Extensión de PlantUML con macros para C4.

> **Recomendación:** La alternativa de "Diagramas como código" es más amigable si deseas tener un primer bosquejo con herramientas de IA. Si embargo, la diagramación visual permite mayor control, puede tener presentaciones más impactantes y resulta más facil de editar o realizar pequeños ajustes. Recomiendo que utilicen `Mermaid` para tener una primera idea de cómo sería el diagrama y, en caso deseen mejorar la presentación, plasmen su diagramación final en `diagrams.net`. 

---

### Algunos Ejemplos

- [Página oficial del modelo C4](https://c4model.com/) — Incluye explicaciones detalladas, ejemplos interactivos y la notación recomendada para cada nivel.
- [Repositorio C4-PlantUML](https://github.com/plantuml-stdlib/C4-PlantUML) — Ejemplos de diagramas C4 como código.
- [Structurizr DSL Examples](https://docs.structurizr.com/dsl/cookbook/) — Ejemplos de uso del DSL de Structurizr para generar diagramas C4.

---
## Referencias Bibliográficas

- Bass, L., Clements, P., & Kazman, R. (2021). *Software Architecture in Practice* (4th ed.). Addison-Wesley Professional.
- Brown, S. (2018). *The C4 model for visualising software architecture.* Disponible en: [https://c4model.com/](https://c4model.com/)
- Richards, M., & Ford, N. (2020). *Fundamentals of Software Architecture.* O'Reilly Media.
