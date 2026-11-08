# Diccionario de Indicadores de Gestión TI

## Objetivo

Definir los indicadores utilizados en los tres productos del portafolio, estableciendo su propósito, fórmula de cálculo, fuente de datos y criterios básicos de interpretación.

El diccionario busca mantener una medición consistente y trazable para apoyar la gestión ejecutiva, la entrega ágil y la operación tecnológica.

## 1. Modelo común de medición

Los indicadores utilizan los siguientes atributos para facilitar su seguimiento y análisis:

| Atributo | Descripción |
|---|---|
| Indicador | Nombre del KPI o métrica. |
| Definición | Qué mide y qué representa. |
| Fórmula | Método de cálculo, cuando corresponda. |
| Línea base | Valor de referencia para comparar. |
| Valor actual | Último valor disponible. |
| Variación | Diferencia respecto de la línea base o período anterior. |
| Meta | Resultado esperado, si está definido. |
| Estado | Cumplimiento respecto de la meta. |
| Tendencia | Evolución del indicador en el tiempo. |
| Período | Intervalo utilizado para la medición. |
| Fuente | Dataset o sistema de origen. |
| Responsable | Rol encargado de su seguimiento. |
| Calidad del dato | Estado de integridad y confiabilidad de la información. |

**Criterios de medición**

- Comparar períodos con igual duración, alcance y población.
- Identificar los períodos parciales y evitar compararlos directamente con períodos completos.
- Diferenciar los valores reales de los datos DEMO o pendientes de validación.
- No reemplazar datos faltantes por cero ni utilizar estimaciones sin identificarlas.
- Interpretar las variaciones considerando el contexto operativo y los objetivos del indicador.

## 2. Gestión Ejecutiva de TI

Esta categoría reúne indicadores para monitorear el desempeño general de iniciativas y servicios tecnológicos, considerando cumplimiento, avance, riesgos y niveles de servicio.

### 2.1 Predictibilidad de hitos

**Definición:** mide el porcentaje de hitos planificados que se cumplen dentro de la fecha comprometida.

**Fórmula:**

\[
\frac{\text{Hitos cumplidos a tiempo}}{\text{Hitos planificados}} \times 100
\]

**Fuente:** `executive-kpis.csv`

**Unidad:** porcentaje (%).

**Interpretación:** un resultado alto refleja mayor predictibilidad en el cumplimiento de los compromisos. Si no existen hitos planificados en el período, el indicador se considera No aplica.

### 2.2 Desviación del avance

**Definición:** mide la diferencia entre el avance real y el avance planificado de una iniciativa.

**Fórmula:**

\[
\text{Avance real (\%)}-\text{Avance planificado (\%)}
\]

**Fuente:** `executive-kpis.csv`

**Unidad:** puntos porcentuales (pp).

**Interpretación:** un resultado positivo indica adelanto respecto del plan; uno negativo representa atraso. Debe analizarse considerando el período y el estado de la iniciativa.

### 2.3 Riesgos críticos abiertos

**Definición:** representa la cantidad de riesgos críticos que permanecen abiertos en el período.

**Fuente:** `executive-kpis.csv`, campo `riesgos_criticos_abiertos`.

**Unidad:** cantidad de riesgos.

**Interpretación:** permite visualizar la exposición agregada al riesgo. El dataset contiene el total consolidado, no el detalle de cada riesgo ni su historial de seguimiento.

### 2.4 Cumplimiento de SLA

**Definición:** mide el porcentaje de incidentes que cumplen el tiempo objetivo de resolución establecido.

**Fuente ejecutiva:** `executive-kpis.csv`.

**Fuente de detalle operacional:** `incidents.csv`.

**Fórmula:**

\[
\frac{\text{Incidentes resueltos dentro del SLA}}{\text{Incidentes elegibles}} \times 100
\]

**Interpretación:** permite evaluar el cumplimiento de los compromisos de servicio. Para los criterios operacionales, el tratamiento de incidentes y tiempos de resolución, consultar la sección **6.4 SLA**.

