# Executive IT Management

## 1. Objetivo

Proporcionar una visión ejecutiva del desempeño del portafolio TI, integrando información de gestión de proyectos, entrega tecnológica y operación de servicios.

El objetivo es facilitar la supervisión de resultados, identificar desviaciones relevantes y apoyar la toma de decisiones de Subgerencia y Dirección.

Este producto consolida indicadores de distintas dimensiones de gestión para entregar una lectura transversal del estado del portafolio.

## 2. Público objetivo

- Subgerencia de Tecnología.
- Gerencia de Tecnología.
- Dirección de Tecnología.
- Responsables de portafolio y gestión de proyectos.
- Stakeholders ejecutivos que requieren visibilidad del desempeño TI.

## 3. Alcance de gestión

El modelo considera cinco dimensiones:

| Dimensión | Enfoque ejecutivo |
|---|---|
| Gestión del portafolio | Cumplimiento de hitos, avance y predictibilidad. |
| Entrega de valor | Cumplimiento de objetivos y compromisos de entrega. |
| Continuidad operacional | Incidentes críticos y recuperación de servicios. |
| Calidad de los cambios | Fallas asociadas a despliegues en producción. |
| Gestión de costos cloud | Evolución y consumo de recursos cloud. |

El producto integra indicadores ejecutivos provenientes de los productos de gestión y operación del portafolio.

## 4. Preguntas de gestión

La información presentada debe permitir responder preguntas como:

- ¿El portafolio está cumpliendo los compromisos y plazos establecidos?
- ¿Qué iniciativas presentan desviaciones relevantes?
- ¿Existen riesgos críticos que requieren intervención ejecutiva?
- ¿Se están produciendo incidentes críticos que puedan afectar la continuidad?
- ¿Qué proporción de los despliegues en producción presenta fallas?
- ¿Cómo evoluciona el consumo de infraestructura cloud?
- ¿Qué decisiones o acciones requieren atención de la dirección?

## 5. Indicadores ejecutivos

### 5.1 Predictibilidad del portafolio

Mide el cumplimiento oportuno de los hitos planificados durante un período.

**Fórmula:**

Cumplimiento de hitos (%) = (Hitos cumplidos a tiempo / Hitos planificados) × 100

**Fuente:** `executive-kpis.csv`

**Interpretación ejecutiva:** permite evaluar la capacidad del portafolio para cumplir los compromisos establecidos y detectar desviaciones en la planificación.

### 5.2 Desviación del avance

Compara el avance real con el avance planificado de las iniciativas.

**Fórmula:**

Desviación del avance (pp) = Avance real (%) - Avance planificado (%)

**Fuente:** `executive-kpis.csv`

**Interpretación ejecutiva:** permite identificar iniciativas adelantadas o retrasadas respecto de su planificación.

### 5.3 Riesgos críticos abiertos

Representa la cantidad de riesgos clasificados como críticos que permanecen abiertos en el período de medición.

**Fórmula:**

Riesgos críticos abiertos = Cantidad de riesgos críticos abiertos

**Fuente:** `executive-kpis.csv`

**Interpretación ejecutiva:** permite identificar situaciones que requieren seguimiento, mitigación o escalamiento.

### 5.4 Incidentes críticos

Representa la cantidad de incidentes registrados con severidad Crítica.

**Fórmula:**

Incidentes críticos = Cantidad de incidentes con severidad Crítica

**Fuente:** `incidents.csv`

**Interpretación ejecutiva:** permite conocer eventos de alta severidad que pueden afectar la continuidad operacional y requerir intervención.

### 5.5 Change Failure Rate

Mide la proporción de despliegues en producción que presentan fallas.

**Fórmula:**

Change Failure Rate (%) = (Despliegues fallidos / Total de despliegues en producción) × 100

**Fuente:** `deployments.csv`

**Interpretación ejecutiva:** permite evaluar la calidad y estabilidad de los cambios liberados en producción.

### 5.6 Consumo cloud

Representa el costo acumulado registrado para los servicios cloud considerados en el período.

**Fórmula:**

Costo Cloud = Suma de costos registrados

**Fuente:** `cloud-monitoring.csv`

**Interpretación ejecutiva:** permite observar el consumo de infraestructura cloud y apoyar el seguimiento presupuestario.

Los valores del dataset son demostrativos y no representan facturación real.

### 5.7 Disponibilidad de servicios

La disponibilidad representa el porcentaje de tiempo durante el cual un servicio permanece operativo respecto del período total observado.

**Fórmula:**

Disponibilidad (%) = (Tiempo disponible / Tiempo total del período) × 100

**Fuente requerida:** registros continuos de disponibilidad por servicio y período.

**Interpretación ejecutiva:** permite evaluar la continuidad de los servicios relevantes para el negocio.

La disponibilidad no se calcula a partir de observaciones semanales aisladas. Para obtener un resultado válido se requiere información temporal suficiente y trazable.

## 6. Fuentes de información

El producto utiliza los siguientes datasets de referencia:

| Dataset | Información utilizada |
|---|---|
| `executive-kpis.csv` | Indicadores de gestión ejecutiva, avance, hitos y riesgos. |
| `agile-delivery.csv` | Información de cumplimiento y desempeño de entrega ágil. |
| `deployments.csv` | Despliegues en producción y resultados de cambios. |
| `incidents.csv` | Incidentes, severidad, resolución y cumplimiento de SLA. |
| `cloud-monitoring.csv` | Observaciones de monitoreo y costos cloud demostrativos. |

Los indicadores deben mantener trazabilidad hacia su fuente y período de medición.

## 7. Criterios de interpretación ejecutiva

La lectura de los indicadores debe considerar:

- El período de medición y la fecha de corte.
- La evolución respecto de períodos anteriores.
- Las desviaciones respecto de compromisos y objetivos.
- La criticidad y el impacto potencial sobre el negocio.
- La confiabilidad y cobertura de los datos disponibles.
- Las dependencias entre iniciativas, servicios y equipos.

Los indicadores deben interpretarse de manera conjunta. Un resultado aislado no representa necesariamente el desempeño integral del portafolio.

## 8. Gobierno y decisiones

La información ejecutiva debe facilitar decisiones relacionadas con:

- Priorización de iniciativas.
- Reasignación de recursos.
- Gestión y escalamiento de riesgos.
- Acciones correctivas sobre desviaciones.
- Continuidad operacional.
- Calidad de las liberaciones.
- Seguimiento del consumo cloud.

Cada desviación relevante debe contar con un responsable, una acción de seguimiento y una fecha de revisión.

## 9. Consideraciones sobre los datos

Los datasets de este repositorio contienen información DEMO para representar escenarios de gestión TI.

Por lo tanto:

- Los resultados no corresponden a indicadores reales de una organización.
- Los valores deben interpretarse como ejemplos de aplicación del modelo.
- Los períodos parciales deben identificarse antes de realizar comparaciones.
- No deben calcularse indicadores cuando la fuente no dispone de los campos o la granularidad temporal necesarios.
- Las métricas ejecutivas deben conservar trazabilidad hacia los datos de origen.
- Las diferencias de definición entre indicadores deben mantenerse explícitas.

## 10. Resultado esperado

El producto entrega una perspectiva consolidada del desempeño del portafolio TI, conectando la gestión ejecutiva con la entrega tecnológica y la operación de servicios.

Su propósito es transformar datos operacionales y de gestión en información útil para la supervisión, el control y la toma de decisiones ejecutivas.
