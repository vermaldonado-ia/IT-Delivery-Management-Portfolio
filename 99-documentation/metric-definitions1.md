# Diccionario de Indicadores de Gestión TI

## 1. Objetivo

Establecer un marco común de medición para los tres productos del
portafolio:

1.  Dashboard Ejecutivo de Gestión TI.
2.  Gestión de Proyectos y Entrega Ágil.
3.  Entrega Técnica y Operaciones TI.

Este documento define los indicadores, sus fórmulas de cálculo, unidades
de medida, fuentes de información, períodos, supuestos y criterios de
interpretación.

Su propósito es asegurar la consistencia de las mediciones, facilitar el
seguimiento de la evolución y entregar información confiable para la
toma de decisiones.

**Clasificación de los datos del portafolio:** los cinco datasets
incluidos en esta versión contienen información DEMO (ficticia). Los
resultados y ejemplos numéricos presentados sirven para validar el
modelo de medición; no representan resultados reales de una
organización.

## 2. Modelo común de medición

Todos los indicadores deben seguir una estructura de medición que
permita comparar la situación inicial con su evolución.

  -----------------------------------------------------------------------
  Elemento                            Descripción
  ----------------------------------- -----------------------------------
  Línea base                          Valor inicial medido y validado,
                                      con período y alcance identificados

  Valor actual                        Último resultado disponible para el
                                      período y alcance definidos

  Variación                           Diferencia entre el valor actual y
                                      la línea base

  Meta                                Resultado esperado, cuando haya
                                      sido aprobado

  Estado                              Condición del indicador según
                                      umbrales previamente definidos

  Tendencia                           Evolución del indicador durante los
                                      períodos analizados

  Período                             Intervalo de tiempo considerado en
                                      la medición

  Alcance                             Equipos, iniciativas, servicios o
                                      población incluidos

  Fuente                              Dataset, sistema o registro del que
                                      provienen los datos

  Calidad del dato                    Completitud, consistencia,
                                      trazabilidad y confiabilidad de la
                                      información
  -----------------------------------------------------------------------

### 2.1. Cálculo de variaciones

**Variación absoluta:**

`Valor actual - Línea base`

**Variación porcentual:**

`((Valor actual - Línea base) / Línea base) × 100`

Cuando la línea base sea cero o no permita un cálculo porcentual válido,
se debe informar la variación absoluta o indicar que la variación
porcentual no aplica.

Para indicadores en los que un valor menor representa un mejor resultado
(por ejemplo, latencia, errores o tiempo de recuperación), la dirección
favorable debe interpretarse de acuerdo con la naturaleza del indicador.

### 2.2. Reglas para establecer metas y estados

-   Las metas deben ser aprobadas por los responsables correspondientes.
-   Los umbrales de los semáforos deben definirse según el contexto y
    los objetivos de gestión.
-   No se deben asignar estados de cumplimiento sin criterios
    previamente establecidos.
-   Una mejora o deterioro debe interpretarse según la naturaleza del
    indicador.
-   Cuando no exista información suficiente, se debe utilizar **No
    medido**, **Sin dato** o **Pendiente de validación**, según
    corresponda.
-   Los datos estimados deben diferenciarse de los datos efectivamente
    medidos.
-   Los períodos parciales deben identificarse y no compararse
    directamente con períodos completos.
-   Los denominadores deben representar la misma población, alcance y
    período que los numeradores.

------------------------------------------------------------------------

# 3. Indicadores de Gestión Ejecutiva TI

Orientados a entregar una visión consolidada del desempeño del
portafolio tecnológico para subgerencia, dirección y stakeholders.

  ---------------------------------------------------------------------------------------------------------------------------
  Indicador         Definición        Fórmula de cálculo                                                    Unidad
  ----------------- ----------------- --------------------------------------------------------------------- -----------------
  Predictibilidad   Porcentaje de     `(Hitos cumplidos a tiempo / Hitos planificados del período) × 100`   \%
  de hitos          hitos                                                                                   
                    planificados para                                                                       
                    el período que se                                                                       
                    cumplieron a                                                                            
                    tiempo                                                                                  

  Desviación de     Diferencia entre  `Avance real (%) - Avance planificado (%)`                            Puntos
  avance            el avance real y                                                                        porcentuales (pp)
                    el avance                                                                               
                    planificado de                                                                          
                    una iniciativa                                                                          

  Riesgos críticos  Cantidad de       Conteo de `riesgos_criticos_abiertos` en el corte                     Cantidad
  abiertos          riesgos                                                                                 
                    clasificados como                                                                       
                    críticos que                                                                            
                    permanecen                                                                              
                    abiertos en la                                                                          
                    fecha de corte                                                                          

  Cumplimiento de   Porcentaje de     `(Casos SLA cumplidos / Casos SLA elegibles) × 100`                   \%
  SLA ejecutivo     casos elegibles                                                                         
                    de una iniciativa                                                                       
                    que cumplieron el                                                                       
                    SLA en el período                                                                       

  Disponibilidad    Porcentaje de     Valor de `disponibilidad_pct` informado en `executive-kpis.csv`       \%
  ejecutiva         disponibilidad                                                                          
                    reportado para                                                                          
                    una iniciativa en                                                                       
                    el corte                                                                                
  ---------------------------------------------------------------------------------------------------------------------------

