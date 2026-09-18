# Etapa 10 - Conclusiones y recomendaciones

## 1. Propósito

Transformar los resultados existentes en conclusiones, implicancias y sugerencias para la toma de decisiones. Se mantiene la secuencia **dato → interpretación → sugerencia**: lo observado fundamenta preguntas y propuestas, sin demostrar sus causas ni anticipar la efectividad de una intervención.

El trabajo es un ejercicio académico sobre un **dataset ficticio de 2500 registros**, con relaciones incorporadas en su generación. Los resultados describen estos registros y no representan automáticamente a la población argentina. El índice es operacional y el modelo predictivo no constituye una herramienta clínica.

Fuentes documentales: [EDA](04_eda.md), [relaciones](05_relaciones.md), [vulnerabilidad](06_vulnerabilidad.md), [modelado](07_modelado.md), [selección de hallazgos](08_seleccion_hallazgos.md) y [dashboard](09_dashboard.md). Las cifras se recuperan de estos informes, sin nuevos análisis ni recálculos. Las decisiones del dashboard documentadas en Etapa 9 resuelven las alternativas que permanecían pendientes en Etapa 8.

## 2. Conclusiones principales

### Conclusión 1. Los indicadores globales requieren una lectura segmentada

- **HALLAZGO:** Los resúmenes generales describen el conjunto, pero no bastan para caracterizar las diferencias de acceso y atención.
- **EVIDENCIA:** Espera media de 64.58 minutos y mediana de 54, con N=2426; acceso a medicación de 67.80%, con N=2500; satisfacción mediana de 4/5, con N=2428. El dashboard agrega el promedio de satisfacción de 3.56/5. Fuentes: Etapas 4 y 9, sección 5.
- **INTERPRETACIÓN:** La diferencia entre media y mediana de espera y los contrastes por segmentos documentados en las etapas siguientes justifican acompañar los totales con distribuciones y denominadores.
- **LIMITACIÓN:** Los indicadores usan distintos N válidos. El promedio de satisfacción resume una escala ordinal y no demuestra intervalos iguales entre niveles.

### Conclusión 2. La espera difiere entre coberturas

- **HALLAZGO:** Las mayores esperas observadas corresponden al grupo Sin cobertura, seguido de Pública y Privada.
- **EVIDENCIA:** Medias de 106.11, 70.19 y 17.60 minutos, respectivamente; medianas de 105, 71 y 18 minutos. N válidos: 826, 777 y 823. Fuente: Etapa 5, sección 3; redondeo corroborado en Etapa 9, sección 9.
- **INTERPRETACIÓN:** La segmentación por cobertura permite ubicar dónde convendría investigar los procesos asociados a las demoras.
- **LIMITACIÓN:** Se excluyen 74 registros sin espera. Las diferencias no identifican un efecto causal de la cobertura; el contraste global previo tampoco establece significación para cada par.

### Conclusión 3. La combinación de cobertura y condición de salud aporta detalle sobre el acceso a medicación

- **HALLAZGO:** El acceso observado varía entre combinaciones y alcanza su menor porcentaje en Sin cobertura / Crónica.
- **EVIDENCIA:** Privada / Aguda: 89.22% (240/269); Sin cobertura / Crónica: 41.99% (118/281). La tabla completa describe las nueve combinaciones sobre N=2500. Fuente: Etapa 5, sección 6.
- **INTERPRETACIÓN:** Sin cobertura / Crónica es un segmento prioritario para investigar barreras de acceso dentro del ejercicio; el promedio global no expresa esta diferencia.
- **LIMITACIÓN:** La comparación es descriptiva, sin pruebas específicas entre celdas, efectos ajustados ni evaluación de interacción. No identifica qué barreras explican el patrón.

### Conclusión 4. La satisfacción se relaciona con la espera y el acceso a medicación