### 2.5 Disponibilidad de servicios

**Definición:** mide el porcentaje de tiempo en que un servicio permanece disponible durante un período determinado.

**Fuente ejecutiva:** `executive-kpis.csv`.

**Fuente de monitoreo:** `cloud-monitoring.csv`.

**Unidad:** porcentaje (%).

**Interpretación:** permite evaluar la continuidad del servicio. Para la definición técnica y los criterios de medición, consultar la sección **5.1 Disponibilidad**.

## 3. Gestión de Proyectos y Entrega Ágil

Esta categoría reúne indicadores para monitorear el cumplimiento de los objetivos de los Sprints, la capacidad de entrega, el flujo de trabajo y los factores que afectan la ejecución de los equipos ágiles.

**Fuente principal:** `agile-delivery.csv`.

**Consideración sobre los datos:** los indicadores corresponden a datos DEMO agregados por equipo y Sprint. No se dispone del historial individual completo de las tareas para recalcular algunas métricas desde sus eventos originales. El Sprint S12 (2 al 15 de noviembre de 2026) se encuentra en curso al corte del 7 de noviembre, por lo que sus resultados no deben compararse con los de Sprints finalizados.

### 3.1 Cumplimiento del objetivo del Sprint

**Definición:** mide el porcentaje de Sprints finalizados en los que se alcanza el objetivo comprometido.

**Fórmula:**

\[
\frac{\text{Sprints con objetivo alcanzado}}{\text{Sprints finalizados}} \times 100
\]

**Campo:** `sprint_goal_alcanzado`.

**Unidad:** porcentaje (%).

**Interpretación:** refleja el cumplimiento del propósito del Sprint. No representa el porcentaje de tareas completadas.

### 3.2 Confiabilidad del compromiso del Sprint

**Definición:** mide el porcentaje de elementos comprometidos que se completan durante el Sprint, considerando los elementos que quedan pendientes.

**Fórmula:**

\[
\frac{\text{Elementos comprometidos}-\text{Trabajo pendiente}}{\text{Elementos comprometidos}} \times 100
\]

**Campos:** `elementos_comprometidos`, `carry_over`.

**Unidad:** porcentaje (%).

**Interpretación:** permite evaluar la confiabilidad de los compromisos del equipo. No debe confundirse con productividad ni con velocidad.

El cálculo supone que los elementos pendientes corresponden a compromisos iniciales no completados y que no existen cancelaciones u otros ajustes que alteren su contabilización.

### 3.3 Trabajo pendiente entre Sprints (Carry-over)

**Definición:** mide la cantidad de elementos comprometidos que no se completan al finalizar el Sprint y pasan al siguiente período.

**Campo:** `carry_over`.

**Unidad:** cantidad de elementos y porcentaje respecto del compromiso inicial.

\[
\frac{\text{Elementos pendientes}}{\text{Elementos comprometidos}} \times 100
\]

**Interpretación:** un valor elevado puede indicar problemas de planificación, dependencias, capacidad o interrupciones. Debe analizarse considerando el contexto del Sprint.

### 3.4 Trabajo no planificado

**Definición:** mide el trabajo que se incorpora durante el Sprint sin formar parte del compromiso inicial.

**Fórmula:**

\[
\frac{\text{Trabajo no planificado}}{\text{Elementos comprometidos}+\text{Trabajo no planificado}} \times 100
\]

**Campos:** `trabajo_no_planificado`, `elementos_comprometidos`.

**Unidad:** cantidad de elementos y porcentaje (%).

**Interpretación:** permite identificar interrupciones o cambios de prioridad que afectan la capacidad comprometida. Los elementos deben contabilizarse sin duplicidades.

### 3.5 Flujo de entrega (Throughput)

**Definición:** mide la cantidad de elementos de trabajo completados durante un período.

**Campo:** `throughput`.

**Unidad:** cantidad de elementos.

