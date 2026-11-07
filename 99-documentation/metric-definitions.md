# Diccionario de Indicadores de Gestión TI

## Objetivo

Establecer un marco común de medición para los tres productos del portafolio. Cada indicador debe contar con una definición, fórmula de cálculo, fuente de información, período de medición, responsable y criterios de interpretación.

El diccionario busca asegurar que los indicadores sean consistentes, comparables y útiles para la toma de decisiones.

## 1. Modelo común de medición

Cada indicador debe considerar los siguientes elementos:

| Elemento | Descripción |
|---|---|
| Indicador | Nombre del indicador de gestión |
| Definición | Qué mide y qué representa |
| Fórmula | Método de cálculo |
| Línea base | Valor inicial de referencia |
| Valor actual | Último valor calculado |
| Variación | Diferencia respecto de la línea base o período anterior |
| Meta | Resultado esperado, cuando exista |
| Estado | Situación del indicador frente a la meta |
| Tendencia | Evolución del indicador en el tiempo |
| Período | Intervalo temporal considerado |
| Fuente | Sistema o dataset de origen |
| Responsable | Rol encargado de validar y analizar el indicador |
| Calidad del dato | Nivel de confiabilidad y completitud de la información |

### Criterios generales

- La línea base debe indicar período, alcance y población considerada.
- Los períodos parciales deben identificarse y no compararse directamente con períodos completos.
- Los datos faltantes deben registrarse como "Sin dato", "No medido" o "Pendiente de validación".
- Los datos ficticios deben identificarse explícitamente como DEMO.
- Las comparaciones entre equipos deben considerar capacidad, contexto, tipo de trabajo y complejidad.
- Las variaciones deben interpretarse considerando el contexto y no únicamente el valor numérico.

## 2. Gestión Ejecutiva de TI

### 2.1 Predictibilidad de entrega

**Definición:** mide el cumplimiento de los compromisos de entrega dentro del período evaluado.

**Fórmula:**

Predictibilidad (%) = (Hitos cumplidos a tiempo / Hitos planificados del período) × 100

**Fuente:** `executive-kpis.csv`

**Interpretación:** permite evaluar la capacidad de cumplimiento de los compromisos establecidos.

**Consideraciones:**
- El indicador se calcula sobre hitos cuyo cumplimiento puede evaluarse en el período.
- Un hito no cumplido dentro de su fecha comprometida no se considera cumplido a tiempo.
- Debe analizarse junto con cambios de alcance, dependencias y riesgos.

### 2.2 Desviación del avance respecto del plan

**Definición:** compara el avance real de una iniciativa con el avance planificado.

**Fórmula:**

Desviación de avance (pp) = Avance real (%) − Avance planificado (%)

**Fuente:** `executive-kpis.csv`

**Interpretación:**
- Resultado positivo: avance superior al planificado.
- Resultado negativo: avance inferior al planificado.
- Resultado igual a cero: avance alineado con el plan.

La desviación se expresa en puntos porcentuales (pp), no como porcentaje relativo.

### 2.3 Riesgos críticos abiertos

**Definición:** cantidad de riesgos clasificados como críticos que permanecen abiertos al momento del corte.

**Fórmula:**

Riesgos críticos abiertos = Valor registrado en el campo `riesgos_criticos_abiertos`.

**Fuente:** `executive-kpis.csv`

**Limitación de los datos DEMO:**

El dataset contiene un valor agregado por iniciativa y fecha de corte. No incluye el detalle individual de los riesgos, su severidad, estado, responsable ni fecha de apertura. Por lo tanto, no permite auditar ni recalcular el conteo desde registros individuales.

### 2.4 Cumplimiento de SLA

**Definición:** porcentaje de casos elegibles que cumplen el tiempo objetivo de resolución establecido en el SLA.

**Fórmula:**

Cumplimiento SLA (%) = (Casos SLA cumplidos / Casos SLA elegibles) × 100

**Fuente:** `executive-kpis.csv` y `incidents.csv`

**Criterio aplicado en los datos DEMO:**
- El cumplimiento se determina utilizando el tiempo de resolución.
- El tiempo de resolución se calcula desde la apertura del incidente hasta la recuperación del servicio.
- Se compara con el objetivo de SLA definido para el incidente.

**Consideraciones:**
- El denominador debe incluir únicamente los casos elegibles.
- Los casos sin información suficiente no deben clasificarse automáticamente como cumplidos.
- La regla de cálculo debe mantenerse consistente entre períodos.

### 2.5 Disponibilidad del servicio

**Definición:** porcentaje del tiempo del período durante el cual un servicio estuvo disponible según el criterio de medición definido.

**Fórmula general:**

Disponibilidad (%) = (Tiempo disponible / Tiempo total medido) × 100

**Fuente:** `executive-kpis.csv` y `cloud-monitoring.csv`

**Interpretación:** permite evaluar la continuidad del servicio.

**Consideraciones:**
- Se debe documentar el período de medición.
- Debe definirse cómo se consideran las ventanas de mantenimiento.
- La disponibilidad no equivale a ausencia de incidentes.
- Los datos DEMO disponibles representan cortes agregados, no telemetría continua.
- Los valores de `executive-kpis.csv` y `cloud-monitoring.csv` tienen diferentes niveles de agregación y alcance. No deben combinarse directamente en un único cálculo sin validar previamente su correspondencia.
- Para el análisis ejecutivo se debe utilizar el indicador consolidado de `executive-kpis.csv`; para el análisis técnico por servicio se debe utilizar `cloud-monitoring.csv`.

## 3. Gestión de Proyectos y Entrega Ágil

### 3.1 Cumplimiento del Sprint Goal

**Definición:** proporción de Sprints finalizados en los que el equipo alcanzó el objetivo definido para el Sprint.

**Fórmula:**

Cumplimiento del Sprint Goal (%) = (Sprints finalizados con Sprint Goal alcanzado / Total de Sprints finalizados evaluables) × 100

**Fuente:** `agile-delivery.csv`

**Campo disponible:** `sprint_goal_alcanzado`.

**Valores registrados:** `Si` y `No`.

**Interpretación:** permite evaluar si los equipos lograron el objetivo que orientó el trabajo del Sprint, más allá de la cantidad de elementos completados.

**Consideraciones:**
- El cálculo considera únicamente Sprints finalizados y evaluables.
- Los registros con valor `Si` se consideran objetivos alcanzados.
- Los registros con valor `No` se consideran objetivos no alcanzados, siempre que el Sprint haya finalizado.
- S12, correspondiente al período del 2 al 15 de noviembre de 2026, se encuentra en curso al corte del 7 de noviembre y debe excluirse del cálculo.
- No debe confundirse con el porcentaje de elementos completados ni con el cumplimiento del compromiso.
- Un Sprint puede completar todos sus elementos comprometidos y no alcanzar el Sprint Goal, o alcanzar el objetivo aunque algunos elementos hayan quedado pendientes.

**Limitación de los datos DEMO:** el campo registra el resultado del Sprint Goal como texto (`Si`/`No`). Para una medición real, el resultado debe validarse al cierre del Sprint con el equipo y los criterios de aceptación del objetivo.

### 3.2 Cumplimiento del compromiso del Sprint

**Definición:** proporción de elementos comprometidos al inicio del Sprint que fueron completados durante el período.

**Fórmula:**

Cumplimiento del compromiso (%) = ((Elementos comprometidos − Carry-over) / Elementos comprometidos) × 100

**Fuente:** `agile-delivery.csv`

**Campos utilizados:**
- `elementos_comprometidos`
- `carry_over`

**Interpretación:** permite evaluar en qué medida el equipo completó el trabajo que se había comprometido a realizar al inicio del Sprint.

**Consideraciones:**
- El cálculo considera exclusivamente el compromiso inicial y los elementos comprometidos que quedaron pendientes.
- El trabajo no planificado debe analizarse por separado y no debe incorporarse al numerador de esta fórmula.
- No debe confundirse el cumplimiento del compromiso con el cumplimiento del Sprint Goal.
- Si no existen elementos comprometidos, el indicador debe registrarse como "No aplica".
- S12, al encontrarse en curso al corte del 7 de noviembre de 2026, debe excluirse de las comparaciones de Sprints finalizados.

