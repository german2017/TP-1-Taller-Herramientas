# Etapa 8 - Selección de hallazgos y visualizaciones

## 1. Objetivo de comunicación

Esta etapa organiza la evidencia existente para una comunicación clara del problema de equidad en el acceso y la atención: tiempos de espera, acceso a medicación y satisfacción. Es una selección editorial, no un nuevo análisis. Todas las cifras se transcriben de los informes anteriores; los recuentos de elementos de este inventario son documentales.

**Pregunta principal, conservada de la Etapa 1:**

> ¿Cómo varían los tiempos de espera, el acceso a medicación y la satisfacción según la cobertura, la condición de salud y la región en este dataset ficticio, y qué diferencias podrían orientar propuestas de mejora de la equidad en la atención e identificar posibles grupos vulnerables, una vez acordada su definición?

El objetivo es explicar qué datos tenemos, qué diferencias se observaron, dónde aparecen dificultades, qué agrega el índice operacional y qué aporta predecir satisfacción. La comunicación debe distinguir observaciones, asociaciones y predicción, y preparar información para decisiones posteriores.

**Fuentes:** [objetivos y requerimientos](01_objetivos.md), [auditoría](02_auditoria_dataset.md), [limpieza](03_limpieza.md), [EDA](04_eda.md), [relaciones](05_relaciones.md), [vulnerabilidad](06_vulnerabilidad.md) y [modelado](07_modelado.md). Los inventarios remiten a estas etapas; no sustituyen sus tablas y limitaciones.

El caso solicita explorar coberturas y esperas, relacionar espera con satisfacción y cobertura con medicación, examinar posibles grupos vulnerables y considerar BI con segmentación por región, cobertura y condición. Para BI menciona espera promedio, porcentaje de acceso y satisfacción promedio. Los objetivos de modelado del caso son más amplios: aquí solo se completó predicción de satisfacción; no se presentan como cumplidas la clasificación de vulnerabilidad ni la predicción de mala atención.

La consigna contempla aproximadamente **20 minutos de exposición y 10 de preguntas**, participación equilibrada del equipo, justificación de visualizaciones y evaluación de contenido, claridad, diseño, comunicación y uso del tiempo. La selección prepara esos requisitos; todavía no produce dashboard, diapositivas ni recomendaciones.

**Contexto indispensable:** dataset ficticio de 2500 registros y 10 variables originales, sin representatividad ni validación externa. La limpieza conservó registros y valores faltantes y normalizó solo dos etiquetas. En análisis descriptivos se usaron casos disponibles; el N efectivo cambia según las variables. El modelado excluyó únicamente targets ausentes y trató los NA de espera dentro del pipeline, sin modificar el dataset.

**Criterios editoriales:** A = relevancia para el problema; B = claridad; C = capacidad para responder la pregunta; D = aporte no redundante; E = utilidad potencial para orientar decisiones; F = lugar en el recorrido EDA → relaciones → vulnerabilidad → modelado. Se evalúan cualitativamente, sin puntajes. ESENCIAL sostiene la historia; ÚTIL la amplía; COMPLEMENTARIO sirve como contexto o detalle; REDUNDANTE puede omitirse del producto principal porque otra pieza cumple mejor esa función. La clasificación depende del uso comunicacional, no de significación estadística.

## 2. Inventario de hallazgos

Se inventarían **25 hallazgos**: los siete de EDA, siete de relaciones, seis del índice y cinco del modelado. La columna de importancia expresa la clasificación editorial. “Descartar” siempre significaría omitir de la comunicación principal, nunca eliminar archivos.