- **HALLAZGO:** Mayores esperas se asocian con menor satisfacción; también se observan distribuciones distintas según acceso a medicación.
- **EVIDENCIA:** Spearman entre espera y satisfacción: ρ=−0.7402, p < 0.001, N=2357. Con acceso a medicación, mediana de satisfacción 4 (N=1640); sin acceso, mediana 3 (N=788). Fuente: Etapa 5, secciones 7 y 8.
- **INTERPRETACIÓN:** La experiencia reportada conviene leerse junto con las condiciones de acceso y atención, manteniendo la distribución ordinal 1–5.
- **LIMITACIÓN:** La correlación no está ajustada por otras variables y excluye 143 registros sin alguna de las dos variables. La comparación por medicación es descriptiva; ninguna de las dos relaciones demuestra causalidad.

### Conclusión 5. El índice permite describir acumulación de dimensiones

- **HALLAZGO:** La coexistencia de las tres dimensiones operacionales tiene distinta presencia según cobertura.
- **EVIDENCIA:** Scores 0/1/2/3: 904/937/471/114 registros, con N=2426. Score 3 por cobertura: Privada 0.00%, Pública 3.09% y Sin cobertura 10.90%; N respectivos 823/777/826. Fuente: Etapa 6, secciones 4 y 6.
- **INTERPRETACIÓN:** El índice ayuda a localizar segmentos donde coinciden condición crónica, falta de acceso a medicación y espera ≥99 minutos. La cobertura sirve para segmentar y no integra la fórmula.
- **LIMITACIÓN:** El score cuenta dimensiones, no gravedad ni riesgo clínico. Depende del umbral y de pesos iguales; un mismo score puede reunir perfiles diferentes. Los 74 registros sin score no equivalen a score 0.

### Conclusión 6. La acumulación de dimensiones se acompaña de diferencias en satisfacción

- **HALLAZGO:** Los scores 2 y 3 presentan medianas de satisfacción menores que los scores 0 y 1.
- **EVIDENCIA:** Medianas por score 0/1/2/3: 4/4/3/2; N respectivos con ambas variables disponibles: 874/912/457/114, total N=2357. Fuente: Etapa 6, sección 8.
- **INTERPRETACIÓN:** La lectura conjunta relaciona acumulación operacional y experiencia declarada. La igualdad de medianas entre scores 0 y 1 refuerza la conveniencia de consultar también las distribuciones.
- **LIMITACIÓN:** Satisfacción no participa de la fórmula, pero procede del mismo dataset sintético. La relación no valida clínica ni externamente el índice y no demuestra un efecto causal del score.

### Conclusión 7. El modelo identifica estructura predictiva dentro del dataset

- **HALLAZGO:** El Decision Tree seleccionado mejora las métricas del baseline que siempre predice satisfacción 4 en el test utilizado.
- **EVIDENCIA:** Macro F1 de 0.5071 frente a 0.0986 y MAE ordinal de 0.5309 frente a 0.9239; N test=486. El árbol obtiene 50.4115% de exactas, 96.5021% dentro de ±1 y 3.4979% de errores ≥2. Fuente: Etapa 7, secciones 5, 8 y 9.
- **INTERPRETACIÓN:** Las variables contienen información predictiva sobre satisfacción, compatible con las relaciones sintéticas ya observadas. El aporte complementa la lectura descriptiva.
- **LIMITACIÓN:** El mismo test participó en la selección del modelo; no hay validación externa. Capacidad predictiva no equivale a causalidad ni habilita recomendaciones clínicas individuales.

## 3. Tiempos de espera

**Dato.** La espera media es de aproximadamente 17.60 minutos en Privada, 70.19 en Pública y 106.11 en Sin cobertura. Las medianas de 18, 71 y 105 minutos acompañan el contraste, con N válidos de 823, 777 y 826 (Etapa 5, sección 3; Etapa 9, sección 9).

**Interpretación.** La diferencia observada permite orientar la investigación hacia los segmentos con mayores demoras, sin atribuirla exclusivamente a la cobertura.

**Sugerencia.** Revisar los procesos asociados a los tiempos de espera, priorizando los segmentos donde se observan mayores demoras. Esto supone plantear una revisión de las etapas del proceso para localizar demoras, analizar capacidad y asignación de recursos, monitorear tiempos segmentados por cobertura e investigar factores adicionales que puedan explicar las diferencias.

