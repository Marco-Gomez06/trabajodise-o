# Actividad: Decisiones de Diseño

## Contexto

El diseño de de software es, en esencia, un **proceso de toma de decisiones**. Cada elección —desde el lenguaje de programación hasta la forma en que se sincronizan dos servicios— condiciona los atributos de calidad del sistema, su evolución a futuro y el esfuerzo que demandará al equipo de desarrollo. Sin embargo, estas decisiones suelen perderse en la memoria del equipo: se toman en una reunión, se implementan, y meses (o años) después nadie recuerda **por qué** se eligió una alternativa sobre otra.

Documentar las decisiones de diseño tiene dos propósitos centrales:

1. **Hacer explícito el razonamiento** detrás de cada elección, de modo que el equipo (presente y futuro) pueda entender el contexto, las restricciones y los trade-offs considerados.
2. **Facilitar la evolución del sistema**, ya que cuando aparezcan nuevos requisitos o restricciones, se podrá revisitar la decisión con conocimiento de causa, en lugar de partir de cero.

En esta actividad trabajaremos con dos elementos: las **categorías de decisiones de diseño** que propone Bass et al. en su libro *Software Architecture in Practice* (2021) y la **plantilla de Architecture Decision Record (ADR)** tomando como referencia a Richards y Ford (2020).

---

## Parte 1: Categorías de Decisiones de Diseño

Bass, Clements y Kazman (2021) proponen agrupar las decisiones arquitectónicas en **siete categorías**. Esta clasificación nos da un marco para asegurar que ninguna dimensión relevante quede sin analizar al diseñar un módulo o sistema.

### 1. Asignación de Responsabilidades

Decisiones sobre **qué hace cada elemento** del sistema. Implica identificar las responsabilidades funcionales y no funcionales y distribuirlas entre módulos, componentes o servicios.

**Ejemplos típicos:**
- ¿La validación de reglas de negocio se hace en el frontend, en el backend o en ambos?
- ¿Existe un módulo dedicado a notificaciones o cada módulo gestiona las suyas?
- ¿Qué componente es responsable de la auditoría de cambios?

### 2. Modelo de Coordinación

Decisiones sobre **cómo se comunican y sincronizan los elementos** entre sí: protocolos, sincronía, garantías de entrega, manejo de tiempo y orden.

**Ejemplos típicos:**
- ¿La comunicación entre dos servicios es síncrona (HTTP/REST) o asíncrona (cola de mensajes)?
- ¿Qué hacemos si el servicio destino no responde? ¿Reintentamos? ¿Cuántas veces?
- ¿Garantizamos entrega exactamente una vez, al menos una vez, o como máximo una vez?

### 3. Modelo de Datos

Decisiones sobre **cómo se estructuran, almacenan y acceden los datos** del sistema: entidades, relaciones, esquemas, consistencia, particionamiento. Es importante tomar en cuenta que estas decisiones pueden variar por cada módulo del sistema y que existen conceptos que será necesario que investiguen.

**Ejemplos típicos:**
- ¿Modelo relacional, documental, clave-valor, grafo, o una combinación (polyglot persistence)?
- ¿Cómo se modela la relación entre un cliente y sus pedidos?
- ¿Aceptamos consistencia eventual en algún módulo o exigimos consistencia fuerte siempre?

### 4. Gestión de Recursos

Decisiones sobre **cómo se administran los recursos limitados** del sistema: hilos, conexiones, memoria, ancho de banda, almacenamiento, presupuesto cloud.

**Ejemplos típicos:**
- ¿Cuántas conexiones simultáneas permite el pool de la base de datos?
- ¿Aplicamos rate limiting a los clientes de la API? ¿Con qué umbrales?
- ¿Cómo manejamos archivos grandes? ¿En memoria, en disco, en almacenamiento de objetos?

### 5. Mapeo entre Elementos Arquitectónicos

Decisiones sobre **cómo se relacionan elementos de distintas vistas** de la arquitectura: módulos a componentes en ejecución, componentes a infraestructura, datos a almacenes físicos.

**Ejemplos típicos:**
- ¿Cada módulo lógico se despliega como un servicio independiente o varios módulos comparten un mismo proceso?
- ¿En qué región o zona se despliega cada servicio?
- ¿Qué módulos comparten base de datos y cuáles tienen la suya propia?

### 6. Tiempo de Enlace

Decisiones sobre **en qué momento se resuelven** los valores, configuraciones o comportamientos del sistema: tiempo de diseño, compilación, despliegue, inicio o ejecución.

**Ejemplos típicos:**
- ¿Las claves de API se compilan en el binario, se leen de variables de entorno o se obtienen de un secret manager en tiempo de ejecución?
- ¿Los feature flags se evalúan en tiempo de despliegue o por solicitud?
- ¿La internacionalización se resuelve en tiempo de build o por sesión de usuario?

### 7. Elección de Tecnología

Decisiones sobre **qué tecnologías concretas** se utilizan para implementar lo definido en las categorías anteriores: lenguajes, frameworks, motores de base de datos, proveedores cloud.

