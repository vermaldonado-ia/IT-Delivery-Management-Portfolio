# Modelo de Datos del Portafolio de Gestión TI

## 1. Objetivo

Definir la estructura, organización, relaciones y reglas de interpretación de los datasets utilizados en los tres productos del portafolio.

El modelo permite mantener trazabilidad entre las fuentes de información, los indicadores de gestión y las visualizaciones ejecutivas.

Todos los registros incluidos en esta versión son ficticios y se utilizan exclusivamente con fines demostrativos.

**Tipo de información:** DEMO.

## 2. Organización de los datos

Los datasets se encuentran en la carpeta:

`04-demo-data/`

| Archivo | Producto | Registros | Nivel de detalle |
|---|---|---:|---|
| `executive-kpis.csv` | 01 - Dashboard Ejecutivo | 36 | Iniciativa y fecha de corte |
| `agile-delivery.csv` | 02 - Gestión Ágil | 48 | Equipo y Sprint |
| `deployments.csv` | 03 - Entrega Técnica y Operaciones | 48 | Despliegue |
| `cloud-monitoring.csv` | 03 - Entrega Técnica y Operaciones | 20 | Servicio y corte semanal |
| `incidents.csv` | 03 - Entrega Técnica y Operaciones | 15 | Incidente |

## 3. Dataset: executive-kpis.csv

### Propósito

Consolidar indicadores de gestión ejecutiva por iniciativa y fecha de corte.

Permite analizar avance, cumplimiento de hitos, riesgos, SLA y disponibilidad.

### Granularidad

Un registro representa una iniciativa en una fecha de corte determinada.

### Estructura

| Campo | Tipo | Descripción |
|---|---|---|
| `fecha_corte` | Fecha | Fecha de actualización del registro |
| `iniciativa_id` | Texto | Identificador único de la iniciativa |
| `iniciativa` | Texto | Nombre de la iniciativa |
| `estado` | Texto | Estado de la iniciativa |
| `avance_planificado_pct` | Decimal | Avance planificado en porcentaje |
| `avance_real_pct` | Decimal | Avance real en porcentaje |
| `hitos_planificados_periodo` | Entero | Hitos planificados para el período |
| `hitos_cumplidos_a_tiempo` | Entero | Hitos cumplidos dentro de la fecha comprometida |
| `riesgos_criticos_abiertos` | Entero | Cantidad de riesgos críticos abiertos |
| `casos_sla_elegibles` | Entero | Casos considerados para medir cumplimiento de SLA |
| `casos_sla_cumplidos` | Entero | Casos que cumplen el SLA |
| `disponibilidad_pct` | Decimal | Disponibilidad registrada del servicio |
| `origen_dato` | Texto | Fuente de origen de la información |
| `tipo_dato` | Texto | Clasificación del registro, DEMO |

### Indicadores asociados

- Predictibilidad de entrega.
- Desviación de avance planificado.
- Riesgos críticos abiertos.
- Cumplimiento de SLA.
- Disponibilidad.

### Consideraciones

- El dataset contiene seis iniciativas y seis cortes por iniciativa.
- Los cortes corresponden a junio, julio, agosto, septiembre, octubre y 7 de noviembre de 2026.
- El corte del 7 de noviembre representa un período parcial.
- No se deben comparar directamente los valores acumulados o de período parcial con meses completos sin considerar su alcance temporal.
- Los hitos deben interpretarse de acuerdo con el período al que corresponden.

## 4. Dataset: agile-delivery.csv

### Propósito

Registrar la evolución de la entrega ágil por equipo y Sprint.

Permite analizar cumplimiento del Sprint Goal, compromiso, carry-over, trabajo no planificado, flujo, impedimentos y calidad.

### Granularidad

Un registro representa un equipo durante un Sprint.

### Estructura