**Preguntas para investigación posterior.** ¿En qué etapas se concentra la demora? ¿Cómo se relacionan la capacidad disponible, la demanda y la asignación de recursos con los tiempos observados? El dataset no mide etapas del proceso ni capacidad instalada; estas preguntas requieren información adicional y no constituyen hallazgos actuales.

**Seguimiento propuesto.** Recuperar los indicadores existentes de media, mediana y N válido de espera por cobertura, acompañados de los faltantes. La evidencia no permite afirmar que cambiar la cobertura reduciría la espera ni estimar el efecto de reorganizar recursos.

## 4. Acceso a medicación

**Dato.** Privada / Aguda presenta 89.22% de acceso (240/269), mientras que Sin cobertura / Crónica presenta 41.99% (118/281), dentro de las nueve combinaciones descriptas en Etapa 5, sección 6.

**Interpretación.** El menor porcentaje observado en Sin cobertura / Crónica justifica considerarlo un segmento prioritario para **investigar**, sin convertir su cobertura o condición en una explicación causal.

**Sugerencia.** Priorizar el análisis de barreras de acceso a medicación, especialmente en combinaciones donde se observan menores porcentajes de acceso. La comparación debe conservar las nueve combinaciones y sus denominadores para contextualizar los extremos.

**Preguntas para investigación posterior, sobre dimensiones no medidas por el dataset:**

- ¿Existe disponibilidad de la medicación requerida?
- ¿Se mantiene la continuidad de entrega?
- ¿Aparecen dificultades administrativas?
- ¿Qué obstáculos de accesibilidad podrían intervenir?
- ¿Qué otras barreras relevantes deberían relevarse?

Estas dimensiones son propuestas de investigación con futuras fuentes de datos; no se presume su presencia ni su contribución al resultado observado. El campo de acceso Sí/No no permite distinguirlas.

**Seguimiento propuesto.** Porcentaje de acceso a medicación por cobertura y condición, acompañado de cantidad de respuestas Sí y N válido de cada combinación, tal como ya se presenta en los informes y el dashboard.

## 5. Acumulación de dimensiones

**Dato.** La proporción de score 3 es 0.00% en Privada, 3.09% en Pública y 10.90% en Sin cobertura, sobre 823, 777 y 826 registros evaluables, respectivamente (Etapa 6, sección 6).

**Definición conservada.** El **Índice operacional de vulnerabilidad en el acceso y la atención** suma un punto por cada dimensión observada: condición crónica, falta de acceso a medicación y espera ≥99 minutos. El umbral corresponde al Q3 original y permanece fijo. Solo hay score cuando las tres dimensiones son observables. Cobertura, región y satisfacción no forman parte de la fórmula.

**Interpretación.** Score 0–3 expresa la cantidad de dimensiones concurrentes. Score 3 identifica su coincidencia simultánea. Score 0 no descarta dificultades ajenas a esta definición; en Privada, la ausencia de score 3 es coherente con que las esperas observadas no alcanzan el umbral.

**Sugerencia.** Utilizar el índice como herramienta descriptiva de priorización de segmentos a investigar y de organización de la evidencia. Consultar sus componentes para comprender qué perfiles reúne cada score, especialmente porque los scores 1 y 2 agrupan combinaciones distintas.

El índice no significa bajo, medio o alto; tampoco riesgo clínico, diagnóstico ni clasificación vulnerable Sí/No. No se propone usarlo directamente para negar, otorgar o limitar prestaciones sanitarias.

**Investigación posterior.** Examinar qué necesidades y barreras quedan fuera de las tres dimensiones y qué información adicional sería necesaria para describirlas. No se revisan aquí pesos, umbral ni definición.

**Seguimiento propuesto.** Distribución del score 0–3 y N evaluable por cobertura, con cantidad de registros sin score. Los 74 NA se conservan como ausencia de información, no como cero dimensiones.

## 6. Satisfacción