### 3.1. Fuentes y campos

Fuente principal: `executive-kpis.csv`.

  -----------------------------------------------------------------------
  Indicador                           Campos
  ----------------------------------- -----------------------------------
  Predictibilidad de hitos            `hitos_cumplidos_a_tiempo`,
                                      `hitos_planificados_periodo`

  Desviación de avance                `avance_real_pct`,
                                      `avance_planificado_pct`

  Riesgos críticos abiertos           `riesgos_criticos_abiertos`

  Cumplimiento de SLA ejecutivo       `casos_sla_cumplidos`,
                                      `casos_sla_elegibles`

  Disponibilidad ejecutiva            `disponibilidad_pct`

  Trazabilidad                        `fecha_corte`, `iniciativa_id`,
                                      `iniciativa`, `origen_dato`,
                                      `tipo_dato`
  -----------------------------------------------------------------------

### 3.2. Criterios de interpretación

-   La predictibilidad se calcula sobre los hitos planificados del
    período, no sobre todos los hitos históricos de la iniciativa.
-   Un hito no cumplido dentro de su fecha comprometida no se considera
    cumplido a tiempo.
-   Los cambios de alcance deben quedar registrados y tener un
    tratamiento consistente.
-   La desviación de avance se expresa en puntos porcentuales (pp), no
    como variación porcentual relativa.
-   `riesgos_criticos_abiertos` representa la cantidad abierta en la
    fecha de corte; no debe sumarse entre cortes como si fueran riesgos
    nuevos, porque un mismo riesgo puede permanecer abierto en más de un
    período.
-   El cumplimiento de SLA ejecutivo utiliza la población elegible
    registrada para cada iniciativa y corte. No debe asumirse que
    coincide con la población de incidentes de `incidents.csv`.
-   La disponibilidad ejecutiva se toma del valor informado en
    `executive-kpis.csv`. No puede recalcularse ni reconciliarse
    automáticamente con `cloud-monitoring.csv` mientras no exista un
    mapeo completo y validado entre iniciativas y servicios, además de
    períodos compatibles.
-   El corte del 7 de noviembre de 2026 es parcial y no debe compararse
    directamente con los cierres mensuales completos.
-   Los datos de este dataset están clasificados como DEMO y tienen como
    origen `Datos ficticios`.

------------------------------------------------------------------------

# 4. Indicadores de Gestión de Proyectos y Entrega Ágil

Orientados al seguimiento de equipos, proyectos, planificación, flujo de
trabajo y evolución de la gestión ágil.

## 4.1. Desempeño de Sprint

  ------------------------------------------------------------------------------------------------------------------------------------------------------
  Indicador         Definición        Fórmula de cálculo                                                                               Unidad
  ----------------- ----------------- ------------------------------------------------------------------------------------------------ -----------------
  Sprint Goal       Porcentaje de     `(Sprints finalizados con objetivo alcanzado / Total de Sprints finalizados evaluables) × 100`   \%
  Achievement       Sprints                                                                                                            
                    finalizados cuyo                                                                                                   
                    objetivo fue                                                                                                       
                    alcanzado                                                                                                          

  Sprint Commitment Porcentaje de     `(Elementos comprometidos y completados / Elementos comprometidos al inicio) × 100`              \%
  Reliability       elementos                                                                                                          
                    comprometidos al                                                                                                   
                    inicio del Sprint                                                                                                  
                    que fueron                                                                                                         
                    completados                                                                                                        

  Carry-over        Cantidad de       `carry_over`                                                                                     Elementos
                    elementos del                                                                                                      
                    compromiso                                                                                                         
                    inicial que                                                                                                        
                    quedaron                                                                                                           
                    pendientes al                                                                                                      
                    cierre del Sprint                                                                                                  

  Carry-over %      Proporción de     `(carry_over / elementos_comprometidos) × 100`                                                   \%
                    elementos                                                                                                          
                    comprometidos                                                                                                      
                    inicialmente que                                                                                                   
                    quedaron                                                                                                           
                    pendientes al                                                                                                      
                    cierre                                                                                                             

  Unplanned Work    Cantidad de       `trabajo_no_planificado`                                                                         Elementos
                    elementos                                                                                                          
                    incorporados                                                                                                       
                    después del                                                                                                        
                    inicio del Sprint                                                                                                  
  ------------------------------------------------------------------------------------------------------------------------------------------------------

