# Diccionario de Indicadores de Gestión TI

## 1. Objetivo

Establecer un marco común de medición para los tres productos del portafolio de Gestión de Entrega TI, mediante la definición de indicadores que permitan evaluar el desempeño ejecutivo, la gestión de proyectos, la entrega ágil y las operaciones tecnológicas.

Este diccionario proporciona criterios homogéneos para interpretar los resultados, establecer relaciones entre indicadores y facilitar la toma de decisiones basada en datos.

Los indicadores se organizan en tres dimensiones:

- **Gestión Ejecutiva TI:** seguimiento del desempeño global de iniciativas, cumplimiento de hitos, avance, riesgos y acuerdos de servicio.
- **Gestión de Proyectos y Entrega Ágil:** medición de compromisos, cumplimiento de objetivos, capacidad de entrega y trabajo pendiente.
- **Entrega Técnica y Operaciones TI:** seguimiento de despliegues, estabilidad, recuperación ante fallas, disponibilidad y monitoreo de servicios.

Los datos utilizados en este portafolio son de carácter demostrativo (DEMO) y tienen como finalidad ilustrar la aplicación de los indicadores. No representan resultados operacionales reales.

---

## 2. Modelo común de medición

### 2.1 Definición de un indicador

Cada indicador debe contar con una definición que permita comprender qué mide, cómo se calcula, cuál es su fuente de información y qué decisiones puede respaldar.

La definición de cada indicador considera:

- Nombre del indicador.
- Objetivo de medición.
- Definición funcional.
- Fórmula de cálculo.
- Unidad de medida.
- Fuente de datos.
- Frecuencia de medición.
- Criterios de interpretación.
- Limitaciones de uso, cuando corresponda.

### 2.2 Tipos de indicadores

Los indicadores se clasifican según su naturaleza:

| Tipo | Descripción |
|---|---|
| Porcentaje | Representa una proporción respecto de un total. |
| Conteo | Representa una cantidad de elementos o eventos. |
| Tiempo | Mide duración, resolución o recuperación. |
| Frecuencia | Mide la cantidad de eventos dentro de un período. |
| Valor monetario | Representa costos o valores económicos. |
| Diferencia | Expresa la desviación entre dos valores. |

### 2.3 Criterios generales de cálculo

Para asegurar consistencia en la medición:

- Los porcentajes deben calcularse sobre una población identificable.
- Los indicadores de tiempo deben utilizar unidades homogéneas.
- Los conteos deben considerar el período y la población definidos.
- Los indicadores de frecuencia deben especificar el intervalo de observación.
- Los resultados deben identificar su fecha de corte.
- Los datos pendientes, faltantes o no aplicables deben distinguirse de los valores iguales a cero.
- Los indicadores deben calcularse utilizando la fuente de datos correspondiente a su definición.

### 2.4 Reglas de interpretación

Los indicadores no deben interpretarse de manera aislada.

Su análisis debe considerar:

- El contexto de la iniciativa o servicio.
- El período evaluado.
- La calidad y cobertura de los datos.
- La existencia de eventos extraordinarios.
- Las dependencias entre equipos y servicios.
- Las diferencias entre datos reales y demostrativos.

Un resultado porcentual favorable no necesariamente representa una mejora operacional si existen diferencias en la población evaluada o en los criterios de medición.

---

## 3. Indicadores de Gestión Ejecutiva TI

### 3.1 Cumplimiento de hitos (Milestone Predictability)

**Objetivo:** medir la capacidad de las iniciativas para cumplir los hitos planificados dentro del período establecido.

**Definición:** representa la proporción de hitos cumplidos oportunamente respecto del total de hitos planificados para el período.

**Fórmula:**