**Limitación de los datos DEMO:** el cálculo depende de que `carry_over` represente correctamente los elementos del compromiso inicial que quedaron sin completar.

### 3.3 Carry-over

**Definición:** cantidad de elementos comprometidos que no fueron completados durante el Sprint y se trasladan a un período posterior.

**Indicadores:**

- Carry-over (elementos): cantidad de elementos comprometidos que quedaron pendientes.
- Carry-over (%): proporción de elementos comprometidos que no fueron completados.

**Fórmulas:**

Carry-over (elementos) = Conteo de elementos comprometidos no completados.

Carry-over (%) = (Elementos comprometidos no completados / Elementos comprometidos) × 100

**Fuente:** `agile-delivery.csv`

**Campo disponible:** `carry_over`.

**Interpretación:** permite identificar compromisos que se trasladan entre Sprints y analizar posibles problemas de planificación, capacidad o dependencias.

**Consideraciones:**
- El valor absoluto se obtiene directamente del campo `carry_over`.
- El porcentaje se calcula respecto de los elementos comprometidos al inicio del Sprint.
- Si no existen elementos comprometidos, el porcentaje debe registrarse como "No aplica".
- Debe mantenerse un criterio consistente para identificar los elementos pendientes.
- S12, al encontrarse en curso al corte del 7 de noviembre, no debe tratarse como un Sprint finalizado.

### 3.4 Trabajo no planificado

**Definición:** cantidad de elementos de trabajo incorporados durante el Sprint que no formaban parte del compromiso inicial.

**Indicadores:**

- Trabajo no planificado (elementos): cantidad de elementos incorporados fuera del compromiso inicial.
- Trabajo no planificado (%): proporción de elementos no planificados respecto del total de elementos gestionados durante el Sprint.

**Fórmulas:**

Trabajo no planificado (elementos) = Conteo de elementos incorporados fuera del compromiso inicial.

Trabajo no planificado (%) = (Elementos de trabajo no planificado / (Elementos comprometidos + Elementos de trabajo no planificado)) × 100

**Fuente:** `agile-delivery.csv`

**Campos utilizados:**
- `elementos_comprometidos`
- `trabajo_no_planificado`

**Interpretación:** permite identificar cuánto trabajo adicional se incorporó durante el Sprint y analizar su posible impacto sobre la capacidad y los compromisos iniciales.

**Consideraciones:**
- El porcentaje considera como denominador la suma de elementos comprometidos y elementos no planificados.
- Los elementos no planificados deben identificarse por separado del compromiso inicial.
- Se debe mantener un criterio uniforme para clasificar el trabajo adicional.
- Es importante identificar si responde a incidentes, urgencias, cambios de prioridad o dependencias.
- No debe interpretarse automáticamente como una falla del equipo.
- Si el total de elementos gestionados es cero, el indicador debe registrarse como "No aplica".
- La fórmula presupone que ambos campos representan cantidades de elementos comparables y no duplicados.

### 3.5 Throughput

**Definición:** cantidad de elementos de trabajo completados durante un Sprint o período determinado.

**Fórmula:**

Throughput = Conteo de elementos completados durante el período.

**Fuente:** `agile-delivery.csv`

**Campo disponible:** `throughput`.

**Unidad:** cantidad de elementos completados.

**Interpretación:** permite observar el volumen de trabajo terminado por un equipo a lo largo del tiempo.

**Consideraciones:**
- No equivale a productividad individual.
- No debe utilizarse para comparar equipos sin considerar el tamaño y la complejidad de los elementos.
- Debe analizarse junto con Cycle Time, calidad y cumplimiento del Sprint Goal.
- No debe confundirse con el cumplimiento del compromiso inicial.
- El trabajo no planificado debe identificarse y analizarse por separado.

**Limitación de los datos DEMO:**

En la muestra actual, `throughput` presenta los mismos valores que `elementos_completados`. No existe un campo independiente que identifique cuántos elementos de trabajo no planificado fueron completados durante el Sprint.

Por esta razón, el indicador debe interpretarse como el volumen registrado en el campo `throughput`, sin atribuirle una separación entre trabajo planificado y no planificado.

S12 debe identificarse como Sprint en curso y no compararse directamente con Sprints finalizados.

### 3.6 Cycle Time

**Definición:** tiempo transcurrido desde que un elemento de trabajo comienza su ejecución activa hasta que queda completado.

**Fórmula conceptual:**

Cycle Time = Fecha y hora de finalización − Fecha y hora de inicio del trabajo activo.

**Fuente:** `agile-delivery.csv`

**Campo disponible:** `cycle_time_mediana_dias`.

**Unidad:** días.

**Agregación:** mediana del Cycle Time de los elementos completados durante el Sprint.

**Interpretación:** permite evaluar cuánto tiempo tarda el equipo en completar los elementos una vez iniciado el trabajo activo. Una reducción sostenida puede reflejar una mejora en el flujo de entrega, siempre que se mantengan criterios comparables de tamaño y complejidad.

**Consideraciones:**
- La mediana reduce la influencia de elementos con tiempos excepcionalmente altos.
- Debe analizarse junto con Lead Time, WIP, throughput y calidad.
- No representa el tiempo total transcurrido desde que se solicita un elemento.
- No debe confundirse con la duración del Sprint.
- No debe utilizarse para comparar equipos sin considerar diferencias en sus procesos y tipos de trabajo.
- S12 debe identificarse como Sprint en curso y no compararse directamente con Sprints finalizados.

**Limitación de los datos DEMO:** el dataset contiene una mediana agregada por equipo y Sprint. No incluye las fechas individuales de inicio y finalización de cada elemento, por lo que no permite reconstruir ni recalcular la distribución individual del Cycle Time.

### 3.7 Lead Time

**Definición:** tiempo transcurrido desde que un elemento de trabajo es solicitado o registrado hasta que queda completado.

**Fórmula conceptual:**

Lead Time = Fecha y hora de finalización − Fecha y hora de solicitud o registro.

**Fuente:** `agile-delivery.csv`

**Campo disponible:** `lead_time_mediana_dias`.

**Unidad:** días.

**Agregación:** mediana del Lead Time de los elementos completados durante el Sprint.

**Interpretación:** permite evaluar el tiempo total que transcurre desde que surge una necesidad hasta que se entrega el resultado. Incluye tanto períodos de espera como períodos de ejecución activa.

**Consideraciones:**
- Incluye tiempos de espera, priorización y ejecución.
- Debe analizarse junto con Cycle Time, WIP y throughput.
- No debe confundirse con la duración del Sprint.
- Una reducción sostenida puede indicar una mejora en la capacidad de respuesta, siempre que se mantengan criterios comparables.
- No debe utilizarse para comparar equipos sin considerar sus procesos y tipos de trabajo.
- S12 debe identificarse como Sprint en curso y no compararse directamente con Sprints finalizados.

**Limitación de los datos DEMO:** el dataset contiene una mediana agregada por equipo y Sprint. No incluye las fechas individuales de solicitud y finalización de cada elemento, por lo que no permite reconstruir ni recalcular la distribución individual del Lead Time.

### 3.8 WIP (Work in Progress)

**Definición:** cantidad de elementos de trabajo que se encuentran iniciados y todavía no han sido completados en un momento determinado.

**Objetivo:** monitorear el volumen de trabajo en curso, identificar posibles situaciones de sobrecarga y analizar su relación con el flujo de entrega.

**Fórmula conceptual:**

\[
WIP = \text{Cantidad de elementos iniciados y no completados}
\]

**Campo disponible:** `wip_promedio`, del dataset `agile-delivery.csv`.

**Unidad de medida:** cantidad promedio de elementos en curso.