### Fuentes y campos

Fuente: `agile-delivery.csv`.

Campos: `sprint_goal_alcanzado`, `elementos_comprometidos`,
`elementos_completados`, `carry_over`, `trabajo_no_planificado`,
`fecha_inicio`, `fecha_fin`, `equipo_id`, `equipo`, `proyecto`, `sprint`
y `tipo_dato`.

### Criterios de interpretación

-   Sprint Goal Achievement mide el logro del objetivo del Sprint; no
    equivale al porcentaje de tareas o elementos completados.
-   Sprint Commitment Reliability mide la proporción del compromiso
    inicial completado. No mide directamente valor de negocio ni
    calidad.
-   El cálculo de Sprint Commitment Reliability supone que los elementos
    pendientes corresponden a compromisos iniciales no completados y que
    no existen cancelaciones u otros ajustes que alteren su
    contabilización. Si existen, deben documentarse y tratarse de forma
    consistente.
-   Carry-over debe analizarse junto con sus causas: dependencias,
    bloqueos, cambios de prioridad, estimaciones o capacidad.
-   El porcentaje de Carry-over utiliza como denominador
    `elementos_comprometidos`; si este valor es cero, el porcentaje no
    aplica.
-   Los elementos incorporados después del inicio deben identificarse
    como trabajo no planificado.
-   Los Sprints en curso no se incluyen en los cálculos de cumplimiento
    de Sprints finalizados.
-   En el dataset actual, S12 tiene estado de objetivo `Pendiente` y
    fecha de término posterior al corte de información. Por tanto, debe
    excluirse de las comparaciones entre Sprints cerrados.
-   La velocidad o cantidad de elementos completados no debe utilizarse
    como medida aislada de productividad ni para comparar equipos
    diferentes.

## 4.2. Flujo de entrega

  -----------------------------------------------------------------------------------
  Indicador         Definición        Fórmula o método de cálculo Unidad
  ----------------- ----------------- --------------------------- -------------------
  Throughput        Cantidad de       Conteo de elementos         Elementos/período
                    elementos de      completados en el período;  
                    trabajo           en el dataset se utiliza    
                    completados       `throughput`                
                    durante un                                    
                    período                                       

  Cycle Time        Tiempo            Mediana del tiempo entre    Días
                    transcurrido      inicio de trabajo y         
                    desde que         finalización; campo         
                    comienza el       disponible:                 
                    trabajo hasta que `cycle_time_mediana_dias`   
                    el elemento se                                
                    completa                                      

  Lead Time         Tiempo            Mediana del tiempo entre    Días
                    transcurrido      solicitud y entrega; campo  
                    desde que se      disponible:                 
                    solicita un       `lead_time_mediana_dias`    
                    elemento hasta                                
                    que se entrega                                

  WIP               Cantidad promedio Promedio de elementos en    Elementos
                    de elementos que  estados definidos como      
                    permanecen en     trabajo en curso; campo     
                    ejecución         disponible: `wip_promedio`  

  Impedimentos      Cantidad de       Campo disponible:           Cantidad
                    impedimentos      `impedimentos`              
                    registrados                                   
                    durante el Sprint                             

  Defectos          Cantidad de       Campo disponible:           Cantidad
                    defectos          `defectos`                  
                    registrados                                   
                    durante el Sprint                             

  Retrabajo         Cantidad de       Campo disponible:           Elementos
                    elementos que     `retrabajo_elementos`       
                    requirieron                                   
                    trabajo adicional                             
                    o corrección                                  
  -----------------------------------------------------------------------------------

### Criterios de interpretación

-   Throughput debe analizarse por período, equipo y tipo de elemento.
-   Cycle Time y Lead Time deben utilizar estados de inicio y término
    claramente definidos.
-   En este dataset, Cycle Time y Lead Time están representados mediante
    medianas en días; no deben interpretarse como promedios.
-   Se recomienda analizar mediana y percentiles, además del promedio,
    cuando la fuente disponga de datos individuales.
-   WIP debe observarse junto con la capacidad y el flujo del equipo.
-   Los impedimentos y defectos deben analizarse considerando su
    impacto, severidad y duración, cuando esa información esté
    disponible.
-   El retrabajo debe interpretarse junto con defectos, calidad y causas
    de corrección.
-   La velocidad de un equipo no debe utilizarse como medida de
    productividad ni para comparar equipos diferentes.

------------------------------------------------------------------------

# 5. Indicadores de Entrega Técnica y Operaciones TI

Este producto reúne indicadores de desempeño de entrega de software,
monitoreo de infraestructura, observabilidad y gestión de servicios
tecnológicos.

## 5.1. Métricas DORA