| Campo | Tipo | Descripción |
|---|---|---|
| `fecha_inicio` | Fecha | Inicio del Sprint |
| `fecha_fin` | Fecha | Fecha de término planificada del Sprint |
| `equipo_id` | Texto | Identificador del equipo |
| `equipo` | Texto | Nombre del equipo |
| `proyecto` | Texto | Proyecto asociado |
| `sprint` | Texto | Identificador del Sprint |
| `sprint_goal` | Texto | Objetivo del Sprint |
| `sprint_goal_alcanzado` | Texto | Resultado registrado del Sprint Goal, con valores Si o No |
| `capacidad_horas` | Decimal | Capacidad disponible expresada en horas |
| `elementos_comprometidos` | Entero | Elementos comprometidos al inicio |
| `elementos_completados` | Entero | Elementos completados |
| `carry_over` | Entero | Elementos comprometidos no completados |
| `trabajo_no_planificado` | Entero | Elementos incorporados fuera del compromiso inicial |
| `throughput` | Entero | Elementos completados durante el Sprint |
| `cycle_time_mediana_dias` | Decimal | Mediana del Cycle Time en días |
| `lead_time_mediana_dias` | Decimal | Mediana del Lead Time en días |
| `wip_promedio` | Decimal | Promedio de elementos en curso |
| `impedimentos` | Entero | Cantidad de impedimentos registrados |
| `defectos` | Entero | Cantidad de defectos registrados |
| `retrabajo_elementos` | Entero | Elementos que requirieron retrabajo |
| `tipo_dato` | Texto | Clasificación del registro, DEMO |

### Equipos incluidos

| Equipo ID | Equipo |
|---|---|
| EQ-01 | Equipo A - Canales Digitales |
| EQ-02 | Equipo B - Integraciones |
| EQ-03 | Equipo C - Plataforma de Datos |
| EQ-04 | Equipo D - Ciberseguridad |

### Indicadores asociados

- Cumplimiento del Sprint Goal.
- Cumplimiento del compromiso.
- Carry-over.
- Trabajo no planificado.
- Throughput.
- Cycle Time.
- Lead Time.
- WIP.
- Impedimentos.
- Defectos y retrabajo.

### Consideraciones

- El dataset contiene cuatro equipos y doce Sprints por equipo.
- Los Sprints tienen una duración planificada de catorce días.
- El Sprint S12 corresponde al período del 2 al 15 de noviembre de 2026.
- Al corte del 7 de noviembre, S12 se encuentra en curso.
- El campo `sprint_goal_alcanzado` contiene valores de texto `Si` y `No`; no corresponde a un campo booleano.
- El valor `No` registrado para S12 no debe interpretarse como un Sprint Goal definitivamente incumplido, porque el Sprint todavía está en curso.
- S12 debe identificarse como período parcial y excluirse de comparaciones de Sprints finalizados y del cálculo definitivo de cumplimiento del Sprint Goal.
- La capacidad se expresa en horas y no debe confundirse con puntos de historia.
- Throughput y elementos completados deben mantener criterios de conteo consistentes.
- La información es ficticia y no representa resultados de equipos reales.

## 5. Dataset: deployments.csv

### Propósito

Registrar los despliegues de software realizados en los servicios de la muestra DEMO.

Permite analizar frecuencia de despliegue, fallos y tiempos de recuperación, además de disponer de una aproximación al Lead Time for Changes.

### Granularidad

Un registro representa un despliegue individual.

### Estructura

| Campo | Tipo | Descripción |
|---|---|---|
| `deployment_id` | Texto | Identificador único del despliegue |
| `fecha_despliegue` | Fecha | Fecha del despliegue |
| `servicio_id` | Texto | Identificador del servicio |
| `servicio` | Texto | Nombre del servicio |
| `entorno` | Texto | Entorno donde se realiza el despliegue |
| `tipo_despliegue` | Texto | Clasificación del despliegue |
| `lead_time_cambios_horas` | Decimal | Duración DEMO aproximada asociada al cambio |
| `estado_despliegue` | Texto | Estado del despliegue |
| `fallo_cambio` | Booleano | Indica si el despliegue fue clasificado como fallido |
| `incidente_id` | Texto | Identificador del incidente relacionado, cuando existe |
| `tiempo_recuperacion_minutos` | Entero | Tiempo de recuperación asociado al fallo |
| `origen_dato` | Texto | Fuente de origen |
| `tipo_dato` | Texto | Clasificación del registro, DEMO |

### Indicadores asociados

- Deployment Frequency.
- Lead Time for Changes, como aproximación DEMO.
- Change Failure Rate.
- Failed Deployment Recovery Time.

### Consideraciones

