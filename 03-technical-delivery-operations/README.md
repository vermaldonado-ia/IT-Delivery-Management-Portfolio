# DevOps & Cloud Operations

## 1. Objetivo

Establecer un modelo de seguimiento de la entrega técnica y la operación de servicios TI, integrando indicadores de despliegue, estabilidad, recuperación de fallas, gestión de incidentes y monitoreo de infraestructura cloud.

El producto busca proporcionar visibilidad sobre la confiabilidad de los cambios liberados en producción y la capacidad de respuesta ante eventos operacionales.

## 2. Público objetivo

- DevOps Engineers.
- Líderes técnicos.
- Delivery Managers.
- Responsables de operaciones TI.
- Responsables de infraestructura cloud.
- Equipos de desarrollo y soporte.
- Responsables de continuidad operacional.

## 3. Alcance de gestión

El modelo considera cinco dimensiones:

| Dimensión | Enfoque |
|---|---|
| Frecuencia de despliegue | Seguimiento de liberaciones exitosas en producción. |
| Estabilidad de cambios | Identificación de despliegues fallidos. |
| Recuperación técnica | Tiempo requerido para recuperar despliegues fallidos. |
| Gestión de incidentes | Resolución, severidad y cumplimiento de SLA. |
| Monitoreo cloud | Observación de servicios, recursos y costos registrados. |

## 4. Indicadores de entrega técnica y operaciones

### 4.1 Deployment Frequency

Mide la cantidad de despliegues exitosos realizados en producción durante un período.

**Fórmula:**

Deployment Frequency = Cantidad de despliegues exitosos en producción

**Fuente:** `deployments.csv`

**Interpretación:** permite observar la frecuencia de liberación de cambios y analizar la capacidad de entrega técnica.

Para este indicador se consideran únicamente los despliegues exitosos en producción.

### 4.2 Lead Time for Changes

Representa el tiempo transcurrido desde el inicio de un cambio hasta su despliegue en producción.

**Fórmula:**

Lead Time for Changes = Fecha de despliegue - Fecha de inicio del cambio

**Fuente:** `deployments.csv`

**Interpretación:** permite analizar cuánto tiempo tarda un cambio en llegar a producción.

El dataset contiene el campo `lead_time_cambios_horas`, pero no dispone de todos los eventos temporales necesarios para reconstruir el proceso completo desde el commit hasta el despliegue.

Por esta razón, el valor disponible debe interpretarse como una aproximación y no como una medición end-to-end basada en eventos fuente.

### 4.3 Change Failure Rate

Mide la proporción de despliegues en producción que presentan fallas.

**Fórmula:**

Change Failure Rate (%) = (Despliegues fallidos / Total de despliegues en producción) × 100

**Fuente:** `deployments.csv`

**Resultado del dataset DEMO:**

Change Failure Rate = (7 / 48) × 100 = 14,58 %

**Interpretación:** permite evaluar la estabilidad de los cambios liberados en producción.

### 4.4 Failed Deployment Recovery Time

Mide el tiempo requerido para recuperar un despliegue fallido.

**Fórmula:**

Failed Deployment Recovery Time = Suma de tiempos de recuperación de despliegues fallidos / Cantidad de despliegues fallidos

**Fuente:** `deployments.csv`

**Resultado del dataset DEMO:**

Tiempo promedio de recuperación = 625 / 7 = 89,29 minutos

**Interpretación:** permite evaluar la capacidad de respuesta técnica ante fallas asociadas a despliegues.

Este indicador se refiere específicamente a la recuperación de despliegues fallidos y no debe confundirse con el MTTR operacional de incidentes.

### 4.5 MTTR operacional

Mide el tiempo promedio transcurrido desde la apertura de un incidente hasta su resolución o recuperación operacional, según la definición del dataset.

**Fórmula:**

MTTR operacional = Suma de tiempos de resolución / Cantidad de incidentes resueltos

**Fuente:** `incidents.csv`

**Resultado del dataset DEMO:**

MTTR operacional = 1.736 / 15 = 115,73 minutos

**Interpretación:** permite evaluar el tiempo promedio requerido para resolver incidentes y recuperar la operación.

Este indicador utiliza `tiempo_resolucion_minutos`, por lo que no representa necesariamente el tiempo desde la detección hasta la recuperación.

### 4.6 Incident SLA Compliance

Mide la proporción de incidentes elegibles que fueron resueltos dentro del SLA establecido.

**Fórmula:**

Incident SLA Compliance (%) = (Incidentes que cumplen el SLA / Total de incidentes elegibles) × 100

**Fuente:** `incidents.csv`

**Resultado del dataset DEMO:**

Incident SLA Compliance = (12 / 15) × 100 = 80 %

