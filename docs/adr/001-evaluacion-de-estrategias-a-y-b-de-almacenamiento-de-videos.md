ADR 001: Estrategia de almacenamiento y distribución de videos para EducaMás

2. Fecha: 22 de marzo de 2026
3. Contexto: La empresa "EducaMás" está desarrollando una plataforma de cursos online y necesita definir la arquitectura de almacenamiento y distribución para sus contenidos en video. Las alternativas evaluadas son el uso de almacenamiento en la nube con CDN (Opción A) y el almacenamiento en servidores propios (Opción B). Para tomar esta decisión, consideramos los siguientes factores:
a. Volumen estimado de videos: Se proyecta alojar aproximadamente 500 horas de video durante el primer año de operación.
b. Tráfico esperado: Se estiman peaks de hasta 10.000 usuarios concurrentes consumiendo video al mismo tiempo.
c. Presupuesto: Contamos con un presupuesto inicial limitado para la compra de infraestructura física (hardware).
d. Requisitos de rendimiento: Es crítico mantener una baja latencia para evitar interrupciones (buffering) en la reproducción de los cursos.
e. Requisitos de seguridad: Se requiere protección contra descargas no autorizadas para proteger la propiedad intelectual de los cursos.
f. Conocimientos técnicos del equipo: El equipo actual tiene experiencia gestionando servidores físicos, pero posee poca experiencia práctica en la configuración de Redes de Entrega de Contenido (CDNs).

4. Decisión: Se elige la Opción A: Almacenamiento en la nube con CDN. Justificación: Aunque el equipo tiene experiencia en servidores propios (Opción B) , mantener 10.000 conexiones concurrentes de video desde un único centro de datos saturaría rápidamente el ancho de banda y requeriría una inversión altísima en hardware, algo incompatible con nuestro presupuesto limitado. La nube nos permite un modelo de pago por uso, y la CDN garantiza que los videos se entregan con baja latencia desde el servidor más cercano geográficamente al estudiante. Además, los proveedores cloud ofrecen firmas de URLs (Signed URLs) que resuelven fácilmente el requisito de seguridad contra descargas no autorizadas.

5. Consecuencias:
a. Impacto en el desarrollo: El equipo de desarrollo deberá aprender e integrar la API del proveedor Cloud (ej. AWS S3 o GCP) y configurar las políticas de la CDN.
b. Impacto en el mantenimiento: La carga operativa disminuye drásticamente, ya que la responsabilidad de mantener los discos duros y la red física recae sobre el proveedor de la nube.
c. Impacto en los costos: Cambiamos de un modelo de inversión inicial (comprar servidores) a un modelo de gasto operativo; pagaremos mensualmente por GB almacenado y por GB transferido a los usuarios.
d. Riesgos: Generamos dependencia tecnológica con un proveedor externo (Vendor lock-in) y existe el riesgo de que los costos mensuales se disparen si el tráfico aumenta sin optimizar la compresión de los videos. Además, hay una curva de aprendizaje inicial para el equipo respecto al uso de la CDN.

6. Estado: Aceptado