- El dataset contiene 48 registros de despliegues.
- Los registros corresponden a cuatro servicios y al período junio-septiembre de 2026.
- Todos los despliegues registrados corresponden al entorno de producción.
- Siete despliegues están clasificados como fallidos.
- Los siete despliegues fallidos tienen identificadores de incidentes asociados.
- El campo `fecha_despliegue` contiene únicamente la fecha, sin información de hora.
- El campo `lead_time_cambios_horas` no dispone de los timestamps de commit y despliegue necesarios para calcular estrictamente DORA Lead Time for Changes.
- Para una medición real se necesitará relacionar el timestamp del commit con el timestamp del despliegue en producción.
- La clasificación de un despliegue como fallido debe basarse en un criterio documentado y consistente.

### Criterio de cálculo de CFR en la muestra DEMO

CFR (%) = (Despliegues fallidos / Total de despliegues en producción) × 100

Con los datos disponibles:

- Despliegues totales: 48.
- Despliegues fallidos: 7.
- CFR = (7 / 48) × 100 = 14,58 %.

Este resultado corresponde exclusivamente a la muestra DEMO.

### Criterio de recuperación

En los despliegues fallidos, el tiempo de recuperación se calcula utilizando:

- Inicio del impacto: `fecha_deteccion` del incidente relacionado.
- Fin del impacto: `fecha_recuperacion` del incidente relacionado.

El campo `tiempo_recuperacion_minutos` debe coincidir entre el registro del despliegue y su incidente relacionado.

## 6. Dataset: cloud-monitoring.csv

### Propósito

Representar observaciones de monitoreo de servicios alojados en infraestructura cloud.

Permite analizar disponibilidad, latencia, errores, utilización de recursos, tráfico de red y costos.

### Granularidad

Un registro representa un servicio en una fecha de corte semanal.

### Estructura

| Campo | Tipo | Descripción |
|---|---|---|
| `fecha_corte` | Fecha | Fecha del corte de monitoreo |
| `servicio_id` | Texto | Identificador del servicio |
| `servicio` | Texto | Nombre del servicio |
| `proveedor_cloud` | Texto | Proveedor de infraestructura cloud |
| `entorno` | Texto | Entorno observado |
| `disponibilidad_pct` | Decimal | Disponibilidad en porcentaje |
| `latencia_p95_ms` | Decimal | Latencia p95 en milisegundos |
| `tasa_errores_pct` | Decimal | Porcentaje de errores |
| `cpu_promedio_pct` | Decimal | Utilización promedio de CPU |
| `memoria_promedio_pct` | Decimal | Utilización promedio de memoria |
| `almacenamiento_usado_pct` | Decimal | Porcentaje de almacenamiento utilizado |
| `trafico_entrada_gb` | Decimal | Volumen semanal de tráfico de entrada, en GB/semana |
| `trafico_salida_gb` | Decimal | Volumen semanal de tráfico de salida, en GB/semana |
| `costo_cloud_usd` | Decimal | Costo semanal de servicios Cloud, en USD/semana |
| `alertas_criticas` | Entero | Cantidad de alertas críticas |
| `origen_dato` | Texto | Fuente de origen |
| `tipo_dato` | Texto | Clasificación del registro, DEMO |

### Indicadores asociados

- Disponibilidad.
- Latencia p95.
- Tasa de errores.
- Utilización de CPU.
- Utilización de memoria.
- Uso de almacenamiento.
- Tráfico de entrada y salida.
- Costo cloud.
- Alertas críticas.

### Interpretación del período de medición

Para este conjunto de datos DEMO, cada registro representa un corte semanal de monitoreo.

- `trafico_entrada_gb`: volumen de tráfico entrante durante la semana, expresado en GB/semana.
- `trafico_salida_gb`: volumen de tráfico saliente durante la semana, expresado en GB/semana.
- `costo_cloud_usd`: costo de servicios Cloud correspondiente a esa semana, expresado en USD/semana.

**Criterio de interpretación:** los valores representan volúmenes y costos semanales, no acumulados. Esta convención se adopta para el modelo DEMO con el propósito de permitir el análisis de tendencias entre semanas. No constituye una validación de datos provenientes de una plataforma Cloud real.

Los valores numéricos originales se mantienen sin modificaciones.

### Consideraciones

