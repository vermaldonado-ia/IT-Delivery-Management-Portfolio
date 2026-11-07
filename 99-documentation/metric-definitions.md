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

### 2.2 Cumplimiento de avance planificado

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

Riesgos críticos abiertos = Conteo de riesgos críticos con estado abierto

**Fuente:** `executive-kpis.csv`

**Interpretación:** permite identificar exposición relevante para la continuidad y los compromisos de las iniciativas.

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

## 3. Gestión de Proyectos y Entrega Ágil

### 3.1 Cumplimiento del Sprint Goal

**Definición:** mide si el equipo alcanzó el objetivo comprometido para el Sprint.

**Fórmula:**

Cumplimiento Sprint Goal (%) = (Sprints con objetivo alcanzado / Sprints evaluados) × 100

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite evaluar el cumplimiento del propósito del Sprint, más allá de la cantidad de elementos completados.

**Consideraciones:**
- El Sprint Goal debe definirse antes de iniciar el Sprint.
- Un Sprint puede completar muchos elementos y no alcanzar su objetivo.
- Los Sprints en curso no deben incluirse en el cálculo de Sprints finalizados.

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

**Definición:** cantidad de trabajo incorporado durante el Sprint que no formaba parte del compromiso inicial.

**Fórmula:**

Trabajo no planificado (%) = (Elementos de trabajo no planificado / Elementos totales gestionados) × 100

**Fuente:** `agile-delivery.csv`

**Consideraciones:**
- Debe existir un criterio uniforme para clasificar trabajo planificado y no planificado.
- Es importante identificar si el trabajo adicional responde a incidentes, urgencias, cambios de prioridad o dependencias.
- No debe interpretarse automáticamente como una falla del equipo.

### 3.5 Throughput

**Definición:** cantidad de elementos de trabajo completados durante un período.

**Fórmula:**

Throughput = Conteo de elementos completados en el período

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite observar el volumen de trabajo entregado por un equipo a lo largo del tiempo.

**Consideraciones:**
- No equivale a productividad individual.
- No debe utilizarse para comparar equipos sin considerar el tamaño y complejidad de los elementos.
- Debe analizarse junto con Cycle Time, calidad y resultados.

### 3.6 Cycle Time

**Definición:** tiempo transcurrido desde que un elemento comienza su ejecución hasta que queda terminado.

**Fórmula:**

Cycle Time = Fecha de finalización − Fecha de inicio de ejecución

**Fuente:** `agile-delivery.csv`

**Unidad:** días.

**Consideraciones:**
- La definición de inicio y término debe mantenerse estable.
- Se recomienda utilizar mediana y percentiles para reducir el efecto de valores extremos.
- En el dataset DEMO se dispone de la mediana de Cycle Time.

### 3.7 Lead Time

**Definición:** tiempo transcurrido desde que se solicita o registra un elemento hasta que queda entregado.

**Fórmula:**

Lead Time = Fecha de entrega − Fecha de solicitud o registro

**Fuente:** `agile-delivery.csv`

**Unidad:** días.

**Consideraciones:**
- Debe definirse claramente el evento inicial.
- No debe confundirse con Cycle Time.
- En el dataset DEMO se dispone de la mediana de Lead Time.

### 3.8 WIP (Work in Progress)

**Definición:** cantidad promedio de elementos que permanecen en ejecución durante un período.

**Fórmula:**

WIP promedio = Promedio de elementos en curso durante el período

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite observar acumulación de trabajo y posibles restricciones de flujo.

### 3.9 Impedimentos

**Definición:** cantidad de impedimentos identificados durante un Sprint.

**Fórmula:**

Impedimentos = Conteo de impedimentos registrados en el Sprint

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite identificar obstáculos que afectan el flujo de entrega y requieren seguimiento.

### 3.10 Defectos y retrabajo

**Definición:** permiten observar problemas de calidad y trabajo que debe repetirse o corregirse.

**Fórmulas:**

- Defectos: conteo de defectos registrados durante el período.
- Retrabajo: cantidad de elementos que requirieron trabajo adicional por correcciones.

**Fuente:** `agile-delivery.csv`

**Consideraciones:**
- Se debe mantener un criterio consistente de registro.
- Los defectos y el retrabajo no son necesariamente equivalentes.
- Deben analizarse junto con el volumen de trabajo entregado.

## 4. Entrega Técnica y DevOps — Métricas DORA

Las métricas DORA permiten observar el desempeño de la entrega de software desde la perspectiva de velocidad y estabilidad.

Se consideran cuatro indicadores:

1. Deployment Frequency.
2. Lead Time for Changes.
3. Change Failure Rate.
4. Failed Deployment Recovery Time.

Deben analizarse conjuntamente y por servicio o aplicación cuando la información lo permita.

### 4.1 Deployment Frequency

**Definición:** frecuencia con que se realizan despliegues exitosos en producción durante un período.

**Fórmula:**

Deployment Frequency = Cantidad de despliegues exitosos en producción / Período

**Fuente:** `deployments.csv`