Las métricas DORA permiten evaluar el desempeño de la entrega de
software desde las dimensiones de velocidad y estabilidad.

  -------------------------------------------------------------------------------------------------------------------------------
  Indicador DORA    Definición        Fórmula o método de cálculo                                           Unidad
  ----------------- ----------------- --------------------------------------------------------------------- ---------------------
  Deployment        Frecuencia de     Conteo de despliegues exitosos en producción por servicio y período   Despliegues/período
  Frequency         despliegues                                                                             
                    exitosos en                                                                             
                    producción                                                                              

  Lead Time for     Tiempo desde que  Fecha/hora de despliegue en producción menos fecha/hora de            Tiempo
  Changes           un cambio se      confirmación del cambio                                               
                    confirma en el                                                                          
                    repositorio hasta                                                                       
                    que llega a                                                                             
                    producción                                                                              

  Change Failure    Porcentaje de     `(Despliegues fallidos / Total de despliegues en producción) × 100`   \%
  Rate              despliegues en                                                                          
                    producción que                                                                          
                    provocan una                                                                            
                    falla y requieren                                                                       
                    intervención o                                                                          
                    corrección                                                                              

  Failed Deployment Tiempo            Promedio de `tiempo_recuperacion_minutos` para despliegues fallidos   Minutos
  Recovery Time     transcurrido                                                                            
                    desde el impacto                                                                        
                    asociado a un                                                                           
                    despliegue                                                                              
                    fallido hasta la                                                                        
                    recuperación del                                                                        
                    servicio                                                                                
  -------------------------------------------------------------------------------------------------------------------------------

### Fuentes y campos

Fuente principal: `deployments.csv`.

-   Deployment Frequency: `fecha_despliegue`, `servicio_id`, `entorno`,
    `estado_despliegue`.
-   Lead Time for Changes: `lead_time_cambios_horas`.
-   Change Failure Rate: `fallo_cambio`, `estado_despliegue`, `entorno`.
-   Failed Deployment Recovery Time: `tiempo_recuperacion_minutos`,
    filtrando despliegues fallidos en producción.
-   Trazabilidad: `deployment_id`, `incidente_id`, `origen_dato`,
    `tipo_dato`.

### Criterios de interpretación DORA

-   Deployment Frequency debe contar despliegues exitosos en producción.
    Los despliegues fallidos no incrementan la frecuencia de despliegues
    exitosos.
-   La frecuencia debe calcularse por servicio y período definido; no se
    deben mezclar ambientes de desarrollo, pruebas y producción.
-   Lead Time for Changes requiere timestamp de confirmación del cambio
    en el repositorio y timestamp de despliegue en producción.
-   En el dataset actual, `lead_time_cambios_horas` está disponible como
    valor agregado por despliegue, pero no se incluyen timestamps
    individuales de commit ni de inicio del cambio. Por ello, se debe
    presentar como una aproximación registrada y no como una medición
    end-to-end recalculable desde eventos fuente.
-   Change Failure Rate utiliza como denominador todos los despliegues
    registrados en producción durante el período y como numerador
    aquellos marcados como fallidos o que provocaron una falla asociada.
-   En el dataset actual existen 48 despliegues de producción: 7
    fallidos y 41 exitosos. El resultado DEMO es
    `(7 / 48) × 100 = 14,58 %`.
-   Failed Deployment Recovery Time utiliza
    `tiempo_recuperacion_minutos` de `deployments.csv` para los
    despliegues fallidos. No debe reemplazarse por el tiempo total de
    resolución de todos los incidentes.
-   En los siete despliegues fallidos, el tiempo promedio de
    recuperación es 89,3 minutos.
-   Los siete despliegues fallidos tienen un incidente vinculado
    mediante `incidente_id`. Los valores de recuperación se reconcilian
    con los registros relacionados de `incidents.csv`.
-   Las cuatro métricas deben analizarse en conjunto. La frecuencia de
    despliegues no representa por sí sola calidad o valor de negocio.
-   No se deben comparar equipos sin considerar diferencias de
    arquitectura, producto, criticidad y proceso de entrega.

## 5.2. Monitoreo Cloud y Observabilidad

