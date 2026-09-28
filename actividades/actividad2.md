# Actividad: Calidad de Software

## Contexto

La funcionalidad de un sistema no es suficiente para garantizar su éxito. Los sistemas son frecuentemente rediseñados no porque sean funcionalmente deficientes —los reemplazos suelen ser funcionalmente idénticos— sino porque son difíciles de mantener, escalar o portar; porque son demasiado lentos; o porque han sido comprometidos por vulnerabilidades de seguridad (Bass et al. 2021). En otras palabras, **el diseño de un software está altamente influenciado por los atributos de calidad**.

Esta actividad aborda la calidad desde dos ángulos complementarios:

1. **Identificación y análisis** de los atributos de calidad más relevantes para el proyecto del grupo, con sustento sobre cómo impactan las decisiones de diseño.
2. **Especificación formal de requisitos de atributos de calidad** haciendo uso de escenarios de calidad, siguiendo la estructura de seis partes propuesta.

---

## Parte 1: Identificación de Atributos de Calidad

Podemos definir un **atributo de calidad (QA)** como una propiedad medible o verificable de un sistema que indica en qué medida satisface las necesidades de sus stakeholders. Se puede pensar en él como la medida de la "utilidad" de un producto a lo largo de alguna dimensión de interés para un stakeholder. **Por ejemplo**, un usuario final (stakeholder) busca acceder rápidamente al sistema; para él, la utilidad se refleja en el tiempo de respuesta (medida de rendimiento): mientras menor sea el tiempo de carga, mayor es el valor percibido del sistema.


> Los atributos de calidad no se alcanzan de manera independiente. Optimizar uno suele generar impactos —positivos o negativos— sobre los demás. Por eso, nuestro diseño debe evaluar y balancear estos efectos cruzados, buscando un punto de equilibrio entre los distintos atributos. **Ejemplo:** mejorar la seguridad (por ejemplo, con autenticación multifactor) tiene un efecto positivo en el sistema, pero introduce mayor fricción en el acceso, impactando la usabilidad.

### Qué incluir en esta sección

Realice un listado de atributos de calidad y relaciónelos al contexto específico de su proyecto. Considere los siguiente aspectos por cada atributo:

- Argumentación de por qué el atributo seleccionados es relevantes para su proceso de negocio.
- Riesgos asociados si no considera adecuadamente en el diseño.
- Impacto en otros atributos de calidad (interacciones).
- Posibles tácticas para llegar al nivel deseado. **Ejemplo:** para alcanzar el nivel deseado de disponibilidad, se pueden aplicar tácticas de redundancia a nivel de infraestructura, como contar con una base de datos en réplica (failover) o desplegar el sistema en múltiples regiones del proveedor cloud, de modo que una caída en una región no afecte la continuidad del servicio.

Puede utilizar este listado como referencia:

1. **Disponibilidad:** Capacidad del sistema de estar operativo y accesible cuando se le requiere. Implica la habilidad de sobrevivir a fallos y recuperarse de ellos 

2. **Rendimiento:** Comportamiento temporal del sistema ante estímulos: tiempo de respuesta, throughput y uso de recursos.

3. **Seguridad:** Capacidad del sistema de proteger los datos y los servicios frente a accesos no autorizados, manteniendo confidencialidad, integridad y disponibilidad.

4. **Mantenibilidad:** Grado en que un sistema puede ser modificado de manera efectiva y eficiente para corregir defectos, mejorar su desempeño o adaptarse a cambios en el entorno.

5. **Usabilidad:** Facilidad con la que los usuarios pueden aprender a usar el sistema, operar sus funciones y recuperarse de errores.

6. **Escalabilidad:** Capacidad del sistema de manejar incrementos en la carga de trabajo —usuarios, transacciones o datos— sin degradación significativa del rendimiento.


## Parte 2: Especificación de Atributos de Calidad mediante Escenarios

### Estructura del Escenario de Atributo de Calidad

El enfoque que utilizaremos en el curso propone capturar los requisitos de atributos de calidad como **escenarios de seis partes**. Esta estructura permite tratar todos los atributos de forma consistente:

| Parte | Descripción |
|---|---|
| **Fuente del estímulo** | Entidad (persona, sistema u otro actor) que genera el estímulo |
| **Estímulo** | Evento o condición que llega al sistema o al proyecto |
| **Artefacto** | Componente del sistema que recibe el estímulo |
| **Entorno** | Circunstancias en las que ocurre el escenario (modo de operación, estado del sistema) |
| **Respuesta** | Comportamiento del sistema como resultado del estímulo |
| **Medida de respuesta** | Criterio cuantificable que permite evaluar si la respuesta es adecuada |

Deben documentar escenarios para cada atributo de calidad relevante del sistema (varios escenarios por atributo). Estos atributos pueden definirse a nivel global o específico por módulos o componentes. Por ejemplo, el módulo de seguridad /login podría tener requisitos de seguridad más estrictos que el módulo de reportes, por su mayor criticidad.

### Ejemplos de Referencia