| ID  | Etapa | Hallazgo                           | Dato principal                                                         | Pregunta que responde                           | Importancia comunicacional | Posible uso final |
| --- | ----- | ---------------------------------- | ---------------------------------------------------------------------- | ----------------------------------------------- | -------------------------- | ----------------- |
| H01 | 4     | Composición de coberturas          | 32.24%–34.04%; N=2500                                                  | ¿Cómo se compone la muestra?                    | ÚTIL                       | Complementario    |
| H02 | 4     | Distribución de edad               | Media 45.40; mediana 45; N=2500                                        | ¿Qué edades están representadas?                | COMPLEMENTARIO             | Complementario    |
| H03 | 4     | Frecuencia de atención             | Media 6.19; mediana 4; N=2500                                          | ¿Con qué frecuencia se atienden?                | COMPLEMENTARIO             | Complementario    |
| H04 | 4     | Espera general                     | Media 64.58 min; mediana 54; N=2426                                    | ¿Cómo son las esperas?                          | ESENCIAL                   | Ambos             |
| H05 | 4     | Acceso general a medicación        | Sí: 1695/2500 (67.80%)                                                 | ¿Qué proporción accede?                         | ÚTIL                       | Dashboard         |
| H06 | 4     | Satisfacción general               | Nivel 4: 794 (32.70%); mediana 4; N=2428                               | ¿Cómo se distribuye la satisfacción?            | ÚTIL                       | Dashboard         |
| H07 | 4     | Espera media por cobertura         | Privada 17.60; Pública 70.19; Sin cobertura 106.11 min; N=2426         | ¿Cómo varía la espera media?                    | ÚTIL                       | Dashboard         |
| H08 | 5     | Condición y frecuencia             | Medianas Saludable 1, Aguda 4, Crónica 13; N=2500                      | ¿La frecuencia difiere por condición?           | COMPLEMENTARIO             | Complementario    |
| H09 | 5     | Cobertura y distribución de espera | Medianas 18, 71 y 105 min; H=1684.378; p<.001; N=2426                  | ¿Cómo difieren las distribuciones?              | ÚTIL                       | Presentación      |
| H10 | 5     | Cobertura y medicación             | Acceso Sí: 48.88%–85.05%; V=.3199; N=2500                              | ¿El acceso se asocia con cobertura?             | ESENCIAL                   | Ambos             |
| H11 | 5     | Condición y medicación             | Acceso Sí: 60.97%–71.41%; V=.1042; N=2500                              | ¿El acceso se asocia con condición?             | ÚTIL                       | Complementario    |
| H12 | 5     | Acceso por cobertura y condición   | Privada/Aguda 89.22% (240/269); Sin cobertura/Crónica 41.99% (118/281) | ¿Dónde aparecen diferencias conjuntas?          | ESENCIAL                   | Ambos             |
| H13 | 5     | Espera y satisfacción              | Spearman −.7402; p<.001; N=2357                                        | ¿Cómo se relacionan espera y satisfacción?      | ESENCIAL                   | Presentación      |
| H14 | 5     | Medicación y satisfacción          | Mediana Sí=4 (N=1640); No=3 (N=788)                                    | ¿Cómo varía la satisfacción según acceso?       | ÚTIL                       | Complementario    |
| H15 | 6     | Disponibilidad del índice          | 2426 calculables (97.04%); 74 NA                                       | ¿A quiénes puede calcularse el score?           | ESENCIAL                   | Ambos             |
| H16 | 6     | Distribución del score             | 0: 37.26%; 1: 38.62%; 2: 19.41%; 3: 4.70%; N=2426                      | ¿Cuántas dimensiones se acumulan?               | ESENCIAL                   | Ambos             |
| H17 | 6     | Combinaciones de dimensiones       | 000: 904; 100: 415; 010: 285; N=2426                                   | ¿Qué perfiles resume el score?                  | ÚTIL                       | Complementario    |
| H18 | 6     | Score y cobertura                  | Score 3: Privada 0.00%, Pública 3.09%, Sin cobertura 10.90%; N=2426    | ¿Cómo varía la acumulación por cobertura?       | ESENCIAL                   | Dashboard         |
| H19 | 6     | Score y región                     | Score 2: CABA 13.78%, Norte 22.32%; N=2426                             | ¿Qué diferencias regionales se describen?       | ÚTIL                       | Complementario    |
| H20 | 6     | Score y satisfacción               | Medianas por score 0–3: 4, 4, 3, 2; N=2357                             | ¿Cómo se relacionan acumulación y satisfacción? | ESENCIAL                   | Ambos             |
| H21 | 7     | Población de modelado              | 2428 modelables; train 1942; test 486; 72 targets ausentes             | ¿Sobre qué casos se evalúa el modelo?           | ÚTIL                       | Presentación      |
| H22 | 7     | Modelo frente a baseline           | Decision Tree: F1=.5071, MAE=.5309; baseline: .0986 y .9239; N=486     | ¿Qué aporta frente a predecir siempre 4?        | ESENCIAL                   | Presentación      |
| H23 | 7     | Magnitud ordinal de errores        | Exactas 50.41%; ±1 96.50%; ≥2 3.50% (17/486)                           | ¿De qué magnitud son los errores?               | ESENCIAL                   | Presentación      |
| H24 | 7     | Confusiones por nivel              | 4→5: 70; 4→3: 38; 3→4: 32; N=486                                       | ¿En qué niveles se equivoca?                    | COMPLEMENTARIO             | Complementario    |
| H25 | 7     | Importancia predictiva             | Espera 63.10%; medicación 26.16%; edad 4.04%                           | ¿Qué variables utiliza más el árbol?            | ÚTIL                       | Presentación      |

**Aplicación de A–F a cada hallazgo:**

| ID  | A · Relevancia | B · Claridad         | C · Capacidad explicativa | D · No redundancia            | E · Utilidad potencial | F · Recorrido  |
| --- | -------------- | -------------------- | ------------------------- | ----------------------------- | ---------------------- | -------------- |
| H01 | Directa        | Inmediata            | Describe muestra/servicio | Aporte propio                 | Contexto               | EDA            |
| H02 | Contextual     | Inmediata            | Describe muestra/servicio | Aporte propio                 | Contexto               | EDA            |
| H03 | Contextual     | Inmediata            | Describe muestra/servicio | Aporte propio                 | Contexto               | EDA            |
| H04 | Directa        | Inmediata            | Describe muestra/servicio | Aporte propio                 | Diferencias a examinar | EDA            |
| H05 | Directa        | Inmediata            | Describe muestra/servicio | Aporte propio                 | Diferencias a examinar | EDA            |
| H06 | Directa        | Inmediata            | Describe muestra/servicio | Aporte propio                 | Diferencias a examinar | EDA            |
| H07 | Directa        | Inmediata            | Describe muestra/servicio | Parcial con H09; media        | Diferencias a examinar | EDA            |
| H08 | Contextual     | Inmediata            | Compara variables         | Aporte propio                 | Contexto               | Relaciones     |
| H09 | Directa        | Requiere explicación | Compara variables         | Parcial con H07; distribución | Diferencias a examinar | Relaciones     |
| H10 | Directa        | Inmediata            | Compara variables         | Complementa H12; marginal     | Diferencias a examinar | Relaciones     |
| H11 | Directa        | Inmediata            | Compara variables         | Complementa H12; marginal     | Diferencias a examinar | Relaciones     |
| H12 | Directa        | Inmediata            | Compara variables         | Aporte propio                 | Diferencias a examinar | Relaciones     |
| H13 | Directa        | Requiere explicación | Compara variables         | Aporte propio                 | Diferencias a examinar | Relaciones     |
| H14 | Directa        | Inmediata            | Compara variables         | Aporte propio                 | Diferencias a examinar | Relaciones     |
| H15 | Directa        | Inmediata            | Describe acumulación      | Aporte propio                 | Alcance de lectura     | Vulnerabilidad |
| H16 | Directa        | Inmediata            | Describe acumulación      | Aporte propio                 | Diferencias a examinar | Vulnerabilidad |
| H17 | Directa        | Requiere explicación | Describe acumulación      | Aporte propio                 | Diferencias a examinar | Vulnerabilidad |
| H18 | Directa        | Inmediata            | Describe acumulación      | Aporte propio                 | Diferencias a examinar | Vulnerabilidad |
| H19 | Directa        | Inmediata            | Describe acumulación      | Aporte propio                 | Diferencias a examinar | Vulnerabilidad |
| H20 | Directa        | Inmediata            | Describe acumulación      | Aporte propio                 | Diferencias a examinar | Vulnerabilidad |
| H21 | Directa        | Requiere explicación | Evalúa predicción         | Aporte propio                 | Alcance de lectura     | Modelado       |
| H22 | Directa        | Requiere explicación | Evalúa predicción         | Aporte propio                 | Alcance predictivo     | Modelado       |
| H23 | Directa        | Requiere explicación | Evalúa predicción         | Amplía H22; errores           | Alcance predictivo     | Modelado       |
| H24 | Contextual     | Requiere explicación | Evalúa predicción         | Amplía H23; clases            | Alcance predictivo     | Modelado       |
| H25 | Directa        | Requiere explicación | Evalúa predicción         | Aporte propio                 | Alcance predictivo     | Modelado       |