Indicadores orientados al seguimiento de la salud, disponibilidad y
comportamiento de aplicaciones e infraestructura tecnológica.

  ----------------------------------------------------------------------------------
  Indicador         Definición        Fórmula o método de cálculo  Unidad
  ----------------- ----------------- ---------------------------- -----------------
  Disponibilidad    Porcentaje de     Valor registrado en          \%
                    disponibilidad    `disponibilidad_pct`         
                    del servicio                                   
                    durante el                                     
                    intervalo                                      
                    evaluado                                       

  Latencia p95      Tiempo de         Percentil 95 de los tiempos  ms
                    respuesta por     de respuesta; valor          
                    debajo del cual   registrado en                
                    se encuentra el   `latencia_p95_ms`            
                    95 % de las                                    
                    solicitudes                                    
                    observadas                                     

  Tasa de errores   Proporción de     Valor registrado en          \%
                    solicitudes que   `tasa_errores_pct`           
                    presentan errores                              
                    respecto del                                   
                    total de                                       
                    solicitudes                                    

  Utilización de    Porcentaje        Valor registrado en          \%
  CPU               promedio de       `cpu_promedio_pct`           
                    capacidad de                                   
                    procesamiento                                  
                    utilizada                                      

  Utilización de    Porcentaje        Valor registrado en          \%
  memoria           promedio de       `memoria_promedio_pct`       
                    memoria utilizada                              

  Utilización de    Porcentaje de     Valor registrado en          \%
  almacenamiento    almacenamiento    `almacenamiento_usado_pct`   
                    utilizado                                      

  Tráfico de red    Volumen de datos  Valor registrado en          GB
  entrante          recibidos durante `trafico_entrada_gb`         
                    el intervalo                                   

  Tráfico de red    Volumen de datos  Valor registrado en          GB
  saliente          enviados durante  `trafico_salida_gb`          
                    el intervalo                                   

  Costo Cloud       Costo Cloud       Valor registrado en          USD
                    registrado para   `costo_cloud_usd`            
                    el servicio y                                  
                    corte                                          

  Alertas críticas  Cantidad de       Conteo registrado en         Cantidad
                    alertas           `alertas_criticas`           
                    clasificadas como                              
                    críticas en el                                 
                    corte                                          
  ----------------------------------------------------------------------------------

### Fuentes y campos

Fuente: `cloud-monitoring.csv`.

Campos: `fecha_corte`, `servicio_id`, `servicio`, `proveedor_cloud`,
`entorno`, `disponibilidad_pct`, `latencia_p95_ms`, `tasa_errores_pct`,
`cpu_promedio_pct`, `memoria_promedio_pct`, `almacenamiento_usado_pct`,
`trafico_entrada_gb`, `trafico_salida_gb`, `costo_cloud_usd`,
`alertas_criticas`, `origen_dato` y `tipo_dato`.

### Criterios de interpretación

-   La latencia p95 representa el percentil 95 de los tiempos de
    respuesta: el 95 % de las solicitudes tiene un tiempo de respuesta
    igual o inferior a ese valor.
-   La tasa de errores debe utilizar una clasificación consistente de
    errores y solicitudes.
-   CPU, memoria y almacenamiento deben analizarse considerando
    capacidad, carga y comportamiento del servicio.
-   El tráfico de red debe identificar por separado información entrante
    y saliente.
-   Los costos Cloud deben considerar moneda, período, servicios
    incluidos y criterios de imputación.
-   La disponibilidad debe utilizar la misma ventana de servicio
    definida para el indicador.
-   Los umbrales de alerta deben establecerse según las características
    y criticidad del servicio.
-   El dataset actual contiene 20 registros, correspondientes a cuatro
    servicios y cinco cortes semanales de septiembre de 2026.
-   Los registros corresponden a AWS, entorno Producción, origen
    CloudWatch y clasificación DEMO.
-   `fecha_corte` representa observaciones semanales; no es telemetría
    continua ni información en tiempo real.
-   `costo_cloud_usd` contiene valores DEMO asociados a los cortes
    semanales. No debe presentarse como facturación real de AWS ni
    sumarse como gasto mensual sin validar el criterio temporal y de
    acumulación.
-   No existe un mapeo completo y validado entre `iniciativa_id` de
    `executive-kpis.csv` y `servicio_id` de este dataset. Por lo tanto,
    no se debe derivar directamente la disponibilidad ejecutiva por
    iniciativa a partir de estos registros.

## 5.3. Operaciones y Gestión de Servicios TI

Indicadores orientados a evaluar la continuidad operacional, atención de
incidentes y cumplimiento de compromisos de servicio.

  ----------------------------------------------------------------------------------------------------------------------------------
  Indicador         Definición        Fórmula o método de cálculo                                                  Unidad
  ----------------- ----------------- ---------------------------------------------------------------------------- -----------------
  Cantidad de       Total de          Conteo de `incidente_id` únicos                                              Cantidad
  incidentes        incidentes                                                                                     
                    registrados                                                                                    
                    durante el                                                                                     
                    período                                                                                        

  MTTR operacional  Tiempo promedio   `Suma de tiempo_resolucion_minutos / Cantidad de incidentes recuperados`     Minutos
                    desde la apertura                                                                              
                    del incidente                                                                                  
                    hasta la                                                                                       
                    recuperación del                                                                               
                    servicio                                                                                       

  Cumplimiento de   Porcentaje de     `(Incidentes con sla_cumplido = Sí / Total de incidentes elegibles) × 100`   \%
  SLA de incidentes incidentes                                                                                     
                    elegibles que                                                                                  
                    cumplieron el SLA                                                                              
                    objetivo                                                                                       

  Incidentes        Cantidad de       Conteo de incidentes con `severidad = Crítica`                               Cantidad
  críticos          incidentes                                                                                     
                    clasificados con                                                                               
                    severidad Crítica                                                                              
  ----------------------------------------------------------------------------------------------------------------------------------