**Consideraciones:**
- Se consideran despliegues realizados en producción.
- Deben excluirse los despliegues fallidos.
- La unidad de presentación puede ser despliegues por semana, mes u otro período definido.

### 4.2 Lead Time for Changes

**Definición:** tiempo transcurrido desde que se confirma un cambio en el repositorio hasta que ese cambio queda desplegado en producción.

**Fórmula:**

Lead Time for Changes = Fecha y hora del despliegue en producción − Fecha y hora del commit

**Fuente requerida para medición estricta:** repositorio de código y registro de despliegues.

**Consideración sobre los datos DEMO:**

El archivo `deployments.csv` contiene el campo `lead_time_cambios_horas`, pero no incluye la fecha y hora del commit ni el timestamp de origen del cambio.

Por esta razón, el valor disponible se considera una **aproximación DEMO** y no una medición estricta de DORA Lead Time for Changes.

Para una medición real será necesario disponer de:
- Timestamp del commit.
- Timestamp del despliegue en producción.
- Identificador que permita relacionar el cambio con el despliegue.

### 4.3 Change Failure Rate (CFR)

**Definición:** porcentaje de despliegues en producción que generan un fallo y requieren una intervención o recuperación.

**Fórmula:**

CFR (%) = (Despliegues fallidos / Total de despliegues en producción) × 100

**Fuente:** `deployments.csv`

**Ejemplo con los datos DEMO actuales:**

- Total de despliegues en producción: 48.
- Despliegues fallidos: 7.

CFR = (7 / 48) × 100 = 14,58 %

**Interpretación:** en esta muestra DEMO, el 14,58 % de los despliegues registrados en producción fueron clasificados como fallidos.

**Criterios de medición:**
- Cada despliegue debe tener un identificador único.
- Un despliegue fallido debe responder a un criterio de clasificación documentado.
- Debe evitarse contar varias veces un mismo despliegue.
- La relación entre despliegue e incidente debe estar respaldada por evidencia.
- El indicador debe calcularse sobre el total de despliegues de producción del mismo período.

### 4.4 Failed Deployment Recovery Time

**Definición:** tiempo transcurrido desde el inicio del impacto provocado por un despliegue fallido hasta la recuperación del servicio.

**Fórmula:**

Failed Deployment Recovery Time = Fecha y hora de recuperación del servicio − Fecha y hora de inicio del impacto

**Fuente:** `deployments.csv` e `incidents.csv`

**Criterio aplicado en los datos DEMO:**

- Inicio del impacto: `fecha_deteccion`.
- Recuperación del servicio: `fecha_recuperacion`.
- El campo `tiempo_recuperacion_minutos` representa la diferencia entre ambos momentos.

**Consideraciones:**
- El inicio del impacto se utiliza como aproximación cuando no existe un timestamp exacto de inicio.
- La recuperación corresponde a la restauración del servicio, no al cierre administrativo del ticket.
- Para el indicador DORA solo deben considerarse incidentes relacionados con despliegues fallidos.
- Los incidentes sin relación demostrada con un despliegue no deben incluirse en este cálculo.

## 5. Cloud Monitoring & Observability

Este módulo permite observar la salud técnica y el comportamiento de los servicios desplegados en infraestructura cloud.

### 5.1 Disponibilidad

**Definición:** porcentaje de tiempo en que un servicio estuvo disponible durante el período medido.

**Fórmula:**

Disponibilidad (%) = (Tiempo disponible / Tiempo total medido) × 100

**Fuente:** `cloud-monitoring.csv`

### 5.2 Latencia p95

**Definición:** tiempo máximo dentro del cual se completó el 95 % de las solicitudes durante el período observado.

**Unidad:** milisegundos (ms).

**Fuente:** `cloud-monitoring.csv`

**Interpretación:** permite observar la experiencia de respuesta del servicio, considerando la distribución de los tiempos de respuesta.

### 5.3 Tasa de errores

**Definición:** porcentaje de solicitudes que finalizaron con error respecto del total de solicitudes procesadas.

**Fórmula:**

Tasa de errores (%) = (Solicitudes con error / Total de solicitudes) × 100

**Fuente:** `cloud-monitoring.csv`

### 5.4 Uso de CPU

**Definición:** porcentaje promedio de utilización de CPU durante el período medido.

**Unidad:** porcentaje.

**Fuente:** `cloud-monitoring.csv`

### 5.5 Uso de memoria

**Definición:** porcentaje promedio de memoria utilizada respecto de la memoria disponible.

**Unidad:** porcentaje.

**Fuente:** `cloud-monitoring.csv`

### 5.6 Uso de almacenamiento

**Definición:** porcentaje de almacenamiento utilizado respecto de la capacidad disponible.

**Unidad:** porcentaje.

**Fuente:** `cloud-monitoring.csv`

### 5.7 Tráfico de red

**Definición:** volumen de datos que ingresa y sale del servicio durante el período medido.

**Campos disponibles:**
- `trafico_entrada_gb`
- `trafico_salida_gb`

**Unidad:** gigabytes por semana (GB/semana).