- El dataset contiene veinte registros.
- Se consideran cuatro servicios y cinco cortes semanales de septiembre de 2026.
- Los datos representan observaciones agregadas por corte y no telemetría continua.
- Los campos de tráfico representan volúmenes DEMO expresados en GB/semana, según la convención definida para este modelo. Esta interpretación no ha sido contrastada con registros reales de la plataforma cloud.
- El costo cloud se expresa en USD/semana como convención del modelo DEMO. No representa facturación real ni permite verificar el costo efectivo del proveedor.
- No deben compararse costos o volúmenes de períodos de distinta duración sin normalización.
- Los registros no permiten reconstruir por sí solos el comportamiento minuto a minuto del servicio.

## 7. Dataset: incidents.csv

### Propósito

Registrar incidentes relacionados con los servicios de la muestra DEMO.

Permite analizar volumen, severidad, detección, recuperación, resolución y cumplimiento de SLA.

### Granularidad

Un registro representa un incidente individual.

### Estructura

| Campo | Tipo | Descripción |
|---|---|---|
| `incidente_id` | Texto | Identificador único del incidente |
| `fecha_apertura` | Fecha y hora | Fecha y hora de apertura |
| `fecha_deteccion` | Fecha y hora | Fecha y hora de detección del impacto |
| `fecha_recuperacion` | Fecha y hora | Fecha y hora de recuperación del servicio |
| `servicio_id` | Texto | Identificador del servicio afectado |
| `servicio` | Texto | Nombre del servicio afectado |
| `severidad` | Texto | Nivel de severidad |
| `categoria` | Texto | Clasificación del incidente |
| `origen` | Texto | Origen del incidente |
| `relacion_despliegue` | Texto | Indica si existe relación con un despliegue |
| `deployment_id` | Texto | Identificador del despliegue relacionado, cuando existe |
| `tiempo_resolucion_minutos` | Entero | Tiempo desde apertura hasta recuperación |
| `tiempo_recuperacion_minutos` | Entero | Tiempo desde detección del impacto hasta recuperación |
| `sla_objetivo_minutos` | Entero | Tiempo objetivo de resolución según SLA |
| `sla_cumplido` | Booleano | Indica si se cumplió el objetivo SLA |
| `causa_raiz` | Texto | Causa raíz registrada |
| `estado` | Texto | Estado del incidente |
| `origen_dato` | Texto | Fuente de origen |
| `tipo_dato` | Texto | Clasificación del registro, DEMO |

### Indicadores asociados

- Cantidad de incidentes.
- Incidentes por severidad.
- Incidentes por servicio.
- MTTR operacional.
- Cumplimiento de SLA.
- Failed Deployment Recovery Time, para incidentes asociados a despliegues fallidos.

### Consideraciones

- El dataset contiene quince incidentes.
- Los registros corresponden al período junio-septiembre de 2026.
- Los quince incidentes se encuentran resueltos.
- Los primeros siete incidentes tienen relación con despliegues fallidos y contienen un `deployment_id` asociado.
- Los ocho restantes no están vinculados a esos despliegues fallidos.
- No existen incidentes abiertos en esta muestra, por lo que no es posible presentar una fotografía de incidentes pendientes al corte.

### Criterios de cálculo de tiempos

**Tiempo de resolución operacional:**

Tiempo de resolución = `fecha_recuperacion` − `fecha_apertura`

El resultado se representa en `tiempo_resolucion_minutos`.

**Tiempo de recuperación utilizado como aproximación DORA:**

Tiempo de recuperación = `fecha_recuperacion` − `fecha_deteccion`

El resultado se representa en `tiempo_recuperacion_minutos`.

En esta muestra DEMO, `fecha_deteccion` se utiliza como aproximación al inicio del impacto.

### Criterio de cumplimiento de SLA

El cumplimiento se determina comparando el tiempo de resolución con el objetivo SLA:

SLA cumplido = Tiempo de resolución ≤ Objetivo SLA

En los registros DEMO, el tiempo utilizado corresponde a `tiempo_resolucion_minutos`.

## 8. Relaciones entre datasets

El modelo utiliza identificadores para mantener la trazabilidad entre servicios, despliegues e incidentes.

### Relaciones principales

