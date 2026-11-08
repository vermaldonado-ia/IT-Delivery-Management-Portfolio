# Demo Data – IT Delivery Management Portfolio

## 1. Objetivo

Esta carpeta contiene los datasets DEMO utilizados para demostrar el modelo de medición y seguimiento del portafolio de gestión TI.

Los datos permiten representar escenarios de gestión ejecutiva, entrega ágil, despliegues tecnológicos, monitoreo cloud y gestión de incidentes.

Su propósito es proporcionar fuentes estructuradas para analizar indicadores, construir visualizaciones y demostrar la trazabilidad entre la gestión de proyectos, la entrega técnica y la operación de servicios.

**Importante:** todos los registros son ficticios y tienen fines demostrativos. No representan resultados operacionales reales de una organización.

## 2. Inventario de datasets

El repositorio contiene cinco archivos CSV:

| Dataset | Registros | Dominio | Propósito |
|---|---:|---|---|
| `executive-kpis.csv` | 36 | Gestión ejecutiva | Seguimiento de iniciativas, avance, hitos, riesgos e indicadores ejecutivos. |
| `agile-delivery.csv` | 48 | Entrega ágil | Seguimiento de equipos, Sprints, objetivos y compromisos de entrega. |
| `deployments.csv` | 48 | Entrega técnica | Registro de despliegues en producción, resultados y recuperación de fallas. |
| `cloud-monitoring.csv` | 20 | Monitoreo cloud | Observaciones de servicios, recursos y costos cloud. |
| `incidents.csv` | 15 | Operaciones TI | Registro de incidentes, severidad, tiempos de resolución y cumplimiento de SLA. |

**Total: 167 registros distribuidos en cinco datasets.**

## 3. Descripción de los datasets

### 3.1 executive-kpis.csv

**Dominio:** Gestión ejecutiva TI.

**Contenido:**

Contiene información de seis iniciativas y seis fechas de corte, utilizada para representar el seguimiento ejecutivo del portafolio.

Permite analizar:

- Cumplimiento de hitos.
- Avance real y planificado.
- Desviación del avance.
- Riesgos críticos abiertos.
- Cumplimiento de SLA ejecutivo.

**Uso principal:**

Construcción de indicadores ejecutivos y seguimiento del desempeño de las iniciativas.

**Consideraciones:**

- El registro del 7 de noviembre de 2026 corresponde a un corte parcial.
- Los indicadores deben interpretarse considerando la fecha de corte.
- La disponibilidad ejecutiva no debe derivarse directamente de Cloud Monitoring sin un mapeo completo entre iniciativas, servicios y períodos compatibles.

### 3.2 agile-delivery.csv

**Dominio:** Gestión de entrega ágil.

**Contenido:**

Contiene 48 registros correspondientes a cuatro equipos y doce Sprints por equipo.

Permite analizar:

- Cumplimiento de objetivos de Sprint.
- Compromisos de entrega.
- Elementos completados y pendientes.
- Carry-over.
- Comportamiento de la entrega por equipo y Sprint.

**Uso principal:**

Evaluación de la predictibilidad y desempeño de los equipos ágiles.

**Consideraciones:**

- El Sprint S12 se encuentra en curso al corte del 7 de noviembre de 2026.
- El Sprint en curso tiene el objetivo pendiente y debe excluirse de los cálculos de cumplimiento de Sprints cerrados.
- Los 44 Sprints cerrados registran 33 objetivos alcanzados y 11 no alcanzados.
- El Sprint Goal Achievement del conjunto de Sprints cerrados es 75%.
- El cumplimiento del objetivo de Sprint no equivale al porcentaje de tareas completadas.
- Sprint Commitment Reliability requiere interpretar correctamente los compromisos iniciales y los elementos pendientes.

### 3.3 deployments.csv

**Dominio:** Entrega técnica y despliegues.

**Contenido:**

Contiene 48 registros de despliegues realizados en producción.

Permite analizar:

- Frecuencia de despliegues exitosos.
- Despliegues fallidos.
- Lead Time for Changes.
- Change Failure Rate.
- Tiempo de recuperación de despliegues fallidos.

**Uso principal:**

Evaluación de la frecuencia de entrega y estabilidad de los cambios liberados en producción.

**Resultados del dataset DEMO:**

| Indicador | Resultado |
|---|---:|
| Total de despliegues | 48 |
| Despliegues exitosos | 41 |
| Despliegues fallidos | 7 |
| Change Failure Rate | 14,58 % |
| Tiempo promedio de recuperación de despliegues fallidos | 89,29 minutos |

**Consideraciones:**

- Deployment Frequency considera únicamente despliegues exitosos en producción.
- Change Failure Rate utiliza el total de despliegues en producción como denominador.
- El campo `lead_time_cambios_horas` representa una aproximación porque no están disponibles todos los eventos temporales necesarios para reconstruir el ciclo completo desde el commit hasta el despliegue.
- El tiempo promedio de recuperación utiliza los siete despliegues fallidos.

### 3.4 cloud-monitoring.csv

**Dominio:** Monitoreo e infraestructura cloud.

**Contenido:**

Contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales durante septiembre de 2026.

Los registros representan observaciones de servicios alojados en infraestructura cloud.

Permite analizar:

- Observaciones de monitoreo.
- Utilización de recursos.
- Costos cloud registrados.
- Comportamiento de los servicios en los cortes disponibles.

**Uso principal:**

Demostrar el seguimiento de infraestructura cloud y la integración de información operacional en el modelo de gestión TI.

**Consideraciones:**