## 3. Inventario de visualizaciones

Se revisan **27 figuras existentes**. Los enlaces abren los archivos originales; no se regeneran ni editan. Los IDs permiten usar tablas separadas por etapa sin repetir rutas en las propuestas. “No” indica material de respaldo en la propuesta actual, no una prohibición para la selección final del equipo. Algunas figuras de composición contextualizan hallazgos sin corresponder a un hallazgo numerado independiente.

**Etapa 4:**

| ID  | Archivo                                                                                             | Etapa | Qué muestra                | Pregunta que responde              | Hallazgo asociado   | Fortaleza              | Limitación                          | Redundancia con otra figura        | Candidato dashboard | Candidato presentación | Clasificación  |
| --- | --------------------------------------------------------------------------------------------------- | ----- | -------------------------- | ---------------------------------- | ------------------- | ---------------------- | ----------------------------------- | ---------------------------------- | ------------------- | ---------------------- | -------------- |
| F01 | [cobertura_distribucion.png](../outputs/figuras/eda/cobertura_distribucion.png)                     | 4     | Composición por cobertura  | ¿Quiénes integran la muestra?      | H01                 | Contexto inmediato     | No mide barreras                    | No directa                         | No                  | No                     | ÚTIL           |
| F02 | [region_distribucion.png](../outputs/figuras/eda/region_distribucion.png)                           | 4     | Composición regional       | ¿Qué regiones están representadas? | Contexto de H19     | Explicita composición  | No mide desigualdad regional        | No directa                         | No                  | No                     | COMPLEMENTARIO |
| F03 | [condicion_salud_distribucion.png](../outputs/figuras/eda/condicion_salud_distribucion.png)         | 4     | Composición por condición  | ¿Qué condiciones se incluyen?      | Contexto de H08/H11 | Categorías claras      | No muestra acceso                   | No directa                         | No                  | No                     | COMPLEMENTARIO |
| F04 | [genero_distribucion.png](../outputs/figuras/eda/genero_distribucion.png)                           | 4     | Composición por género     | ¿Cómo se compone la muestra?       | Contexto EDA        | Lectura simple         | Sin relación analizada con atención | No directa                         | No                  | No                     | COMPLEMENTARIO |
| F05 | [edad_distribucion.png](../outputs/figuras/eda/edad_distribucion.png)                               | 4     | Distribución de edad       | ¿Qué edades aparecen?              | H02                 | Muestra extensión      | No conecta edad con barreras        | No directa                         | No                  | No                     | COMPLEMENTARIO |
| F06 | [frecuencia_atencion_distribucion.png](../outputs/figuras/eda/frecuencia_atencion_distribucion.png) | 4     | Distribución de frecuencia | ¿Cuánto se usa la atención?        | H03                 | Muestra heterogeneidad | Mezcla condiciones                  | Parcial con F12                    | No                  | No                     | COMPLEMENTARIO |
| F07 | [tiempo_espera_distribucion.png](../outputs/figuras/eda/tiempo_espera_distribucion.png)             | 4     | Distribución de espera     | ¿Cómo son las esperas?             | H04                 | Introduce dispersión   | No segmenta; N=2426                 | Alta con F08                       | No                  | Principal              | ESENCIAL       |
| F08 | [tiempo_espera_boxplot.png](../outputs/figuras/eda/tiempo_espera_boxplot.png)                       | 4     | Resumen de espera          | ¿Cómo se dispersa la espera?       | H04                 | Síntesis de cuartiles  | Menos intuitivo que F07             | Alta con F07; F13 agrega cobertura | No                  | No                     | REDUNDANTE     |
| F09 | [acceso_medicacion_distribucion.png](../outputs/figuras/eda/acceso_medicacion_distribucion.png)     | 4     | Acceso Sí/No               | ¿Cuántos acceden?                  | H05                 | Muy clara              | No segmenta                         | Alta con KPI 67.80%                | No                  | No                     | REDUNDANTE     |
| F10 | [satisfaccion_distribucion.png](../outputs/figuras/eda/satisfaccion_distribucion.png)               | 4     | Niveles de satisfacción    | ¿Cómo se distribuye la respuesta?  | H06                 | Respeta ordinalidad    | 72 NA; no resume diferencias        | Parcial con F17/F22                | Sí                  | No                     | ÚTIL           |
| F11 | [espera_promedio_cobertura.png](../outputs/figuras/eda/espera_promedio_cobertura.png)               | 4     | Medias por cobertura       | ¿Cómo varía la espera media?       | H07                 | Responde KPI del caso  | Media oculta dispersión             | Alta temática con F13              | Sí                  | No                     | ÚTIL           |

**Etapa 5:**