**Interpretación:** permite observar la capacidad de entrega y su evolución. En este conjunto de datos coincide con `elementos_completados` y no distingue entre elementos planificados y no planificados.

### 3.6 Tiempo de ciclo (Cycle Time)

**Definición:** mide el tiempo transcurrido desde que un elemento comienza su ejecución hasta que se completa.

**Campo:** `cycle_time_mediana_dias`.

**Unidad:** días.

**Agregación:** mediana por equipo y Sprint.

**Interpretación:** permite evaluar la fluidez del proceso de entrega. Un aumento puede reflejar bloqueos, dependencias o acumulación de trabajo en curso.

### 3.7 Tiempo de entrega (Lead Time)

**Definición:** mide el tiempo transcurrido desde que se registra una solicitud hasta que el elemento se completa.

**Campo:** `lead_time_mediana_dias`.

**Unidad:** días.

**Agregación:** mediana por equipo y Sprint.

**Interpretación:** representa el tiempo de respuesta desde la solicitud hasta la entrega. Incluye el tiempo previo al inicio del trabajo, a diferencia del tiempo de ciclo.

### 3.8 Trabajo en curso (WIP)

**Definición:** representa la cantidad promedio de elementos iniciados que permanecen sin completar.

**Campo:** `wip_promedio`.

**Unidad:** cantidad promedio de elementos.

**Interpretación:** permite observar la acumulación de trabajo en curso. Un valor elevado puede aumentar los tiempos de entrega y dificultar la identificación de bloqueos.

### 3.9 Impedimentos

**Definición:** mide la cantidad de impedimentos registrados durante el Sprint.

**Campo:** `impedimentos`.

**Unidad:** cantidad de impedimentos.

**Interpretación:** permite identificar obstáculos que afectan el flujo de trabajo. El conjunto de datos contiene valores agregados, sin detalle de responsables, duración o estado individual.

### 3.10 Defectos

**Definición:** mide la cantidad de defectos identificados durante el período.

**Campo:** `defectos`.

**Unidad:** cantidad de defectos.

**Interpretación:** permite monitorear señales de calidad del producto. El dato agregado no incluye severidad, causa raíz ni estado individual de cada defecto.

### 3.11 Retrabajo (Rework)

**Definición:** mide la cantidad de elementos de trabajo que requieren correcciones o ejecución adicional.

**Campo:** `retrabajo_elementos`.

**Unidad:** cantidad de elementos.

**Interpretación:** permite identificar trabajo adicional asociado a correcciones o ajustes. No representa horas ni costos de retrabajo y no debe asumirse que todo defecto genera retrabajo.

## 4. Entrega Técnica y DevOps — Métricas DORA

Esta categoría reúne indicadores para evaluar la frecuencia de despliegues, el tiempo de entrega de cambios y la estabilidad de las liberaciones en producción.

**Fuentes principales:** `deployments.csv` e `incidents.csv`.

**Consideración sobre los datos:** el conjunto DEMO contiene 48 registros de despliegues de cuatro servicios, correspondientes al período junio-septiembre de 2026. Se identifican siete despliegues fallidos y sus incidentes asociados. Los datos permiten ilustrar el análisis DORA, pero no representan una medición productiva validada.

### 4.1 Frecuencia de despliegue (Deployment Frequency)

**Definición:** mide la frecuencia con que se realizan despliegues exitosos en producción durante un período.

**Criterio de cálculo:** contabilizar los despliegues con entorno de producción y estado exitoso, agrupados por servicio y período.

**Campos:** `fecha_despliegue`, `servicio`, `entorno`, `estado_despliegue`.

**Unidad:** cantidad de despliegues por período.

**Interpretación:** permite observar la capacidad de entrega de cambios en producción. Una mayor frecuencia no implica necesariamente mayor valor de negocio ni mejor calidad.

### 4.2 Tiempo de entrega de cambios (Lead Time for Changes)

**Definición:** mide el tiempo transcurrido desde que un cambio se confirma en el repositorio hasta que se despliega en producción.

**Campo:** `lead_time_cambios_horas`.

