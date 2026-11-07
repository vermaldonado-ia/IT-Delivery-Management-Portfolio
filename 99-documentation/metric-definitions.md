# Diccionario de Indicadores de Gestión TI

## 1. Objetivo

Establecer un marco común de medición para los tres productos del portafolio:

1. Dashboard Ejecutivo de Gestión TI.
2. Gestión de Proyectos y Entrega Ágil.
3. Entrega Técnica y Operaciones TI.

Este documento define los indicadores, sus fórmulas de cálculo, unidades de medida, fuentes de información y criterios de interpretación.

Su propósito es asegurar la consistencia de las mediciones, facilitar el seguimiento de la evolución y entregar información confiable para la toma de decisiones.

Cada indicador debe permitir comprender qué se mide, cómo se calcula, cuál es su alcance y qué decisión de gestión puede apoyar.

---

## 2. Modelo común de medición

Todos los indicadores deben seguir una estructura de medición que permita comparar la situación inicial con su evolución.

| Elemento | Descripción |
|---|---|
| Línea base | Valor inicial medido y validado |
| Valor actual | Último resultado disponible |
| Variación | Diferencia entre el valor actual y la línea base |
| Meta | Resultado esperado, cuando haya sido aprobado |
| Estado | Condición del indicador según umbrales definidos |
| Tendencia | Evolución del indicador durante los períodos analizados |
| Período | Intervalo de tiempo considerado en la medición |
| Fuente | Sistema o registro del que provienen los datos |

### 2.1. Cálculo de variaciones

**Variación absoluta:**

Valor actual - Línea base

**Variación porcentual:**

((Valor actual - Línea base) / Línea base) × 100

Cuando la línea base sea cero o no permita un cálculo porcentual válido, se debe informar la variación absoluta o indicar que la variación porcentual no aplica.

### 2.2. Reglas para establecer metas y estados

- Las metas deben ser aprobadas por los responsables correspondientes.
- Los umbrales de los semáforos deben definirse según el contexto y los objetivos de gestión.
- No se deben asignar estados de cumplimiento sin criterios previamente establecidos.
- Una mejora o deterioro debe interpretarse según la naturaleza del indicador.
- Cuando no exista información suficiente, se debe utilizar **No medido** o **Sin dato**.
- Los datos estimados deben diferenciarse de los datos efectivamente medidos.

---

# 3. Indicadores de Gestión Ejecutiva TI

Orientados a entregar una visión consolidada del desempeño del portafolio tecnológico para subgerencia, dirección y stakeholders.

| Indicador | Definición | Fórmula de cálculo | Unidad |
|---|---|---|---|
| Predictibilidad de entrega | Porcentaje de compromisos planificados que fueron entregados según lo acordado | (Compromisos entregados / Compromisos planificados) × 100 | % |
| Cumplimiento de hitos | Porcentaje de hitos completados dentro de la fecha comprometida | (Hitos completados a tiempo / Hitos con vencimiento en el período) × 100 | % |
| Riesgos críticos abiertos | Cantidad de riesgos clasificados como críticos que permanecen sin resolver | Conteo de riesgos críticos abiertos | Cantidad |
| Cumplimiento de SLA | Porcentaje de compromisos de servicio cumplidos dentro del tiempo acordado | (Compromisos cumplidos dentro del SLA / Total de compromisos elegibles) × 100 | % |
| Disponibilidad del servicio | Porcentaje de tiempo en que el servicio estuvo disponible durante el período evaluado | ((Tiempo acordado de servicio - Tiempo de indisponibilidad) / Tiempo acordado de servicio) × 100 | % |

### Criterios de interpretación

- La predictibilidad debe considerar los compromisos definidos al inicio del período.
- Los cambios de alcance deben quedar registrados y tener un tratamiento consistente.
- El cumplimiento de hitos debe considerar únicamente los hitos cuyo vencimiento corresponde al período.
- Los riesgos críticos deben tener responsable, impacto, probabilidad y plan de tratamiento.
- La disponibilidad debe considerar la ventana de servicio acordada y las exclusiones definidas contractualmente.
- El cumplimiento de SLA debe utilizar compromisos elegibles y reglas de medición documentadas.

---

# 4. Indicadores de Gestión de Proyectos y Entrega Ágil

Orientados al seguimiento de equipos, proyectos, planificación, flujo de trabajo y evolución de la gestión ágil.

## 4.1. Desempeño de Sprint