| ID  | Archivo                                                                                            | Etapa | Qué muestra                      | Pregunta que responde                 | Hallazgo asociado | Fortaleza                       | Limitación                        | Redundancia con otra figura          | Candidato dashboard | Candidato presentación | Clasificación  |
| --- | -------------------------------------------------------------------------------------------------- | ----- | -------------------------------- | ------------------------------------- | ----------------- | ------------------------------- | --------------------------------- | ------------------------------------ | ------------------- | ---------------------- | -------------- |
| F12 | [frecuencia_por_condicion.png](../outputs/figuras/relaciones/frecuencia_por_condicion.png)         | 5     | Frecuencia por condición         | ¿Cómo difiere la frecuencia?          | H08               | Conecta condición y utilización | Utilización no equivale a barrera | Parcial con F06                      | No                  | No                     | COMPLEMENTARIO |
| F13 | [espera_por_cobertura_boxplot.png](../outputs/figuras/relaciones/espera_por_cobertura_boxplot.png) | 5     | Espera por cobertura             | ¿Cómo difieren las distribuciones?    | H09/H07           | Incluye dispersión              | Requiere explicar boxplot         | Alta temática con F11                | No                  | Principal              | ESENCIAL       |
| F14 | [acceso_por_cobertura.png](../outputs/figuras/relaciones/acceso_por_cobertura.png)                 | 5     | Acceso por cobertura             | ¿Cómo varía el acceso?                | H10               | Comparación directa             | No separa condición               | Parcial con F16, que la detalla      | No                  | No                     | ÚTIL           |
| F15 | [acceso_por_condicion.png](../outputs/figuras/relaciones/acceso_por_condicion.png)                 | 5     | Acceso por condición             | ¿Cómo varía el acceso?                | H11               | Comparación sencilla            | No separa cobertura               | Parcial con F16                      | No                  | No                     | ÚTIL           |
| F16 | [acceso_cobertura_condicion.png](../outputs/figuras/relaciones/acceso_cobertura_condicion.png)     | 5     | Acceso en combinaciones          | ¿Dónde aparecen mayores dificultades? | H12/H10           | Integra dos dimensiones         | Descriptiva; N por celda          | Amplía F14/F15, no mismos marginales | Sí                  | Principal              | ESENCIAL       |
| F17 | [espera_por_satisfaccion.png](../outputs/figuras/relaciones/espera_por_satisfaccion.png)           | 5     | Espera por nivel de satisfacción | ¿Cómo se relacionan?                  | H13               | Puente hacia experiencia        | No expresa causalidad; N=2357     | Parcial con F10                      | No                  | Principal              | ESENCIAL       |
| F18 | [satisfaccion_por_acceso.png](../outputs/figuras/relaciones/satisfaccion_por_acceso.png)           | 5     | Satisfacción según acceso        | ¿Cómo difiere con medicación?         | H14               | Complementa espera              | Descriptiva; 72 NA                | Temática con F17/F22                 | No                  | No                     | ÚTIL           |

**Etapa 6:**

| ID  | Archivo                                                                                                          | Etapa | Qué muestra                | Pregunta que responde             | Hallazgo asociado | Fortaleza                    | Limitación                            | Redundancia con otra figura            | Candidato dashboard | Candidato presentación | Clasificación |
| --- | ---------------------------------------------------------------------------------------------------------------- | ----- | -------------------------- | --------------------------------- | ----------------- | ---------------------------- | ------------------------------------- | -------------------------------------- | ------------------- | ---------------------- | ------------- |
| F19 | [score_vulnerabilidad_distribucion.png](../outputs/figuras/vulnerabilidad/score_vulnerabilidad_distribucion.png) | 6     | Distribución del score 0–3 | ¿Cuántas dimensiones se acumulan? | H15/H16           | Introduce el índice          | Mismo score admite perfiles distintos | Base de F20/F21                        | Sí                  | Principal              | ESENCIAL      |
| F20 | [score_por_cobertura.png](../outputs/figuras/vulnerabilidad/score_por_cobertura.png)                             | 6     | Score por cobertura        | ¿Dónde se acumulan dimensiones?   | H18               | Localiza diferencias         | Depende de componentes y umbral       | Complementa F19; parcial con F16       | Sí                  | No                     | ESENCIAL      |
| F21 | [score_por_region.png](../outputs/figuras/vulnerabilidad/score_por_region.png)                                   | 6     | Score por región           | ¿Cómo varía regionalmente?        | H19               | Aporta dimensión territorial | Sin inferencia ni ajuste              | Misma forma que F20; distinta pregunta | No                  | No                     | ÚTIL          |
| F22 | [satisfaccion_por_score.png](../outputs/figuras/vulnerabilidad/satisfaccion_por_score.png)                       | 6     | Satisfacción según score   | ¿Cómo se vinculan?                | H20               | Conecta índice y experiencia | No valida externamente el índice      | Parcial con F17; agrega acumulación    | Sí                  | Apoyo                  | ESENCIAL      |

**Etapa 7:**

| ID  | Archivo                                                                                              | Etapa | Qué muestra              | Pregunta que responde             | Hallazgo asociado    | Fortaleza                   | Limitación                               | Redundancia con otra figura      | Candidato dashboard  | Candidato presentación | Clasificación  |
| --- | ---------------------------------------------------------------------------------------------------- | ----- | ------------------------ | --------------------------------- | -------------------- | --------------------------- | ---------------------------------------- | -------------------------------- | -------------------- | ---------------------- | -------------- |
| F23 | [comparacion_modelos.png](../outputs/figuras/modelado/comparacion_modelos.png)                       | 7     | Comparación predictiva   | ¿Qué aporta sobre baseline?       | H22/H23              | Referencia común            | Test usado también para selección        | Parcial con F27                  | No; pendiente equipo | Principal              | ESENCIAL       |
| F24 | [matriz_confusion_decision_tree.png](../outputs/figuras/modelado/matriz_confusion_decision_tree.png) | 7     | Confusiones del árbol    | ¿Dónde falla el seleccionado?     | H24                  | Detalle por nivel           | Densa para exposición breve              | Detalla F23/F27                  | No                   | No                     | COMPLEMENTARIO |
| F25 | [matriz_confusion_random_forest.png](../outputs/figuras/modelado/matriz_confusion_random_forest.png) | 7     | Confusiones del bosque   | ¿Dónde falla el alternativo?      | Contraste de H22/H24 | Trazabilidad del comparador | Distrae del seleccionado                 | Función similar a F24            | No                   | No                     | REDUNDANTE     |
| F26 | [importancia_variables_modelo.png](../outputs/figuras/modelado/importancia_variables_modelo.png)     | 7     | Importancias agregadas   | ¿Qué utiliza más el seleccionado? | H25                  | Conecta con espera y acceso | Impureza no causal; sesgos               | No directa                       | No; pendiente equipo | Apoyo                  | ÚTIL           |
| F27 | [distribucion_error_ordinal.png](../outputs/figuras/modelado/distribucion_error_ordinal.png)         | 7     | Distancia de los errores | ¿Cuánto se alejan predicciones?   | H23                  | Respeta orden en evaluación | Distancias no prueban intervalos iguales | Alta con métricas de F23 y texto | No                   | No                     | REDUNDANTE     |