### Fuentes y campos

Fuente: `incidents.csv`.

Campos: `incidente_id`, `fecha_apertura`, `fecha_deteccion`,
`fecha_recuperacion`, `servicio_id`, `servicio`, `severidad`,
`categoria`, `origen`, `relacion_despliegue`, `deployment_id`,
`tiempo_resolucion_minutos`, `tiempo_recuperacion_minutos`,
`sla_objetivo_minutos`, `sla_cumplido`, `causa_raiz`, `estado`,
`origen_dato` y `tipo_dato`.

### Criterios de interpretación

-   La clasificación de incidentes debe utilizar una matriz de severidad
    documentada.
-   El MTTR operacional de este diccionario se calcula con
    `tiempo_resolucion_minutos`, que representa el tiempo desde la
    apertura hasta la recuperación/resolución registrada para el
    incidente.
-   El dataset actual contiene 15 incidentes resueltos. La suma de
    `tiempo_resolucion_minutos` es 1.736 minutos y el promedio es
    `1.736 / 15 = 115,7 minutos`.
-   El cumplimiento de SLA utiliza incidentes elegibles con valor de
    cumplimiento registrado. En el dataset actual hay 15 incidentes
    elegibles: 12 cumplidos y 3 incumplidos, equivalente a
    `(12 / 15) × 100 = 80 %`.
-   Los incidentes críticos se cuentan exclusivamente cuando
    `severidad = Crítica`. No se deben incorporar incidentes de
    severidad Alta si la definición del indicador se limita a Crítica.
-   Los incidentes recurrentes deben analizarse para identificar causas
    y oportunidades de prevención.
-   La cantidad de incidentes no debe interpretarse de forma aislada,
    sin considerar criticidad, impacto y volumen de operación.
-   `tiempo_recuperacion_minutos` mide el intervalo desde la detección
    hasta la recuperación. Se utiliza para la comparación con el tiempo
    de recuperación DORA cuando el incidente está vinculado a un
    despliegue fallido.
-   El MTTR operacional y Failed Deployment Recovery Time de DORA no son
    intercambiables: utilizan poblaciones y puntos de inicio distintos.

### 5.3.1. MTTR operacional versus recuperación DORA

  -------------------------------------------------------------------------------------
  Dimensión               MTTR operacional              Failed Deployment Recovery Time
                                                        (DORA)
  ----------------------- ----------------------------- -------------------------------
  Fuente principal        `incidents.csv`               `deployments.csv`

  Campo de cálculo        `tiempo_resolucion_minutos`   `tiempo_recuperacion_minutos`

  Inicio de medición      Apertura del incidente        Impacto asociado al despliegue
                                                        fallido / recuperación
                                                        registrada

  Población               Todos los incidentes          Solo despliegues fallidos en
                          elegibles y recuperados       producción

  Resultado DEMO actual   115,7 minutos                 89,3 minutos

  Uso                     Evaluar el tiempo operacional Evaluar la recuperación
                          de resolución/recuperación de asociada a cambios fallidos
                          incidentes                    
  -------------------------------------------------------------------------------------

Los siete incidentes vinculados a despliegues fallidos (INC-001 a
INC-007) corresponden a los siete despliegues fallidos registrados. Los
valores de `tiempo_recuperacion_minutos` coinciden entre ambos datasets
para esas relaciones.

No se deben comparar ambos promedios como si midieran exactamente el
mismo proceso. El MTTR operacional incluye 15 incidentes y mide desde la
apertura; la métrica DORA considera siete despliegues fallidos y utiliza
el tiempo de recuperación asociado al despliegue.

------------------------------------------------------------------------

# 6. Gobierno de los Indicadores

