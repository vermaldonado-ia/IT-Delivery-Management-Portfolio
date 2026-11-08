# Agile Delivery Management

## 1. Objetivo

Establecer un modelo de seguimiento y evaluación de la entrega ágil, proporcionando visibilidad sobre el desempeño de los equipos, el cumplimiento de los objetivos de Sprint y la evolución del trabajo comprometido.

El producto busca facilitar la identificación de desviaciones, mejorar la predictibilidad de la entrega y apoyar la toma de decisiones de los responsables de proyectos y equipos.

## 2. Público objetivo

- Project Managers.
- Scrum Masters.
- Delivery Managers.
- Líderes de equipos de desarrollo.
- Product Owners.
- Responsables de gestión y seguimiento de proyectos TI.

## 3. Alcance de gestión

El modelo considera las siguientes dimensiones:

| Dimensión | Enfoque |
|---|---|
| Cumplimiento de objetivos | Evaluación de los objetivos definidos para cada Sprint. |
| Confiabilidad del compromiso | Relación entre el trabajo comprometido y el completado. |
| Trabajo pendiente | Seguimiento de elementos trasladados entre Sprints. |
| Capacidad de entrega | Volumen de elementos completados por equipo y período. |
| Flujo de trabajo | Seguimiento del tiempo de ciclo de los elementos. |
| Trabajo no planificado | Visibilidad de trabajo incorporado fuera de la planificación inicial, cuando existan datos suficientes. |

## 4. Indicadores de entrega ágil

### 4.1 Sprint Goal Achievement

Mide la proporción de Sprints cerrados en los que se alcanzó el objetivo definido.

**Fórmula:**

Sprint Goal Achievement (%) = (Sprints con objetivo alcanzado / Total de Sprints cerrados) × 100

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite evaluar la consistencia con la que los equipos alcanzan los objetivos establecidos para cada Sprint.

Los Sprints en curso o sin resultado definitivo deben excluirse del cálculo.

### 4.2 Sprint Commitment Reliability

Mide la proporción de elementos comprometidos inicialmente que fueron completados durante el Sprint.

**Fórmula:**

Sprint Commitment Reliability (%) = (Elementos comprometidos completados / Elementos comprometidos inicialmente) × 100

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite analizar la confiabilidad de los compromisos asumidos por los equipos.

Su cálculo requiere que los elementos pendientes representen compromisos iniciales no completados y que se identifiquen las cancelaciones o modificaciones del compromiso.

### 4.3 Carry-over

Mide la proporción de elementos comprometidos que no fueron completados y se trasladaron al siguiente Sprint.

**Fórmula:**

Carry-over (%) = (Elementos pendientes trasladados / Elementos comprometidos) × 100

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite identificar trabajo que permanece pendiente al cierre de un Sprint y analizar posibles problemas de planificación, capacidad o dependencias.

### 4.4 Throughput

Representa la cantidad de elementos de trabajo completados durante un período determinado.

**Fórmula:**

Throughput = Cantidad de elementos completados

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite observar el volumen de trabajo finalizado por equipo y período.

Debe utilizarse para analizar tendencias y no como una medida aislada de productividad individual.

### 4.5 Cycle Time

Mide el tiempo transcurrido desde que comienza el trabajo efectivo de un elemento hasta que finaliza.

**Fórmula:**

Cycle Time = Fecha de finalización - Fecha de inicio del trabajo

**Fuente:** `agile-delivery.csv`

**Interpretación:** permite evaluar la velocidad de flujo del trabajo y detectar posibles demoras durante la ejecución.

Cuando la fuente entrega una métrica agregada, como la mediana de Cycle Time, debe conservarse su definición y unidad de medida.

### 4.6 Trabajo no planificado

Representa el trabajo incorporado durante un Sprint que no formaba parte de la planificación inicial.

**Fórmula conceptual:**

Trabajo no planificado (%) = (Trabajo no planificado / Trabajo total considerado) × 100

**Fuente:** requiere campos que permitan identificar y cuantificar el trabajo planificado y no planificado.

**Interpretación:** permite analizar el impacto de solicitudes imprevistas, cambios de prioridad e interrupciones sobre la planificación del equipo.

No debe calcularse cuando la fuente no dispone de información suficiente para identificar ambos componentes.

## 5. Fuente de información

El producto utiliza el dataset:

| Dataset | Información |
|---|---|
| `agile-delivery.csv` | Información de equipos, Sprints, objetivos, compromisos, elementos completados y trabajo pendiente. |

La información debe analizarse considerando el equipo, el Sprint y la fecha de corte correspondiente.

## 6. Criterios de análisis

Para interpretar correctamente los indicadores se deben considerar:

- Diferencias de capacidad entre equipos.
- Alcance y complejidad del trabajo comprometido.
- Cambios de prioridad durante el Sprint.
- Dependencias técnicas y funcionales.
- Trabajo no planificado e interrupciones.
- Sprints cerrados y Sprints en curso.
- Tendencias históricas y comportamiento por equipo.

Los indicadores deben utilizarse para identificar oportunidades de mejora y no para establecer comparaciones descontextualizadas entre equipos.

## 7. Visualización y seguimiento

La información puede organizarse mediante las siguientes vistas:

| Vista | Información principal |
|---|---|
| Resumen de entrega | Cumplimiento de objetivos y compromisos. |
| Seguimiento por equipo | Evolución de indicadores por equipo. |
| Evolución por Sprint | Tendencias de cumplimiento y trabajo pendiente. |
| Flujo de trabajo | Throughput y Cycle Time. |
| Desviaciones | Carry-over y trabajo no planificado, cuando existan datos suficientes. |

## 8. Gobierno y acciones de mejora

El seguimiento de los indicadores debe facilitar acciones relacionadas con:

- Revisión de la planificación de los Sprints.
- Ajuste de compromisos según capacidad disponible.
- Identificación de dependencias e impedimentos.
- Análisis de causas de incumplimiento.
- Reducción del trabajo pendiente.
- Mejora continua del flujo de entrega.
- Coordinación entre equipos y stakeholders.

Las acciones de mejora deben contar con responsables y seguimiento.

## 9. Consideraciones sobre los datos

Los datos del repositorio son DEMO y representan escenarios ficticios de gestión ágil.

Se deben considerar las siguientes restricciones:

- Los Sprints en curso no deben incorporarse a indicadores de cumplimiento de Sprints cerrados.
- Sprint Goal Achievement no equivale al porcentaje de tareas completadas.
- Sprint Commitment Reliability requiere una definición consistente del compromiso inicial.
- Carry-over debe calcularse sobre elementos comprometidos y trasladados.
- Throughput representa volumen de elementos completados, no productividad individual.
- Las métricas agregadas deben conservar su definición original.
- No deben calcularse indicadores cuando faltan campos necesarios para su determinación.

## 10. Resultado esperado

El producto proporciona una visión estructurada del desempeño de la entrega ágil, permitiendo evaluar el cumplimiento de objetivos, la confiabilidad de los compromisos y el comportamiento del flujo de trabajo.

Su propósito es transformar los datos de ejecución de los equipos en información útil para la gestión, la planificación y la mejora continua de la entrega de productos y servicios TI.