**Aplicación de A–F a cada visualización:** la fortaleza y la limitación del inventario fundamentan la claridad y capacidad explicativa; aquí se explicita el conjunto de criterios.

| ID  | A · Relevancia | B · Claridad   | C · Capacidad explicativa        | D · No redundancia                     | E · Utilidad potencial | F · Recorrido  |
| --- | -------------- | -------------- | -------------------------------- | -------------------------------------- | ---------------------- | -------------- |
| F01 | Directa        | Lectura rápida | Composición por cobertura        | No directa                             | Contexto               | EDA            |
| F02 | Contextual     | Lectura rápida | Composición regional             | No directa                             | Contexto               | EDA            |
| F03 | Contextual     | Lectura rápida | Composición por condición        | No directa                             | Contexto               | EDA            |
| F04 | Contextual     | Lectura rápida | Composición por género           | No directa                             | Contexto               | EDA            |
| F05 | Contextual     | Lectura rápida | Distribución de edad             | No directa                             | Contexto               | EDA            |
| F06 | Contextual     | Lectura rápida | Distribución de frecuencia       | Parcial con F12                        | Contexto               | EDA            |
| F07 | Directa        | Lectura rápida | Distribución de espera           | Alta con F08                           | Diferencias a examinar | EDA            |
| F08 | Directa        | Lectura guiada | Resumen de espera                | Alta con F07; F13 agrega cobertura     | Diferencias a examinar | EDA            |
| F09 | Directa        | Lectura rápida | Acceso Sí/No                     | Alta con KPI 67.80%                    | Diferencias a examinar | EDA            |
| F10 | Directa        | Lectura rápida | Niveles de satisfacción          | Parcial con F17/F22                    | Diferencias a examinar | EDA            |
| F11 | Directa        | Lectura rápida | Medias por cobertura             | Alta temática con F13                  | Diferencias a examinar | EDA            |
| F12 | Contextual     | Lectura guiada | Frecuencia por condición         | Parcial con F06                        | Diferencias a examinar | Relaciones     |
| F13 | Directa        | Lectura guiada | Espera por cobertura             | Alta temática con F11                  | Diferencias a examinar | Relaciones     |
| F14 | Directa        | Lectura rápida | Acceso por cobertura             | Parcial con F16, que la detalla        | Diferencias a examinar | Relaciones     |
| F15 | Directa        | Lectura rápida | Acceso por condición             | Parcial con F16                        | Diferencias a examinar | Relaciones     |
| F16 | Directa        | Lectura guiada | Acceso en combinaciones          | Amplía F14/F15, no mismos marginales   | Diferencias a examinar | Relaciones     |
| F17 | Directa        | Lectura guiada | Espera por nivel de satisfacción | Parcial con F10                        | Diferencias a examinar | Relaciones     |
| F18 | Directa        | Lectura rápida | Satisfacción según acceso        | Temática con F17/F22                   | Diferencias a examinar | Relaciones     |
| F19 | Directa        | Lectura rápida | Distribución del score 0–3       | Base de F20/F21                        | Diferencias a examinar | Vulnerabilidad |
| F20 | Directa        | Lectura rápida | Score por cobertura              | Complementa F19; parcial con F16       | Diferencias a examinar | Vulnerabilidad |
| F21 | Directa        | Lectura rápida | Score por región                 | Misma forma que F20; distinta pregunta | Diferencias a examinar | Vulnerabilidad |
| F22 | Directa        | Lectura guiada | Satisfacción según score         | Parcial con F17; agrega acumulación    | Diferencias a examinar | Vulnerabilidad |
| F23 | Directa        | Lectura guiada | Comparación predictiva           | Parcial con F27                        | Alcance predictivo     | Modelado       |
| F24 | Contextual     | Lectura guiada | Confusiones del árbol            | Detalla F23/F27                        | Alcance predictivo     | Modelado       |
| F25 | Directa        | Lectura guiada | Confusiones del bosque           | Función similar a F24                  | Alcance predictivo     | Modelado       |
| F26 | Directa        | Lectura guiada | Importancias agregadas           | No directa                             | Alcance predictivo     | Modelado       |
| F27 | Directa        | Lectura guiada | Distancia de los errores         | Alta con métricas de F23 y texto       | Alcance predictivo     | Modelado       |

## 4. Historia analítica propuesta

**Contexto → acceso y espera.** Los 2500 registros ficticios permiten describir experiencias de atención, con coberturas de proporciones similares (H01). La espera general (H04) introduce una dificultad concreta; sus diferencias por cobertura (H07/H09) y las combinaciones de cobertura y condición para medicación (H12) muestran por qué el promedio global es insuficiente.

**Acceso y espera → satisfacción.** La asociación negativa entre espera y satisfacción (H13) conecta la prestación con la experiencia declarada. La satisfacción según acceso a medicación (H14) complementa esa lectura, aunque queda como respaldo para evitar acumular gráficos similares.

**Satisfacción → acumulación de dimensiones.** El índice reúne condición crónica, falta de medicación y espera desde 99 minutos, con igual peso. H15/H16 explican a cuántos casos se aplica y qué significa el score; H18 ubica diferencias por cobertura y H20 conecta el resumen con satisfacción.

**Acumulación → modelado.** El índice describe dimensiones concurrentes; el modelo realiza otra tarea: predecir satisfacción con ocho variables originales, sin utilizar el score ni sus dimensiones derivadas. H22/H23 muestran su aporte y sus errores frente a una referencia trivial; H25 conecta el uso predictivo de espera y medicación con las relaciones ya observadas.

**Modelado → información para decisiones posteriores.** La historia deja identificadas diferencias descriptivas, segmentos a examinar y límites de predicción. No establece causas, prioridades de intervención ni recomendaciones finales: estos datos sintéticos no acreditan efectos en pacientes reales.

En toda comunicación se usará **Índice operacional de vulnerabilidad en el acceso y la atención**. El score 0–3 cuenta dimensiones; no representa categorías bajo/medio/alto, una clasificación vulnerable Sí/No, un diagnóstico ni riesgo clínico. El umbral de espera proviene del tercer cuartil documentado, no de un criterio clínico. La satisfacción no forma parte de su fórmula y su asociación con el índice no constituye validación externa.