**Dato.** Las medianas de satisfacción por score 0/1/2/3 son 4/4/3/2, con N conjunto=2357. El dashboard informa promedio global de 3.56/5 y mediana global de 4/5, con N=2428. La asociación espera–satisfacción es negativa (ρ=−0.7402; N=2357). Fuentes: Etapa 6, sección 8; Etapa 9, sección 5; Etapa 5, sección 7.

**Interpretación.** Satisfacción es ordinal 1–5. Sus niveles y distribución aportan información que no queda contenida en el promedio. Las asociaciones sugieren que conviene contextualizar la experiencia reportada con los indicadores de acceso y atención.

**Sugerencia.** Monitorear la satisfacción junto con indicadores de acceso y atención, evitando interpretarla de manera aislada. Espera y medicación aportan las asociaciones ya documentadas; cobertura y condición permiten contextualizar los perfiles de acceso; el score resume la concurrencia de dimensiones. Esta lectura conjunta no estima efectos independientes ni demuestra que una modificación de esos factores produciría una mejora de satisfacción.

**Investigación posterior.** Preguntar qué aspectos de la experiencia de atención y de las expectativas podrían faltar en los registros. Son dimensiones a relevar, no explicaciones verificadas por el análisis actual.

**Seguimiento propuesto.** Distribución de niveles 1–5, mediana y N válido, globales y en los segmentos ya disponibles; mediana y distribución por score con el N de ambas variables observables. Mantener el promedio existente del dashboard como complemento, sin asumir distancias iguales entre niveles.

## 7. Aporte del modelado

La [Etapa 7](07_modelado.md), secciones 5 y 8–11, seleccionó **Decision Tree** frente a Random Forest mediante el criterio comparativo allí documentado. El **baseline predice siempre la clase 4**, mayoritaria en train. Se transcriben exactamente las métricas publicadas sobre el mismo test:

| Estrategia | Macro F1 | MAE ordinal | Exactas (%) | Dentro de ±1 (%) | Errores ≥2 (%) | N test |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Baseline: siempre nivel 4 | 0.0986 | 0.9239 | 32.7160 | 80.6584 | 19.3416 | 486 |
| Seleccionado: Decision Tree | 0.5071 | 0.5309 | 50.4115 | 96.5021 | 3.4979 | 486 |

Dentro de ±1 incluye las exactas. Los errores ≥2 del árbol corresponden a 17 casos. El MAE distingue distancias numéricas entre niveles, sin acreditar intervalos psicológicos iguales de satisfacción.

Los ocho predictores utilizados fueron **Region, Edad, Genero, Condicion_Salud, Cobertura_Salud, Frecuencia_Atencion, Tiempo_Espera_min y Acceso_Medicacion**. Las principales importancias agregadas fueron Tiempo_Espera_min **63.1003%**, Acceso_Medicacion **26.1623%** y Edad **4.0425%**. No se usaron ID_Paciente, Score_Vulnerabilidad ni Dim_*.

El resultado aporta evidencia de estructura predictiva en las variables del dataset sintético, que contiene relaciones incorporadas durante su generación. Las importancias reflejan reducciones de impureza en train, con posibles sesgos; no son efectos causales ni aportes independientes. **Capacidad predictiva ≠ causalidad.**

El test participó en la selección comparativa, por lo que el desempeño del ganador no constituye una evaluación independiente de esa selección. Además, la exploración previa había observado el dataset completo. No hay validación externa; espera y acceso deben estar disponibles al predecir, de modo que el ejercicio no acredita un pronóstico previo a la atención. El modelo complementa las conclusiones, sin ocupar el centro de las recomendaciones ni constituir una herramienta clínica.

## 8. Matriz de líneas de acción

La priorización consiste en orientar preguntas hacia diferencias observadas, sin puntajes, categorías de prioridad ni un orden de efectividad supuesto. Las fuentes y los denominadores de cada evidencia se detallan en las secciones 3–6.