| Indicador | Definición | Fórmula de cálculo | Unidad |
|---|---|---|---|
| Cumplimiento del objetivo del Sprint | Porcentaje de Sprints cuyo Sprint Goal fue alcanzado | (Sprints con objetivo alcanzado / Total de Sprints finalizados) × 100 | % |
| Cumplimiento del compromiso | Porcentaje de elementos comprometidos al inicio del Sprint que fueron completados | (Elementos comprometidos al inicio y completados / Elementos comprometidos al inicio) × 100 | % |
| Carry-over | Elementos comprometidos que no fueron completados y pasan al siguiente Sprint | Conteo de elementos pendientes al cierre del Sprint | Cantidad |
| Porcentaje de Carry-over | Proporción de elementos comprometidos que quedaron pendientes al cierre | (Elementos pendientes del compromiso inicial / Elementos comprometidos al inicio) × 100 | % |
| Trabajo no planificado | Cantidad de elementos incorporados después del inicio del Sprint | Conteo de elementos incorporados durante el Sprint | Cantidad |

### Criterios de interpretación

- El Sprint Goal debe evaluarse considerando el objetivo acordado y no solamente la cantidad de tareas terminadas.
- El cumplimiento del compromiso debe utilizar el alcance registrado al inicio del Sprint.
- Los elementos incorporados posteriormente deben identificarse como trabajo no planificado.
- El Carry-over debe analizarse junto con sus causas: dependencias, bloqueos, cambios de prioridad, estimaciones o capacidad.
- El cumplimiento de puntos o tareas no demuestra por sí solo el valor entregado.

## 4.2. Flujo de entrega

| Indicador | Definición | Fórmula de cálculo | Unidad |
|---|---|---|---|
| Throughput | Cantidad de elementos de trabajo completados durante un período | Conteo de elementos que alcanzan el estado de terminado | Elementos/período |
| Cycle Time | Tiempo transcurrido desde que comienza el trabajo hasta que el elemento se completa | Fecha y hora de finalización - Fecha y hora de inicio del trabajo | Tiempo |
| Lead Time | Tiempo transcurrido desde que se solicita un elemento hasta que se entrega | Fecha y hora de entrega - Fecha y hora de solicitud | Tiempo |
| WIP | Cantidad de elementos de trabajo que permanecen en ejecución | Conteo de elementos en estados definidos como trabajo en curso | Cantidad |
| Antigüedad del trabajo pendiente | Tiempo que lleva un elemento sin completarse desde que comenzó su ejecución | Fecha y hora actual - Fecha y hora de inicio del trabajo | Tiempo |
| Impedimentos activos | Cantidad de elementos de trabajo que se encuentran bloqueados | Conteo de elementos bloqueados | Cantidad |

### Criterios de interpretación

- El Throughput debe analizarse por período y tipo de elemento.
- Cycle Time y Lead Time deben utilizar estados de inicio y término claramente definidos.
- Se recomienda analizar mediana y percentiles, además del promedio, para identificar la distribución de los tiempos.
- El WIP debe observarse junto con la capacidad y el flujo del equipo.
- La antigüedad de los elementos pendientes permite detectar trabajo estancado.
- Los impedimentos deben registrar fecha de inicio, responsable y tiempo de resolución.
- La velocidad de un equipo no debe utilizarse como medida de productividad ni para comparar equipos diferentes.

---

# 5. Indicadores de Entrega Técnica y Operaciones TI

Este producto reúne indicadores de desempeño de entrega de software, monitoreo de infraestructura, observabilidad y gestión de servicios tecnológicos.

## 5.1. Métricas DORA

Las métricas DORA permiten evaluar el desempeño de la entrega de software desde dos dimensiones principales: velocidad y estabilidad.

| Indicador DORA | Definición | Fórmula o método de cálculo | Unidad |
|---|---|---|---|
| Deployment Frequency (Frecuencia de despliegues) | Frecuencia con que se realizan despliegues exitosos en producción | Cantidad de despliegues exitosos en producción / Período analizado | Despliegues/período |
| Lead Time for Changes (Tiempo de entrega de cambios) | Tiempo desde que un cambio se confirma en el repositorio hasta que llega a producción | Fecha y hora de despliegue en producción - Fecha y hora de confirmación del cambio | Tiempo |
| Change Failure Rate (Tasa de fallas por cambios) | Porcentaje de despliegues que provocan fallas y requieren intervención o corrección | (Despliegues que generan fallas / Total de despliegues en producción) × 100 | % |
| Failed Deployment Recovery Time (Tiempo de recuperación ante despliegues fallidos) | Tiempo necesario para recuperar el servicio después de un despliegue que provoca una falla | Fecha y hora de recuperación del servicio - Fecha y hora de inicio del impacto | Tiempo |

### Criterios de interpretación DORA

- Las cuatro métricas deben analizarse en conjunto.
- La frecuencia de despliegues no representa por sí sola calidad o valor de negocio.
- El Lead Time for Changes debe utilizar puntos de inicio y término consistentes.
- La Change Failure Rate requiere una definición documentada de qué se considera una falla asociada a un despliegue.
- El tiempo de recuperación debe considerar el momento en que se restablece el servicio, no solamente cuando se cierra administrativamente el incidente.
- Las métricas deben analizarse por servicio o aplicación y considerando su contexto.
- No se deben comparar equipos sin considerar diferencias de arquitectura, producto, criticidad y proceso de entrega.