**Interpretación:**
- Un WIP elevado puede indicar acumulación de trabajo, sobrecarga o dificultades para finalizar elementos.
- Un WIP reducido puede favorecer la concentración y el flujo de entrega, siempre que exista suficiente trabajo disponible.
- Debe analizarse junto con Throughput, Cycle Time, impedimentos y capacidad del equipo.
- No existe un límite universal de WIP. Para evaluar si el nivel es adecuado, se necesita conocer la política o límite de trabajo en curso definido por el equipo.

**Consideraciones sobre los datos:**
- El dataset registra `wip_promedio` como un valor agregado por equipo y Sprint.
- No contiene registros diarios ni el historial de entrada y salida de cada elemento.
- Por lo tanto, no permite reconstruir la evolución diaria del WIP ni verificar cuánto tiempo permaneció cada elemento en curso.
- Las comparaciones entre equipos deben considerar sus características, capacidad y políticas de trabajo.
- El Sprint S12 está en curso y sus valores son parciales; no debe compararse directamente con Sprints finalizados.

**Fuente:** `agile-delivery.csv`.

**Tipo de dato:** DEMO.

### 3.9 Impedimentos (Impediments)

**Definición:** cantidad de obstáculos registrados durante un Sprint que dificultan o bloquean el avance del equipo.

**Objetivo:** monitorear las dificultades que afectan la ejecución del trabajo, identificar recurrencias y facilitar acciones de resolución o escalamiento.

**Fórmula conceptual:**

\[
\text{Impedimentos} = \text{Cantidad de impedimentos registrados durante el Sprint}
\]

**Campo disponible:** `impedimentos`, del dataset `agile-delivery.csv`.

**Unidad de medida:** cantidad de impedimentos por equipo y Sprint.

**Interpretación:**
- Un aumento puede señalar dependencias, problemas técnicos, decisiones pendientes o restricciones externas.
- Una disminución puede reflejar una mejor gestión de obstáculos, pero no necesariamente una mejora del flujo de entrega.
- Es importante analizar los impedimentos junto con Cycle Time, Lead Time, Carry-over y cumplimiento del Sprint Goal.
- La cantidad por sí sola no mide la gravedad, duración ni impacto de los impedimentos.

**Consideraciones sobre los datos:**
- El dataset registra una cantidad agregada de impedimentos por equipo y Sprint.
- No contiene detalle individual, fechas de apertura y resolución, responsable, severidad ni tiempo de bloqueo.
- Por lo tanto, no permite calcular el tiempo promedio de resolución ni identificar la antigüedad de los impedimentos.
- Para un análisis más completo se requiere un registro individual de impedimentos.
- El Sprint S12 está en curso y sus valores son parciales; no debe compararse directamente con Sprints finalizados.

**Fuente:** `agile-delivery.csv`.

**Tipo de dato:** DEMO.

### 3.10 Defectos (Defects)

**Definición:** cantidad de defectos registrados durante un Sprint, asociados a problemas de calidad identificados en los elementos de trabajo.

**Objetivo:** monitorear la calidad de los entregables, identificar tendencias y detectar posibles necesidades de mejora en los procesos de desarrollo y validación.

**Fórmula conceptual:**

\[
\text{Defectos} = \text{Cantidad de defectos registrados durante el Sprint}
\]

**Campo disponible:** `defectos`, del dataset `agile-delivery.csv`.

**Unidad de medida:** cantidad de defectos por equipo y Sprint.

**Interpretación:**
- Un aumento de defectos puede indicar problemas de calidad, validación insuficiente o mayor complejidad del trabajo.
- Una disminución puede reflejar mejoras en las prácticas de calidad, aunque debe analizarse junto con el volumen de trabajo entregado.
- Es importante observar su relación con Throughput, retrabajo y cumplimiento del Sprint Goal.
- La cantidad de defectos no permite determinar por sí sola la severidad ni el impacto sobre los usuarios o el negocio.

**Consideraciones sobre los datos:**
- El dataset registra una cantidad agregada de defectos por equipo y Sprint.
- No contiene identificación individual, severidad, fecha de detección, estado ni causa raíz de cada defecto.
- Por lo tanto, no permite calcular tasas de defectos por entrega, tiempos de resolución ni distribución por severidad.
- Para un análisis de calidad más completo se requiere un registro individual de defectos.
- El Sprint S12 está en curso y sus valores son parciales; no debe compararse directamente con Sprints finalizados.

**Fuente:** `agile-delivery.csv`.

**Tipo de dato:** DEMO.

### 3.11 Retrabajo (Rework)

**Definición:** cantidad de elementos de trabajo que requieren volver a ejecutarse, corregirse o modificarse debido a problemas detectados durante su desarrollo o validación.

**Objetivo:** identificar el esfuerzo adicional generado por correcciones y analizar su posible impacto en la capacidad y el flujo de entrega del equipo.

**Fórmula conceptual:**

\[
\text{Retrabajo} = \text{Cantidad de elementos registrados como retrabajo durante el Sprint}
\]

**Campo disponible:** `retrabajo_elementos`, del dataset `agile-delivery.csv`.

**Unidad de medida:** cantidad de elementos con retrabajo por equipo y Sprint.

**Interpretación:**
- Un aumento puede indicar problemas de calidad, requisitos poco claros, cambios de alcance o validaciones tardías.
- Una disminución puede reflejar mejoras en la calidad y estabilidad de los entregables.
- Debe analizarse junto con Defectos, Throughput, Cycle Time y cumplimiento del Sprint Goal.
- El retrabajo representa elementos afectados, no necesariamente horas de esfuerzo ni costo adicional.

**Consideraciones sobre los datos:**
- El dataset registra una cantidad agregada de elementos con retrabajo por equipo y Sprint.
- No contiene horas dedicadas, costo asociado, causa raíz ni identificación individual de los elementos.
- Por lo tanto, no permite calcular el esfuerzo o costo real del retrabajo ni establecer sus causas.
- No debe asumirse que cada defecto genera un elemento de retrabajo o que ambos indicadores tienen una relación directa.
- El Sprint S12 está en curso y sus valores son parciales; no debe compararse directamente con Sprints finalizados.

**Fuente:** `agile-delivery.csv`.

**Tipo de dato:** DEMO.

## 4. Entrega Técnica y DevOps — Métricas DORA

Las métricas DORA permiten observar el desempeño de la entrega de software desde la perspectiva de velocidad y estabilidad.

Se consideran cuatro indicadores:

1. Deployment Frequency.
2. Lead Time for Changes.
3. Change Failure Rate.
4. Failed Deployment Recovery Time.

Deben analizarse conjuntamente y por servicio o aplicación cuando la información lo permita.

### 4.1 Deployment Frequency (Frecuencia de Despliegue)

**Definición:** frecuencia con la que un servicio realiza despliegues exitosos en un entorno productivo durante un período determinado.

**Objetivo:** monitorear la capacidad de los equipos para entregar cambios de software en producción de manera frecuente y sostenida.

**Fórmula:**

\[
\text{Deployment Frequency} =
\frac{\text{Cantidad de despliegues exitosos en producción}}{\text{Período de medición}}
\]

**Campos disponibles:** `fecha_despliegue`, `servicio`, `entorno` y `estado_despliegue`, del dataset `deployments.csv`.

**Unidad de medida:** despliegues exitosos por servicio y período.

**Criterio de cálculo:**
- Considerar únicamente despliegues en producción.
- Contabilizar como exitosos aquellos cuyo estado indique que finalizaron correctamente.
- Excluir los despliegues fallidos del numerador.
- Definir y mantener un período de medición consistente para facilitar el análisis de tendencias.

**Interpretación:**
- Una mayor frecuencia puede reflejar una capacidad de entrega más continua.
- Una menor frecuencia puede estar relacionada con ciclos de liberación extensos, dependencias o procesos de aprobación.
- Debe analizarse junto con Lead Time for Changes, Change Failure Rate y Failed Deployment Recovery Time.
- Una frecuencia elevada no implica automáticamente mayor calidad ni mayor valor de negocio.