| Dataset origen | Campo | Dataset relacionado | Campo |
|---|---|---|---|
| `deployments.csv` | `incidente_id` | `incidents.csv` | `incidente_id` |
| `incidents.csv` | `deployment_id` | `deployments.csv` | `deployment_id` |
| `cloud-monitoring.csv` | `servicio_id` | `deployments.csv` | `servicio_id` |
| `incidents.csv` | `servicio_id` | `deployments.csv` | `servicio_id` |

### Reglas de relación

- `deployment_id` identifica de forma única cada despliegue.
- `incidente_id` identifica de forma única cada incidente.
- Un despliegue puede no tener incidente asociado.
- Un incidente puede no estar relacionado con un despliegue.
- En la muestra DEMO, los siete despliegues fallidos están relacionados con siete incidentes.
- La relación debe verificarse mediante los identificadores, no solamente por coincidencia de fechas o nombres.
- `servicio_id` permite agrupar información de despliegues, monitoreo e incidentes por servicio.
- Los datasets ejecutivos y ágiles tienen granularidades diferentes y no deben unirse directamente sin una dimensión de iniciativa, proyecto o equipo que permita establecer una relación válida.

## 9. Reglas de calidad y validación

Antes de utilizar los datasets para generar indicadores o dashboards se deben verificar las siguientes reglas.

### 9.1 Integridad

- Los identificadores únicos no deben estar duplicados.
- Los identificadores relacionados deben existir en el dataset correspondiente.
- Las fechas deben respetar el orden cronológico esperado.
- Los campos obligatorios no deben estar vacíos.

### 9.2 Consistencia

- Los porcentajes deben encontrarse dentro de rangos válidos.
- Los tiempos deben ser iguales o mayores que cero.
- Los valores de despliegues fallidos deben ser coherentes con el estado registrado.
- Los incidentes asociados a despliegues deben mantener consistencia entre ambos archivos.
- Los cálculos de tiempo deben coincidir con las fechas de origen.

### 9.3 Reglas temporales

- Los períodos deben identificarse claramente.
- Los cortes parciales deben diferenciarse de los períodos completos.
- Las comparaciones deben realizarse entre períodos equivalentes.
- Los datos históricos deben conservar su fecha de corte.

### 9.4 Calidad y trazabilidad

Cada dataset debe permitir identificar:

- Fuente de información.
- Fecha de corte.
- Período representado.
- Tipo de dato.
- Regla de cálculo.
- Limitaciones conocidas.

## 10. Limitaciones conocidas de la muestra DEMO

| Dataset | Limitación | Implicación |
|---|---|---|
| Executive KPIs | Último corte parcial | No comparar directamente con meses completos |
| Agile Delivery | Sprint S12 en curso | Excluirlo de comparaciones de Sprints finalizados |
| Deployments | Sin timestamp de commit | Lead Time for Changes es una aproximación |
| Deployments | Fecha de despliegue sin hora | No permite análisis de precisión horaria |
| Cloud Monitoring | Cinco cortes semanales | No representa telemetría continua |
| Cloud Monitoring | Períodos de costo y tráfico definidos como convenciones DEMO | Interpretar los valores como GB/semana y USD/semana, sin considerarlos mediciones o facturación real |
| Incidents | Todos los incidentes resueltos | No permite analizar incidentes abiertos |
| Incidents | Inicio del impacto aproximado por detección | Recovery Time DORA es una aproximación DEMO |

## 11. Relación con los productos del portafolio

| Producto | Datasets principales | Propósito |
|---|---|---|
| 01 - Dashboard Ejecutivo de Gestión TI | `executive-kpis.csv` | Consolidar desempeño, riesgos y cumplimiento |
| 02 - Gestión de Proyectos y Entrega Ágil | `agile-delivery.csv` | Analizar planificación, flujo y evolución de equipos |
| 03 - Entrega Técnica y Operaciones TI | `deployments.csv`, `cloud-monitoring.csv`, `incidents.csv` | Analizar entrega técnica, salud de servicios y operación |

## 12. Principio de gobierno de datos

Los indicadores deben ser trazables hasta su fuente y contar con definiciones consistentes.

La calidad de un dashboard depende de la calidad, integridad y contexto de los datos que lo alimentan.

Por ello, el portafolio adopta el siguiente principio:

**Fuente de datos → Validación → Modelo de información → Indicadores → Visualización → Análisis → Decisión.**
