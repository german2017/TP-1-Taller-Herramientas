# Etapa 7 - Modelado predictivo de satisfacción

## 1. Objetivo

Predecir los niveles 1–5 de Satisfaccion y comparar Decision Tree y Random Forest frente a una regla de clase mayoritaria. Satisfacción es ordinal, aunque los dos clasificadores aprenden clases nominales; el orden se incorpora a la evaluación mediante distancia absoluta. Es un ejercicio sobre datos ficticios, no un sistema clínico ni un modelo para uso real. Se leyeron los seis informes anteriores.

El escenario es estimar satisfacción cuando se conocen espera y acceso a medicación. No es una predicción previa a la atención: la disponibilidad temporal de estas variables no está documentada y no se presupone un despliegue prospectivo.

## 2. Preparación de los datos

Fuente exclusiva: data/processed/dataset_salud_publica_limpio.xlsx. Se conservan sus 2500 filas; solo en la muestra de modelado se excluyen 72 sin target. **N modelable=2428**. Se retienen los 71 registros con target presente y espera faltante.

Predictores autorizados: Region, Edad, Genero, Condicion_Salud, Cobertura_Salud, Frecuencia_Atencion, Tiempo_Espera_min, Acceso_Medicacion.

ID_Paciente se excluye por ser identificador y no predictor sustantivo. Score_Vulnerabilidad y Dim_* se excluyen porque fueron construidos posteriormente y son redundantes con originales; no se carga el dataset analítico para entrenar. No se usa ninguna variable derivada de satisfacción. Convertir el target disponible a entero conserva sus cinco niveles; no se modifica la columna fuente.

## 3. Partición train/test

Split estratificado por Satisfaccion, test_size=0.20, random_state=42: **train=1942**, **test=486**, total=2428. El redondeo del tamaño de test produce 486 registros. Train y test no comparten filas.

| Nivel | N total | Total % | N train | Train % | N test | Test %  |
| ----: | ------: | ------: | ------: | ------: | -----: | ------: |
|     1 |     139 |  5.7249 |     111 |  5.7158 |     28 |  5.7613 |
|     2 |     328 | 13.5091 |     262 | 13.4912 |     66 | 13.5802 |
|     3 |     576 | 23.7232 |     461 | 23.7384 |    115 | 23.6626 |
|     4 |     794 | 32.7018 |     635 | 32.6982 |    159 | 32.7160 |
|     5 |     591 | 24.3410 |     473 | 24.3563 |    118 | 24.2798 |

La distribución del target se informa para verificar estratificación. El test no participa en ajuste, imputación, codificación ni validación cruzada. Tras entrenar las configuraciones fijas, se evalúan una sola vez sobre el mismo test. No se reajustan parámetros con esos resultados.

## 4. Preprocesamiento