Cada indicador incorporado a un dashboard debe contar con una ficha de
definición y gobierno.

  -----------------------------------------------------------------------
  Campo                               Descripción
  ----------------------------------- -----------------------------------
  Nombre                              Nombre oficial del indicador

  Objetivo                            Propósito de gestión que busca
                                      apoyar

  Definición                          Descripción precisa de lo que se
                                      mide

  Fórmula                             Método de cálculo documentado

  Unidad                              Porcentaje, cantidad, tiempo, costo
                                      u otra unidad

  Frecuencia                          Diaria, semanal, por Sprint,
                                      mensual u otra

  Período                             Intervalo utilizado para la
                                      medición

  Alcance                             Equipos, servicios, proyectos o
                                      población considerada

  Fuente                              Sistema o dataset de origen de la
                                      información

  Campos                              Columnas utilizadas para numerador,
                                      denominador y trazabilidad

  Responsable del dato                Persona o área responsable de la
                                      calidad del registro

  Responsable de gestión              Persona o área que interpreta y
                                      utiliza el indicador

  Línea base                          Valor inicial validado

  Meta                                Objetivo aprobado, cuando exista

  Umbrales                            Criterios definidos para
                                      interpretar el estado

  Calidad del dato                    Nivel de completitud, consistencia
                                      y confiabilidad

  Fecha de actualización              Última fecha de actualización de la
                                      medición

  Limitaciones                        Supuestos, exclusiones y
                                      restricciones de comparabilidad
  -----------------------------------------------------------------------

## 6.1. Fuentes de información del portafolio

Los cinco datasets incluidos en este portafolio son:

  --------------------------------------------------------------------------------
  Dataset                  Propósito                    Registros Período /
                                                                  granularidad
  ------------------------ ---------------- --------------------- ----------------
  `executive-kpis.csv`     Indicadores                         36 Seis iniciativas
                           ejecutivos por                         y seis cortes
                           iniciativa                             entre junio y
                                                                  noviembre de
                                                                  2026

  `agile-delivery.csv`     Métricas de                         48 Cuatro equipos y
                           Sprint y flujo                         doce Sprints por
                           ágil                                   equipo

  `deployments.csv`        Despliegues y                       48 Cuatro
                           métricas DORA                          servicios, junio
                                                                  a septiembre de
                                                                  2026

  `cloud-monitoring.csv`   Monitoreo Cloud                     20 Cuatro servicios
                           y observabilidad                       y cinco cortes
                                                                  semanales de
                                                                  septiembre de
                                                                  2026

  `incidents.csv`          Incidentes,                         15 Incidentes
                           recuperación y                         registrados
                           SLA                                    entre junio y
                                                                  septiembre de
                                                                  2026
  --------------------------------------------------------------------------------

Total: **167 registros**. Los cinco datasets están clasificados como
DEMO.

### 6.1.1. Sistemas de origen representados

Según los campos de trazabilidad de los datasets, se representan las
siguientes fuentes: datos ficticios para los indicadores ejecutivos,
registros DEMO de gestión ágil, despliegues, CloudWatch para monitoreo y
registros DEMO de incidentes. La presencia de un nombre de herramienta o
plataforma en un dataset no implica que exista una conexión operacional
real con dicha herramienta.

## 6.2. Trazabilidad de los indicadores

Cada indicador debe permitir identificar:

-   Nombre y definición.
-   Objetivo de medición.
-   Fórmula o criterio de cálculo.
-   Unidad de medida.
-   Dataset y campos de origen.
-   Período de medición y fecha de corte.
-   Población y alcance considerados.
-   Responsable de seguimiento.
-   Limitaciones y supuestos conocidos.
-   Clasificación del dato (DEMO, REAL o PENDIENTE DE VALIDACIÓN).

## 6.3. Calidad y consistencia de los datos

Antes de utilizar un indicador en un análisis ejecutivo se debe
verificar:

-   Integridad de los registros.
-   Consistencia de fechas y períodos.
-   Ausencia de duplicados en identificadores que deban ser únicos.
-   Correspondencia entre identificadores relacionados.
-   Unidades de medida.
-   Coherencia entre numeradores y denominadores.
-   Identificación de datos faltantes o no validados.
-   Consistencia de estados y criterios de inclusión.
-   Diferenciación entre períodos completos y parciales.

### 6.3.1. Relaciones y límites entre datasets

-   Los siete despliegues fallidos de `deployments.csv` se vinculan con
    siete incidentes mediante `incidente_id` y `deployment_id`. Los
    tiempos de recuperación asociados coinciden entre ambos datasets.
-   `executive-kpis.csv` y `incidents.csv` contienen indicadores de SLA
    con poblaciones y alcances diferentes. No se debe exigir que sus
    porcentajes coincidan.
-   La disponibilidad ejecutiva por iniciativa no puede derivarse
    directamente de `cloud-monitoring.csv`, porque no existe un mapeo
    completo y validado entre iniciativas y servicios y los períodos de
    medición no son equivalentes.
-   Los cortes semanales de Cloud Monitoring no deben compararse
    directamente con los cortes ejecutivos mensuales o parciales sin
    definir una regla de agregación y alineación temporal.
-   El corte ejecutivo del 7 de noviembre de 2026 es parcial y debe
    distinguirse de los cierres mensuales.
-   El Sprint S12 está en curso en el corte disponible y debe excluirse
    de las comparaciones de Sprints finalizados.
-   Los valores de costo Cloud son DEMO y no representan facturación
    real.

