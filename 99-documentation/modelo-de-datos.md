# Modelo de Datos del Portafolio de Gestión TI

## 1. Objetivo

Definir la estructura y organización de los datos que alimentarán los tres productos del portafolio:

1. Dashboard Ejecutivo de Gestión TI.
2. Gestión de Proyectos y Entrega Ágil.
3. Entrega Técnica y Operaciones TI.

El modelo busca mantener consistencia entre las fuentes de información, los indicadores, las visualizaciones y los reportes ejecutivos.

## 2. Principios de diseño

- Separar los datos por dominio de gestión.
- Mantener trazabilidad de las fuentes.
- Utilizar períodos de medición consistentes.
- Diferenciar datos reales, estimados y ficticios.
- Evitar duplicidad de registros.
- Permitir consolidación ejecutiva sin perder el detalle operativo.
- Mantener correspondencia con el Diccionario de Indicadores de Gestión TI.

## 3. Organización de los datos

### 3.1. Gestión Ejecutiva TI

Archivo de referencia: `executive-kpis.csv`

| Campo | Descripción |
|---|---|
| fecha_corte | Fecha de actualización |
| iniciativa | Nombre de la iniciativa |
| estado | Estado general |
| avance_porcentual | Porcentaje de avance |
| hitos_planificados | Hitos comprometidos |
| hitos_cumplidos | Hitos completados a tiempo |
| riesgos_criticos | Riesgos críticos abiertos |
| cumplimiento_sla | Porcentaje de cumplimiento |
| disponibilidad | Porcentaje de disponibilidad |
| origen_dato | Fuente de información |
| tipo_dato | DEMO o REAL |

### 3.2. Gestión de Proyectos y Entrega Ágil

Archivo de referencia: `agile-delivery.csv`

| Campo | Descripción |
|---|---|
| fecha_corte | Fecha de medición |
| equipo | Equipo evaluado |
| proyecto | Proyecto asociado |
| sprint | Identificador del Sprint |
| sprint_goal | Objetivo del Sprint |
| sprint_goal_alcanzado | Resultado del objetivo |
| elementos_comprometidos | Elementos comprometidos al inicio |
| elementos_completados | Elementos completados |
| carry_over | Elementos pendientes |
| trabajo_no_planificado | Elementos incorporados durante el Sprint |
| throughput | Elementos completados |
| cycle_time | Tiempo de ciclo |
| lead_time | Tiempo de entrega |
| wip | Trabajo en curso |
| impedimentos | Elementos bloqueados |
| tipo_dato | DEMO o REAL |

### 3.3. Entrega Técnica y Operaciones TI

Archivo de referencia: `technical-operations.csv`

| Campo | Descripción |
|---|---|
| fecha_corte | Fecha de medición |
| servicio | Aplicación o servicio evaluado |
| frecuencia_despliegues | Despliegues exitosos |
| lead_time_cambios | Tiempo de entrega de cambios |
| tasa_fallas_cambios | Porcentaje de fallas asociadas a cambios |
| tiempo_recuperacion | Tiempo de recuperación |
| disponibilidad | Porcentaje de disponibilidad |
| latencia_p95 | Latencia del percentil 95 |
| tasa_errores | Porcentaje de solicitudes con error |
| utilizacion_cpu | Porcentaje de CPU utilizada |
| utilizacion_memoria | Porcentaje de memoria utilizada |
| almacenamiento | Porcentaje de almacenamiento utilizado |
| trafico_red | Volumen de tráfico |
| costo_cloud | Costo de infraestructura |
| incidentes | Cantidad de incidentes |
| mttr | Tiempo medio de recuperación |
| tipo_dato | DEMO o REAL |

## 4. Reglas de calidad de datos

- Las fechas deben utilizar un formato consistente: `YYYY-MM-DD`.
- Los porcentajes deben almacenarse como valores numéricos.
- Los tiempos deben identificar su unidad de medida.
- Los campos sin información no deben completarse con valores inventados.
- Los registros DEMO deben identificarse claramente.
- Los indicadores calculados deben conservar la trazabilidad de sus datos de origen.
- Los valores agregados deben respetar la definición del diccionario de indicadores.

## 5. Relación entre los productos

El Dashboard Ejecutivo consolida información proveniente de la gestión ágil y de la entrega técnica y operacional.

Los productos especializados conservan el detalle necesario para analizar las causas, tendencias y desviaciones.

La consolidación ejecutiva no debe reemplazar el análisis operativo ni ocultar las diferencias entre proyectos, equipos y servicios.

## 6. Consideraciones

Este modelo constituye una estructura inicial para datos de demostración.

Los campos y fuentes definitivas podrán ajustarse según los sistemas disponibles, la calidad de los datos y las necesidades de gestión.

Todos los datos ficticios deben estar identificados como DEMO y no representan información real de ninguna organización.
