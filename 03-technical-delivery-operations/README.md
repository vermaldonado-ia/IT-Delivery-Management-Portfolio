# 03. Entrega Técnica y Operaciones TI

## Desempeño tecnológico, confiabilidad y continuidad operacional

### 1. Objetivo

Establecer un modelo de seguimiento de la entrega técnica y las operaciones TI que permita observar la frecuencia y estabilidad de los despliegues, la salud de los servicios tecnológicos y la capacidad de respuesta ante incidentes.

El enfoque integra indicadores técnicos y operacionales para facilitar el control, identificar riesgos y apoyar decisiones de gestión.

### 2. Audiencia

- Delivery Managers.
- Líderes de tecnología.
- Equipos DevOps y SRE.
- Infraestructura y Cloud.
- Operaciones TI.
- Gestión de servicios tecnológicos.

### 3. Componentes de seguimiento

#### 3.1. Métricas DORA

Permiten evaluar el desempeño de la entrega de software desde la perspectiva de velocidad y estabilidad.

Indicadores:
- Deployment Frequency: frecuencia de despliegues.
- Lead Time for Changes: tiempo desde que un cambio se confirma en el repositorio hasta que llega a producción.
- Change Failure Rate: porcentaje de despliegues que generan fallas o requieren corrección.
- Failed Deployment Recovery Time: tiempo necesario para recuperar el servicio después de un despliegue fallido.

Estas métricas deben interpretarse en conjunto y considerando el contexto de cada servicio y equipo.

#### 3.2. Monitoreo Cloud y Observabilidad

Seguimiento de la salud y comportamiento de aplicaciones e infraestructura tecnológica.

Indicadores:
- Disponibilidad de servicios.
- Latencia, incluyendo percentil 95 (p95).
- Tasa de errores.
- Uso de CPU y memoria.
- Capacidad de almacenamiento.
- Tráfico y comportamiento de red.
- Alertas y eventos relevantes.
- Costos de infraestructura Cloud.

Las herramientas pueden incluir AWS CloudWatch, Azure Monitor, Datadog, Grafana o Prometheus, según la plataforma utilizada.

#### 3.3. Operaciones y Gestión de Servicios TI

Permite evaluar la continuidad y capacidad de respuesta operacional.

Indicadores:
- Cantidad de incidentes.
- Clasificación por severidad.
- MTTR: tiempo medio de resolución.
- Disponibilidad del servicio.
- Cumplimiento de SLA.
- Cumplimiento de SLO.
- Incidentes recurrentes.

#### 3.4. Riesgo Técnico y Confiabilidad

Seguimiento de condiciones que pueden comprometer la continuidad o estabilidad de los servicios.

Considera:
- Fallas recurrentes.
- Despliegues con incidentes asociados, cuando exista trazabilidad.
- Componentes críticos.
- Dependencias tecnológicas.
- Capacidad y utilización de recursos.
- Riesgos de continuidad operacional.

### 4. Enfoque de gestión

**Línea base → Evolución → Resultado → Acción correctiva o preventiva**

El seguimiento permite identificar tendencias, evaluar la estabilidad de los servicios y priorizar acciones según el impacto y nivel de riesgo.

### 5. Criterios de interpretación

- Las métricas DORA miden el desempeño de la entrega de software, no el valor de negocio.
- El monitoreo Cloud permite observar el comportamiento de infraestructura y aplicaciones.
- Los incidentes operacionales deben analizarse según su impacto y causa.
- No se debe atribuir un incidente a un despliegue sin evidencia que respalde esa relación.
- SLA y SLO deben interpretarse según sus definiciones y compromisos.
- Los indicadores deben considerar el período de medición y el contexto del servicio.

### 6. Datos de demostración

Los datos utilizados en este producto son ficticios y están identificados como **DEMO**.

No representan información real de infraestructura, empresas, clientes ni servicios productivos.