## 6.4. Tratamiento de datos faltantes

Cuando no exista información suficiente para calcular un indicador,
utilizar una clasificación explícita:

-   **Sin dato:** no existe información disponible para el período.
-   **No medido:** la fuente no registra el indicador requerido.
-   **Pendiente de validación:** existe información, pero no se ha
    confirmado su calidad.
-   **No aplica:** el indicador no corresponde al contexto analizado.
-   **En curso:** el período o actividad todavía no ha finalizado y el
    resultado no puede considerarse definitivo.

No se deben sustituir datos faltantes por cero ni generar resultados
estimados sin identificar explícitamente el supuesto utilizado.

## 6.5. Clasificación de los datos

-   **DEMO:** datos ficticios utilizados para demostrar el
    funcionamiento del modelo.
-   **REAL:** datos provenientes de sistemas o fuentes operacionales
    verificables y autorizadas.
-   **PENDIENTE DE VALIDACIÓN:** información cuyo origen, consistencia o
    exactitud todavía no ha sido comprobada.

Los datos DEMO no deben presentarse como resultados reales de
organizaciones o clientes.

## 6.6. Evolución y mantenimiento

El diccionario debe mantenerse actualizado cuando:

-   Se incorporen nuevos indicadores.
-   Cambien las fuentes de información.
-   Se modifiquen fórmulas o criterios de cálculo.
-   Se incorporen nuevas plataformas o servicios.
-   Se identifiquen limitaciones o problemas de calidad en los datos.

Toda modificación debe conservar la trazabilidad entre la fuente, el
modelo de datos, el indicador y su representación en los dashboards.

------------------------------------------------------------------------

# 7. Principios de Interpretación Ejecutiva

Los indicadores deben interpretarse considerando el contexto
operacional, el período de medición y las características de cada equipo
o servicio.

1.  **Output no es Outcome:** completar trabajo no demuestra
    automáticamente la obtención de valor de negocio.
2.  **Velocidad no es productividad:** los puntos de historia y la
    velocidad no deben utilizarse para comparar equipos.
3.  **Despliegues no equivalen a valor entregado:** Deployment Frequency
    mide actividad de entrega técnica, no impacto de negocio.
4.  **Disponibilidad no equivale a ausencia de incidentes:** un servicio
    puede presentar incidentes sin superar su umbral de
    indisponibilidad.
5.  **Correlación no demuestra causalidad:** no atribuir fallas a
    despliegues sin evidencia.
6.  **Los indicadores deben analizarse en conjunto:** una mejora en una
    métrica no siempre significa una mejora global.
7.  **Comparabilidad requiere equivalencia:** no comparar períodos,
    equipos, servicios o poblaciones sin validar alcance, granularidad y
    reglas de cálculo.
8.  **Los datos DEMO no son resultados operacionales:** los valores
    ficticios sirven para demostrar cálculos y visualizaciones, no para
    evaluar el desempeño real de una organización.

------------------------------------------------------------------------

# 8. Aplicación del Diccionario en el Portafolio

  -----------------------------------------------------------------------
  Producto                            Indicadores principales
  ----------------------------------- -----------------------------------
  01\. Dashboard Ejecutivo de Gestión Predictibilidad de hitos,
  TI                                  desviación de avance, riesgos
                                      críticos abiertos, cumplimiento de
                                      SLA ejecutivo y disponibilidad
                                      ejecutiva

  02\. Gestión de Proyectos y Entrega Sprint Goal Achievement, Sprint
  Ágil                                Commitment Reliability, Carry-over,
                                      Unplanned Work, Throughput, Cycle
                                      Time, Lead Time, WIP, impedimentos,
                                      defectos y retrabajo

  03\. Entrega Técnica y Operaciones  Métricas DORA, disponibilidad,
  TI                                  latencia, errores, utilización de
                                      recursos, tráfico, costos Cloud,
                                      alertas, incidentes, MTTR
                                      operacional y SLA de incidentes
  -----------------------------------------------------------------------

El Dashboard Ejecutivo puede consolidar indicadores de los productos 02
y 03, manteniendo el detalle técnico y operativo en sus respectivos
módulos. La consolidación debe respetar la trazabilidad, los períodos y
las poblaciones de cada indicador; no se deben combinar métricas que no
sean directamente comparables.

------------------------------------------------------------------------

## 9. Principio de Gestión

**Medir para comprender. Analizar para decidir. Actuar para mejorar.**

El valor de un indicador no está únicamente en su resultado numérico,
sino en la capacidad de explicar una situación, identificar
desviaciones, anticipar riesgos y respaldar decisiones de gestión.

Este diccionario constituye la referencia metodológica para definir,
calcular, interpretar y presentar los indicadores del portafolio.

> Todos los datos de demostración de este portafolio son ficticios y no
> representan el desempeño de ninguna organización real.