- Los registros corresponden a observaciones semanales, no a telemetría continua ni monitoreo en tiempo real.
- Los campos de tráfico representan volúmenes DEMO expresados en GB/semana, según la convención definida para este modelo. Esta interpretación no ha sido contrastada con registros reales de la plataforma cloud.
- El costo cloud se expresa en USD/semana como convención del modelo DEMO. No representa facturación real ni permite verificar el costo efectivo del proveedor.
- Las observaciones disponibles no permiten calcular disponibilidad temporal continua.
- No existe un mapeo completo entre las iniciativas ejecutivas y los servicios monitoreados.

### 3.5 incidents.csv

**Dominio:** Gestión de incidentes y operaciones TI.

**Contenido:**

Contiene 15 incidentes resueltos.

Permite analizar:

- Severidad de incidentes.
- Tiempos de resolución.
- Tiempos de recuperación.
- Cumplimiento de SLA.
- Incidentes críticos.

**Uso principal:**

Evaluación de la capacidad de respuesta operacional y seguimiento de la gestión de incidentes.

**Resultados del dataset DEMO:**

| Indicador | Resultado |
|---|---:|
| Total de incidentes resueltos | 15 |
| Incidentes que cumplen SLA | 12 |
| Incident SLA Compliance | 80 % |
| Incidentes críticos | 1 |
| MTTR operacional | 115,73 minutos |

**Consideraciones:**

- `tiempo_resolucion_minutos` representa el tiempo desde la apertura hasta la resolución del incidente.
- `tiempo_recuperacion_minutos` representa el tiempo desde la detección hasta la recuperación.
- Ambos campos tienen puntos de inicio diferentes y no deben utilizarse como si midieran el mismo indicador.
- El MTTR operacional se calcula utilizando los tiempos de resolución de los 15 incidentes.

## 4. Relaciones entre datasets

Los datasets permiten analizar relaciones entre la entrega técnica y la operación de servicios.

### 4.1 Despliegues e incidentes

Los siete despliegues fallidos tienen incidentes asociados.

| Despliegue | Incidente | Tiempo de recuperación (min) |
|---|---|---:|
| DEP-003 | INC-001 | 95 |
| DEP-008 | INC-002 | 140 |
| DEP-014 | INC-003 | 110 |
| DEP-020 | INC-004 | 85 |
| DEP-027 | INC-005 | 75 |
| DEP-034 | INC-006 | 65 |
| DEP-043 | INC-007 | 55 |

Esta relación permite analizar el comportamiento de los despliegues fallidos y su recuperación operacional.

El promedio de recuperación de estos siete despliegues es de 89,29 minutos.

### 4.2 Gestión ejecutiva y monitoreo cloud

Los indicadores ejecutivos y las observaciones de monitoreo cloud representan dimensiones complementarias de gestión.

Sin embargo, los datasets no disponen de un mapeo completo entre iniciativas ejecutivas y servicios monitoreados.

Por lo tanto, no se debe establecer una relación directa de disponibilidad entre ambos datasets sin incorporar previamente las correspondencias necesarias.

## 5. Resumen de validación

Los cinco datasets fueron revisados considerando cantidad de registros, consistencia de indicadores, períodos de medición y restricciones de interpretación.

| Dataset | Registros | Validación |
|---|---:|---|
| `executive-kpis.csv` | 36 | Seis iniciativas y seis fechas de corte. |
| `agile-delivery.csv` | 48 | Cuatro equipos y doce Sprints por equipo. |
| `deployments.csv` | 48 | 41 despliegues exitosos y 7 fallidos. |
| `cloud-monitoring.csv` | 20 | Cuatro servicios y cinco cortes semanales. |
| `incidents.csv` | 15 | Quince incidentes resueltos. |

**Total validado: 167 registros.**

## 6. Criterios de uso de los datos

Para utilizar correctamente estos datasets se deben respetar los siguientes criterios:

1. Mantener la trazabilidad entre los indicadores y sus fuentes.
2. Considerar las fechas de corte y los períodos de medición.
3. Excluir registros incompletos o pendientes cuando el indicador requiera resultados definitivos.
4. No asumir relaciones entre datasets que no estén respaldadas por identificadores o correspondencias verificables.
5. Diferenciar los tiempos de recuperación de despliegues y los tiempos de resolución de incidentes.
6. No calcular indicadores cuando los campos o la granularidad disponibles sean insuficientes.
7. Identificar siempre los datos como DEMO.

## 7. Limitaciones conocidas

Los datasets tienen un propósito demostrativo y presentan restricciones que deben mantenerse explícitas:

- No representan información real de una organización.
- No constituyen una integración automática con Jira, GitHub, Jenkins, SonarQube, AWS u otras plataformas.
- No contienen telemetría continua de infraestructura cloud.
- Los costos cloud no corresponden a facturación real.
- No existe trazabilidad completa entre iniciativas ejecutivas y servicios cloud.
- Algunos indicadores requieren información adicional para obtener una medición operacional completa.

Estas restricciones forman parte del alcance del portafolio y permiten demostrar un uso responsable de los datos y de los indicadores de gestión.

## 8. Resultado esperado

Los datasets proporcionan una base demostrativa para construir un modelo integrado de IT Delivery Management.

Su utilización permite demostrar cómo la información de gestión ejecutiva, entrega ágil, despliegues, monitoreo cloud e incidentes puede transformarse en indicadores para apoyar la supervisión, el control y la toma de decisiones.

El valor del modelo no depende únicamente de visualizar métricas, sino también de mantener definiciones consistentes, trazabilidad de los datos y criterios claros de interpretación.