| Línea de acción | Hallazgo que la sustenta | Qué se propone | Qué debería investigarse | Indicador para seguimiento | Limitación |
| --- | --- | --- | --- | --- | --- |
| Tiempos de espera | Medias Privada/Pública/Sin cobertura: 17.60/70.19/106.11 min | Revisar procesos en los segmentos con mayores demoras | Etapas de demora, capacidad, asignación de recursos y factores adicionales; requieren información no medida | Media y mediana de espera por cobertura; N válido | Asociación sin efecto causal identificado; 74 NA |
| Acceso a medicación | Privada/Aguda: 89.22%; Sin cobertura/Crónica: 41.99% | Investigar barreras en combinaciones con menor acceso | Disponibilidad, continuidad, trámites, accesibilidad y otras barreras; no medidas | Porcentaje de acceso, cantidad Sí y N válido por cobertura y condición | Comparación descriptiva; el campo Sí/No no identifica mecanismos |
| Acumulación de dimensiones | Score 3 por cobertura: 0.00%/3.09%/10.90% | Usar el índice para describir y orientar la investigación de segmentos | Perfiles componentes y dimensiones omitidas que requerirían otras fuentes | Distribución score 0–3 por cobertura, N evaluable y sin score | Índice operacional sin validación clínica; depende de fórmula y umbral |
| Satisfacción | Medianas por score 0/1/2/3: 4/4/3/2; asociación negativa con espera | Leer satisfacción junto con acceso, espera y perfiles | Aspectos de experiencia y expectativas no relevados | Distribución 1–5, mediana y N válido; lectura conjunta por score | Escala ordinal; asociación no causal ni validación del índice |

## 9. Indicadores de seguimiento

Se propone utilizar únicamente indicadores ya existentes. Esta sección define cómo leerlos y no calcula nuevos valores, metas ni umbrales.

| Línea | Indicadores existentes y referencia | Denominador y criterio de lectura |
| --- | --- | --- |
| Espera | Media y mediana en minutos por cobertura; N válido (Etapa 5, sección 3; Etapa 9, sección 6) | Registros con espera observable dentro de cada cobertura; informar faltantes y consultar conjuntamente media y mediana |
| Medicación | Porcentaje de acceso Sí, cantidad Sí y N válido por cobertura y condición (Etapa 5, sección 6) | Respuestas de acceso observables dentro de cada combinación; conservar N de cada celda |
| Acumulación | Distribución del score 0–3, N evaluable y cantidad sin score, global y por cobertura (Etapa 6, secciones 3, 4 y 6) | Registros con las tres dimensiones observables; porcentajes dentro de cada cobertura; no sustituir NA por 0 |
| Satisfacción | Distribución de niveles 1–5, mediana y N válido; distribución y mediana por score; promedio existente como complemento (Etapa 6, sección 8; Etapa 9, secciones 5–7) | Satisfacción observable; al cruzar con score, ambas variables presentes. N global=2428 y N conjunto=2357 |

En los segmentos del dashboard se deben leer los denominadores propios de cada selección, sin trasladar los N globales. Los grupos pequeños o vacíos requieren conservar el contexto de disponibilidad de datos.

El seguimiento propuesto es una pauta para organizar la lectura de indicadores. El dataset actual no documenta una serie temporal con la cual evaluar tendencias o cambios posteriores a intervenciones. Un seguimiento longitudinal requeriría futuras fuentes comparables y referencias temporales; no se atribuyen mejoras ni deterioros con los datos existentes.

## 10. Qué no podemos concluir

- **No demostramos causalidad.** Las diferencias y asociaciones no prueban que cobertura, espera, acceso o score causen un resultado; tampoco estiman efectos independientes.
- **No evaluamos efectividad real de políticas sanitarias.** No se implementaron ni compararon intervenciones; las sugerencias orientan investigación y monitoreo.
- **No podemos generalizar a Argentina.** Son 2500 registros ficticios, sin representatividad poblacional y con relaciones incorporadas en su generación.
- **No realizamos diagnóstico clínico.** Ningún resultado habilita una recomendación sanitaria individual.
- **El índice operacional no está validado clínicamente.** Cuenta tres dimensiones con pesos iguales y un umbral relativo al dataset; no clasifica gravedad ni vulnerabilidad Sí/No y omite otras dificultades.
- **El modelo no está validado externamente.** Su selección utilizó el mismo test; las importancias no son efectos causales y la predicción requiere conocer espera y acceso.
- **Las variables no explican todos los mecanismos** detrás de espera, medicación o satisfacción. Disponibilidad, continuidad, procesos administrativos, capacidad y expectativas son preguntas pendientes, no hallazgos.
- **Los faltantes y la escala limitan la lectura.** Se desconoce el mecanismo de los NA, los N cambian entre indicadores y satisfacción es ordinal. Las pruebas exploratorias previas y las comparaciones descriptivas no autorizan conclusiones más amplias que las documentadas.