**Ejemplos típicos:**
- ¿Qué lenguaje y framework usamos para el backend?
- ¿Qué motor de base de datos elegimos para persistir los datos del módulo?
- ¿Qué proveedor cloud y qué servicios específicos utilizamos?

> **Importante:** Una decisión puede tener implicaciones en varias de las categorías presentadas (por ejemplo, elegir Kafka es a la vez una decisión de coordinación y de tecnología). Lo importante es usarlas como **lista de verificación** para no dejar fuera ninguna dimensión relevante del diseño.

---

## Parte 2: Estructura de un Architecture Decision Record (ADR)

Un **Architecture Decision Record (ADR)** es un documento breve que captura una decisión arquitectónica significativa, su contexto y sus consecuencias. Richards y Ford (2020) destacan que los ADR son una de las herramientas más efectivas para combatir lo que llaman *architectural amnesia*: la pérdida progresiva del razonamiento detrás de las decisiones a medida que el equipo cambia y el sistema evoluciona.

Cada ADR debe ser **autocontenido, conciso y enfocado a una sola decisión**. No es un documento de diseño extenso ni un manual: idealmente cabe en una página y puede leerse en pocos minutos.

### Plantilla de ADR

| Sección | Descripción |
|---|---|
| **Título** | Frase corta y descriptiva que identifique inequívocamente la decisión. Idealmente formulada como una elección entre alternativas (ej. "Elección entre tipado estático y dinámico para el backend"). |
| **Contexto** | Describe el problema o situación que motiva la decisión. Debe ser específico: características del módulo, restricciones del proyecto, volúmenes esperados, atributos de calidad priorizados, normativa aplicable, capacidades del equipo. Sin un contexto claro, la decisión no puede ser evaluada críticamente. |
| **Alternativas** | Liste **al menos dos alternativas viables**, con una descripción suficiente de cada una. No basta con nombrarlas: indique cómo resolverían el problema, sus ventajas y sus limitaciones. Use fuentes confiables (documentación oficial, libros, papers, benchmarks); evite delegar la búsqueda íntegramente a una IA. |
| **Criterios de Elección** | Factores concretos que se usarán para comparar las alternativas: rendimiento, costo, mantenibilidad, capacidades del equipo, time-to-market, soporte de la comunidad, cumplimiento normativo. Sea específico sobre **cómo** cada criterio impacta al sistema en construcción. |
| **Decisión** | Declare con claridad la alternativa seleccionada. Una sola oración suele ser suficiente. |
| **Sustento** | Justifique la decisión apoyándose en los criterios de elección y el contexto. Explique los trade-offs aceptados (qué se sacrifica) y por qué son aceptables. Mencione características técnicas concretas que ofrezcan ventajas para el caso particular. |

---

## Parte 3: Entregable

Cada estudiante debe identificar y documentar **al menos 10 decisiones de diseño relevantes para su módulo** del proyecto, distribuidas a través de las siete categorías presentadas en la Parte 1.

### Lineamientos

- **Cobertura por categoría:** procuren cubrir las siete categorías descritas. No es obligatorio tener exactamente una decisión por categoría, pero **ninguna categoría debería quedar sin al menos una decisión** salvo justificación clara (por ejemplo, si su módulo no tiene decisiones de binding time relevantes, indíquenlo en el documento).
- **Decisiones reales y específicas:** cada ADR debe corresponder a una decisión efectivamente tomada para su módulo. Eviten decisiones genéricas que aplicarían a cualquier sistema; aterrícenlas a su contexto.
- **Alternativas honestas:** las alternativas planteadas deben ser realistas. Si solo hay una opción viable, probablemente no es una decisión de diseño que valga la pena documentar.
- **Trazabilidad con atributos de calidad:** siempre que sea posible, conecten el sustento con los atributos de calidad priorizados en actividades anteriores.
- **Formato:** Documente cada decisión de diseño independientemente (puede revisar los ejemplos) y considere además una tabla de resumen. Por el momento, utilice un archivo markdown por módulo. El docente proporcionará la estructura final posteriormente para que ustedes puedan incluir sus cambios.

### Tabla resumen (incluir en el README del entregable)

| ID | Título | Categoría | Estado |
|---|---|---|---|
| ADR-001 | ... | Elección de Tecnología | Aceptado |
| ADR-002 | ... | Modelo de Datos | Aceptado |
| ... | ... | ... | ... |

---

## Ejemplos de Referencia (CrediMype)

A continuación se muestran dos ADR de ejemplo correspondientes a un sistema ficticio (CrediMype, una plataforma de créditos para microempresas). Sirven como guía de profundidad y formato esperados; **no son plantillas para copiar**.

### ADR-001 — Elección entre tipado estático y dinámico para el stack de desarrollo

**Categoría:** Elección de Tecnología