ColumnTransformer dentro de Pipeline: OneHotEncoder(handle_unknown='ignore', sparse_output=False) para Region, Genero, Condicion_Salud, Cobertura_Salud y Acceso_Medicacion; Edad y Frecuencia_Atencion pasan sin cambios; SimpleImputer(strategy='median') procesa exclusivamente Tiempo_Espera_min. No se escala. Encoder e imputador se ajustan exclusivamente con train y, durante CV, solo con el train de cada pliegue. La imputación es temporal para el modelo: conserva la decisión previa de mantener NA en archivos y análisis descriptivos. [Prevención de leakage con pipelines](https://scikit-learn.org/stable/common_pitfalls.html).

Mediana de espera aprendida con train: **55.00 min**. NA de espera retenidos: train=55, test=16. La igualdad de la mediana aprendida y la mediana de train se verificó en ambos modelos y en los diez ajustes internos de CV.

**Estabilidad descriptiva en train (cinco pliegues):**

| Modelo        | Macro F1 medio | DE macro F1 | MAE medio | DE MAE |
| ------------- | -------------: | ----------: | --------: | -----: |
| Decision Tree |         0.4918 |      0.0214 |    0.5268 | 0.0258 |
| Random Forest |         0.4812 |      0.0260 |    0.5428 | 0.0199 |

Cada pliegue usa aproximadamente 1553–1554 registros para ajustar y 388–389 para validar. Estas DE describen variación entre pliegues de una sola partición de train; no son intervalos de confianza ni prueban estabilidad externa. No se eligieron nuevos hiperparámetros con CV ni con test.

## 5. Baseline

Se predice siempre la clase **4**, la más frecuente de train (635/1942). No es un tercer modelo principal.

| Estrategia | Accuracy | Macro Precision | Macro Recall | Macro F1 | MAE ordinal | Exactas % | Dentro de ±1 % | Error >=2 % |
| ---------- | -------: | --------------: | -----------: | -------: | ----------: | --------: | -------------: | ----------: |
| Baseline   |   0.3272 |          0.0654 |       0.2000 |   0.0986 |      0.9239 |   32.7160 |        80.6584 |     19.3416 |

Dentro de ±1 incluye aciertos exactos. Las métricas macro dan igual peso a cada clase. Cuando una clase no recibe predicciones, su precisión se registra como 0 con zero_division=0.

## 6. Decision Tree

criterion='gini', max_depth=6, min_samples_leaf=10, min_samples_split=2, random_state=42. Se limita profundidad y tamaño mínimo de hoja para reducir particiones pequeñas y facilitar lectura del árbol. No se busca el máximo ajuste de train.

| Modelo        | Accuracy | Macro Precision | Macro Recall | Macro F1 | MAE ordinal | Exactas % | Dentro de ±1 % | Error >=2 % |
| ------------- | -------: | --------------: | -----------: | -------: | ----------: | --------: | -------------: | ----------: |
| Decision Tree |   0.5041 |          0.5447 |       0.5108 |   0.5071 |      0.5309 |   50.4115 |        96.5021 |      3.4979 |

**Classification report (test):**

| Clase/promedio | Precision | Recall | F1     | Support |
| -------------- | --------: | -----: | -----: | ------: |
| 1              |    0.8000 | 0.4286 | 0.5581 |      28 |
| 2              |    0.4458 | 0.5606 | 0.4966 |      66 |
| 3              |    0.4336 | 0.4261 | 0.4298 |     115 |
| 4              |    0.4712 | 0.3082 | 0.3726 |     159 |
| 5              |    0.5731 | 0.8305 | 0.6782 |     118 |
| macro avg      |    0.5447 | 0.5108 | 0.5071 |     486 |
| weighted avg   |    0.5025 | 0.5041 | 0.4879 |     486 |

Accuracy global=0.5041, N test=486.

**Visualización:** Matriz de conteos con orden 1–5; filas reales y columnas predichas permiten localizar confusiones cercanas y extremas.

![matriz_confusion_decision_tree.png](../outputs/figuras/modelado/matriz_confusion_decision_tree.png)

Confusiones dirigidas más frecuentes: real 4 → predicho 5: 70; real 4 → predicho 3: 38; real 3 → predicho 4: 32. Errores de exactamente un nivel: 224; de ≥2: 17; extremos 1→5=0, 5→1=0. Menor recall en nivel(es) 4: 0.3082. Los soportes por clase condicionan la estabilidad de estos porcentajes.

## 7. Random Forest

n_estimators=200, criterion='gini', max_depth=10, min_samples_leaf=3, min_samples_split=2, max_features='sqrt', bootstrap=True, n_jobs=1, random_state=42. Se promedian 200 árboles con muestreo bootstrap y subconjuntos de features; límites moderados reducen hojas mínimas. La estructura del conjunto es menos interpretable que un árbol individual.

| Modelo        | Accuracy | Macro Precision | Macro Recall | Macro F1 | MAE ordinal | Exactas % | Dentro de ±1 % | Error >=2 % |
| ------------- | -------: | --------------: | -----------: | -------: | ----------: | --------: | -------------: | ----------: |
| Random Forest |   0.4918 |          0.5044 |       0.4758 |   0.4840 |      0.5412 |   49.1770 |        96.7078 |      3.2922 |

**Classification report (test):**

| Clase/promedio | Precision | Recall | F1     | Support |
| -------------- | --------: | -----: | -----: | ------: |
| 1              |    0.6316 | 0.4286 | 0.5106 |      28 |
| 2              |    0.3966 | 0.3485 | 0.3710 |      66 |
| 3              |    0.4403 | 0.5130 | 0.4739 |     115 |
| 4              |    0.4706 | 0.4025 | 0.4339 |     159 |
| 5              |    0.5827 | 0.6864 | 0.6304 |     118 |
| macro avg      |    0.5044 | 0.4758 | 0.4840 |     486 |
| weighted avg   |    0.4899 | 0.4918 | 0.4869 |     486 |

Accuracy global=0.4918, N test=486.

**Visualización:** Matriz de conteos con orden 1–5; filas reales y columnas predichas permiten localizar confusiones cercanas y extremas.

![matriz_confusion_random_forest.png](../outputs/figuras/modelado/matriz_confusion_random_forest.png)

Confusiones dirigidas más frecuentes: real 4 → predicho 5: 56; real 4 → predicho 3: 37; real 5 → predicho 4: 34. Errores de exactamente un nivel: 231; de ≥2: 16; extremos 1→5=0, 5→1=0. Menor recall en nivel(es) 2: 0.3485. Los soportes por clase condicionan la estabilidad de estos porcentajes.

## 8. Comparación de modelos

| Modelo        | Accuracy | Macro Precision | Macro Recall | Macro F1 | MAE ordinal | Exactas % | Dentro de ±1 % | Error >=2 % |
| ------------- | -------: | --------------: | -----------: | -------: | ----------: | --------: | -------------: | ----------: |
| Baseline      |   0.3272 |          0.0654 |       0.2000 |   0.0986 |      0.9239 |   32.7160 |        80.6584 |     19.3416 |
| Decision Tree |   0.5041 |          0.5447 |       0.5108 |   0.5071 |      0.5309 |   50.4115 |        96.5021 |      3.4979 |
| Random Forest |   0.4918 |          0.5044 |       0.4758 |   0.4840 |      0.5412 |   49.1770 |        96.7078 |      3.2922 |

**Criterio fijado antes de evaluar:** entre los dos modelos, sumar los rangos de macro F1 (mayor es mejor), MAE ordinal (menor) y porcentaje de errores ≥2 (menor). Si hay empate se elige menor DE de macro F1 en CV de train y, si persiste, Decision Tree por interpretabilidad. Accuracy se informa, pero no decide. La matriz de confusión se revisa para identificar clases difíciles y errores extremos.

| Modelo        | Rango F1 | Rango MAE | Rango errores ≥2 | Suma de rangos |
| ------------- | -------: | --------: | ---------------: | -------------: |
| Decision Tree |   1.0000 |    1.0000 |           2.0000 |         4.0000 |
| Random Forest |   2.0000 |    2.0000 |           1.0000 |         5.0000 |

**Modelo seleccionado para análisis posterior: Decision Tree.** Confusiones dirigidas más frecuentes: real 4 → predicho 5: 70; real 4 → predicho 3: 38; real 3 → predicho 4: 32. Errores de exactamente un nivel: 224; de ≥2: 17; extremos 1→5=0, 5→1=0. Menor recall en nivel(es) 4: 0.3082.

La selección comparativa solicitada usa los resultados de este test una sola vez, sin reajuste. Por eso el test ya no constituye una estimación independiente de la selección del ganador; haría falta otra evaluación externa para confirmarla. La CV de train aporta contexto de estabilidad, sin justificar superioridad poblacional.

**Visualización:** Tres paneles separan macro F1, MAE ordinal y errores grandes en sus propias unidades; no se mezclan porcentajes con niveles en un mismo eje.

![comparacion_modelos.png](../outputs/figuras/modelado/comparacion_modelos.png)

## 9. Análisis ordinal de errores

Modelo: **Decision Tree**; N test=486. MAE ordinal = promedio de |nivel real − nivel predicho| = **0.5309**. La distancia en niveles permite distinguir 5→4 (1) de 5→1 (4), pero no prueba que la escala tenga distancias psicológicas iguales.

| Error absoluto | Cantidad | Porcentaje test |
| -------------: | -------: | --------------: |
|              0 |      245 |         50.4115 |
|              1 |      224 |         46.0905 |
|              2 |       17 |          3.4979 |
|              3 |        0 |          0.0000 |
|              4 |        0 |          0.0000 |

Exactas=50.41%; dentro de ±1=96.50% (incluye exactas); error ≥2=3.50% (17 casos); errores extremos=0.

Errores grandes por nivel real (porcentaje dentro de cada nivel, no del test total):

| Nivel real | N test | Error ≥2 (n) | Error ≥2 (%) |
| ---------: | -----: | -----------: | -----------: |
|          1 |     28 |            2 |       7.1429 |
|          2 |     66 |            6 |       9.0909 |
|          3 |    115 |            4 |       3.4783 |
|          4 |    159 |            2 |       1.2579 |
|          5 |    118 |            3 |       2.5424 |

No se muestran IDs ni se construyen reglas nuevas a partir de los errores.

**Visualización:** Barras 0–4 distinguen aciertos, errores vecinos y saltos grandes; complementan la matriz sin ocultar errores poco frecuentes.

![distribucion_error_ordinal.png](../outputs/figuras/modelado/distribucion_error_ordinal.png)

## 10. Importancia de variables

Importancias del modelo seleccionado: **Decision Tree**.

**A. Features transformadas:**

| Feature transformada                       | Variable original   | Importancia |
| ------------------------------------------ | ------------------- | ----------: |
| espera__Tiempo_Espera_min                  | Tiempo_Espera_min   |      0.6310 |
| categoricas__Acceso_Medicacion_Sí          | Acceso_Medicacion   |      0.1317 |
| categoricas__Acceso_Medicacion_No          | Acceso_Medicacion   |      0.1299 |
| numericas__Edad                            | Edad                |      0.0404 |
| numericas__Frecuencia_Atencion             | Frecuencia_Atencion |      0.0228 |
| categoricas__Genero_Otro                   | Genero              |      0.0086 |
| categoricas__Cobertura_Salud_Sin cobertura | Cobertura_Salud     |      0.0071 |
| categoricas__Genero_F                      | Genero              |      0.0066 |
| categoricas__Region_Sur                    | Region              |      0.0051 |
| categoricas__Condicion_Salud_Aguda         | Condicion_Salud     |      0.0050 |
| categoricas__Genero_M                      | Genero              |      0.0048 |
| categoricas__Condicion_Salud_Saludable     | Condicion_Salud     |      0.0048 |
| categoricas__Condicion_Salud_Crónica       | Condicion_Salud     |      0.0022 |
| categoricas__Region_Buenos Aires           | Region              |      0.0000 |
| categoricas__Region_CABA                   | Region              |      0.0000 |
| categoricas__Region_Centro                 | Region              |      0.0000 |
| categoricas__Region_Norte                  | Region              |      0.0000 |
| categoricas__Cobertura_Salud_Privada       | Cobertura_Salud     |      0.0000 |
| categoricas__Cobertura_Salud_Pública       | Cobertura_Salud     |      0.0000 |

**B. Variables originales:** las categorías OneHot se asignan mediante categories_ y el orden del ColumnTransformer, sin adivinar nombres por prefijos. Se suman sus importancias y se conservan las numéricas individuales.

| Variable original   | Importancia agregada | Porcentaje |
| ------------------- | -------------------: | ---------: |
| Tiempo_Espera_min   |               0.6310 |    63.1003 |
| Acceso_Medicacion   |               0.2616 |    26.1623 |
| Edad                |               0.0404 |     4.0425 |
| Frecuencia_Atencion |               0.0228 |     2.2755 |
| Genero              |               0.0200 |     2.0038 |
| Condicion_Salud     |               0.0119 |     1.1943 |
| Cobertura_Salud     |               0.0071 |     0.7111 |
| Region              |               0.0051 |     0.5103 |

Suma agregada verificada: **1.000000**. Son reducciones de impureza acumuladas en train, no efectos causales ni aportes independientes. Pueden favorecer variables continuas o con muchas categorías; variables relacionadas pueden repartirse importancia. La suma por variable facilita lectura pero no elimina ese sesgo. [Limitaciones de la importancia por impureza](https://scikit-learn.org/stable/auto_examples/ensemble/plot_forest_importances.html).

**Visualización:** Barras horizontales muestran las ocho variables originales tras sumar categorías OneHot, sin confundir codificaciones individuales con variables sustantivas.

![importancia_variables_modelo.png](../outputs/figuras/modelado/importancia_variables_modelo.png)

## 11. Interpretación crítica

El modelo seleccionado obtiene macro F1=0.5071 frente a 0.0986 del baseline, y MAE=0.5309 frente a 0.9239. Acertó exactamente en 50.41% y quedó dentro de ±1 en 96.50%; registró 17 errores de ≥2 y 0 extremos. La mejora observada se evalúa conjuntamente, no solo por accuracy; no se realizó una prueba de superioridad entre modelos.

Variables con mayor importancia: Tiempo_Espera_min: 63.10%; Acceso_Medicacion: 26.16%; Edad: 4.04%. La relevancia predictiva observada de espera y acceso es compatible con el EDA y las relaciones sintéticas documentadas; no es un descubrimiento causal ni una validación independiente del generador de datos. La importancia indica uso en particiones del modelo y no necesidad causal.

Decision Tree tiene profundidad realizada 6 y 50 hojas; Random Forest reúne 200 árboles. El árbol ofrece una estructura individual inspeccionable; el bosque tiene mayor complejidad. La CV informa variación dentro de train, pero una semilla y un dataset no prueban estabilidad frente a otros escenarios.

## 12. Hallazgos

### Hallazgo 1

**RESULTADO:** Modelable=2428, train=1942, test=486; 72 targets ausentes excluidos y 71 esperas faltantes retenidas.

**INTERPRETACIÓN:** El flujo permite modelar los casos con etiqueta sin perderlos por NA en espera.

**LIMITACIÓN:** No se aprende de los 72 sin target; se desconoce el mecanismo de ausencia.

### Hallazgo 2

**RESULTADO:** Decision Tree: macro F1=0.5071, MAE=0.5309; baseline F1=0.0986, MAE=0.9239, mismo test N=486.

**INTERPRETACIÓN:** Las métricas permiten contrastar capacidad predictiva con una estrategia trivial.

**LIMITACIÓN:** La selección sobre el test impide tomar la estimación del ganador como evaluación externa independiente.

### Hallazgo 3

**RESULTADO:** Exactas=50.41%; dentro de ±1=96.50%; error ≥2=3.50% (17/486).

**INTERPRETACIÓN:** La evaluación ordinal distingue fallos vecinos de saltos grandes.

**LIMITACIÓN:** La distancia numérica no acredita intervalos iguales de satisfacción.

### Hallazgo 4

**RESULTADO:** Confusiones dirigidas más frecuentes: real 4 → predicho 5: 70; real 4 → predicho 3: 38; real 3 → predicho 4: 32. Errores de exactamente un nivel: 224; de ≥2: 17; extremos 1→5=0, 5→1=0. Menor recall en nivel(es) 4: 0.3082. N test=486.

**INTERPRETACIÓN:** La matriz permite localizar dificultades por clase además del acierto global.

**LIMITACIÓN:** Los niveles con menor soporte tienen estimaciones más variables; no se crean reglas nuevas.

### Hallazgo 5

**RESULTADO:** Tiempo_Espera_min: 63.10%; Acceso_Medicacion: 26.16%; Edad: 4.04%; suma total de importancias=1.0000.

**INTERPRETACIÓN:** El modelo utiliza más estas variables según reducción de impureza en train.

**LIMITACIÓN:** Importancia no equivale a causalidad; puede tener sesgos de cardinalidad y redundancia.

## 13. Limitaciones

Datos ficticios con relaciones incorporadas, sin validación externa ni representatividad. Las etapas exploratorias previas observaron el dataset completo: el split de esta etapa evita leakage de ajuste y preprocesamiento, pero no vuelve completamente ciega la exploración previa. La selección final entre dos modelos usa el mismo test; no se afina después, y se reconoce el posible optimismo de seleccionar al ganador. CV se limita a cinco pliegues de train y no certifica estabilidad en otra población.

Los clasificadores optimizan clases nominales, no una pérdida ordinal; MAE se añade para evaluar distancias en niveles. La mediana de espera simplifica la información ausente y puede reducir variabilidad; se aprende solo con train pero no recupera el valor verdadero. No se analizan calibración, equidad, despliegue o desempeño temporal. Espera y acceso deben estar disponibles al predecir, lo cual limita cualquier lectura prospectiva. No se infiere causalidad, no se proponen decisiones clínicas ni recomendaciones finales.

Entregables: notebooks/07_modelado.ipynb, reports/07_modelado.md y cinco figuras en outputs/figuras/modelado/. No se serializa el modelo. Ejecutar el notebook reproduce entrenamiento, evaluación y figuras.

Entorno: Python 3.12.3, pandas 3.0.5, NumPy 2.5.3, scikit-learn 1.9.1, matplotlib 3.11.2.

**Control final aprobado:** split estratificado 42 sin solapamiento; 2428 modelables, 1942 train y 486 test; encoder e imputador dentro de pipelines, con medianas de cada train verificadas; test usado solo para predicciones y evaluación comparativa, sin fit ni reajuste posterior; ocho predictores autorizados; matrices 5×5 en orden 1–5, mismo test para las tres estrategias; importancia extraída solo del seleccionado y suma agregada igual a 1. Datos y entregables anteriores intactos por comparación exacta y SHA-256. Sin IDs de pacientes en el informe.

SHA-256 del procesado conservado: 6707074a0d805b2fce33f461c10c9335adcb5ab302d960bc0e963db868b983bd.
