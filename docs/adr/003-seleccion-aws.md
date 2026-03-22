1. Título
ADR 003: Selección de AWS (S3 y CloudFront) como proveedor de almacenamiento y CDN.
2. Fecha
22 de marzo de 2026.
3. Contexto
Tras aprobar la adopción de una arquitectura en la nube con CDN (ADR 002) para la plataforma "EducaMás", es necesario definir el proveedor tecnológico específico. Se evaluaron los principales referentes del mercado (AWS y Google Cloud Platform).
Para esta decisión, se analizaron los siguientes factores del proyecto:
a. Volumen estimado de videos: Se esperan 500 horas de video en el primer año.
b. Tráfico esperado: Se esperan 10.000 usuarios concurrentes en horas pico.
c. Presupuesto: Presupuesto limitado para infraestructura inicial.
d. Requisitos de rendimiento: Baja latencia en la reproducción de videos.
e. Requisitos de seguridad: Protección estricta contra descargas no autorizadas.
f. Conocimientos técnicos del equipo: Poca experiencia previa en la configuración y gestión de CDNs.
4. Decisión
Se decide ACEPTAR a Amazon Web Services (AWS) como proveedor, utilizando Amazon S3 para el almacenamiento base y Amazon CloudFront como CDN.
Justificación:
Seguridad integrada: CloudFront ofrece Signed URLs (URLs firmadas) de forma nativa, lo que resuelve directamente la necesidad de proteger los videos contra descargas públicas y accesos no autorizados.
Rendimiento y latencia: AWS cuenta con Edge Locations (nodos de CDN) estratégicos, incluyendo infraestructura física en Santiago de Chile. Esto garantiza una entrega de video con latencia mínima y sin interrupciones para el público a nivel local y regional.
Curva de aprendizaje: Al ser el proveedor con mayor cuota de mercado, existe una extensa documentación, SDKs maduros y una inmensa comunidad de soporte, lo que ayudará a mitigar la falta de experiencia del equipo con CDNs.
5. Consecuencias
a. Impacto en el desarrollo: El equipo deberá integrar el SDK de AWS en el backend (por ejemplo, utilizando tecnologías como Spring Boot) para orquestar la subida de archivos a S3 y la generación automatizada de las URLs firmadas de CloudFront.
b. Impacto en el mantenimiento: La delegación completa del mantenimiento del hardware y la red global al proveedor, garantizando alta disponibilidad sin esfuerzo operativo de nuestra parte.
c. Impacto en los costos: Se aplicará un modelo de precios de pago por uso (OPEX), facturando de manera mensual exactamente por los GB almacenados en S3 y los GB transferidos a través de CloudFront.
d. Riesgos: Fuerte dependencia tecnológica (Vendor lock-in) con el ecosistema de AWS. Además, una mala configuración en las políticas de caché de la CDN podría generar costos inesperados por transferencias redundantes desde S3.
6. Estado
Aceptado.