**Unidad:** horas.

**Agregación recomendada:** mediana por servicio y período.

**Limitación:** el dataset contiene duraciones agregadas, pero no las marcas de tiempo individuales de cada commit y despliegue. Por tanto, este indicador es una aproximación DEMO y no permite validar el cálculo DORA original desde los eventos fuente.

**Interpretación:** permite observar la rapidez con que los cambios llegan a producción.

### 4.3 Tasa de fallos de cambios (Change Failure Rate)

**Definición:** mide el porcentaje de despliegues en producción que generan una falla y requieren intervención correctiva.

**Fórmula:**

\[
\frac{\text{Despliegues fallidos en producción}}{\text{Total de despliegues en producción}} \times 100
\]

**Campos:** `fallo_cambio`, `estado_despliegue`, `entorno`, `incidente_id`.

**Unidad:** porcentaje (%).

**Ejemplo DEMO:** se identifican siete despliegues fallidos. La tasa definitiva debe calcularse utilizando como denominador únicamente los despliegues realizados en producción durante el mismo período.

**Limitación:** el dataset identifica fallas asociadas a despliegues, pero no contiene evidencia detallada de cada acción correctiva, como rollback, hotfix o restauración.

**Interpretación:** permite evaluar la estabilidad de los cambios liberados en producción. Debe analizarse junto con la frecuencia de despliegue y los tiempos de recuperación.

### 4.4 Tiempo de recuperación de despliegues fallidos (Failed Deployment Recovery Time)

**Definición:** mide el tiempo transcurrido desde la detección del impacto de un despliegue fallido hasta la recuperación del servicio.

**Fuente:** `incidents.csv`, para incidentes asociados a despliegues fallidos.

**Campos:** `fecha_deteccion`, `fecha_recuperacion`, `incidente_id`.

**Unidad:** tiempo de recuperación.

**Limitación:** se utiliza la fecha de detección como referencia de inicio. El resultado depende de la disponibilidad y consistencia de las marcas de tiempo del dataset.

**Interpretación:** permite evaluar la capacidad de respuesta y recuperación ante fallas provocadas por despliegues. No debe confundirse con el MTTR operacional, cuya definición y alcance se presentan en la sección **6.2**.

## 5. Monitoreo y Observabilidad Cloud

Esta categoría reúne indicadores para monitorear la disponibilidad, el rendimiento, el consumo de recursos y los costos de los servicios alojados en infraestructura cloud.

**Fuente principal:** `cloud-monitoring.csv`.

**Consideración sobre los datos:** el dataset contiene 20 registros de cuatro servicios, distribuidos en cinco cortes semanales de septiembre de 2026. Los valores son agregados y corresponden a datos DEMO; no incluyen telemetría individual ni series temporales originales. Los volúmenes de tráfico y costos representan convenciones de demostración, no registros reales de facturación.

### 5.1 Disponibilidad de servicios

**Definición:** mide el porcentaje de tiempo en que un servicio permanece disponible durante un período.

**Campo:** `disponibilidad_pct`.

**Unidad:** porcentaje (%).

**Interpretación:** permite evaluar la continuidad del servicio y detectar variaciones que puedan afectar su operación.

### 5.2 Latencia de respuesta (p95)

**Definición:** representa el tiempo de respuesta por debajo del cual se encuentra el 95 % de las solicitudes observadas.

**Campo:** `latencia_p95_ms`.

**Unidad:** milisegundos (ms).

**Interpretación:** permite evaluar el rendimiento percibido por los usuarios y detectar degradaciones en los tiempos de respuesta.

### 5.3 Tasa de errores

**Definición:** mide el porcentaje de solicitudes que generan errores respecto del total de solicitudes procesadas.

**Campo:** `tasa_errores_pct`.

**Unidad:** porcentaje (%).

**Interpretación:** permite identificar problemas de estabilidad y calidad del servicio. Debe analizarse junto con la disponibilidad y la latencia.

### 5.4 Utilización de CPU