**Consideraciones sobre los datos:**
- El dataset contiene 48 registros de despliegues correspondientes a cuatro servicios.
- Los registros corresponden a despliegues en producción entre junio y septiembre de 2026.
- Se identifican siete despliegues fallidos.
- `fecha_despliegue` contiene únicamente la fecha, sin hora de ejecución.
- Por lo tanto, permite calcular frecuencias por día, semana o mes, pero no analizar horarios ni intervalos precisos entre despliegues.
- Los resultados deben calcularse por servicio y período, evitando comparar servicios con contextos de entrega diferentes.

**Fuente:** `deployments.csv`.

**Tipo de dato:** DEMO.

### 4.2 Lead Time for Changes (Tiempo de Entrega de Cambios)

**Definición:** tiempo transcurrido desde que un cambio de código se confirma en el sistema de control de versiones hasta que queda desplegado en producción.

**Objetivo:** medir la velocidad del proceso de entrega de software e identificar demoras entre la incorporación de cambios y su disponibilidad en producción.

**Fórmula conceptual:**

\[
\text{Lead Time for Changes} =
\text{Fecha y hora del despliegue en producción}
-
\text{Fecha y hora del commit}
\]

**Campo disponible:** `lead_time_cambios_horas`, del dataset `deployments.csv`.

**Unidad de medida:** horas por cambio desplegado.

**Criterio de cálculo:**
- En una medición DORA estricta, se requiere la marca de tiempo del commit y la marca de tiempo del despliegue correspondiente en producción.
- El indicador debe calcularse sobre cambios efectivamente desplegados.
- Para analizar la tendencia, se recomienda utilizar la mediana del período, evitando que unos pocos valores extremos distorsionen la interpretación.

**Interpretación:**
- Un Lead Time menor puede reflejar un flujo de entrega más ágil y menos esperas entre etapas.
- Un aumento puede señalar demoras en revisiones, pruebas, aprobaciones, integración o despliegue.
- Debe analizarse junto con Deployment Frequency, Change Failure Rate y Failed Deployment Recovery Time.
- Un Lead Time reducido no garantiza por sí solo calidad ni valor de negocio.

**Consideraciones sobre los datos:**
- El dataset contiene el campo `lead_time_cambios_horas`, expresado en horas.
- No dispone de fechas y horas individuales de commit ni de despliegue.
- Por lo tanto, no es posible recalcular ni verificar el indicador mediante su fórmula DORA estricta.
- El valor disponible debe tratarse como una aproximación DEMO y no como una medición DORA validada.
- Para una medición rigurosa se requiere integrar información de control de versiones y despliegues, con marcas de tiempo correlacionables por cambio.

**Fuente:** `deployments.csv`.

**Tipo de dato:** DEMO — aproximación, no medición DORA estricta.

### 4.3 Change Failure Rate (Tasa de Fallos de Cambios)

**Definición:** porcentaje de despliegues en producción que generan fallos y requieren una intervención correctiva, como una reversión, hotfix o recuperación del servicio.

**Objetivo:** evaluar la estabilidad y calidad del proceso de entrega de software, identificando qué proporción de los cambios desplegados genera problemas en producción.

**Fórmula:**

\[
CFR =
\frac{\text{Despliegues fallidos en producción}}
{\text{Total de despliegues en producción}}
\times 100
\]

**Campos disponibles:** `fallo_cambio`, `estado_despliegue`, `entorno` e `incidente_id`, del dataset `deployments.csv`.

**Unidad de medida:** porcentaje (%).

**Criterio de cálculo:**
- Considerar únicamente despliegues en producción.
- Identificar los despliegues fallidos mediante el campo `fallo_cambio` y validar su correspondencia con `estado_despliegue`.
- Dividir la cantidad de despliegues fallidos por el total de despliegues del período.
- Expresar el resultado como porcentaje.
- Mantener un período de medición consistente para analizar tendencias.

**Ejemplo con datos DEMO:**

\[
CFR = \frac{7}{48}\times100 = 14,58\%
\]

**Interpretación:**
- Un CFR elevado puede indicar problemas de calidad, pruebas insuficientes, cambios de alto riesgo o debilidades en los controles de despliegue.
- Una disminución sostenida puede reflejar mejoras en las prácticas de validación y estabilidad de las entregas.
- Debe analizarse junto con Deployment Frequency, Lead Time for Changes y Failed Deployment Recovery Time.
- Una tasa baja no garantiza ausencia de incidentes ni demuestra por sí sola la calidad del producto.

**Consideraciones sobre los datos:**
- El dataset contiene 48 despliegues en producción correspondientes a cuatro servicios.
- Se identifican siete despliegues fallidos.
- El CFR calculado para el conjunto de datos es 14,58%.
- Los siete despliegues fallidos están asociados a identificadores de incidentes en `incidents.csv`.
- La clasificación de fallo se basa en los campos disponibles en el dataset DEMO; no se dispone de evidencia detallada sobre reversión, hotfix o intervención requerida para cada caso.
- Por lo tanto, el resultado debe interpretarse como una aproximación DEMO de Change Failure Rate, no como una medición DORA validada mediante registros operacionales completos.

**Fuente:** `deployments.csv`, con referencias cruzadas a `incidents.csv`.

**Tipo de dato:** DEMO — aproximación basada en despliegues fallidos registrados.

### 4.4 Failed Deployment Recovery Time (Tiempo de Recuperación ante Fallos de Despliegue)

**Definición:** tiempo transcurrido desde que se detecta el impacto de un despliegue fallido hasta que el servicio afectado recupera su funcionamiento.

**Objetivo:** evaluar la capacidad de los equipos para responder y recuperar servicios después de fallos asociados a cambios desplegados en producción.

**Fórmula conceptual:**

\[
\text{Recovery Time} =
\text{Fecha y hora de recuperación}
-
\text{Fecha y hora de detección del impacto}
\]

**Campos disponibles:** `tiempo_recuperacion_minutos`, `fecha_deteccion`, `fecha_recuperacion` y `deployment_id`, del dataset `incidents.csv`.

**Unidad de medida:** minutos.

**Criterio de cálculo:**
- Considerar incidentes asociados a despliegues fallidos en producción.
- Utilizar `fecha_deteccion` como referencia de inicio del impacto en este modelo DEMO.
- Utilizar `fecha_recuperacion` como referencia de restablecimiento del servicio.
- Calcular el tiempo transcurrido entre ambos momentos.
- Para analizar el comportamiento del indicador, se recomienda utilizar la mediana y observar también los casos de mayor duración.

**Interpretación:**
- Un tiempo menor puede reflejar una mayor capacidad de respuesta y recuperación.
- Un aumento puede señalar dificultades en diagnóstico, coordinación, reversión, corrección o validación del servicio.
- Debe analizarse junto con Change Failure Rate, Deployment Frequency y Lead Time for Changes.
- Una recuperación rápida no significa necesariamente que se haya identificado y eliminado la causa raíz.

**Consideraciones sobre los datos:**
- El dataset `incidents.csv` contiene 15 incidentes resueltos.
- Siete incidentes están relacionados con despliegues fallidos mediante `deployment_id`.
- Para este indicador DORA se consideran únicamente esos siete incidentes asociados a despliegues fallidos.
- `tiempo_recuperacion_minutos` representa el intervalo entre detección y recuperación, no desde la apertura del incidente.
- Los valores de recuperación de los siete incidentes relacionados coinciden con los registrados en `deployments.csv`.
- El modelo utiliza `fecha_deteccion` como aproximación al inicio del impacto; se debe validar este criterio con los registros operacionales en una implementación real.
- No debe confundirse con el MTTR operacional, que considera la población de incidentes recuperados y utiliza un alcance distinto.

**Fuente:** `incidents.csv`, con referencias cruzadas a `deployments.csv`.

**Tipo de dato:** DEMO — aproximación basada en incidentes asociados a despliegues fallidos.

## 5. Cloud Monitoring & Observability

Este módulo permite observar la salud técnica y el comportamiento de los servicios desplegados en infraestructura cloud.

### 5.1 Disponibilidad (Availability)

**Definición:** porcentaje del tiempo en que un servicio estuvo operativo y accesible durante un período de medición.

**Objetivo:** monitorear la continuidad de los servicios cloud e identificar degradaciones que puedan afectar su operación.