**Fuente:** `cloud-monitoring.csv`

**Criterio aplicado en los datos DEMO:**

- `trafico_entrada_gb`: volumen semanal de tráfico entrante.
- `trafico_salida_gb`: volumen semanal de tráfico saliente.
- Los valores representan volúmenes semanales, no tasas instantáneas de transferencia ni velocidades de red.
- Esta convención se adopta para el modelo DEMO y no constituye una validación de datos provenientes de una plataforma Cloud real.

Para calcular una tasa de transferencia se necesitarían datos de volumen asociados a una duración conocida y una fórmula de conversión consistente.

### 5.8 Costo cloud

**Definición:** costo asociado al consumo de servicios cloud durante el período evaluado.

**Unidad:** dólares estadounidenses por semana (USD/semana).

**Fuente:** `cloud-monitoring.csv`

**Criterio aplicado en los datos DEMO:**

- `costo_cloud_usd` representa el costo semanal de servicios Cloud.
- Los valores se interpretan como costos de cada semana, no como acumulados.
- Esta convención se adopta para el modelo DEMO y no constituye una validación de información de facturación real.

**Consideraciones:**
- Los costos deben analizarse por servicio y proveedor cuando exista información.
- No deben compararse períodos de distinta duración sin normalización.
- Los datos DEMO deben identificarse como ficticios.

**Nota sobre la muestra DEMO de Cloud Monitoring:**

El dataset contiene cinco cortes semanales correspondientes a septiembre de 2026. Se trata de datos agregados por corte, no de telemetría continua. Por tanto, los gráficos deben presentarse como observaciones semanales de la muestra disponible.

## 6. IT Service Operations

Este módulo permite evaluar la gestión de incidentes, recuperación del servicio y cumplimiento de acuerdos de nivel de servicio.

### 6.1 Cantidad de incidentes

**Definición:** número de incidentes registrados durante el período.

**Fórmula:**

Cantidad de incidentes = Conteo de incidentes registrados en el período

**Fuente:** `incidents.csv`

**Consideraciones:**
- Se deben identificar los incidentes por severidad y servicio.
- Los incidentes deben contarse una sola vez mediante su identificador.
- Debe distinguirse entre incidentes abiertos, en curso y resueltos cuando exista esa información.

### 6.2 MTTR operacional

**Definición:** tiempo promedio transcurrido desde la apertura de un incidente hasta la recuperación del servicio.

**Fórmula:**

MTTR operacional = Suma de tiempos de recuperación desde la apertura / Cantidad de incidentes recuperados

**Fuente:** `incidents.csv`

**Criterio aplicado en los datos DEMO:**

- Inicio: `fecha_apertura`.
- Término: `fecha_recuperacion`.
- Campo asociado: `tiempo_resolucion_minutos`.

**Consideraciones:**
- Se incluyen los incidentes recuperados que forman parte de la población evaluada.
- Los incidentes no recuperados no deben incorporarse como si tuvieran un tiempo de recuperación conocido.
- Debe documentarse el criterio de selección y el período.

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

### 6.4 Cumplimiento de SLA por incidente

**Definición:** determina si un incidente fue resuelto dentro del tiempo objetivo establecido.

**Fórmula:**

Cumplimiento SLA = Tiempo de resolución ≤ Objetivo SLA

**Fuente:** `incidents.csv`

**Criterio aplicado en los datos DEMO:**
- Tiempo de resolución: desde `fecha_apertura` hasta `fecha_recuperacion`.
- Objetivo: `sla_objetivo_minutos`.
- Resultado: `sla_cumplido`.

### 6.5 Incidentes críticos

**Definición:** cantidad de incidentes clasificados con severidad crítica durante el período.

**Fórmula:**

Incidentes críticos = Conteo de incidentes con severidad crítica

**Fuente:** `incidents.csv`

**Interpretación:** permite identificar eventos con mayor impacto sobre la continuidad del servicio.

## 7. Gobierno y Calidad de Indicadores

Para asegurar la confiabilidad del modelo de gestión se establecen los siguientes criterios:

### 7.1 Trazabilidad

Cada indicador debe permitir identificar:
- Fuente de información.
- Fecha de extracción o corte.
- Período evaluado.
- Regla de cálculo.
- Responsable de validación.

### 7.2 Calidad del dato

Se deben revisar:
- Completitud.
- Consistencia.
- Duplicidad.
- Validez de fechas.
- Integridad de relaciones entre datasets.
- Coherencia de unidades de medida.

### 7.3 Responsabilidad

Cada indicador debe tener un responsable funcional que valide su definición, origen y uso.

La responsabilidad de medición no implica necesariamente que dicho rol sea responsable de ejecutar la actividad técnica que origina el dato.

### 7.4 Datos DEMO

Todos los datasets de este portafolio utilizan información ficticia.

Los resultados calculados deben identificarse como DEMO y no deben atribuirse a organizaciones, clientes o servicios reales.

Los indicadores que no puedan calcularse estrictamente con los campos disponibles deben identificarse como aproximaciones o quedar pendientes de información adicional.

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