**Definición:** representa el porcentaje promedio de utilización de la capacidad de procesamiento.

**Campo:** `cpu_promedio_pct`.

**Unidad:** porcentaje (%).

**Interpretación:** permite identificar niveles elevados de consumo de procesamiento y posibles necesidades de optimización o escalamiento.

### 5.5 Utilización de memoria

**Definición:** representa el porcentaje promedio de memoria utilizada respecto de la capacidad disponible.

**Campo:** `memoria_promedio_pct`.

**Unidad:** porcentaje (%).

**Interpretación:** permite detectar presión sobre la memoria y anticipar posibles problemas de rendimiento.

### 5.6 Utilización de almacenamiento

**Definición:** mide el porcentaje de capacidad de almacenamiento utilizada respecto de la capacidad disponible.

**Campo:** `almacenamiento_usado_pct`.

**Unidad:** porcentaje (%).

**Interpretación:** permite monitorear el consumo de almacenamiento y anticipar necesidades de ampliación de capacidad.

### 5.7 Tráfico de red

**Definición:** representa el volumen de datos que ingresan y salen de los servicios durante el período.

**Campos:** `trafico_entrada_gb`, `trafico_salida_gb`.

**Unidad:** gigabytes (GB) por período.

**Interpretación:** permite observar el comportamiento del tráfico de red y detectar variaciones relevantes en el consumo.

### 5.8 Costo de infraestructura Cloud

**Definición:** representa el costo estimado de infraestructura cloud asociado a cada servicio durante el período.

**Campo:** `costo_cloud_usd`.

**Unidad:** dólares estadounidenses (USD) por período.

**Interpretación:** permite ilustrar el seguimiento de costos y comparar su evolución entre servicios. Los valores DEMO no deben interpretarse como facturación real ni utilizarse para decisiones financieras.

## 6. Operación de Servicios TI

Esta categoría reúne indicadores para monitorear el volumen de incidentes, los tiempos de resolución, el cumplimiento de los niveles de servicio y la severidad de las interrupciones.

**Fuente principal:** `incidents.csv`.

**Consideración sobre los datos:** el dataset contiene 15 incidentes registrados entre junio y septiembre de 2026. Todos figuran como resueltos. Los datos son DEMO y no incluyen un contrato SLA real ni información sobre impacto económico o cantidad de usuarios afectados.

### 6.1 Volumen de incidentes

**Definición:** mide la cantidad de incidentes registrados durante un período.

**Campo:** `incidente_id`.

**Unidad:** cantidad de incidentes.

**Interpretación:** permite observar la evolución de las interrupciones y detectar variaciones en la demanda de soporte. El dataset no contiene una fotografía histórica de incidentes abiertos al cierre de cada período.

### 6.2 Tiempo medio de resolución (MTTR)

**Definición:** mide el tiempo promedio transcurrido desde la apertura de un incidente hasta la recuperación del servicio.

**Campo:** `tiempo_resolucion_minutos`.

**Fórmula:**

\[
\frac{\text{Suma de tiempos de resolución}}{\text{Cantidad de incidentes resueltos}}
\]

**Unidad:** minutos u horas.

**Criterio de cálculo:** considerar los incidentes resueltos según su fecha de apertura. Los incidentes aún abiertos deben mantenerse separados y no incorporarse al promedio.

**Interpretación:** permite evaluar la capacidad operacional para resolver incidentes. Debe analizarse considerando la severidad y el contexto de cada interrupción.

### 6.3 MTTR operacional versus tiempo de recuperación DORA

Ambos indicadores miden tiempos de recuperación, pero utilizan poblaciones y puntos de inicio diferentes.

| Criterio | MTTR operacional | Recuperación DORA |
|---|---|---|
| Población | Incidentes operacionales | Incidentes asociados a despliegues fallidos |
| Inicio | Apertura del incidente | Detección del impacto del despliegue |
| Término | Recuperación del servicio | Recuperación del servicio |
| Fuente | `incidents.csv` | `incidents.csv` |
| Propósito | Evaluar la resolución operacional | Evaluar la capacidad de recuperación ante fallos de cambios |