\[
\text{Cumplimiento de hitos (\%)} =
\frac{\text{Hitos cumplidos a tiempo}}
{\text{Hitos planificados}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `executive-kpis.csv`.

**Interpretación:** un valor elevado refleja mayor cumplimiento de los compromisos de planificación.

Debe analizarse considerando cambios de alcance, reprogramaciones y modificaciones de fechas comprometidas.

### 3.2 Desviación del avance (Progress Deviation)

**Objetivo:** identificar diferencias entre el avance real y el avance planificado de una iniciativa.

**Definición:** mide la diferencia entre el porcentaje de avance real y el porcentaje de avance planificado para una fecha de corte.

**Fórmula:**

\[
\text{Desviación del avance (pp)} =
\text{Avance real (\%)} -
\text{Avance planificado (\%)}
\]

**Unidad de medida:** puntos porcentuales (pp).

**Fuente:** `executive-kpis.csv`.

**Interpretación:**

- Resultado positivo: avance real superior al planificado.
- Resultado igual a cero: avance real coincidente con el plan.
- Resultado negativo: avance real inferior al planificado.

La desviación debe interpretarse considerando el alcance y las condiciones de ejecución de la iniciativa.

### 3.3 Riesgos críticos abiertos (Open Critical Risks)

**Objetivo:** identificar la exposición de las iniciativas a riesgos de alta criticidad.

**Definición:** representa la cantidad de riesgos clasificados como críticos que permanecen abiertos en una fecha de corte.

**Fórmula:**

\[
\text{Riesgos críticos abiertos} =
\text{Cantidad de riesgos críticos abiertos}
\]

**Unidad de medida:** cantidad de riesgos.

**Fuente:** `executive-kpis.csv`.

**Interpretación:** un mayor número de riesgos críticos abiertos representa una mayor exposición potencial para la iniciativa.

Este indicador debe complementarse con el seguimiento de responsables, acciones de mitigación y fechas comprometidas.

### 3.4 Cumplimiento del acuerdo de servicio ejecutivo (Executive SLA Compliance)

**Objetivo:** medir el cumplimiento de los compromisos de servicio definidos para las iniciativas.

**Definición:** representa la proporción de casos elegibles que cumplen el acuerdo de nivel de servicio establecido.

**Fórmula:**

\[
\text{Cumplimiento SLA (\%)} =
\frac{\text{Casos elegibles que cumplen el SLA}}
{\text{Total de casos elegibles}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `executive-kpis.csv`.

**Interpretación:** un valor elevado representa mayor cumplimiento de los compromisos de servicio.

El cálculo debe considerar exclusivamente los casos elegibles y las reglas de medición establecidas para el período.

### 3.5 Disponibilidad ejecutiva (Executive Availability)

**Objetivo:** proporcionar una visión ejecutiva de la disponibilidad de los servicios asociados a las iniciativas.

**Definición:** representa el porcentaje de tiempo durante el cual un servicio se encuentra disponible respecto del período total evaluado.

**Fórmula general:**

\[
\text{Disponibilidad (\%)} =
\frac{\text{Tiempo disponible}}
{\text{Tiempo total del período}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente potencial:** `cloud-monitoring.csv`, sujeto a la existencia de una relación verificable entre iniciativas y servicios.

**Interpretación:** un valor elevado representa mayor disponibilidad del servicio durante el período evaluado.

**Limitación:** no se debe calcular ni atribuir disponibilidad ejecutiva directamente desde los datos de monitoreo si no existe un mapeo completo entre iniciativas, servicios y períodos de observación compatibles.

---

## 4. Indicadores de Gestión de Proyectos y Entrega Ágil

### 4.1 Cumplimiento del objetivo del Sprint (Sprint Goal Achievement)

**Objetivo:** medir el cumplimiento del objetivo definido para cada Sprint.

**Definición:** representa la proporción de Sprints cerrados cuyo objetivo fue alcanzado.

**Fórmula:**

\[
\text{Sprint Goal Achievement (\%)} =
\frac{\text{Sprints con objetivo alcanzado}}
{\text{Total de Sprints cerrados}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `agile-delivery.csv`.

**Interpretación:** permite evaluar la consistencia con que los equipos alcanzan los objetivos comprometidos para cada Sprint.

**Criterio de cálculo:** los Sprints en curso no deben incluirse en el denominador.

En el conjunto de datos DEMO, el Sprint S12 se encuentra en curso al corte del 7 de noviembre de 2026 y su resultado está registrado como `Pendiente`.

Por lo tanto, debe excluirse de las comparaciones de Sprints cerrados.

En los datos DEMO:

- Sprints cerrados: 44.
- Sprints con objetivo alcanzado: 33.
- Sprints con objetivo no alcanzado: 11.

**Resultado DEMO:**

\[
\frac{33}{44}\times100 = 75\%
\]

El cumplimiento del objetivo del Sprint es del 75 %.

### 4.2 Fiabilidad del compromiso del Sprint (Sprint Commitment Reliability)

**Objetivo:** evaluar la capacidad del equipo para completar los elementos comprometidos al inicio del Sprint.

**Definición:** representa la proporción de elementos comprometidos que fueron completados durante el Sprint.

**Fórmula:**

\[
\text{Sprint Commitment Reliability (\%)} =
\frac{\text{Elementos comprometidos completados}}
{\text{Elementos comprometidos inicialmente}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `agile-delivery.csv`.

**Interpretación:** permite identificar diferencias entre el compromiso inicial y el trabajo efectivamente completado.

**Consideración:** la interpretación supone que los elementos pendientes corresponden a compromisos iniciales no completados y que no existen cancelaciones o ajustes que alteren la población comprometida.

No debe confundirse con el cumplimiento del objetivo del Sprint, ya que ambos indicadores miden aspectos diferentes.

### 4.3 Trabajo pendiente trasladado al siguiente Sprint (Carry-over)

**Objetivo:** identificar el volumen de trabajo comprometido que no se completa dentro del Sprint y se traslada a un período posterior.

**Definición:** mide la proporción de elementos pendientes respecto del total de elementos comprometidos inicialmente.

**Fórmula:**

\[
\text{Carry-over (\%)} =
\frac{\text{Elementos pendientes trasladados}}
{\text{Elementos comprometidos}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `agile-delivery.csv`.

**Interpretación:** un valor elevado puede indicar dificultades de planificación, cambios de prioridad, dependencias externas o capacidad insuficiente.

Debe analizarse junto con la fiabilidad del compromiso y el cumplimiento del objetivo del Sprint.

### 4.4 Trabajo no planificado (Unplanned Work)

**Objetivo:** identificar el trabajo incorporado durante el Sprint que no formaba parte del compromiso inicial.

**Definición:** representa la proporción de trabajo no planificado respecto de la carga de trabajo considerada para el análisis.

**Fórmula general:**

\[
\text{Trabajo no planificado (\%)} =
\frac{\text{Trabajo no planificado}}
{\text{Trabajo total considerado}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `agile-delivery.csv`, cuando los campos disponibles permiten identificar y cuantificar el trabajo no planificado.

**Interpretación:** un valor elevado puede reflejar interrupciones, incidentes, cambios de prioridad o deficiencias en la planificación.

**Limitación:** no debe calcularse si el conjunto de datos no permite identificar de manera diferenciada el trabajo planificado y el no planificado. Un conteo de trabajo no planificado, por sí solo, no permite obtener este porcentaje.

### 4.5 Elementos completados (Throughput)

**Objetivo:** medir el volumen de elementos de trabajo completados por un equipo durante un período determinado.

**Definición:** representa la cantidad de elementos finalizados dentro del período de observación.

**Fórmula:**

\[
\text{Throughput} =
\text{Cantidad de elementos completados}
\]

**Unidad de medida:** cantidad de elementos.

**Fuente:** `agile-delivery.csv`, campo `elementos_completados`.

**Interpretación:** permite observar la evolución del flujo de entrega del equipo.

No debe utilizarse como medida aislada de productividad ni compararse entre equipos con tamaños de elementos o criterios de estimación diferentes.

**Limitación:** el valor corresponde a un agregado registrado por equipo y Sprint. No permite reconstruir el detalle de cada elemento ni separar automáticamente trabajo planificado y no planificado.

### 4.6 Tiempo de ciclo (Cycle Time)

**Objetivo:** medir el tiempo transcurrido desde que un elemento comienza su ejecución hasta que queda completado.

**Definición:** representa la duración del trabajo en curso hasta su finalización.

**Fórmula conceptual:**

\[
\text{Cycle Time} =
\text{Fecha de finalización} -
\text{Fecha de inicio del trabajo}
\]

**Unidad de medida:** horas o días.

**Fuente:** `agile-delivery.csv`, campo `cycle_time_mediana_dias`.

**Interpretación:** permite identificar demoras y oportunidades de mejora en el flujo de trabajo.

**Limitación:** el conjunto de datos contiene un valor agregado de mediana por equipo y Sprint. No dispone del detalle de fechas de inicio y finalización de cada elemento para reconstruir el cálculo individual.

El valor registrado debe interpretarse como una métrica agregada y no como un cálculo recalculable desde eventos individuales.

---

## 5. Indicadores de Entrega Técnica y Operaciones TI

### 5.1 Frecuencia de despliegues (Deployment Frequency)

**Objetivo:** medir la frecuencia con que se realizan despliegues exitosos en producción.

**Definición:** representa la cantidad de despliegues exitosos realizados en el ambiente de producción durante un período determinado.

**Fórmula:**

\[
\text{Deployment Frequency} =
\text{Cantidad de despliegues exitosos en producción}
\]

**Unidad de medida:** cantidad de despliegues por período.

**Fuente:** `deployments.csv`.

**Interpretación:** permite observar la frecuencia de entrega de cambios a producción.

**Criterio de cálculo:** se consideran exclusivamente los despliegues exitosos en producción. Los despliegues fallidos no deben contabilizarse como entregas exitosas.

### 5.2 Tiempo de entrega de cambios (Lead Time for Changes)

**Objetivo:** medir el tiempo transcurrido desde que se realiza un cambio hasta que queda desplegado en producción.

**Definición:** representa el tiempo necesario para llevar un cambio desde su origen en el desarrollo hasta su despliegue en producción.

**Fórmula conceptual:**

\[
\text{Lead Time for Changes} =
\text{Fecha de despliegue} -
\text{Fecha de inicio del cambio}
\]

**Unidad de medida:** horas o días.

**Fuente:** `deployments.csv`, campo `lead_time_cambios_horas`.

**Interpretación:** permite evaluar la velocidad del proceso de entrega técnica.

**Limitación de los datos DEMO:** el archivo contiene el campo `lead_time_cambios_horas`, pero no dispone de todos los eventos y marcas de tiempo necesarios para reconstruir el proceso completo desde el origen del cambio hasta producción.

Por esta razón, el valor debe interpretarse como una aproximación registrada y no como un cálculo integral basado en eventos fuente.

### 5.3 Tasa de fallas por cambios (Change Failure Rate)

**Objetivo:** medir la proporción de despliegues que generan fallas o requieren una intervención correctiva.

**Definición:** representa el porcentaje de despliegues que resultan fallidos respecto del total de despliegues realizados en producción.

**Fórmula:**

\[
\text{Change Failure Rate (\%)} =
\frac{\text{Despliegues fallidos}}
{\text{Total de despliegues en producción}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `deployments.csv`.

**Interpretación:** un valor elevado indica mayor proporción de cambios que generan fallas.

En el conjunto de datos DEMO se registran:

- Total de despliegues en producción: 48.
- Despliegues exitosos: 41.
- Despliegues fallidos: 7.

**Resultado DEMO:**

\[
\frac{7}{48}\times100 = 14,58\%
\]

El resultado representa una tasa de fallas por cambios del 14,58 %.

### 5.4 Tiempo de recuperación de despliegues fallidos (Failed Deployment Recovery Time)

**Objetivo:** medir el tiempo necesario para recuperar el servicio después de una falla asociada a un despliegue.

**Definición:** representa el tiempo transcurrido desde la detección de la falla hasta la recuperación del servicio.

**Fórmula:**

\[
\text{Tiempo promedio de recuperación} =
\frac{\sum \text{Tiempos de recuperación}}
{\text{Cantidad de despliegues fallidos}}
\]

**Unidad de medida:** minutos.

**Fuente:** `deployments.csv`, campo `tiempo_recuperacion_minutos`.

**Interpretación:** un menor tiempo de recuperación refleja una mayor capacidad de respuesta ante fallas de despliegue.

En los datos DEMO se registran siete despliegues fallidos, con los siguientes tiempos de recuperación:

- 95 minutos.
- 140 minutos.
- 110 minutos.
- 85 minutos.
- 75 minutos.
- 65 minutos.
- 55 minutos.

**Resultado DEMO:**

\[
\frac{95+140+110+85+75+65+55}{7}
= 89,29 \text{ minutos}
\]

El tiempo promedio de recuperación de despliegues fallidos es de aproximadamente 89,3 minutos.

Este indicador debe diferenciarse del tiempo de resolución operacional de incidentes, ya que ambos pueden utilizar puntos de inicio distintos.

### 5.5 Tiempo medio de resolución de incidentes (Operational MTTR)

**Objetivo:** medir el tiempo promedio necesario para resolver los incidentes registrados en los servicios tecnológicos.

**Definición:** representa el tiempo transcurrido desde la apertura del incidente hasta su recuperación o resolución operacional, según el criterio definido en el conjunto de datos.

**Fórmula:**

\[
\text{MTTR operacional} =
\frac{\sum \text{Tiempos de resolución}}
{\text{Cantidad de incidentes resueltos}}
\]

**Unidad de medida:** minutos.

**Fuente:** `incidents.csv`, campo `tiempo_resolucion_minutos`.

**Interpretación:** permite evaluar la capacidad operacional para resolver incidentes.

En los datos DEMO se registran:

- Incidentes resueltos: 15.
- Tiempo acumulado de resolución: 1.736 minutos.

**Resultado DEMO:**

\[
\frac{1736}{15} = 115,73 \text{ minutos}
\]

El MTTR operacional promedio es de aproximadamente 115,7 minutos.

**Consideración:** el campo `tiempo_resolucion_minutos` mide el tiempo desde la apertura hasta la recuperación o resolución del incidente. No debe confundirse con el tiempo desde la detección hasta la recuperación.

### 5.6 Cumplimiento del acuerdo de nivel de servicio de incidentes (Incident SLA Compliance)

**Objetivo:** medir el cumplimiento de los tiempos de atención y resolución establecidos para los incidentes.

**Definición:** representa la proporción de incidentes que cumplen el acuerdo de nivel de servicio respecto del total de incidentes elegibles evaluados.

**Fórmula:**

\[
\text{Incident SLA Compliance (\%)} =
\frac{\text{Incidentes que cumplen el SLA}}
{\text{Total de incidentes elegibles}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `incidents.csv`.

**Interpretación:** un valor elevado refleja mayor cumplimiento de los compromisos de resolución.

En los datos DEMO:

- Incidentes evaluados: 15.
- Incidentes que cumplen el SLA: 12.

**Resultado DEMO:**

\[
\frac{12}{15}\times100 = 80\%
\]

El cumplimiento del SLA de incidentes es del 80 %.

### 5.7 Incidentes críticos (Critical Incidents)

**Objetivo:** identificar la cantidad de incidentes que presentan la máxima severidad definida para la operación.

**Definición:** representa el número de incidentes clasificados como críticos dentro del período evaluado.

**Fórmula:**

\[
\text{Incidentes críticos} =
\text{Cantidad de incidentes con severidad Crítica}
\]

**Unidad de medida:** cantidad de incidentes.

**Fuente:** `incidents.csv`.

**Interpretación:** permite identificar eventos de alta severidad que requieren atención prioritaria y seguimiento ejecutivo.

**Criterio de clasificación:** deben contabilizarse exclusivamente los incidentes cuya severidad esté registrada como `Crítica`. Los incidentes clasificados como `Alta` no deben incorporarse a este indicador.

En los datos DEMO se registra un incidente con severidad Crítica.

### 5.8 Disponibilidad de servicios Cloud (Cloud Service Availability)

**Objetivo:** medir la disponibilidad de los servicios tecnológicos alojados en infraestructura Cloud.

**Definición:** representa el porcentaje de tiempo durante el cual un servicio se encuentra disponible respecto del período total de observación.

**Fórmula general:**

\[
\text{Disponibilidad Cloud (\%)} =
\frac{\text{Tiempo disponible}}
{\text{Tiempo total observado}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `cloud-monitoring.csv`.

**Interpretación:** permite evaluar la continuidad de los servicios y detectar períodos de degradación o indisponibilidad.

**Limitaciones de los datos DEMO:**

- Los registros representan observaciones de monitoreo y no telemetría continua.
- La información corresponde a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- La fuente de monitoreo es CloudWatch.
- Los datos corresponden a infraestructura AWS en ambiente de producción.
- No deben interpretarse como mediciones en tiempo real.
- La disponibilidad calculada debe considerar la granularidad de las observaciones y no asumir que los registros representan automáticamente todo el tiempo del período.

### 5.9 Utilización de recursos Cloud (Cloud Resource Utilization)

**Objetivo:** observar el nivel de utilización de los recursos tecnológicos en infraestructura Cloud.

**Definición:** representa el nivel de utilización de los recursos monitoreados, como CPU, memoria u otros indicadores disponibles en la fuente.

**Fórmula general:**

\[
\text{Utilización del recurso (\%)} =
\frac{\text{Recurso utilizado}}
{\text{Capacidad total del recurso}}
\times 100
\]

**Unidad de medida:** porcentaje.

**Fuente:** `cloud-monitoring.csv`.

**Interpretación:** permite identificar posibles situaciones de saturación, subutilización o necesidad de optimización de recursos.

La interpretación debe considerar el tipo de recurso, la capacidad provisionada y el comportamiento del servicio.

**Limitación:** los valores agregados de monitoreo permiten analizar las observaciones registradas, pero no deben interpretarse como una medición continua de utilización si la fuente no proporciona esa granularidad.

### 5.10 Costo de infraestructura Cloud (Cloud Cost)

**Objetivo:** realizar seguimiento de los costos asociados a la infraestructura Cloud.

**Definición:** representa el valor monetario registrado para los servicios o recursos monitoreados durante el período evaluado.

**Fórmula:**

\[
\text{Costo Cloud} =
\sum \text{Costos registrados}
\]

**Unidad de medida:** dólares estadounidenses (USD).

**Fuente:** `cloud-monitoring.csv`, campo `costo_cloud_usd`.

**Interpretación:** permite observar la evolución de los costos y detectar variaciones que puedan requerir análisis de optimización.

**Limitación:** los valores de `costo_cloud_usd` del conjunto de datos son demostrativos. No representan facturación real de AWS ni deben utilizarse como evidencia de ahorro o gasto operacional.

---

## 6. Gobierno de los Indicadores

### 6.1 Responsabilidad y trazabilidad

Cada indicador debe contar con una definición formal, una fuente de datos identificable y un responsable de su seguimiento.

La trazabilidad permite verificar:

- El origen de los datos.
- La fecha de extracción o corte.
- Los criterios utilizados para el cálculo.
- Las transformaciones aplicadas.
- La consistencia entre el dato original y el resultado presentado.

Los cambios en las fórmulas o criterios de medición deben quedar documentados para evitar diferencias de interpretación entre períodos.

### 6.2 Calidad de los datos

La calidad de los datos es una condición necesaria para garantizar la confiabilidad de los indicadores.

Se deben considerar las siguientes dimensiones:

| Dimensión | Descripción |
|---|---|
| Completitud | Disponibilidad de los campos requeridos para el cálculo. |
| Consistencia | Coherencia entre los datos relacionados. |
| Exactitud | Correspondencia entre el dato registrado y el evento que representa. |
| Trazabilidad | Posibilidad de identificar el origen y las transformaciones del dato. |
| Oportunidad | Disponibilidad de los datos dentro del período requerido. |
| Validez | Cumplimiento de las reglas y formatos definidos. |

Un indicador calculado sobre datos incompletos o inconsistentes debe identificarse como parcial o no disponible, según corresponda.

### 6.3 Tratamiento de datos faltantes

Los datos faltantes deben tratarse de acuerdo con su naturaleza.

Se deben diferenciar los siguientes casos:

- **Cero:** representa un valor medido igual a cero.
- **Nulo:** representa ausencia de información.
- **Pendiente:** representa información cuyo resultado todavía no está disponible.
- **No aplica:** representa un indicador que no corresponde a la situación evaluada.
- **No disponible:** representa información que no puede calcularse por falta de datos suficientes.

No se deben reemplazar automáticamente los datos faltantes por cero, ya que esto puede distorsionar los resultados y generar conclusiones incorrectas.

### 6.4 Clasificación de datos demostrativos (DEMO)

Los conjuntos de datos utilizados en el portafolio tienen carácter demostrativo.

Su propósito es permitir la validación de fórmulas, la construcción de tableros y la presentación de escenarios de gestión.

Por lo tanto:

- Los valores no representan resultados reales de empresas o servicios.
- Los costos Cloud no corresponden a facturación real.
- Los incidentes y despliegues son registros de ejemplo.
- Los resultados porcentuales representan exclusivamente los datos contenidos en los archivos DEMO.
- Las conclusiones deben limitarse al alcance del escenario demostrado.
- Los tableros y reportes deben identificar claramente el carácter demostrativo de la información.

### 6.5 Frecuencia de actualización y fecha de corte

Cada indicador debe tener una frecuencia de actualización acorde con su naturaleza y fuente de datos.

| Dimensión | Frecuencia de referencia |
|---|---|
| Gestión Ejecutiva TI | Según ciclo de seguimiento y fecha de corte. |
| Gestión de Proyectos y Entrega Ágil | Por Sprint o período de seguimiento. |
| Entrega Técnica y Operaciones TI | Según frecuencia de despliegues, monitoreo e incidentes. |

La frecuencia indicada es una referencia de gestión. La disponibilidad efectiva depende de la actualización de las fuentes de datos.

Los resultados deben identificar la fecha de corte utilizada para evitar comparaciones entre períodos incompatibles.

---

## 7. Principios de Interpretación Ejecutiva

### 7.1 Interpretación contextual

Los indicadores deben analizarse considerando el contexto de la iniciativa, el equipo o el servicio evaluado.

No es recomendable establecer conclusiones únicamente a partir de un valor aislado.

### 7.2 Análisis de tendencias

La evolución de los indicadores permite identificar patrones, desviaciones y oportunidades de mejora.

Cuando los datos lo permitan, se recomienda comparar períodos consecutivos y observar la tendencia, evitando conclusiones basadas en una única medición.

### 7.3 Relación entre indicadores

Los indicadores pueden complementarse para entregar una visión más completa de la gestión.

Algunos ejemplos:

- El cumplimiento de hitos puede analizarse junto con la desviación del avance y los riesgos críticos abiertos.
- El cumplimiento del objetivo del Sprint puede analizarse junto con la fiabilidad del compromiso y el trabajo pendiente.
- La frecuencia de despliegues puede analizarse junto con la tasa de fallas por cambios.
- El tiempo de recuperación de despliegues fallidos puede analizarse junto con el MTTR operacional.
- La disponibilidad Cloud puede complementarse con indicadores de monitoreo y utilización de recursos.

La relación entre indicadores debe considerar que sus fuentes, períodos y unidades de medición pueden ser diferentes.

### 7.4 Tiempo de recuperación DORA versus MTTR operacional

El tiempo de recuperación de despliegues fallidos y el MTTR operacional son indicadores relacionados, pero no equivalentes.

| Característica | Recuperación de despliegues fallidos | MTTR operacional |
|---|---|---|
| Objetivo | Medir recuperación ante fallas asociadas a despliegues. | Medir resolución de incidentes operacionales. |
| Fuente | `deployments.csv` | `incidents.csv` |
| Punto de inicio | Detección de la falla. | Apertura del incidente. |
| Punto de término | Recuperación del servicio. | Recuperación o resolución operacional. |
| Unidad | Minutos | Minutos |

En los datos DEMO, los siete despliegues fallidos tienen incidentes asociados:

| Despliegue | Incidente | Tiempo de recuperación (minutos) |
|---|---|---:|
| DEP-003 | INC-001 | 95 |
| DEP-008 | INC-002 | 140 |
| DEP-014 | INC-003 | 110 |
| DEP-020 | INC-004 | 85 |
| DEP-027 | INC-005 | 75 |
| DEP-034 | INC-006 | 65 |
| DEP-043 | INC-007 | 55 |

**Promedio de recuperación de despliegues fallidos:**

\[
\frac{95+140+110+85+75+65+55}{7}
= 89,29 \text{ minutos}
\]

El promedio de recuperación de despliegues fallidos es de aproximadamente 89,3 minutos.

**MTTR operacional:**

\[
\frac{1736}{15}
= 115,73 \text{ minutos}
\]

El MTTR operacional promedio es de aproximadamente 115,7 minutos.

Aunque existe relación entre ambos indicadores, no deben compararse directamente como si midieran exactamente el mismo intervalo temporal.

### 7.5 Uso responsable de los indicadores

Los indicadores deben utilizarse para facilitar la toma de decisiones y promover mejoras en los procesos.

No deben emplearse de manera aislada para evaluar el desempeño individual de las personas ni para establecer comparaciones entre equipos sin considerar diferencias de contexto, alcance y complejidad.

---

## 8. Aplicación del Diccionario en el Portafolio

### 8.1 Integración con los productos del portafolio

El diccionario establece la referencia común para la construcción y presentación de indicadores en los tres productos del portafolio.

Su aplicación permite mantener consistencia entre las fuentes de datos, los cálculos y la visualización de resultados.

| Producto | Aplicación principal |
|---|---|
| Gestión Ejecutiva TI | Seguimiento de iniciativas, cumplimiento, avance, riesgos y acuerdos de servicio. |
| Gestión de Proyectos y Entrega Ágil | Seguimiento de Sprints, compromisos, objetivos y flujo de trabajo. |
| Entrega Técnica y Operaciones TI | Seguimiento de despliegues, fallas, recuperación, incidentes y monitoreo Cloud. |

### 8.2 Fuentes de datos del portafolio

El portafolio utiliza cinco conjuntos de datos demostrativos.

| Archivo | Registros | Propósito |
|---|---:|---|
| `executive-kpis.csv` | 36 | Indicadores ejecutivos de iniciativas. |
| `agile-delivery.csv` | 48 | Seguimiento de equipos y Sprints. |
| `deployments.csv` | 48 | Registro de despliegues técnicos. |
| `cloud-monitoring.csv` | 20 | Observaciones de monitoreo Cloud. |
| `incidents.csv` | 15 | Registro y resolución de incidentes. |
| **Total** | **167** | **Registros demostrativos.** |

### 8.3 Criterios de utilización de las fuentes

Cada conjunto de datos debe utilizarse de acuerdo con su finalidad:

- `executive-kpis.csv`: seguimiento ejecutivo de iniciativas y fechas de corte.
- `agile-delivery.csv`: análisis de desempeño de equipos y Sprints.
- `deployments.csv`: análisis de despliegues, fallas y tiempos de recuperación.
- `cloud-monitoring.csv`: análisis de observaciones de monitoreo y utilización de recursos Cloud.
- `incidents.csv`: análisis de incidentes, tiempos de resolución y cumplimiento de SLA.

No se deben combinar fuentes diferentes sin validar previamente la relación entre sus registros, períodos y criterios de medición.

### 8.4 Limitaciones conocidas de los conjuntos de datos

Para evitar interpretaciones incorrectas, se deben considerar las siguientes limitaciones:

**Gestión Ejecutiva TI**

- Los indicadores se calculan según los campos disponibles en el archivo.
- La disponibilidad ejecutiva requiere una relación verificable entre iniciativas y servicios.
- El corte del 7 de noviembre de 2026 debe interpretarse como parcial cuando corresponda.

**Gestión de Proyectos y Entrega Ágil**

- El archivo contiene cuatro equipos y doce Sprints por equipo.
- El Sprint S12 se encuentra en curso al corte del 7 de noviembre de 2026.
- Los Sprints en curso no deben incorporarse a los indicadores de cumplimiento de Sprints cerrados.
- El cumplimiento del objetivo del Sprint no equivale al porcentaje de tareas completadas.
- Los indicadores agregados no permiten reconstruir el detalle individual de cada elemento de trabajo.

**Entrega Técnica**

- El archivo contiene 48 despliegues en producción.
- Se registran 41 despliegues exitosos y 7 fallidos.
- El tiempo de entrega de cambios corresponde a un valor registrado y no a una reconstrucción integral desde eventos fuente.
- Los tiempos de recuperación deben interpretarse según su punto de inicio y término.

**Monitoreo Cloud**

- El archivo contiene 20 observaciones.
- Representa cuatro servicios y cinco cortes semanales de septiembre de 2026.
- Los registros no representan telemetría continua ni monitoreo en tiempo real.
- Los costos son valores demostrativos y no facturación real.

**Incidentes**

- El archivo contiene 15 incidentes resueltos.
- El tiempo de resolución y el tiempo de recuperación representan intervalos diferentes.
- Se registra un incidente con severidad Crítica.
- Los incidentes de severidad Alta no deben contabilizarse como críticos.

### 8.5 Evolución del modelo de medición

El diccionario puede evolucionar a medida que se incorporen nuevas fuentes de datos, integraciones y capacidades de análisis.

Las futuras mejoras pueden considerar:

- Integración con Jira para obtener métricas ágiles.
- Integración con herramientas de CI/CD para obtener métricas de despliegue.
- Integración con plataformas de monitoreo para obtener métricas operacionales.
- Automatización de cálculos y actualización de indicadores.
- Construcción de tableros ejecutivos y operacionales.
- Incorporación de criterios de gobierno y calidad de datos.

Toda incorporación debe mantener la trazabilidad entre la fuente, la fórmula y el resultado presentado.

---

## 9. Principio de Gestión

Los indicadores de Gestión TI deben permitir transformar los datos en información útil para la toma de decisiones.

Su valor no reside únicamente en medir resultados, sino en facilitar la identificación de desviaciones, anticipar riesgos, mejorar la entrega de valor y fortalecer la gestión de los servicios tecnológicos.

Un modelo de medición efectivo debe mantener tres principios fundamentales:

- **Consistencia:** utilizar definiciones y fórmulas homogéneas.
- **Trazabilidad:** garantizar que cada resultado pueda relacionarse con su fuente de información.
- **Contexto:** interpretar los resultados considerando las condiciones reales de ejecución y operación.

El objetivo final es disponer de una visión integrada de la gestión ejecutiva, la entrega ágil y las operaciones TI, promoviendo una cultura de mejora continua basada en evidencia.
