# Registro de Decisión Arquitectónica (ADR)

## 1. Título

Decisión sobre la estrategia de almacenamiento y entrega de videos para EducaMás.

## 2. Fecha

23 de marzo de 2026.

## 3. Contexto

La plataforma "EducaMás" necesita definir la infraestructura para alojar sus clases. Se debaten dos alternativas: **Opción A** (Almacenamiento en la nube con CDN) y **Opción B** (Almacenamiento en servidores propios). Para decidir, consideramos los siguientes factores del proyecto:

- **Volumen estimado de videos:** Se esperan 500 horas de video en el primer año.
- **Tráfico esperado:** Se proyectan picos de hasta 10,000 usuarios concurrentes.
- **Presupuesto:** La empresa tiene un presupuesto muy limitado para infraestructura inicial.
- **Requisitos de rendimiento:** Se exige baja latencia (los videos deben cargar rápido y sin cortes).
- **Requisitos de seguridad:** Es obligatorio proteger el contenido contra descargas no autorizadas (piratería).
- **Conocimientos técnicos del equipo:** El equipo tiene experiencia gestionando servidores, pero poca experiencia en configuración de CDNs.

## 4. Decisión

Se elige la **Opción A** (Almacenamiento en la nube con CDN).

**Justificación:** A pesar de que el equipo tiene más experiencia con servidores propios (Opción B), comprar hardware físico que soporte a 10,000 usuarios al mismo tiempo supera por completo nuestro presupuesto limitado. La Opción A nos permite evitar gastos iniciales altos, delegar el mantenimiento físico, y cumplir con el requisito de baja latencia gracias a la distribución geográfica de la CDN.

## 5. Consecuencias

- **Impacto en el desarrollo:** Los desarrolladores tendrán que investigar y aprender a integrar la API del proveedor Cloud y de la CDN. Además, deberán programar la generación de URLs firmadas para cumplir con el requisito de bloquear las descargas de videos.
- **Impacto en el mantenimiento:** Habrá un alivio operativo importante, ya que el mantenimiento de los servidores físicos será responsabilidad del proveedor de la nube.
- **Impacto en los costos:** Pasaremos de un modelo de inversión inicial (comprar servidores) a un modelo de pago mensual. Se incurrirá en costos solo por el almacenamiento usado y la transferencia de datos.
- **Riesgos:** Existe el riesgo de dependencia tecnológica con el proveedor de la nube (Vendor lock-in). Además, si no se configuran bien las alertas de presupuesto, un pico anómalo de tráfico podría generar una factura alta.

## 6. Estado

**Aceptado.**