**Criterio:** no comparar directamente ambos valores sin considerar sus diferencias de alcance y metodología.

### 6.4 Cumplimiento de SLA

**Definición:** mide el porcentaje de incidentes resueltos dentro del tiempo objetivo de servicio.

**Fórmula:**

\[
\frac{\text{Incidentes que cumplen el SLA}}{\text{Incidentes elegibles}} \times 100
\]

**Campos:** `sla_cumplido`, `tiempo_resolucion_minutos`, `sla_objetivo_minutos`.

**Unidad:** porcentaje (%).

**Interpretación:** permite evaluar el cumplimiento de los tiempos de resolución establecidos. En este dataset, el SLA es una referencia DEMO y no representa un compromiso contractual validado.

Se consideran elegibles los incidentes resueltos que cuentan con un objetivo SLA válido para el período evaluado.

### 6.5 Incidentes críticos

**Definición:** mide la cantidad de incidentes clasificados como críticos según su severidad.

**Campos:** `incidente_id`, `severidad`, `fecha_apertura`.

**Unidad:** cantidad de incidentes.

**Interpretación:** permite identificar interrupciones de mayor severidad y monitorear su evolución. El dataset no incluye impacto económico ni cantidad de usuarios afectados.

## 7. Gobierno, Calidad y Trazabilidad de Indicadores

Esta sección establece los criterios para asegurar la consistencia, calidad, trazabilidad y mantenimiento de los indicadores del portafolio.

### 7.1 Clasificación de los datos

Los indicadores deben identificar claramente el estado de validación de sus fuentes:

| Clasificación | Descripción |
|---|---|
| DEMO | Datos de demostración utilizados para ilustrar el funcionamiento de los indicadores. |
| REAL | Datos provenientes de fuentes operacionales verificadas. |
| PENDIENTE DE VALIDACIÓN | Datos cuya integridad, origen o consistencia aún no han sido comprobados. |

La clasificación debe estar disponible para interpretar correctamente los resultados y evitar presentar datos de demostración como mediciones reales.

### 7.2 Trazabilidad de los indicadores

Cada indicador debe contar, según la información disponible, con los siguientes atributos:

- Nombre y definición.
- Objetivo y fórmula de cálculo.
- Unidad de medida y período.
- Fuente de datos y responsable.
- Línea base, valor actual y meta, cuando corresponda.
- Estado, tendencia y calidad del dato.
- Limitaciones metodológicas relevantes.

Los atributos que no estén disponibles deben identificarse explícitamente, sin completar información mediante supuestos no validados.

### 7.3 Calidad e integridad de los datos

Antes de utilizar un indicador, se deben considerar los siguientes controles:

- Integridad de los registros y campos obligatorios.
- Consistencia de fechas y períodos de medición.
- Identificación de registros duplicados.
- Coherencia de identificadores y relaciones entre datasets.
- Consistencia de unidades, fórmulas y denominadores.
- Identificación de valores faltantes o pendientes de validación.

**Tratamiento de información faltante:**

| Estado | Uso |
|---|---|
| Sin dato | El valor no está disponible en la fuente. |
| No medido | No existe medición para el indicador en el período. |
| Pendiente de validación | El valor requiere revisión antes de utilizarse. |
| No aplica | El indicador no corresponde al contexto o período evaluado. |

Los valores faltantes no deben reemplazarse automáticamente por cero ni por estimaciones no identificadas.

### 7.4 Interpretación y comparabilidad

La interpretación de los indicadores debe considerar:

- Comparar períodos y equipos con alcances equivalentes.
- Identificar períodos parciales antes de evaluar tendencias.
- Analizar las métricas en conjunto y no de manera aislada.
- Evitar atribuir causalidad a relaciones que solo muestran correlación.
- Considerar las limitaciones de las fuentes y los datos DEMO.
- Diferenciar indicadores con definiciones o poblaciones distintas, como el MTTR operacional y el tiempo de recuperación DORA.