**Fórmula conceptual:**

\[
\text{Disponibilidad (\%)} =
\frac{\text{Tiempo disponible}}
{\text{Tiempo total de medición}}
\times 100
\]

**Campo disponible:** `disponibilidad_pct`, del dataset `cloud-monitoring.csv`.

**Unidad de medida:** porcentaje (%).

**Criterio de cálculo:**
- Utilizar el porcentaje de disponibilidad registrado para cada servicio y período.
- Mantener una ventana de medición consistente.
- Para calcular disponibilidad desde eventos operacionales, se requieren registros de tiempo disponible e indisponibilidad.
- No asumir que el porcentaje registrado puede reconstruirse sin esos eventos.

**Interpretación:**
- Una disponibilidad elevada indica mayor continuidad operacional durante el período observado.
- Una disminución puede señalar interrupciones, degradaciones o problemas de infraestructura o aplicación.
- Debe analizarse junto con incidentes, SLA, latencia y tasa de errores.
- La disponibilidad no equivale a ausencia de incidentes: pueden existir incidentes sin interrupción total del servicio.

**Consideraciones sobre los datos:**
- El dataset contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- `disponibilidad_pct` es un valor agregado por servicio y corte semanal.
- No se dispone de eventos individuales de caída, duración de interrupciones ni ventanas de mantenimiento.
- Por lo tanto, no es posible recalcular ni auditar la disponibilidad desde eventos de monitoreo.
- Los valores deben interpretarse como datos DEMO agregados, no como mediciones verificadas de una plataforma cloud real.

**Fuente:** `cloud-monitoring.csv`.

**Tipo de dato:** DEMO.

### 5.2 Latencia p95 (Percentil 95 de Latencia)

**Definición:** tiempo de respuesta por debajo del cual se completa el 95% de las solicitudes observadas durante un período de medición.

**Objetivo:** monitorear el rendimiento y la capacidad de respuesta de los servicios, identificando degradaciones que pueden no ser visibles al analizar únicamente el promedio.

**Fórmula conceptual:**

\[
p95 = \text{Percentil 95 de los tiempos de respuesta registrados}
\]

**Campo disponible:** `latencia_p95_ms`, del dataset `cloud-monitoring.csv`.

**Unidad de medida:** milisegundos (ms).

**Criterio de cálculo:**
- Utilizar los tiempos de respuesta individuales registrados durante la ventana de medición.
- Ordenar las observaciones de menor a mayor.
- Calcular el percentil 95 según el método estadístico definido por la herramienta de monitoreo.
- Si se utiliza un valor p95 previamente agregado, conservar la definición y ventana de medición de su fuente.

**Interpretación:**
- Una latencia p95 menor generalmente indica una mejor capacidad de respuesta para la mayoría de las solicitudes.
- Un aumento puede señalar saturación de recursos, consultas lentas, dependencias externas o problemas de red.
- Debe analizarse junto con disponibilidad, tasa de errores, CPU, memoria y tráfico.
- El p95 no representa el tiempo máximo ni el promedio de respuesta: aproximadamente el 5% de las solicitudes puede superar ese valor.

**Consideraciones sobre los datos:**
- El dataset contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- `latencia_p95_ms` representa un valor agregado por servicio y corte semanal.
- No se dispone de los tiempos de respuesta individuales que originaron cada percentil.
- Por lo tanto, no es posible recalcular el p95 ni verificar su distribución estadística a partir del dataset disponible.
- Los valores deben interpretarse como datos DEMO agregados, no como mediciones verificadas de una plataforma de observabilidad real.

**Fuente:** `cloud-monitoring.csv`.

**Tipo de dato:** DEMO.

### 5.3 Tasa de Errores (Error Rate)

**Definición:** porcentaje de solicitudes que generan errores respecto del total de solicitudes procesadas por un servicio durante un período determinado.

**Objetivo:** monitorear la estabilidad de los servicios y detectar problemas que puedan afectar la experiencia de los usuarios o la continuidad operacional.

**Fórmula:**

\[
\text{Error Rate (\%)} =
\frac{\text{Cantidad de solicitudes con error}}
{\text{Total de solicitudes procesadas}}
\times 100
\]

**Campo disponible:** `tasa_errores_pct`, del dataset `cloud-monitoring.csv`.

**Unidad de medida:** porcentaje (%).

**Criterio de cálculo:**
- Considerar las solicitudes procesadas durante una ventana de medición definida.
- Identificar las solicitudes que terminaron en error según los criterios de la plataforma de monitoreo.
- Dividir las solicitudes con error por el total de solicitudes procesadas.
- Mantener una clasificación consistente de errores y una ventana de medición comparable.

**Interpretación:**
- Una tasa de errores elevada puede indicar fallos de aplicación, problemas de integración, dependencias no disponibles o saturación de recursos.
- Un aumento sostenido puede anticipar degradaciones del servicio.
- Debe analizarse junto con latencia p95, disponibilidad, incidentes y alertas críticas.
- Una tasa baja no garantiza que el servicio esté completamente libre de problemas; también deben considerarse la severidad y el impacto de los errores.

**Consideraciones sobre los datos:**
- El dataset contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- `tasa_errores_pct` representa un valor agregado por servicio y corte semanal.
- No se dispone del número total de solicitudes ni del detalle individual de solicitudes exitosas y fallidas.
- Por lo tanto, no es posible recalcular ni auditar la tasa de errores a partir de los datos disponibles.
- Los valores deben interpretarse como datos DEMO agregados, no como mediciones verificadas de una plataforma de observabilidad real.

**Fuente:** `cloud-monitoring.csv`.

**Tipo de dato:** DEMO.

### 5.4 Utilización de CPU (CPU Utilization)

**Definición:** porcentaje promedio de capacidad de procesamiento utilizada por un recurso o servicio durante un período de medición.

**Objetivo:** monitorear el consumo de recursos de procesamiento, identificar posibles situaciones de saturación y anticipar necesidades de optimización o escalabilidad de infraestructura.

**Fórmula conceptual:**

\[
\text{CPU Utilization (\%)} =
\frac{\text{Capacidad de CPU utilizada}}
{\text{Capacidad total de CPU disponible}}
\times 100
\]

**Campo disponible:** `cpu_promedio_pct`, del dataset `cloud-monitoring.csv`.

**Unidad de medida:** porcentaje promedio (%).

**Criterio de cálculo:**
- Utilizar las mediciones de utilización de CPU registradas durante la ventana de monitoreo.
- Calcular el promedio de utilización correspondiente al período.
- Mantener una ventana de medición consistente para analizar tendencias.
- Considerar la capacidad asignada al recurso y su configuración de escalabilidad.

**Interpretación:**
- Una utilización elevada y sostenida puede indicar saturación o necesidad de ampliar la capacidad disponible.
- Una utilización muy baja puede representar capacidad ociosa y oportunidades de optimización de costos.
- Las variaciones puntuales deben analizarse en contexto, considerando la demanda y los patrones de carga.
- Debe analizarse junto con memoria, latencia p95, tasa de errores y tráfico.
- Un porcentaje elevado no implica necesariamente un problema si el servicio mantiene sus objetivos de rendimiento y disponibilidad.

**Consideraciones sobre los datos:**
- El dataset contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- `cpu_promedio_pct` representa un valor promedio agregado por servicio y corte semanal.
- No se dispone de mediciones individuales, máximos, mínimos ni series temporales de utilización.
- Por lo tanto, no es posible identificar picos de consumo ni reconstruir la evolución de CPU dentro de cada semana.
- Los valores deben interpretarse como datos DEMO agregados, no como mediciones verificadas de una plataforma cloud real.

**Fuente:** `cloud-monitoring.csv`.

**Tipo de dato:** DEMO.

### 5.5 Utilización de Memoria (Memory Utilization)

**Definición:** porcentaje promedio de memoria utilizada respecto de la memoria total disponible en un recurso de infraestructura durante un período de medición.

**Objetivo:** monitorear el consumo de memoria, identificar posibles situaciones de presión o saturación y anticipar necesidades de optimización o ampliación de capacidad.