## 5. Candidatos para dashboard

Propuesta editorial de **seis figuras**, sujeta a la decisión del equipo. El dashboard priorizaría una lectura descriptiva del acceso, la espera y el índice. Los KPIs usarían los resultados existentes siguientes; no se calculan indicadores nuevos.

| KPI candidato                      | Resultado existente                 | N efectivo / ausencias | Estado y precaución                                           |
| ---------------------------------- | ----------------------------------- | ---------------------- | ------------------------------------------------------------- |
| Tiempo promedio de espera          | 64.58 min                           | 2426 / 74 NA           | Solicitado por el caso; acompañar con dispersión o mediana 54 |
| Porcentaje con acceso a medicación | 67.80%                              | 2500 / sin NA          | Solicitado por el caso; no equivale a calidad integral        |
| Satisfacción                       | Mediana 4; distribución por niveles | 2428 / 72 NA           | Alternativas al promedio; decisión del equipo pendiente       |
| Disponibilidad del índice          | 97.04% calculable                   | 2426 / 74 NA           | Contexto de cobertura del indicador, no desempeño del sistema |

**Tensión pendiente sobre satisfacción:** el caso solicita satisfacción promedio, pero la variable es ordinal y las etapas anteriores evitaron asumir distancias iguales entre niveles. Se proponen mediana y distribución por niveles como alternativas; no se acepta ni se reemplaza silenciosamente el promedio solicitado. No se calcula la media en esta etapa. El equipo debe acordar cómo satisfacer el requisito y documentar la justificación; la mediana sola puede ocultar distribuciones diferentes.

| Figura                                 | Pregunta                                     | Por qué incluirla                                   | Qué decisión posterior podría orientar               | Limitación a recordar                                          |
| -------------------------------------- | -------------------------------------------- | --------------------------------------------------- | ---------------------------------------------------- | -------------------------------------------------------------- |
| F11 · Espera media por cobertura       | ¿Cómo cambia la espera media?                | Conecta KPI y segmentación del caso                 | Qué diferencias de espera examinar con mayor detalle | No informa toda la dispersión; N=823/777/826 según cobertura   |
| F16 · Acceso por cobertura y condición | ¿Dónde difiere el acceso a medicación?       | Muestra combinaciones más informativas que el total | Qué segmentos examinar en el diagnóstico de acceso   | Comparación descriptiva; mostrar denominadores de celdas       |
| F10 · Distribución de satisfacción     | ¿Cómo se distribuyen los niveles?            | Evita depender de un único resumen ordinal          | Cómo comunicar la experiencia reportada              | 72 NA; KPI de satisfacción pendiente                           |
| F19 · Distribución del score           | ¿Cuántas dimensiones se acumulan?            | Explica el significado del índice                   | Qué extensión tiene la acumulación descrita          | 74 NA; no mide severidad clínica                               |
| F20 · Score por cobertura              | ¿Cómo cambia la acumulación según cobertura? | Integra segmentación y dimensiones                  | Qué diferencias de cobertura requieren discusión     | La cobertura no integra la fórmula; depende de los componentes |
| F22 · Satisfacción por score           | ¿Cómo se vinculan acumulación y experiencia? | Conecta el índice con el resultado de interés       | Qué aporta el índice a la lectura de satisfacción    | N=2357; no valida el índice ni identifica efectos causales     |

Los segmentadores candidatos son **Region, Cobertura_Salud y Condicion_Salud**, solicitados por el caso. Su funcionamiento interactivo se diseñará en una etapa posterior; las imágenes existentes son estáticas y no se presentan como filtrables. Cada vista futura deberá informar N efectivo y NA según variables y selección, sin reutilizar denominadores globales para segmentos. Aquí no se calculan resultados filtrados.

Para vulnerabilidad se proponen F19 como introducción, F20 para diferencias por cobertura y F22 para el vínculo con satisfacción. El equipo debe decidir cuál priorizar si reduce el espacio. F21 queda disponible como respaldo territorial: no se interpreta su exclusión editorial como ausencia de diferencias regionales.

## 6. Candidatos para presentación

Propuesta de **ocho figuras: seis principales y dos de apoyo**. Las de apoyo se usarían solo si ayudan al relato y caben en los 20 minutos; no se propone recorrer todas las vistas del dashboard.

| Orden | Figura                                 | Etapa          | Papel     | Función en el relato                                     |
| ----: | -------------------------------------- | -------------- | --------- | -------------------------------------------------------- |
|     1 | F07 · Distribución de espera           | EDA            | Principal | Introducir magnitud y dispersión de espera               |
|     2 | F13 · Espera por cobertura             | Relaciones     | Principal | Mostrar diferencias de distribución más allá de la media |
|     3 | F16 · Acceso por cobertura y condición | Relaciones     | Principal | Ubicar diferencias conjuntas en medicación               |
|     4 | F17 · Espera por satisfacción          | Relaciones     | Principal | Conectar atención y experiencia reportada                |
|     5 | F19 · Distribución del score           | Vulnerabilidad | Principal | Explicar acumulación de dimensiones y casos calculables  |
|     6 | F22 · Satisfacción por score           | Vulnerabilidad | Apoyo     | Conectar índice y satisfacción sin hablar de validación  |
|     7 | F23 · Comparación de modelos           | Modelado       | Principal | Contrastar el seleccionado con el baseline               |
|     8 | F26 · Importancia de variables         | Modelado       | Apoyo     | Conectar uso predictivo con espera y medicación          |

**Modelado acotado:** F23 sería la figura principal y F26 el único apoyo adicional del modelado. Los detalles de matrices, codificación y validación cruzada quedan para preguntas. Se recuperan los valores de la tabla de test de [Etapa 7](07_modelado.md), conservando su precisión:

| Estrategia                  | Macro F1 | MAE ordinal | Exactas (%) | Dentro de ±1 (%) | Errores ≥2 (%) | N test |
| --------------------------- | -------: | ----------: | ----------: | ---------------: | -------------: | -----: |
| Baseline: siempre nivel 4   |   0.0986 |      0.9239 |     32.7160 |          80.6584 |        19.3416 |    486 |
| Seleccionado: Decision Tree |   0.5071 |      0.5309 |     50.4115 |          96.5021 |         3.4979 |    486 |

El baseline usa la clase más frecuente de train. Decision Tree fue seleccionado con el criterio comparativo documentado; Random Forest permanece como comparador en F23 y en el respaldo. No se reentrena ni se reelige el modelo.

Los ocho predictores fueron Tiempo_Espera_min, Acceso_Medicacion, Edad, Frecuencia_Atencion, Genero, Condicion_Salud, Cobertura_Salud y Region. No se usaron ID_Paciente ni el índice o sus dimensiones. Las principales importancias agregadas del seleccionado, según la tabla previa, fueron **Tiempo_Espera_min 63.1003%, Acceso_Medicacion 26.1623% y Edad 4.0425%**.

**Capacidad predictiva ≠ causalidad.** Las importancias son reducciones de impureza en train, con posibles sesgos, no efectos independientes. La selección comparativa utilizó el mismo test y las etapas exploratorias ya habían visto el dataset completo; no hay evaluación externa independiente. Espera y acceso deben estar disponibles al predecir, de modo que no se presenta el modelo como pronóstico previo a la atención. El MAE ordinal usa distancias entre niveles sin demostrar que los intervalos de satisfacción sean iguales.

## 7. Material de respaldo

Todo elemento fuera de las listas principales se clasifica para su conservación como **MATERIAL DE RESPALDO**, incluso si su valoración editorial es ÚTIL. No se elimina ningún archivo.

| Material                       | Elementos                                                        | Motivo para reservarlo                                                    |
| ------------------------------ | ---------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Composición y contexto         | F01–F06; H01–H03                                                 | Describen la muestra; compiten por tiempo con las barreras de atención    |
| Espera global alternativa      | F08                                                              | Redundancia con F07; F13 agrega segmentación                              |
| Acceso global en gráfico       | F09                                                              | El KPI comunica el mismo total con menor espacio                          |
| Utilización por condición      | F12; H08                                                         | Correcto, pero menos central para el relato de acceso y satisfacción      |
| Acceso marginal                | F14/F15; detalles H10/H11                                        | F16 prioriza combinaciones; conservar marginales para preguntas           |
| Satisfacción según medicación  | F18; H14                                                         | Complementa F17/F22, pero agrega una relación similar al relato           |
| Combinaciones del índice       | Tabla de perfiles de Etapa 6; H17                                | Aclara que un mismo score reúne perfiles diferentes                       |
| Dimensión territorial          | F21; H19                                                         | Aporta región; mejor como consulta si se prioriza cobertura               |
| Diagnóstico técnico del modelo | F24/F25/F27; H24                                                 | Detalle de errores y comparador; F23 más texto bastan en el relato        |
| Estadística de relaciones      | Tablas completas, H, χ², p, V, frecuencias esperadas             | Trazabilidad y supuestos para preguntas; evitar una exposición de pruebas |
| Modelado técnico               | Classification reports, CV, hiperparámetros, importancias OneHot | Sustentan reproducibilidad sin ocupar el bloque principal                 |
| Auditoría y preparación        | Informes y notebooks previos, controles de integridad y NA       | Respaldan el N efectivo y la conservación del dataset                     |

F11 y F13 tienen redundancia temática, pero se proponen en productos diferentes: media para el dashboard y distribución para la exposición. F14/F15 y F16 no son equivalentes estadísticos: los marginales y las combinaciones responden preguntas distintas, aunque mostrar todos recarga la comunicación. F19, F20 y F22 también responden preguntas distintas; reducirlos sería una decisión de espacio, no una declaración de equivalencia.

Las dos figuras de apoyo de presentación pasan a respaldo si no se utilizan. Las tablas completas y todas las figuras originales permanecen disponibles para las preguntas del docente.

## 8. Resultados clave

Se proponen **diez resultados clave**, correspondientes a H04, H10, H12, H13, H15, H16, H18, H20, H22 y H23, los diez hallazgos clasificados como ESENCIAL.

**H04 · Espera general**

- **HALLAZGO:** La espera presenta dispersión y una media superior a la mediana.
- **EVIDENCIA:** Media 64.58 min; mediana 54; N=2426 (Etapa 4).
- **INTERPRETACIÓN:** Un único promedio no describe todas las experiencias de espera.
- **LIMITACIÓN:** Se excluyen 74 NA y no se explica la causa de las esperas.

**H10 · Cobertura y medicación**

- **HALLAZGO:** El acceso a medicación difiere según cobertura.
- **EVIDENCIA:** Porcentajes de acceso Sí entre 48.88% y 85.05%; V=.3199; N=2500 (Etapa 5).
- **INTERPRETACIÓN:** La cobertura organiza diferencias relevantes para describir el acceso.
- **LIMITACIÓN:** La asociación observada en datos ficticios no identifica un efecto causal.

**H12 · Combinaciones de acceso**

- **HALLAZGO:** Las combinaciones de cobertura y condición muestran contrastes de acceso.
- **EVIDENCIA:** Privada/Aguda: 89.22% (240/269); Sin cobertura/Crónica: 41.99% (118/281) (Etapa 5).
- **INTERPRETACIÓN:** Examinar combinaciones evita que el total oculte perfiles con experiencias distintas.
- **LIMITACIÓN:** La comparación de estas celdas es descriptiva y no proviene de pruebas específicas entre las nueve combinaciones.

**H13 · Espera y satisfacción**

- **HALLAZGO:** Espera y satisfacción presentan una asociación negativa.
- **EVIDENCIA:** Spearman −.7402; p<.001; N=2357 (Etapa 5).
- **INTERPRETACIÓN:** En estos registros, mayores esperas se asocian con niveles menores de satisfacción.
- **LIMITACIÓN:** No demuestra causalidad y excluye 143 registros sin alguna de las dos variables.

**H15 · Disponibilidad del índice**