**Interpretación:** permite evaluar el cumplimiento de los compromisos de atención y resolución de incidentes.

### 4.7 Incidentes críticos

Representa la cantidad de incidentes registrados con severidad Crítica.

**Fórmula:**

Incidentes críticos = Cantidad de incidentes con severidad Crítica

**Fuente:** `incidents.csv`

**Resultado del dataset DEMO:**

Incidentes críticos = 1

**Interpretación:** permite identificar eventos de máxima severidad que requieren atención prioritaria y seguimiento.

## 5. Monitoreo Cloud

El monitoreo cloud permite observar el comportamiento de los servicios y recursos de infraestructura mediante registros de observación.

### 5.1 Disponibilidad Cloud

Representa el porcentaje de tiempo durante el cual un servicio permanece disponible respecto del período total observado.

**Fórmula:**

Disponibilidad Cloud (%) = (Tiempo disponible / Tiempo total observado) × 100

**Fuente:** `cloud-monitoring.csv`

**Restricción:** el dataset contiene observaciones semanales aisladas y no registros continuos de disponibilidad. Por lo tanto, no permite calcular una disponibilidad temporal real.

### 5.2 Utilización del recurso

Representa la proporción de capacidad utilizada respecto de la capacidad total disponible.

**Fórmula:**

Utilización del recurso (%) = (Recurso utilizado / Capacidad total del recurso) × 100

**Fuente:** `cloud-monitoring.csv`

**Interpretación:** permite analizar el nivel de utilización de los recursos monitoreados, siempre que los campos de capacidad y utilización sean compatibles y estén disponibles.

### 5.3 Costo Cloud

Representa la suma de los costos registrados para los servicios cloud considerados.

**Fórmula:**

Costo Cloud = Suma de costos registrados

**Fuente:** `cloud-monitoring.csv`

**Interpretación:** permite observar la evolución del costo registrado y apoyar el análisis de consumo de infraestructura.

Los valores del dataset son DEMO y no corresponden a facturación real de un proveedor cloud.

## 6. Fuentes de información

| Dataset | Información |
|---|---|
| `deployments.csv` | Despliegues en producción, resultados, lead time y recuperación de fallas. |
| `incidents.csv` | Incidentes, severidad, tiempos de resolución y cumplimiento de SLA. |
| `cloud-monitoring.csv` | Observaciones de servicios, recursos y costos cloud. |

Los indicadores deben mantener trazabilidad hacia los registros de origen y sus períodos de medición.

## 7. Criterios de interpretación

Para interpretar los indicadores se deben considerar:

- Ambiente en el que se realizó el despliegue.
- Resultado del despliegue.
- Período de medición.
- Severidad de los incidentes.
- Diferencia entre detección, recuperación y resolución.
- Relación entre despliegues fallidos e incidentes asociados.
- Granularidad y continuidad de los datos de monitoreo.
- Naturaleza DEMO de los valores de infraestructura y costos.

Los indicadores deben analizarse de manera conjunta para evitar conclusiones basadas en una única métrica.

## 8. Gobierno y mejora continua

El seguimiento de los indicadores debe facilitar acciones relacionadas con:

- Mejora de los procesos de despliegue.
- Reducción de fallas en producción.
- Análisis de causas raíz.
- Optimización de los tiempos de recuperación.
- Cumplimiento de los SLA.
- Fortalecimiento del monitoreo.
- Gestión de capacidad y costos cloud.
- Coordinación entre desarrollo y operaciones.

Las acciones correctivas deben contar con responsables, prioridades y seguimiento.

## 9. Consideraciones sobre los datos

Los datasets de este repositorio contienen información DEMO para representar escenarios de operación TI.

Se deben considerar las siguientes restricciones:

- Deployment Frequency considera únicamente despliegues exitosos en producción.
- Change Failure Rate utiliza el total de despliegues en producción como denominador.
- Lead Time for Changes es una aproximación cuando no existen eventos temporales completos.
- Failed Deployment Recovery Time mide la recuperación de despliegues fallidos.
- MTTR operacional utiliza los tiempos de resolución registrados en incidentes.
- Ambos indicadores de recuperación tienen definiciones y puntos de inicio diferentes.
- Las observaciones semanales de Cloud Monitoring no permiten calcular disponibilidad continua.
- Los costos cloud son demostrativos y no representan facturación real.
- No deben calcularse indicadores cuando faltan campos o granularidad suficientes.

## 10. Resultado esperado

El producto proporciona una visión estructurada de la confiabilidad de los despliegues, la recuperación ante fallas y el comportamiento de los servicios cloud.

Su propósito es conectar la entrega técnica con la operación de servicios, facilitando el seguimiento de estabilidad, continuidad y eficiencia operacional.
