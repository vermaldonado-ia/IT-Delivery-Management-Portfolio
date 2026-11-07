# Diccionario de Indicadores de Gestión TI

## Objetivo

Establecer un marco común de medición para los tres productos del portafolio. Cada indicador debe tener una definición, fórmula de cálculo, fuente de información, período de medición y responsable.

## 1. Gestión Ejecutiva TI

| Indicador | Definición | Objetivo de gestión |
|---|---|---|
| Predictibilidad de entrega | Porcentaje de compromisos planificados que se entregan según lo acordado | Evaluar confiabilidad de entrega |
| Cumplimiento de hitos | Hitos completados a tiempo respecto de los hitos comprometidos | Controlar cumplimiento del cronograma |
| Riesgos críticos abiertos | Cantidad de riesgos críticos sin resolver | Facilitar decisiones y escalamiento |
| Cumplimiento de SLA | Porcentaje de compromisos de servicio cumplidos | Evaluar desempeño del servicio |
| Disponibilidad del servicio | Porcentaje de tiempo en que un servicio está disponible | Evaluar continuidad operacional |

## 2. Gestión de Proyectos y Entrega Ágil

| Indicador | Definición | Objetivo de gestión |
|---|---|---|
| Cumplimiento del objetivo del Sprint | Porcentaje de Sprints cuyo objetivo fue alcanzado | Evaluar logro de objetivos |
| Cumplimiento del compromiso | Elementos completados respecto de los comprometidos | Analizar confiabilidad de planificación |
| Carry-over | Trabajo que pasa de un Sprint al siguiente | Identificar trabajo pendiente |
| Throughput | Cantidad de elementos completados por período | Analizar volumen de entrega |
| Cycle Time | Tiempo desde el inicio del trabajo hasta su finalización | Identificar restricciones del flujo |
| Lead Time | Tiempo desde la solicitud hasta la entrega | Evaluar capacidad de respuesta |
| WIP | Cantidad de elementos en curso | Identificar exceso de trabajo simultáneo |
| Impedimentos | Elementos de trabajo bloqueados | Visibilizar obstáculos |

## 3. Entrega Técnica y Operaciones

### Indicadores DORA

- Frecuencia de despliegues: frecuencia con que se realizan despliegues en producción.
- Tiempo de entrega de cambios: tiempo desde el registro del código hasta su puesta en producción.
- Tasa de fallas por cambios: proporción de despliegues que generan fallas y requieren intervención.
- Tiempo de recuperación de despliegues fallidos: tiempo necesario para recuperar el servicio después de un despliegue fallido.

### Monitoreo Cloud y Observabilidad

- Disponibilidad: porcentaje de tiempo en que el servicio está disponible.
- Latencia p95: tiempo de respuesta por debajo del cual se completa el 95 % de las solicitudes.
- Tasa de errores: proporción de solicitudes que presentan errores.
- Utilización de CPU: consumo de capacidad de procesamiento.
- Utilización de memoria: consumo de memoria.
- Utilización de almacenamiento: capacidad de almacenamiento utilizada.
- Tráfico de red: volumen de información transmitida.
- Costo Cloud: consumo económico de infraestructura durante un período.

### Operaciones y Gestión de Servicios TI

- Cantidad de incidentes: incidentes registrados durante el período.
- MTTR: tiempo medio de recuperación del servicio.
- Cumplimiento de SLA: porcentaje de incidentes o solicitudes atendidos dentro de los compromisos establecidos.
- Incidentes críticos: cantidad de incidentes de alta severidad.

## Gobierno de los Indicadores

Cada indicador debe documentar:

- Definición y fórmula de cálculo.
- Unidad de medida.
- Período de medición.
- Alcance y población considerada.
- Sistema fuente.
- Responsable del dato.
- Calidad y confiabilidad de la información.
- Línea base y meta, cuando estén validadas.

## Criterios de Interpretación

- No comparar equipos sin considerar su contexto.
- No interpretar la velocidad como productividad.
- No confundir trabajo completado con valor de negocio.
- No atribuir incidentes a despliegues sin evidencia.
- Utilizar «No medido» o «Sin dato» cuando no exista información confiable.

> Todos los datos de demostración de este portafolio son ficticios y no representan el desempeño de ninguna organización real.