**Fórmula conceptual:**

\[
\text{Memory Utilization (\%)} =
\frac{\text{Memoria utilizada}}
{\text{Memoria total disponible}}
\times 100
\]

**Campo disponible:** `memoria_promedio_pct`, del dataset `cloud-monitoring.csv`.

**Unidad de medida:** porcentaje promedio (%).

**Criterio de cálculo:**
- Utilizar las mediciones de memoria registradas durante la ventana de monitoreo.
- Calcular el promedio de utilización correspondiente al período.
- Mantener una ventana de medición consistente para analizar tendencias.
- Considerar la memoria asignada al recurso y las características de la carga de trabajo.

**Interpretación:**
- Una utilización elevada y sostenida puede indicar presión de memoria o riesgo de degradación del servicio.
- Una utilización baja puede representar capacidad disponible, aunque debe evaluarse según la demanda y los requerimientos de la aplicación.
- Los aumentos repentinos pueden estar relacionados con cambios en la carga, procesos intensivos o posibles fugas de memoria.
- Debe analizarse junto con CPU, latencia p95, tasa de errores y disponibilidad.
- Un porcentaje elevado no implica necesariamente una falla si el servicio mantiene un comportamiento estable y cumple sus objetivos operacionales.

**Consideraciones sobre los datos:**
- El dataset contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- `memoria_promedio_pct` representa un valor promedio agregado por servicio y corte semanal.
- No se dispone de mediciones individuales, máximos, mínimos ni series temporales de utilización.
- Por lo tanto, no es posible identificar picos de consumo ni reconstruir la evolución de memoria dentro de cada semana.
- Los valores deben interpretarse como datos DEMO agregados, no como mediciones verificadas de una plataforma cloud real.

**Fuente:** `cloud-monitoring.csv`.

**Tipo de dato:** DEMO.

### 5.6 Utilización de Almacenamiento (Storage Utilization)

**Definición:** porcentaje de capacidad de almacenamiento utilizada respecto de la capacidad total disponible en un recurso durante un período de medición.

**Objetivo:** monitorear el consumo de almacenamiento, identificar tendencias de crecimiento y anticipar necesidades de ampliación, limpieza u optimización de capacidad.

**Fórmula conceptual:**

\[
\text{Storage Utilization (\%)} =
\frac{\text{Espacio de almacenamiento utilizado}}
{\text{Capacidad total de almacenamiento disponible}}
\times 100
\]

**Campo disponible:** `almacenamiento_usado_pct`, del dataset `cloud-monitoring.csv`.

**Unidad de medida:** porcentaje (%).

**Criterio de cálculo:**
- Utilizar las mediciones de espacio ocupado y capacidad total disponible.
- Calcular el porcentaje de utilización correspondiente al período.
- Mantener una ventana de medición consistente para analizar tendencias.
- Considerar la capacidad asignada, las políticas de retención y los requerimientos de crecimiento.

**Interpretación:**
- Una utilización elevada y sostenida puede anticipar riesgos de agotamiento de espacio.
- Un crecimiento continuo puede indicar la necesidad de ampliar capacidad o revisar políticas de almacenamiento y retención.
- Una utilización baja puede representar capacidad disponible, aunque debe evaluarse junto con la demanda proyectada y el costo asociado.
- Debe analizarse junto con costos cloud, tráfico y comportamiento de los servicios.
- Un porcentaje elevado no implica necesariamente una falla si existe capacidad suficiente y una planificación adecuada.

**Consideraciones sobre los datos:**
- El dataset contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- `almacenamiento_usado_pct` representa un valor agregado por servicio y corte semanal.
- No se dispone de la capacidad total en GB o TB ni del volumen de almacenamiento utilizado.
- Por lo tanto, no es posible determinar el espacio absoluto disponible ni proyectar una fecha de agotamiento de capacidad.
- Los valores deben interpretarse como datos DEMO agregados, no como mediciones verificadas de una plataforma cloud real.

**Fuente:** `cloud-monitoring.csv`.

**Tipo de dato:** DEMO.

### 5.7 Tráfico de Red (Network Traffic)

**Definición:** volumen de datos transferidos hacia y desde los servicios alojados en infraestructura cloud durante un período determinado.

**Objetivo:** monitorear el consumo de red, identificar variaciones en los patrones de tráfico y evaluar su posible impacto en el rendimiento y los costos de infraestructura.

**Fórmulas conceptuales:**

\[
\text{Tráfico total} =
\text{Tráfico de entrada} + \text{Tráfico de salida}
\]

\[
\text{Variación del tráfico (\%)} =
\frac{\text{Tráfico período actual} - \text{Tráfico período anterior}}
{\text{Tráfico período anterior}}
\times 100
\]

**Campos disponibles:**
- `trafico_entrada_gb`: volumen de datos recibidos.
- `trafico_salida_gb`: volumen de datos enviados.

Ambos campos pertenecen al dataset `cloud-monitoring.csv`.

**Unidad de medida:** GB/semana para cada tipo de tráfico y para el volumen total semanal.

**Criterio de cálculo:**
- Considerar los volúmenes de entrada y salida registrados durante cada período semanal.
- Calcular el tráfico total sumando ambos valores.
- Comparar períodos equivalentes para identificar tendencias.
- Mantener la misma unidad y ventana de medición.

**Interpretación:**
- Un aumento del tráfico puede estar relacionado con mayor demanda, crecimiento de usuarios, transferencias de archivos o integración entre servicios.
- Un aumento sostenido del tráfico de salida puede tener impacto en los costos de transferencia de datos cloud.
- Una disminución puede reflejar menor demanda o cambios en los patrones de consumo; no necesariamente representa una mejora.
- Debe analizarse junto con disponibilidad, latencia, tasa de errores y costos cloud.
- Las variaciones deben interpretarse considerando la demanda y el comportamiento esperado de cada servicio.

**Consideraciones sobre los datos:**
- El dataset contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- `trafico_entrada_gb` y `trafico_salida_gb` representan volúmenes semanales, expresados en GB/semana.
- Esta interpretación corresponde a una convención definida para el modelo DEMO; no ha sido validada contra registros reales de una plataforma cloud.
- No se dispone del detalle de transferencias individuales, destinos, regiones, zonas o tipos de tráfico.
- Por lo tanto, no es posible identificar transferencias específicas ni determinar su costo real.
- Los valores deben interpretarse como datos DEMO agregados.

**Fuente:** `cloud-monitoring.csv`.

**Tipo de dato:** DEMO.

### 5.8 Costo Cloud (Cloud Cost)

**Definición:** costo asociado al consumo de recursos y servicios de infraestructura cloud durante un período determinado.

**Objetivo:** monitorear la evolución del gasto cloud, identificar variaciones relevantes y detectar oportunidades de optimización financiera sin comprometer el rendimiento ni la disponibilidad de los servicios.

**Fórmula conceptual:**

\[
\text{Costo Cloud} =
\sum \text{Costos de los recursos y servicios cloud del período}
\]

**Campo disponible:** `costo_cloud_usd`, del dataset `cloud-monitoring.csv`.

**Unidad de medida:** USD/semana.

**Criterio de cálculo:**
- Considerar los costos asociados a los recursos y servicios cloud durante el período semanal.
- Mantener una moneda y ventana de medición consistentes.
- Comparar períodos equivalentes para identificar tendencias y variaciones.
- Para un análisis financiero completo, integrar los costos por servicio, recurso, ambiente y categoría de consumo.

**Interpretación:**
- Un aumento puede estar relacionado con mayor consumo, crecimiento de la demanda, ampliación de infraestructura o cambios en los precios de los servicios.
- Una disminución puede reflejar optimización de recursos, menor demanda o cambios en el consumo.
- Debe analizarse junto con tráfico de red, utilización de CPU, memoria, almacenamiento y demanda de los servicios.
- La reducción de costos no debe evaluarse de manera aislada: debe conservarse el nivel de servicio y los objetivos de disponibilidad y rendimiento.
- El análisis puede apoyar iniciativas de FinOps, como dimensionamiento adecuado de recursos, identificación de capacidad ociosa y control presupuestario.