## 5.2. Monitoreo Cloud y Observabilidad

Indicadores orientados al seguimiento de la salud, disponibilidad y comportamiento de aplicaciones e infraestructura tecnológica.

| Indicador | Definición | Fórmula o método de cálculo | Unidad |
|---|---|---|---|
| Disponibilidad | Porcentaje de tiempo en que un servicio permanece disponible | ((Tiempo de servicio acordado - Tiempo de indisponibilidad) / Tiempo de servicio acordado) × 100 | % |
| Latencia p95 | Tiempo de respuesta por debajo del cual se encuentra el 95 % de las solicitudes observadas | Percentil 95 de los tiempos de respuesta registrados | ms o s |
| Tasa de errores | Proporción de solicitudes que presentan errores respecto del total de solicitudes | (Solicitudes con error / Total de solicitudes) × 100 | % |
| Utilización de CPU | Porcentaje de capacidad de procesamiento utilizada | (CPU utilizada / CPU disponible) × 100 | % |
| Utilización de memoria | Porcentaje de memoria utilizada respecto de la memoria disponible | (Memoria utilizada / Memoria disponible) × 100 | % |
| Utilización de almacenamiento | Porcentaje de capacidad de almacenamiento utilizada | (Almacenamiento utilizado / Capacidad total disponible) × 100 | % |
| Tráfico de red | Volumen de información transmitida o recibida durante un período | Total de bytes transmitidos o recibidos / Tiempo observado | Bytes/s, MB/s o Mbps |
| Costo Cloud | Gasto de infraestructura y servicios Cloud durante un período | Suma de los costos registrados en el período | Moneda |

### Criterios de interpretación

- La latencia p95 representa el percentil 95 de los tiempos de respuesta: el 95 % de las solicitudes tiene un tiempo de respuesta igual o inferior a ese valor.
- La tasa de errores debe utilizar una clasificación consistente de errores y solicitudes.
- CPU, memoria y almacenamiento deben analizarse considerando capacidad, carga y comportamiento del servicio.
- El tráfico de red debe identificar si corresponde a información entrante, saliente o ambas.
- Los costos Cloud deben considerar moneda, período, servicios incluidos y criterios de imputación.
- La disponibilidad debe utilizar la misma ventana de servicio definida para el indicador.
- Los umbrales de alerta deben establecerse según las características y criticidad del servicio.

## 5.3. Operaciones y Gestión de Servicios TI

Indicadores orientados a evaluar la continuidad operacional, atención de incidentes y cumplimiento de compromisos de servicio.

| Indicador | Definición | Fórmula o método de cálculo | Unidad |
|---|---|---|---|
| Cantidad de incidentes | Total de incidentes registrados durante el período | Conteo de incidentes registrados | Cantidad |
| MTTR (Mean Time to Repair/Restore) | Tiempo medio necesario para recuperar el servicio después de incidentes | Suma de tiempos de recuperación / Cantidad de incidentes recuperados | Tiempo |
| Cumplimiento de SLA | Porcentaje de incidentes o solicitudes elegibles atendidos dentro del compromiso establecido | (Incidentes o solicitudes dentro del SLA / Total de casos elegibles) × 100 | % |
| Incidentes críticos | Cantidad de incidentes clasificados como críticos según la matriz de severidad | Conteo de incidentes críticos | Cantidad |

### Criterios de interpretación

- La clasificación de incidentes debe utilizar una matriz de severidad documentada.
- El MTTR debe definir si mide recuperación del servicio o resolución definitiva del incidente.
- Se recomienda separar los incidentes por severidad y servicio.
- El cumplimiento de SLA debe considerar las reglas contractuales, horarios de servicio y exclusiones.
- Los incidentes recurrentes deben analizarse para identificar causas y oportunidades de prevención.
- La cantidad de incidentes no debe interpretarse de forma aislada, sin considerar criticidad, impacto y volumen de operación.

---

# 6. Gobierno de los Indicadores

Cada indicador incorporado a un dashboard debe contar con una ficha de definición y gobierno.

| Campo | Descripción |
|---|---|
| Nombre | Nombre oficial del indicador |
| Objetivo | Propósito de gestión que busca apoyar |
| Definición | Descripción precisa de lo que se mide |
| Fórmula | Método de cálculo documentado |
| Unidad | Porcentaje, cantidad, tiempo, costo u otra unidad |
| Frecuencia | Diaria, semanal, por Sprint, mensual u otra |
| Período | Intervalo utilizado para la medición |
| Alcance | Equipos, servicios, proyectos o población considerada |
| Fuente | Sistema de origen de la información |
| Responsable del dato | Persona o área responsable de la calidad del registro |
| Responsable de gestión | Persona o área que interpreta y utiliza el indicador |
| Línea base | Valor inicial validado |
| Meta | Objetivo aprobado, cuando exista |
| Umbrales | Criterios definidos para interpretar el estado |
| Calidad del dato | Nivel de completitud, consistencia y confiabilidad |
| Fecha de actualización | Última fecha de actualización de la medición |

