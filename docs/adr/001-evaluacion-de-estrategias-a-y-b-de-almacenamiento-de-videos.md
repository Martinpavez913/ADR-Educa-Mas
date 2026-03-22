1. Título
ADR 001: Evaluación de estrategias A y B de almacenamiento de videos.
2. Fecha
22 de marzo de 2026.
3. Contexto
La empresa "EducaMás" necesita definir la estrategia de almacenamiento y distribución para los videos de sus cursos. En este documento se evalúan las opciones A y B. La primera opción (A), consta de almacenamiento en la nube con CDN (Red de Entrega de Contenido): Utilizar un servicio de almacenamiento en la nube como AWS S3 o Google Cloud Storage, combinado con una CDN para la entrega eficiente de los videos a los usuarios, mientras que la segunda opción (B), consiste en almacenamiento y mantención en servidores propios de la empresa.
Para este análisis, consideramos las siguientes variables del proyecto:
Volumen estimado de videos: Se proyectan 500 horas de video durante el primer año.
Tráfico esperado: Peaks de 10.000 usuarios concurrentes.
Presupuesto: Infraestructura con presupuesto limitado.
Requisitos de rendimiento: Reproducción de vídeo con baja latencia.
Requisitos de seguridad: Protección contra descargas no autorizadas.
Conocimientos técnicos: El equipo posee experiencia en la gestión de servidores físicos.
4. Decisión
Se decide RECHAZAR la Opción B de almacenamiento en servidores propios.
Justificación: El motivo principal de este rechazo es la incapacidad de escalar de forma elástica y rentable. Transmitir video a 10.000 usuarios concurrentes exige un ancho de banda masivo y un alto poder de procesamiento. En un entorno de servidores propios (on-premise), la única forma de soportar este peak es sobredimensionando la infraestructura desde el día uno (comprando servidores y enlaces de red gigantescos "por si acaso"), lo cual es inviable debido a nuestro presupuesto limitado.
Si la plataforma tiene un crecimiento repentino de estudiantes, los servidores físicos se saturarían, provocando alta latencia y fallos en la reproducción. La escalabilidad física es lenta (requiere comprar, instalar y configurar nuevo hardware), lo que nos impediría reaccionar a tiempo ante el éxito comercial de los cursos.


5. Consecuencias
Impacto en el desarrollo: Al descartar esta opción, el equipo de desarrollo no podrá aprovechar su experiencia actual en la gestión de servidores locales para el almacenamiento de medios, obligándonos a adoptar tecnologías externas.
Impacto en el mantenimiento: El equipo se libera de la carga operativa de mantener discos duros, reemplazar hardware dañado y gestionar la red física.
Impacto en los costos: Se evitan los altísimos costos iniciales de inversión en hardware (CAPEX) y los costos de mantenimiento de centros de datos propios.
Riesgos: Evitamos el riesgo de caída del servicio por cuellos de botella en nuestra red local en horas punta, pero adquirimos el desafío de buscar y asegurar una solución externa que cumpla con las expectativas.
6. Estado
Rechazado.