**Contexto:**
El equipo de desarrollo de CrediMype está compuesto por **3 desarrolladores** con experiencia en Java, JavaScript y Python. La empresa atraviesa una etapa de crecimiento acelerado en la que se incorporan nuevas funcionalidades cada pocas semanas, por lo que la **velocidad de iteración** es un factor crítico. Al mismo tiempo, el sistema gestiona datos financieros sensibles, lo que exige niveles adecuados de **seguridad y robustez**, especialmente en los módulos transaccionales. El equipo no cuenta, por ahora, con perfiles dedicados al frontend, por lo que cualquier reducción en la cantidad de stacks distintos a mantener tiene impacto directo en la productividad.

**Alternativas:**
1. **Lenguaje de tipado estático (Java + Kotlin para backend, TypeScript para frontend).**
   - Detección temprana de errores de tipo en tiempo de compilación.
   - Mejor soporte de refactor automático en IDEs.
   - Curva de adopción mayor para nuevos desarrolladores y mayor verbosidad en código.
2. **Lenguaje de tipado dinámico (JavaScript con Node.js en backend y frontend, Python para tareas de soporte).**
   - Permite usar un único lenguaje en frontend y backend, reduciendo el costo cognitivo del equipo.
   - Ecosistema NPM con alta disponibilidad de librerías para integraciones financieras.
   - Mayor riesgo de errores que solo se manifiestan en tiempo de ejecución, mitigable con linters y tests.

**Criterios de Elección:**
- **Velocidad de desarrollo** en las primeras fases del producto.
- **Reducción de la cantidad de lenguajes** que el equipo debe dominar simultáneamente.
- **Flexibilidad** para ajustar funcionalidades con frecuencia.
- **Seguridad y robustez** en módulos financieros (mitigable con prácticas complementarias).

**Decisión:**
Se adopta JavaScript/TypeScript como lenguaje principal del stack, ejecutándose sobre Node.js en backend y un framework SPA en frontend.

**Sustento:**
La unificación del lenguaje en frontend y backend permite que cualquier integrante del equipo pueda intervenir en cualquier capa, lo que es determinante para un equipo de 3 personas en fase de crecimiento. Si bien un lenguaje estáticamente tipado reduciría la cantidad de errores en tiempo de ejecución, este riesgo se mitiga adoptando **TypeScript** (que aporta tipado opcional sin renunciar al ecosistema JS), una **suite de tests automatizados** y revisiones de código obligatorias para los módulos financieros. El trade-off aceptado es asumir mayor disciplina de pruebas a cambio de un stack más homogéneo y mayor velocidad de iteración.

---

### ADR-002 — Modelo de datos para el módulo de CRM

**Categoría:** Modelo de Datos

**Contexto:**
El módulo de **CRM** de CrediMype almacena información de los clientes y, principalmente, el historial de **interacciones con el equipo de soporte**: tickets, mensajes por distintos canales (correo, WhatsApp, llamadas), notas internas y archivos adjuntos. La estructura de estas interacciones es **heterogénea y cambiante**: cada canal aporta campos distintos y se prevé incorporar nuevos canales en los próximos meses. El módulo opera de forma **aislada de los módulos transaccionales** (créditos, pagos), que sí requieren propiedades ACID estrictas. Se proyecta un volumen alto de eventos: ~50.000 interacciones diarias en el primer año, con crecimiento esperado del 100% anual.

**Alternativas:**
1. **Modelo relacional (PostgreSQL).**
   - Garantiza integridad referencial y soporta JSONB para campos semiestructurados.
   - Capacidad probada del equipo para operarlo y respaldarlo.
   - El esquema rígido obliga a migraciones cada vez que se añade un canal o campo nuevo.
2. **Modelo documental (MongoDB).**
   - Permite que cada interacción tenga su propio esquema sin migraciones.
   - Escalabilidad horizontal mediante sharding nativo.
   - Pierde garantías de integridad referencial fuera de un mismo documento; requiere disciplina aplicativa para mantener consistencia.

**Criterios de Elección:**
- **Flexibilidad de esquema** para soportar nuevos canales sin migraciones disruptivas.
- **Escalabilidad horizontal** ante el crecimiento proyectado.
- **Aislamiento del módulo CRM** respecto a los módulos financieros críticos.
- **Costos operativos** y experiencia del equipo en operación de la base de datos.

**Decisión:**
Se adopta MongoDB como motor de persistencia para el módulo de CRM, manteniendo PostgreSQL como motor estándar en los demás módulos transaccionales.

**Sustento:**
La naturaleza semiestructurada y cambiante de las interacciones favorece un modelo documental, que permite incorporar nuevos canales sin migraciones costosas. El módulo CRM no participa en transacciones financieras, por lo que la pérdida de garantías ACID transversales es asumible. La escalabilidad horizontal de MongoDB cubre el crecimiento proyectado sin necesidad de arquitecturas de sharding manual sobre PostgreSQL. El trade-off aceptado es introducir un segundo motor de base de datos en el stack —con su correspondiente costo operativo— a cambio de una flexibilidad estructural que sería costosa de obtener con un modelo relacional puro.

---