**Consideraciones sobre los datos:**
- El dataset contiene 20 registros correspondientes a cuatro servicios y cinco cortes semanales de septiembre de 2026.
- `costo_cloud_usd` representa un costo semanal por servicio, expresado en USD/semana.
- Esta interpretación corresponde a una convención definida para el modelo DEMO; no ha sido validada contra facturación real de un proveedor cloud.
- No se dispone del desglose por recurso, tipo de instancia, almacenamiento, transferencia, región ni descuentos aplicados.
- Por lo tanto, no es posible identificar los componentes específicos del gasto ni verificar el costo facturado.
- Los valores deben interpretarse como datos DEMO agregados, no como costos reales de AWS, Azure o Google Cloud.

**Fuente:** `cloud-monitoring.csv`.

**Tipo de dato:** DEMO.

## 6. IT Service Operations

Este módulo permite evaluar la gestión de incidentes, recuperación del servicio y cumplimiento de acuerdos de nivel de servicio.

### 6.1 Volumen de Incidentes (Incident Volume)

**Definición:** cantidad de incidentes registrados durante un período determinado, independientemente de su severidad o causa.

**Objetivo:** monitorear la demanda operacional, identificar tendencias y detectar posibles aumentos en las interrupciones o degradaciones de los servicios TI.

**Fórmula:**

\[
\text{Volumen de Incidentes} =
\text{Cantidad de incidentes registrados durante el período}
\]

**Campo disponible:** `incidente_id`, del dataset `incidents.csv`.

**Unidad de medida:** cantidad de incidentes por período.

**Criterio de cálculo:**
- Contabilizar cada incidente una sola vez.
- Agrupar los incidentes según su fecha de apertura.
- Definir períodos consistentes para analizar tendencias.
- Segmentar los resultados por servicio, severidad, categoría u origen cuando la información esté disponible.

**Interpretación:**
- Un aumento puede indicar mayor inestabilidad, crecimiento de la demanda o cambios en la capacidad de detección y registro.
- Una disminución puede reflejar mejoras operacionales, aunque también podría estar relacionada con cambios en los criterios de registro.
- Debe analizarse junto con MTTR, cumplimiento de SLA, disponibilidad y severidad.
- El volumen por sí solo no representa el impacto operacional: un incidente crítico puede ser más relevante que varios incidentes menores.

**Consideraciones sobre los datos:**
- El dataset contiene 15 incidentes registrados entre junio y septiembre de 2026.
- Todos los incidentes disponibles figuran como resueltos.
- El conjunto de datos permite analizar el volumen histórico registrado, pero no representa necesariamente la totalidad de los incidentes de una operación real.
- No contiene una fotografía de incidentes abiertos al momento del corte.
- Los resultados deben interpretarse como datos DEMO y no como evidencia de desempeño operacional real.

**Fuente:** `incidents.csv`.

**Tipo de dato:** DEMO.

### 6.2 MTTR (Mean Time to Recover)

**Definición:** tiempo promedio transcurrido desde la apertura de un incidente hasta la recuperación del servicio afectado.

**Objetivo:** evaluar la capacidad de respuesta y recuperación operacional, identificando oportunidades para reducir los tiempos de interrupción y mejorar la continuidad de los servicios.

**Fórmula:**

\[
MTTR =
\frac{\sum \text{Tiempos de resolución de incidentes recuperados}}
{\text{Cantidad de incidentes recuperados}}
\]

**Campo disponible:** `tiempo_resolucion_minutos`, del dataset `incidents.csv`.

**Unidad de medida:** minutos.

**Criterio de cálculo:**
- Considerar los incidentes cuyo servicio haya sido recuperado.
- Utilizar el tiempo transcurrido desde `fecha_apertura` hasta `fecha_recuperacion`.
- Calcular el promedio de los tiempos de resolución de los incidentes incluidos en el período.
- Mantener criterios consistentes de inicio y término para facilitar la comparación histórica.

**Interpretación:**
- Un MTTR menor puede reflejar una mayor capacidad de respuesta y resolución operacional.
- Un aumento puede indicar dificultades de diagnóstico, escalamiento, coordinación o recuperación.
- Debe analizarse junto con volumen de incidentes, severidad, cumplimiento de SLA y disponibilidad.
- Un promedio puede ocultar incidentes de larga duración; conviene complementar el análisis con mediana y segmentación por severidad.
- Una recuperación rápida no implica necesariamente que se haya eliminado la causa raíz.

**Consideraciones sobre los datos:**
- El dataset contiene 15 incidentes y todos figuran como resueltos.
- `tiempo_resolucion_minutos` representa el intervalo entre `fecha_apertura` y `fecha_recuperacion`.
- Para este modelo, el MTTR operacional considera los incidentes recuperados, independientemente de si están relacionados con despliegues.
- No debe confundirse con Failed Deployment Recovery Time de DORA, que considera únicamente incidentes asociados a despliegues fallidos y utiliza `fecha_deteccion` como inicio del impacto.
- El conjunto de datos no incluye incidentes abiertos ni permite analizar tiempos de recuperación pendientes.
- Los resultados deben interpretarse como datos DEMO y no como evidencia de desempeño operacional real.

**Fuente:** `incidents.csv`.

**Tipo de dato:** DEMO.

### 6.3 Tiempo de recuperación DORA versus MTTR operacional

Ambos indicadores miden tiempos relacionados con la recuperación, pero no representan la misma población ni necesariamente el mismo punto de inicio.

| Característica | Recovery Time DORA | MTTR operacional |
|---|---|---|
| Población | Incidentes relacionados con despliegues fallidos | Incidentes operacionales evaluados |
| Inicio | Detección del impacto | Apertura del incidente |
| Término | Recuperación del servicio | Recuperación del servicio |
| Fuente | Deployments e incidents | Incidents |
| Propósito | Medir recuperación ante fallos de cambios | Medir desempeño de recuperación operacional |

**Importante:** no deben mezclarse ambos resultados en un único indicador, porque sus criterios de inicio y población son diferentes.

### 6.4 Cumplimiento de SLA (SLA Compliance)

**Definición:** porcentaje de incidentes elegibles que fueron resueltos dentro del tiempo objetivo establecido en el Service Level Agreement (SLA).

**Objetivo:** monitorear el cumplimiento de los compromisos de servicio, identificar desviaciones y apoyar decisiones de mejora en la gestión operacional.

**Fórmula:**

\[
\text{SLA Compliance (\%)} =
\frac{\text{Incidentes elegibles que cumplen el SLA}}
{\text{Total de incidentes elegibles}}
\times 100
\]

**Campos disponibles:** `sla_cumplido`, `tiempo_resolucion_minutos` y `sla_objetivo_minutos`, del dataset `incidents.csv`.

**Unidad de medida:** porcentaje (%).

**Criterio de cálculo:**
- Considerar los incidentes elegibles para evaluación de SLA.
- Comparar `tiempo_resolucion_minutos` con `sla_objetivo_minutos`.
- Contabilizar como cumplidos aquellos incidentes cuyo tiempo de resolución sea menor o igual al objetivo establecido.
- Dividir los incidentes cumplidos por el total de incidentes elegibles.
- Mantener criterios de elegibilidad y períodos de medición consistentes.

**Interpretación:**
- Un porcentaje elevado indica mayor cumplimiento de los compromisos de servicio.
- Una disminución puede señalar problemas de capacidad, tiempos de respuesta, escalamiento o complejidad de los incidentes.
- Debe analizarse junto con volumen de incidentes, MTTR, severidad y disponibilidad.
- Un resultado global puede ocultar incumplimientos concentrados en servicios o incidentes críticos.

**Consideraciones sobre los datos:**
- El dataset contiene 15 incidentes y todos figuran como resueltos.
- `sla_cumplido` registra el resultado del cumplimiento para cada incidente.
- La evaluación utiliza `tiempo_resolucion_minutos`, calculado desde `fecha_apertura` hasta `fecha_recuperacion`.
- `sla_objetivo_minutos` representa el tiempo objetivo de resolución definido para cada incidente.
- No se dispone de contratos SLA reales ni de reglas de elegibilidad adicionales.
- Por lo tanto, el indicador representa la convención del modelo DEMO y no evidencia de cumplimiento contractual real.