| **Atributo de Calidad** | **Fuente del Estímulo** | **Estímulo** | **Artefacto** | **Entorno** | **Respuesta** | **Medida de Respuesta** |
|---|---|---|---|---|---|---|
| **Disponibilidad** | Servidor de base de datos en la nube | Fallo inesperado del servidor principal | Módulo de Gestión de Solicitudes | Operación en horario de alta demanda | El sistema conmuta automáticamente al servidor de respaldo sin pérdida de sesión | El sistema está disponible el 99.9% del tiempo; la recuperación ocurre en menos de 30 segundos |
| **Disponibilidad** | Equipo de desarrollo | Despliegue de nueva versión del sistema | Servicio de Autenticación | Fuera del horario de atención (22:00–06:00) | El sistema entra en modo de mantenimiento programado con notificación previa a usuarios | El tiempo de inactividad no supera 15 minutos; los usuarios reciben notificación con al menos 24 horas de anticipación |
| **Rendimiento** | Usuarios finales (estudiantes / usuarios concurrentes) | 500 solicitudes simultáneas de consulta de estado | Módulo de Consulta / Búsqueda | Período de alta demanda (inicio de ciclo académico) | El sistema procesa todas las solicitudes en paralelo sin errores de timeout | El tiempo de respuesta no supera los 2 segundos para el percentil 95 de las solicitudes |
| **Rendimiento** | Administrador del sistema | Consulta masiva de registros históricos (> 1 millón de filas) | Servicio de Reportes | Operación normal fuera de hora pico | El sistema ejecuta la consulta mediante índices optimizados y devuelve los resultados paginados | El tiempo de respuesta no excede los 5 segundos; el uso de CPU no supera el 70% durante la consulta |
| **Seguridad** | Usuario no autenticado (externo) | Intento de acceso a datos sensibles sin credenciales válidas | Módulo de Control de Acceso | Operación normal en línea | El sistema rechaza la solicitud, registra el intento en el log de auditoría y bloquea la IP tras 5 intentos fallidos | El 100% de los intentos no autorizados son bloqueados; el log de auditoría registra IP, timestamp y tipo de intento en menos de 1 segundo |
| **Seguridad** | Desarrollador interno | Solicitud de cambio que afecta datos personales de usuarios | Módulo de Gestión de Usuarios | Ambiente de desarrollo / QA | El sistema requiere aprobación de un segundo revisor antes de aplicar el cambio en producción | Ningún cambio que afecte datos sensibles se despliega sin doble aprobación; trazabilidad completa en el historial de cambios |
| **Mantenibilidad** | Equipo de desarrollo | Solicitud de incorporar un nuevo proveedor de notificaciones (ej. cambiar SMS por WhatsApp) | Módulo de Notificaciones | Post-despliegue, en operación normal | El equipo reemplaza el adaptador del proveedor sin modificar la lógica de negocio ni otros módulos | El cambio requiere modificar únicamente 1 componente; el tiempo de implementación y prueba no supera 4 horas de trabajo |
| **Mantenibilidad** | Product Owner | Solicitud de nuevo campo en el formulario de registro | Módulo de Registro / Formularios | Operación normal | El campo se incorpora en el modelo de datos, la interfaz y la validación de forma independiente al resto del sistema | El cambio no afecta más de 3 artefactos; no requiere modificaciones en otros módulos |
| **Usabilidad** | Usuario nuevo sin experiencia previa | Primer intento de completar el flujo principal del módulo | Interfaz de usuario del módulo principal | Primer uso del sistema, sin capacitación previa | El sistema guía al usuario mediante mensajes claros, validaciones en línea y ayuda contextual | El usuario completa el flujo principal en no más de 3 pasos y sin errores en el 80% de los casos observados en pruebas de usabilidad |
| **Escalabilidad** | Incremento de usuarios registrados | Crecimiento del 200% en el número de usuarios activos respecto al año anterior | Infraestructura del sistema (servidor de aplicaciones y BD) | Crecimiento orgánico planificado | El sistema escala horizontalmente de forma automática o semiautomática sin intervención de código | El tiempo de respuesta promedio se mantiene por debajo de 3 segundos con el doble de usuarios concurrentes; el costo de infraestructura crece de forma proporcional, no exponencial |

---

## Referencias Bibliográficas

> Los siguientes textos son la bibliografía de referencia del curso y **son materia de evaluación (control de lectura)**. Se espera que el alumno conozca los conceptos fundamentales presentados en estos capítulos.

- Bass, L., Clements, P., & Kazman, R. (2021). *Software Architecture in Practice* (4th ed.). Addison-Wesley Professional. [**Capítulo 3: Understanding Quality Attributes.**](https://drive.google.com/file/d/1ZFOIJDiITemYbqq5xpZYJgGyXPAX9mUp/view?usp=drive_link)

- Pressman, R., & Maxim, B. (2019). *Software Engineering: A Practitioner's Approach* (9th ed.). McGraw-Hill Education. [**Capítulo 15: Quality Concepts.**](https://drive.google.com/file/d/1w2P1pP9N9GX2xzvsTGLxn2rbjvjA6fzd/view?usp=drive_link)