- **HALLAZGO:** El índice puede calcularse en la mayoría de los registros.
- **EVIDENCIA:** 2426 casos calculables (97.04%); 74 NA (Etapa 6).
- **INTERPRETACIÓN:** La cobertura de cálculo debe acompañar cualquier comunicación del score.
- **LIMITACIÓN:** Los registros sin espera quedan sin score y no se interpretan como score cero.

**H16 · Distribución del score**

- **HALLAZGO:** El score distingue cantidad de dimensiones concurrentes.
- **EVIDENCIA:** Scores 0/1/2/3: 904/937/471/114; N=2426 (Etapa 6).
- **INTERPRETACIÓN:** El resumen permite comunicar acumulación de dimensiones de acceso y atención.
- **LIMITACIÓN:** Un mismo score puede reunir combinaciones diferentes y no expresa severidad clínica.

**H18 · Score por cobertura**

- **HALLAZGO:** La distribución del score cambia según cobertura.
- **EVIDENCIA:** Score 3: Privada 0.00%, Pública 3.09%, Sin cobertura 10.90%; N respectivos 823/777/826 (Etapa 6).
- **INTERPRETACIÓN:** La segmentación muestra dónde coinciden las tres dimensiones dentro del dataset.
- **LIMITACIÓN:** El patrón depende de la fórmula y del umbral de espera y no demuestra un efecto de la cobertura.

**H20 · Score y satisfacción**

- **HALLAZGO:** Las medianas de satisfacción son menores en los scores 2 y 3.
- **EVIDENCIA:** Medianas por score 0/1/2/3: 4/4/3/2; N=2357 (Etapa 6).
- **INTERPRETACIÓN:** La acumulación descrita se conecta con la experiencia declarada de atención.
- **LIMITACIÓN:** Esta asociación en el mismo dataset no valida externamente el índice.

**H22 · Comparación predictiva**

- **HALLAZGO:** Decision Tree mejora las métricas del baseline en el test utilizado.
- **EVIDENCIA:** Macro F1 .5071 frente a .0986; MAE .5309 frente a .9239; N=486 (Etapa 7).
- **INTERPRETACIÓN:** Los predictores aportan información respecto de asignar siempre satisfacción 4.
- **LIMITACIÓN:** El mismo test intervino en la selección, por lo que no es una evaluación externa independiente.

**H23 · Errores ordinales**

- **HALLAZGO:** El acierto exacto y la proximidad ordinal muestran aspectos distintos.
- **EVIDENCIA:** Exactas 50.41%; dentro de ±1 96.50%; errores ≥2 3.50% (17/486) (Etapa 7).
- **INTERPRETACIÓN:** Muchos desaciertos son de un nivel, por lo que conviene comunicar su magnitud junto con el acierto exacto.
- **LIMITACIÓN:** La distancia numérica entre niveles no acredita intervalos iguales de satisfacción.

## 9. Estructura narrativa propuesta

**Dashboard:** bloque de contexto y N efectivo; KPIs candidatos de espera, acceso y satisfacción con decisión pendiente; vistas F11/F16 para barreras; F10 para niveles de satisfacción; F19/F20/F22 para el índice y su relación con la experiencia. Segmentadores candidatos: región, cobertura y condición. La eventual inclusión del modelo queda pendiente y exigiría revisar el espacio disponible.

**Presentación, como recorrido temático y no como diapositivas:**

1. Contexto: problema de equidad en el acceso y la atención.
2. Pregunta principal y datos: carácter ficticio, registros, preparación y N efectivo.
3. Evidencia exploratoria: magnitud y distribución de espera, con F07.
4. Diferencias en acceso y espera: cobertura y condición, con F13/F16.
5. Experiencia reportada: relación entre espera y satisfacción, con F17.
6. Índice operacional de vulnerabilidad en el acceso y la atención: definición, distribución F19 y, como apoyo, F22.
7. Modelado de satisfacción: referencia trivial, aporte y límites, con F23 y opcionalmente F26.
8. Síntesis de la evidencia que responde la pregunta y limitaciones del proyecto.
9. Espacio posterior para conclusiones y recomendaciones que el equipo elaborará en la etapa correspondiente; aquí no se redactan.

La distribución del tiempo y de las intervenciones se acordará con el equipo para respetar los 20 minutos y la participación equilibrada. El material de respaldo sostiene los 10 minutos de preguntas.

## 10. Decisiones pendientes

| Decisión del equipo        | Alternativas o criterio a discutir                                       | Qué queda pendiente                                                                 |
| -------------------------- | ------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| KPI de satisfacción        | Promedio solicitado por el caso frente a mediana y distribución ordinal  | Resolver el requisito y documentar la justificación antes de construir el dashboard |
| Cantidad final de gráficos | Seis candidatos dashboard; ocho presentación con dos apoyos              | Elegir el número final según espacio y tiempo                                       |
| Prioridad del índice       | F19 distribución; F20 cobertura; F22 satisfacción; F21 respaldo regional | Definir qué vista se prioriza y cómo conservar contexto y limitaciones              |
| Detalle del modelo         | F23 principal; F26 apoyo; matrices y CV en respaldo                      | Acordar cuánto explicar de métricas, errores e importancias                         |
| Modelo en dashboard        | Mantener foco descriptivo e índice o incorporar evidencia predictiva     | Decidir inclusión y qué elemento reemplazaría                                       |
| Segmentación y N efectivo  | Región, cobertura y condición; NA por variables de cada vista            | Definir funcionamiento y rotulado de los filtros en la etapa de construcción        |
| Organización oral          | Recorrido propuesto y dos figuras de apoyo opcionales                    | Distribuir intervenciones y tiempo; elegir apoyos tras ensayo                       |

Estas son propuestas para revisión, no decisiones adoptadas automáticamente. La definición del índice ya acordada en Etapa 6 se conserva; no se proponen categorías nuevas.

**Control de alcance:** esta etapa genera únicamente este informe. No ejecuta notebooks, recalcula resultados, modifica datasets o entregables previos, entrena modelos ni crea figuras. No introduce conclusiones causales, categorías de score, clasificación binaria de vulnerabilidad, recomendaciones finales, dashboard o presentación. Los números analíticos proceden de los informes enlazados; los resultados del generador sintético no se convierten en evidencia de causalidad ni de representatividad.