## 11. Conclusión general

El análisis permitió comprender que, dentro del dataset ficticio estudiado, el acceso y la atención presentan diferencias que los indicadores globales no alcanzan a describir. La segmentación por cobertura mostró contrastes en los tiempos de espera, mientras que su combinación con la condición de salud permitió reconocer perfiles con menor acceso a medicación. Estos patrones ofrecen un punto de partida para formular preguntas sobre procesos y barreras que el conjunto de datos no mide.

La satisfacción adquirió mayor sentido al relacionarse con la espera, el acceso a medicación y la acumulación de dimensiones operacionales. El índice ayudó a organizar esa concurrencia, aunque su definición no representa gravedad clínica. El modelado agregó evidencia de estructura predictiva y complementó el recorrido descriptivo, con límites derivados del carácter sintético de los datos y de su evaluación interna.

La información puede orientar la revisión de procesos, la investigación de segmentos y el seguimiento conjunto de indicadores existentes. Su utilidad consiste en fundamentar dónde profundizar el análisis, sin anticipar resultados de intervenciones. Como cierre, el trabajo muestra el valor de integrar evidencia, interpretación y propuestas manteniendo sus diferencias: describir asociaciones no demuestra causas, validar internamente no garantiza aplicación externa y estudiar registros ficticios no permite generalizar conclusiones a la población argentina.

## 12. Versión breve para presentación

Cuatro pares de hallazgo y sugerencia para una explicación oral aproximada de 20–30 segundos por par. Son notas de exposición; no se crean diapositivas.

### 1. Espera

**Hallazgo:** La espera media fue de 17.60 minutos en Privada, 70.19 en Pública y 106.11 en Sin cobertura. **Sugerencia:** Revisar los procesos en los segmentos con mayores demoras y monitorear media, mediana y N válido. La diferencia orienta preguntas; no demuestra que la cobertura cause la espera.

### 2. Medicación

**Hallazgo:** El acceso fue de 89.22% en Privada / Aguda y 41.99% en Sin cobertura / Crónica. **Sugerencia:** Investigar especialmente este último segmento y considerar disponibilidad, continuidad, trámites y accesibilidad como preguntas futuras. Esas barreras no fueron medidas; el seguimiento disponible es el porcentaje de acceso acompañado del N de cada combinación.

### 3. Acumulación

**Hallazgo:** El score 3 apareció en 0.00% de Privada, 3.09% de Pública y 10.90% de Sin cobertura. **Sugerencia:** Utilizar la distribución del índice para identificar dónde investigar la coincidencia de las tres dimensiones. El score cuenta dimensiones operacionales; no expresa gravedad clínica ni debe determinar el otorgamiento o la restricción de prestaciones.

### 4. Satisfacción

**Hallazgo:** Las medianas de satisfacción fueron 4, 4, 3 y 2 para los scores 0, 1, 2 y 3. **Sugerencia:** Monitorear su distribución y mediana junto con espera, medicación, cobertura y condición de salud. Esta lectura conjunta contextualiza la experiencia declarada, pero la asociación observada en datos ficticios no demuestra causalidad ni valida clínicamente el índice.

**Control de alcance:** se crea exclusivamente este informe. Las cifras proceden de resultados documentados; las preguntas futuras se distinguen de los hallazgos. No se realizan nuevos análisis, recálculos, cambios de datasets, gráficos, entrenamientos, modificaciones del dashboard, notebooks ni diapositivas. Se conserva la definición del score y no se introducen recomendaciones clínicas individuales ni generalizaciones a población real.