## 6.1. Fuentes de información posibles

Dependiendo de la organización y de las herramientas utilizadas, los datos pueden provenir de:

- Jira y Azure DevOps: planificación, Sprints, backlog y flujo de trabajo.
- GitHub, GitLab y Bitbucket: repositorios y actividad de cambios.
- Jenkins y otras herramientas CI/CD: procesos de integración y despliegue.
- SonarQube: indicadores de calidad de código.
- AWS CloudWatch y Azure Monitor: monitoreo de infraestructura y aplicaciones.
- Grafana y Prometheus: observabilidad y métricas técnicas.
- Plataformas ITSM: incidentes, solicitudes y SLA.
- Sistemas financieros o de gestión Cloud: costos de infraestructura.

La fuente definitiva debe corresponder al sistema realmente utilizado y autorizado por la organización.

---

# 7. Criterios de Calidad e Interpretación

Para mantener la confiabilidad del portafolio se deben aplicar los siguientes principios:

1. **Trazabilidad:** cada indicador debe tener una fuente identificable.
2. **Consistencia:** las definiciones y fórmulas deben mantenerse estables durante los períodos comparados.
3. **Contexto:** los indicadores deben interpretarse considerando el alcance, capacidad y condiciones de operación.
4. **Comparabilidad:** no comparar equipos o servicios sin verificar que las condiciones de medición sean equivalentes.
5. **Transparencia:** diferenciar datos medidos, estimados y ficticios.
6. **Calidad:** no presentar resultados sin validar integridad y consistencia de los datos.
7. **Accionabilidad:** los indicadores deben facilitar decisiones y acciones concretas.
8. **Evolución:** mantener una línea base que permita observar cambios a lo largo del tiempo.

### Distinciones fundamentales

- Output no es lo mismo que Outcome: completar trabajo no demuestra automáticamente la obtención de valor de negocio.
- Velocidad no es productividad: los puntos de historia no deben utilizarse para comparar equipos.
- Despliegues no equivalen a valor entregado: la frecuencia de despliegue mide actividad de entrega técnica.
- Disponibilidad no equivale a ausencia de incidentes: un servicio puede presentar incidentes sin superar su umbral de indisponibilidad.
- Correlación no demuestra causalidad: no atribuir fallas a despliegues sin evidencia.
- Una mejora en un indicador no siempre significa una mejora global: se deben considerar sus efectos sobre otros indicadores.

---

# 8. Tratamiento de Datos Faltantes y Datos DEMO

Cuando no exista información suficiente para calcular un indicador, utilizar:

- **No medido:** el indicador todavía no cuenta con medición.
- **Sin dato:** la fuente no proporciona información suficiente para el período.
- **No aplica:** el indicador no corresponde al alcance evaluado.
- **Pendiente de validación:** existe información, pero todavía no ha sido verificada.

Los datos de demostración deben estar identificados explícitamente como **DEMO** y utilizar información ficticia.

No se deben presentar datos ficticios como resultados reales de empresas, clientes, proyectos, equipos o servicios productivos.

---

# 9. Aplicación del Diccionario en el Portafolio

| Producto | Indicadores principales |
|---|---|
| 01. Dashboard Ejecutivo de Gestión TI | Predictibilidad, cumplimiento de hitos, riesgos críticos, SLA y disponibilidad |
| 02. Gestión de Proyectos y Entrega Ágil | Sprint Goal, cumplimiento del compromiso, Carry-over, Throughput, Cycle Time, Lead Time, WIP e impedimentos |
| 03. Entrega Técnica y Operaciones TI | Métricas DORA, disponibilidad, latencia, errores, utilización de recursos, costos Cloud, incidentes y MTTR |

El Dashboard Ejecutivo puede consolidar indicadores de los productos 02 y 03, manteniendo el detalle técnico y operativo en sus respectivos módulos.

---

## 10. Principio de Gestión

**Medir para comprender. Analizar para decidir. Actuar para mejorar.**

El valor de un indicador no está únicamente en su resultado numérico, sino en la capacidad de explicar una situación, identificar desviaciones, anticipar riesgos y respaldar decisiones de gestión.

Este diccionario constituye la referencia metodológica para definir, calcular, interpretar y presentar los indicadores del portafolio.

> Todos los datos de demostración de este portafolio son ficticios y no representan el desempeño de ninguna organización real.
