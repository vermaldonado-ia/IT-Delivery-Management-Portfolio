# Modelo de Datos del Portafolio

## 1. Objetivo

Este documento define la estructura de los conjuntos de datos utilizados en el portafolio de Gestión y Delivery TI.

El modelo permite construir indicadores, dashboards ejecutivos y análisis de evolución, manteniendo trazabilidad entre los datos, las métricas y las decisiones de gestión.

Todos los registros de este repositorio son **datos ficticios de demostración (DEMO)**. No representan información de clientes ni de organizaciones reales.

## 2. Arquitectura de datos

El portafolio utiliza tres dominios de información:

| Dominio | Archivo principal | Propósito |
|---|---|---|
| Gestión ejecutiva | `executive-kpis.csv` | Seguimiento de iniciativas, avance, hitos, riesgos y SLA |
| Entrega ágil | `agile-delivery.csv` | Seguimiento de equipos, Sprints, cumplimiento y flujo de trabajo |
| Entrega técnica y operaciones | En desarrollo | Seguimiento de despliegues, servicios, infraestructura e incidentes |

## 3. Dataset: Gestión ejecutiva

**Archivo:** `04-demo-data/executive-kpis.csv`

**Unidad de análisis:** una iniciativa en una fecha de corte.

### Campos

| Campo | Descripción |
|---|---|
| `fecha_corte` | Fecha de referencia del registro |
| `iniciativa_id` | Identificador único de la iniciativa |
| `iniciativa` | Nombre de la iniciativa |
| `estado` | Estado general de la iniciativa |
| `avance_planificado_pct` | Porcentaje de avance planificado |
| `avance_real_pct` | Porcentaje de avance real |
| `hitos_planificados_periodo` | Hitos planificados para el período |
| `hitos_cumplidos_a_tiempo` | Hitos cumplidos dentro del plazo |
| `riesgos_criticos_abiertos` | Cantidad de riesgos críticos abiertos |
| `casos_sla_elegibles` | Casos considerados para medir cumplimiento de SLA |
| `casos_sla_cumplidos` | Casos que cumplieron el SLA |
| `disponibilidad_pct` | Porcentaje de disponibilidad del servicio |
| `origen_dato` | Fuente de los datos |
| `tipo_dato` | Identifica si el registro es DEMO o real |

### Indicadores derivados

- Desviación del avance: avance real menos avance planificado.
- Cumplimiento de hitos: hitos cumplidos a tiempo / hitos planificados.
- Cumplimiento de SLA: casos SLA cumplidos / casos SLA elegibles.
- Evolución de riesgos críticos.
- Tendencia de disponibilidad.

**Consideración:** cuando el denominador sea cero o no existan datos suficientes, el indicador debe mostrarse como no disponible, no como 0%.

## 4. Dataset: Gestión de proyectos y entrega ágil

**Archivo:** `04-demo-data/agile-delivery.csv`

**Unidad de análisis:** un equipo durante un Sprint.

### Campos

| Campo | Descripción |
|---|---|
| `fecha_inicio` | Fecha de inicio del Sprint |
| `fecha_fin` | Fecha programada de término del Sprint |
| `equipo_id` | Identificador del equipo |
| `equipo` | Nombre del equipo |
| `proyecto` | Proyecto o producto asociado |
| `sprint` | Número o identificador del Sprint |
| `sprint_goal` | Objetivo comprometido para el Sprint |
| `sprint_goal_alcanzado` | Indica si se alcanzó el Sprint Goal |
| `capacidad_horas` | Capacidad disponible del equipo en horas |
| `elementos_comprometidos` | Elementos comprometidos al inicio |
| `elementos_completados` | Elementos completados durante el Sprint |
| `carry_over` | Elementos pendientes trasladados al siguiente Sprint |
| `trabajo_no_planificado` | Trabajo incorporado después de la planificación |
| `throughput` | Cantidad de elementos completados |
| `cycle_time_mediana_dias` | Mediana de días desde inicio de trabajo hasta finalización |
| `lead_time_mediana_dias` | Mediana de días desde solicitud hasta entrega |
| `wip_promedio` | Promedio de elementos en curso |
| `impedimentos` | Cantidad de impedimentos registrados |
| `defectos` | Cantidad de defectos identificados |
| `retrabajo_elementos` | Cantidad de elementos que requirieron retrabajo |
| `tipo_dato` | Identifica si el registro es DEMO o real |

### Indicadores derivados

- Cumplimiento del Sprint Goal.
- Cumplimiento del compromiso.
- Carry-over.
- Trabajo no planificado.
- Throughput por Sprint.
- Cycle Time y Lead Time.
- WIP promedio.
- Impedimentos, defectos y retrabajo.
- Evolución de la capacidad y predictibilidad del equipo.

### Reglas de interpretación

1. El cumplimiento del Sprint Goal debe analizarse separadamente del porcentaje de elementos completados.
2. La velocidad o cantidad de elementos completados no debe utilizarse como medida aislada de productividad.
3. No se deben comparar equipos sin considerar diferencias de contexto, capacidad, tipo de trabajo y tamaño de los elementos.
4. Los Sprints en curso deben distinguirse de los Sprints cerrados.
5. El Sprint 12 del conjunto DEMO se encuentra en curso al 7 de noviembre de 2026. Sus valores son parciales y no deben compararse directamente con Sprints cerrados.
6. El throughput representa cantidad de elementos completados; no equivale necesariamente a valor de negocio entregado.

## 5. Dataset: Entrega técnica y operaciones TI

**Estado:** pendiente de construcción.

Este dominio incorporará información para analizar tres dimensiones:

### 5.1. DORA y despliegues

- Frecuencia de despliegue.
- Lead Time for Changes.
- Change Failure Rate.
- Failed Deployment Recovery Time.

### 5.2. Cloud Monitoring y Observabilidad

- Disponibilidad.
- Latencia p95.
- Tasa de errores.
- Uso de CPU y memoria.
- Capacidad de almacenamiento.
- Tráfico de red.
- Costos de infraestructura.

### 5.3. Operaciones TI

- Incidentes.
- Severidad.
- MTTR.
- Cumplimiento de SLA.
- Continuidad operacional.

Estos indicadores se analizarán según su contexto y fuente de información. No se atribuirán incidentes a despliegues sin evidencia de relación causal.

## 6. Reglas generales de calidad de datos

- Cada dataset debe tener una unidad de análisis claramente definida.
- Las fechas deben utilizar el formato `YYYY-MM-DD`.
- Los porcentajes deben expresarse de forma consistente.
- Los valores desconocidos deben identificarse como no disponibles, no reemplazarse arbitrariamente por cero.
- Los datos DEMO deben identificarse explícitamente.
- Los registros deben mantener consistencia entre períodos, equipos e iniciativas.
- Los indicadores calculados deben tener una definición documentada.
- Los datos parciales deben distinguirse de los períodos cerrados.

## 7. Trazabilidad y uso en dashboards

Los datos se utilizarán para construir visualizaciones que permitan:

1. Establecer una línea base.
2. Observar la evolución por período.
3. Identificar desviaciones y tendencias.
4. Interpretar riesgos y problemas de entrega.
5. Evaluar resultados y cumplimiento.
6. Facilitar decisiones de gestión.

La información ejecutiva debe presentar indicadores consolidados y relevantes para la toma de decisiones. El detalle operativo y técnico debe permanecer en los módulos especializados.

## 8. Principio de gestión

**Línea base → Evolución → Resultado → Decisión**

El propósito del modelo no es solamente visualizar indicadores, sino convertir datos de gestión y entrega TI en información útil para la toma de decisiones.