**Fuente:** `incidents.csv`.

**Tipo de dato:** DEMO.

### 6.5 Incidentes Críticos (Critical Incidents)

**Definición:** cantidad de incidentes clasificados con severidad crítica durante un período determinado.

**Objetivo:** identificar eventos de alto impacto que requieren atención prioritaria, coordinación entre equipos y, cuando corresponda, escalamiento a niveles de gestión.

**Fórmula:**

\[
\text{Incidentes Críticos} =
\text{Cantidad de incidentes con severidad crítica}
\]

**Campos disponibles:** `incidente_id`, `severidad` y `fecha_apertura`, del dataset `incidents.csv`.

**Unidad de medida:** cantidad de incidentes críticos por período.

**Criterio de cálculo:**
- Identificar los incidentes cuya clasificación de severidad corresponda a crítica.
- Contabilizar cada incidente una sola vez.
- Agruparlos según su fecha de apertura.
- Mantener criterios de clasificación consistentes durante el período de análisis.

**Interpretación:**
- Un aumento puede indicar mayor exposición a riesgos operacionales o problemas relevantes en los servicios.
- Una disminución puede reflejar mejoras en estabilidad y prevención, aunque también debe verificarse que los criterios de clasificación no hayan cambiado.
- Debe analizarse junto con disponibilidad, MTTR, cumplimiento de SLA y servicios afectados.
- La cantidad no representa por sí sola el impacto económico, duración ni alcance de cada incidente.

**Consideraciones sobre los datos:**
- El dataset contiene 15 incidentes registrados entre junio y septiembre de 2026.
- El campo `severidad` permite segmentar los incidentes por nivel de criticidad.
- No se dispone de una valoración cuantitativa del impacto económico, cantidad de usuarios afectados ni pérdida de negocio.
- Por lo tanto, el indicador permite monitorear el volumen de incidentes críticos, pero no cuantificar su impacto total.
- Los resultados deben interpretarse como datos DEMO y no como evidencia de desempeño operacional real.

**Fuente:** `incidents.csv`.

**Tipo de dato:** DEMO.

## 7. Reglas de Gobierno, Calidad y Trazabilidad de Indicadores

### 7.1 Clasificación de los datos

Todos los indicadores deben identificar claramente el origen y la naturaleza de la información utilizada.

- **DEMO:** datos ficticios utilizados para demostrar el funcionamiento del modelo.
- **REAL:** datos provenientes de sistemas o fuentes operacionales verificables.
- **PENDIENTE DE VALIDACIÓN:** información cuyo origen, consistencia o exactitud todavía no ha sido comprobada.

Los datos DEMO no deben presentarse como resultados reales de organizaciones o clientes.

### 7.2 Trazabilidad de los indicadores

Cada indicador debe permitir identificar:

- Nombre y definición.
- Objetivo de medición.
- Fórmula o criterio de cálculo.
- Unidad de medida.
- Dataset y campos de origen.
- Período de medición.
- Responsable de seguimiento.
- Limitaciones y supuestos conocidos.

### 7.3 Calidad y consistencia de los datos

Antes de utilizar un indicador en un análisis ejecutivo se debe verificar:

- Integridad de los registros.
- Consistencia de fechas y períodos.
- Ausencia de duplicados.
- Correspondencia entre identificadores relacionados.
- Unidades de medida.
- Coherencia entre numeradores y denominadores.
- Identificación de datos faltantes o no validados.

### 7.4 Tratamiento de datos faltantes

Cuando no exista información suficiente para calcular un indicador, se debe utilizar una clasificación explícita:

- **Sin dato:** no existe información disponible.
- **No medido:** la fuente no registra el indicador requerido.
- **Pendiente de validación:** existe información, pero no se ha confirmado su calidad.
- **No aplica:** el indicador no corresponde al contexto analizado.

No se deben sustituir datos faltantes por cero ni generar resultados estimados sin identificar explícitamente el supuesto utilizado.

### 7.5 Interpretación y uso ejecutivo

Los indicadores deben interpretarse considerando el contexto operacional, el período de medición y las características de cada equipo o servicio.

Se deben respetar los siguientes principios:

- Diferenciar Output de Outcome.
- No interpretar Velocity como una medida de productividad comparable entre equipos.
- No asumir causalidad a partir de correlaciones.
- No interpretar Deployment Frequency como una medida directa de valor de negocio.
- No confundir disponibilidad con ausencia de incidentes.
- Diferenciar MTTR operacional de Failed Deployment Recovery Time de DORA.
- Evitar comparaciones entre períodos completos y períodos parciales.

### 7.6 Evolución y mantenimiento

El diccionario debe mantenerse actualizado cuando:

- Se incorporen nuevos indicadores.
- Cambien las fuentes de información.
- Se modifiquen fórmulas o criterios de cálculo.
- Se incorporen nuevas plataformas o servicios.
- Se identifiquen limitaciones o problemas de calidad en los datos.

Toda modificación debe conservar la trazabilidad entre la fuente, el modelo de datos, el indicador y su representación en los dashboards.

## 8. Principios de interpretación

1. **Output no equivale a Outcome:** completar actividades o entregables no demuestra por sí solo la generación de valor de negocio.
2. **Velocidad no equivale a productividad:** una mayor cantidad de entregas no necesariamente representa mayor valor.
3. **Velocity no permite comparar productividad entre equipos:** debe utilizarse como herramienta de planificación del propio equipo.
4. **Deployment Frequency no equivale a valor de negocio:** mide frecuencia de despliegue, no impacto comercial.
5. **Disponibilidad no equivale a ausencia de incidentes:** un servicio puede presentar incidentes sin perder completamente su disponibilidad.
6. **Correlación no demuestra causalidad:** una variación simultánea de indicadores no demuestra que uno sea causa del otro.
7. **Los indicadores requieren contexto:** capacidad, alcance, complejidad, dependencias y calidad de los datos deben considerarse antes de tomar decisiones.
8. **Las métricas DORA deben analizarse conjuntamente:** la velocidad de entrega debe interpretarse junto con la estabilidad y recuperación.
9. **Los datos parciales requieren cautela:** un período incompleto no debe compararse directamente con uno completo.
10. **La medición debe impulsar decisiones:** cada indicador debe contribuir a identificar desviaciones, riesgos, oportunidades o acciones de mejora.

## 9. Mapa de indicadores por producto

| Producto | Ámbito | Indicadores principales |
|---|---|---|
| 01 - Dashboard Ejecutivo de Gestión TI | Gestión ejecutiva | Predictibilidad, avance, hitos, riesgos, SLA y disponibilidad |
| 02 - Gestión de Proyectos y Entrega Ágil | Delivery y agilidad | Sprint Goal, compromiso, carry-over, trabajo no planificado, throughput, Cycle Time, Lead Time, WIP, impedimentos y calidad |
| 03 - Entrega Técnica y Operaciones TI | DevOps y operaciones | DORA, disponibilidad, latencia, errores, infraestructura cloud, costos, incidentes, MTTR y SLA |

## 10. Fuentes de datos del portafolio

| Dataset | Producto | Contenido |
|---|---|---|
| `executive-kpis.csv` | 01 | Indicadores ejecutivos por iniciativa y corte |
| `agile-delivery.csv` | 02 | Métricas de entrega ágil por equipo y Sprint |
| `deployments.csv` | 03 | Historial DEMO de despliegues |
| `cloud-monitoring.csv` | 03 | Observaciones semanales de monitoreo cloud |
| `incidents.csv` | 03 | Registro DEMO de incidentes y recuperación |

---

**Principio rector del portafolio:**

La gestión de TI debe permitir comprender qué se comprometió, qué se entregó, cómo evolucionó el desempeño, qué resultados se obtuvieron y qué decisiones deben tomarse para mejorar la entrega de valor.
