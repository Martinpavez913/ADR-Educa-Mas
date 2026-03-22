1. Título
ADR 002: Adopción de almacenamiento en la nube con CDN para la distribución de videos.
2. Fecha
23 de marzo de 2026.
3. Contexto
Tras rechazar la infraestructura local por problemas de escalabilidad (ADR 001), el equipo evalúa la Opción A, que consiste en utilizar un servicio de almacenamiento en la nube (como AWS S3 o Google Cloud Storage) combinado con una CDN (Red de Entrega de Contenido) para la entrega eficiente de los videos a los usuarios.
Para esta evaluación, nos basamos en los siguientes factores del proyecto:
a. Volumen estimado de videos: Se esperan 500 horas de video en el primer año.
b. Tráfico esperado: Se esperan 10.000 usuarios concurrentes en horas pico.
c. Presupuesto: Presupuesto limitado para infraestructura.
d. Requisitos de rendimiento: Baja latencia en la reproducción de videos.
e. Requisitos de seguridad: Protección contra descargas no autorizadas.
f. Conocimientos técnicos del equipo: El equipo tiene experiencia en la gestión de servidores, pero poca experiencia con CDNs.
4. Decisión
Se decide ACEPTAR la Opción A (Almacenamiento en la nube con CDN).
Justificación y análisis de opciones: Para cumplir con la expectativa de 10.000 usuarios concurrentes consumiendo video con baja latencia , una arquitectura basada en la nube es la única viable considerando nuestro presupuesto limitado para infraestructura inicial. La CDN distribuirá la carga de tráfico a nivel global, evitando cuellos de botella.
Pros: Escalabilidad automática, pago por uso (sin inversión inicial en hardware), y herramientas nativas de los proveedores Cloud (como URLs firmadas) que facilitan la protección contra descargas no autorizadas.
Contras: El equipo técnico tiene una brecha de conocimiento respecto a las CDNs , por lo que habrá una curva de aprendizaje inicial que afectará los tiempos de desarrollo.
5. Consecuencias
a. Impacto en el desarrollo: Se requerirá integrar con la API del proveedor de la nube y la CDN. Esto implica que el equipo deberá invertir tiempo en capacitarse sobre estas tecnologías.
b. Impacto en el mantenimiento: El mantenimiento de la infraestructura será responsabilidad del proveedor de la nube, lo que reduce drásticamente la carga operativa de nuestro equipo.
c. Impacto en los costos: Se incurrirá en costos de almacenamiento y transferencia de datos, pero se evitarán los costos de hardware y mantenimiento de servidores. Pasamos de un modelo de inversión (CAPEX) a uno de gasto operativo (OPEX).
d. Riesgos: Existe dependencia de un proveedor externo y un posible aumento de costos a largo plazo si el tráfico de la plataforma crece sin una optimización adecuada del peso de los videos.
6. Estado
Aceptado.