### 7.5 Mantenimiento y evolución

El diccionario debe actualizarse cuando se incorporen nuevos indicadores, cambien las fuentes de datos o se modifiquen las fórmulas y criterios de medición.

Toda modificación debe mantener la trazabilidad de la definición, el origen del dato y la metodología utilizada.

## 8. Principios Ejecutivos de Interpretación

Los indicadores deben utilizarse como herramientas de análisis y toma de decisiones, considerando el contexto operativo y los objetivos del negocio.

1. **Medir resultados y no solo actividad:** diferenciar los productos entregados (Output) del valor o impacto generado (Outcome).

2. **Interpretar la capacidad de entrega en contexto:** analizar Throughput, velocidad y cumplimiento de compromisos considerando el tamaño, la complejidad y las condiciones de trabajo de cada equipo.

3. **Analizar las métricas técnicas en conjunto:** interpretar las métricas DORA, disponibilidad, incidentes y errores de forma complementaria, evitando conclusiones basadas en un único indicador.

4. **Priorizar tendencias y contexto sobre comparaciones aisladas:** considerar períodos equivalentes, calidad de los datos, cambios operativos y limitaciones de las fuentes antes de comparar resultados.

5. **Convertir las mediciones en decisiones:** utilizar los indicadores para identificar desviaciones, anticipar riesgos, priorizar mejoras y evaluar resultados.

## 9. Mapa de Indicadores por Producto

El portafolio se organiza en tres productos de análisis, cada uno con un propósito de gestión específico.

| Producto | Enfoque | Indicadores principales |
|---|---|---|
| Producto 01: Gestión Ejecutiva de TI | Seguimiento del desempeño y cumplimiento de iniciativas y servicios. | Predictibilidad, desviación del avance, riesgos críticos, cumplimiento de SLA y disponibilidad. |
| Producto 02: Entrega Ágil | Seguimiento de compromisos, capacidad de entrega y flujo de trabajo. | Cumplimiento del objetivo del Sprint, confiabilidad del compromiso, Carry-over, trabajo no planificado, Throughput, Cycle Time, Lead Time, WIP, impedimentos, defectos y retrabajo. |
| Producto 03: DevOps y Operaciones TI | Seguimiento de despliegues, estabilidad, observabilidad y continuidad operacional. | Métricas DORA, disponibilidad, latencia, errores, utilización de recursos, tráfico de red, costos cloud, volumen de incidentes, MTTR, SLA e incidentes críticos. |

## 10. Fuentes de Datos

El portafolio utiliza cinco conjuntos de datos DEMO para representar las distintas dimensiones de gestión tecnológica.

| Dataset | Propósito |
|---|---|
| `executive-kpis.csv` | Indicadores consolidados de gestión ejecutiva, avance, riesgos, SLA y disponibilidad. |
| `agile-delivery.csv` | Métricas de planificación, cumplimiento y flujo de entrega de equipos ágiles. |
| `deployments.csv` | Registro de despliegues y datos para el análisis de métricas DORA. |
| `cloud-monitoring.csv` | Indicadores de disponibilidad, rendimiento, consumo de recursos y costos cloud. |
| `incidents.csv` | Registro de incidentes, tiempos de resolución, cumplimiento de SLA y recuperación de servicios. |

Los datasets permiten ilustrar el modelo de medición y la relación entre indicadores, fuentes de información y decisiones de gestión. No representan registros operacionales reales.

## Principio rector del portafolio

Los indicadores de gestión TI deben transformar los datos en información útil para la toma de decisiones.

El portafolio integra la gestión ejecutiva, la entrega ágil y la operación tecnológica bajo criterios comunes de medición, trazabilidad y calidad de datos.

Su propósito es facilitar la identificación de desviaciones, anticipar riesgos, evaluar el desempeño y orientar acciones de mejora continua, considerando siempre el contexto y las limitaciones de la información disponible.
