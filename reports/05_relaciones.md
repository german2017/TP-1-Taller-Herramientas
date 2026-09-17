# Etapa 5 - Análisis de relaciones

## 1. Objetivo y metodología

Analizar diferencias, evidencia estadística y magnitud de las relaciones planteadas en el caso, exclusivamente en el dataset ficticio procesado. Se leyeron los informes de las Etapas 1–4. Cada análisis selecciona temporalmente casos completos solo en las variables necesarias e informa N y exclusiones; el dataset y sus NA permanecen intactos.

**α = 0.05**, contrastes globales o bilaterales según corresponda. Se aplican cinco pruebas principales: dos Kruskal-Wallis, dos chi-cuadrado y un Spearman. Los p-values son nominales, sin ajuste por multiplicidad: se interpretan como exploratorios, no como confirmación simultánea de todas las hipótesis. Un p-value pequeño no mide fuerza ni relevancia práctica. No se realizan post-hoc: las preguntas globales no requieren contrastar cada par.

Una fila representa un paciente y los 2500 IDs son únicos; eso es compatible con observaciones separadas, pero no demuestra independencia estadística. La independencia se adopta como supuesto de trabajo del ejercicio; no se documentan muestreo ni posibles agrupamientos. Los contrastes describen compatibilidad con hipótesis bajo ese supuesto y no permiten generalizar a población real.

Desviaciones estándar muestrales (ddof=1), cuartiles con interpolación lineal. Satisfacción se conserva ordinal, con rangos medios para empates en Spearman. Se usa p < 0.001 para valores extremadamente pequeños, incluso si el cálculo en coma flotante devuelve cero por subdesbordamiento; no significa probabilidad matemáticamente nula.

Entorno: Python 3.12.3, pandas 3.0.5, scipy 1.18.1, matplotlib 3.11.2.

## 2. Condición de salud y frecuencia de atención

N efectivo: **2500**; excluidos por NA: **0**.

| Grupo     | N   | Media  | Mediana | DE    | Q1    | Q3     | Mínimo | Máximo |
| --------- | --: | -----: | ------: | ----: | ----: | -----: | -----: | -----: |
| Saludable | 828 |  1.488 |   1.000 | 1.116 | 1.000 |  3.000 |      0 |      3 |
| Aguda     | 829 |  4.031 |   4.000 | 1.385 | 3.000 |  5.000 |      2 |      6 |
| Crónica   | 843 | 12.926 |  13.000 | 4.192 | 9.000 | 16.000 |      6 |     20 |

**Visualización y justificación:** Boxplots en orden lógico comparan mediana, intervalo intercuartílico, dispersión y solapamiento. Bigotes de 1.5 × IQR; puntos exteriores, si existen, se conservan y no se consideran errores automáticamente.

![frecuencia_por_condicion.png](../outputs/figuras/relaciones/frecuencia_por_condicion.png)

Evaluación previa: el conteo tiene empates y límites observados distintos: Saludable 0–3, Aguda 2–6 y Crónica 6–20. Las DE y los IQR de la tabla muestran dispersiones diferentes; no se presume normalidad ni igualdad de forma. Kruskal-Wallis es adecuado como contraste global de rangos de tres grupos independientes bajo el supuesto indicado; no se interpreta exclusivamente como diferencia de medianas. Cada grupo supera cinco observaciones. [Método y corrección de empates: SciPy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.kruskal.html).

**Kruskal-Wallis:** H=2042.640, gl=2, p < 0.001, N=2500. log10(p) de la aproximación χ²₂ = -443.55. Se rechaza la hipótesis global de distribuciones iguales a α=0.05. Hay evidencia de diferencias en rangos entre grupos; no se identifica inferencialmente cada par. La magnitud descriptiva se aprecia en medianas 1, 4 y 13 consultas y en sus IQR; el p-value no cuantifica esa separación.

## 3. Cobertura y tiempo de espera

| Cobertura     | N total | N disponible | NA  | Media min | Mediana min | DE min | Q1 min | Q3 min  |
| ------------- | ------: | -----------: | --: | --------: | ----------: | -----: | -----: | ------: |
| Privada       |     843 |          823 |  20 |    17.601 |      18.000 |  7.502 | 11.000 |  24.000 |
| Pública       |     806 |          777 |  29 |    70.192 |      71.000 | 29.254 | 45.000 |  95.000 |
| Sin cobertura |     851 |          826 |  25 |   106.111 |     105.000 | 43.260 | 70.000 | 144.000 |

N efectivo total: **2426**; excluidos por NA: **74**.

**Visualización y justificación:** Boxplots en orden lógico comparan mediana, intervalo intercuartílico, dispersión y solapamiento. Bigotes de 1.5 × IQR; puntos exteriores, si existen, se conservan y no se consideran errores automáticamente.

![espera_por_cobertura_boxplot.png](../outputs/figuras/relaciones/espera_por_cobertura_boxplot.png)

Evaluación previa: los rangos observados son 5–30, 20–120 y 30–180 minutos; los IQR son 13, 50 y 74 minutos. Hay dispersiones distintas y duraciones acotadas con empates; no se supone normalidad. Se aplica Kruskal-Wallis como contraste global de rangos, con cientos de casos por grupo, sin atribuir todo el resultado a diferencias de medianas.

**Kruskal-Wallis:** H=1684.378, gl=2, p < 0.001, N=2426; log10(p) aproximado χ²₂=-365.76. Se rechaza la hipótesis global a α=0.05. Medianas 18, 71 y 105 min para Privada, Pública y Sin cobertura: diferencias observadas de ubicación y dispersión. No se concluye que la cobertura cause la espera ni que cada par sea significativo.

## 4. Cobertura y acceso a medicación

N efectivo: **2500**; excluidos por NA: **0**. Porcentajes dentro de cada grupo.

| Cobertura_Salud | Sí (n) | No (n) | N   | Sí (%) | No (%) |
| --------------- | -----: | -----: | --: | -----: | -----: |
| Privada         |    717 |    126 | 843 | 85.053 | 14.947 |
| Pública         |    562 |    244 | 806 | 69.727 | 30.273 |
| Sin cobertura   |    416 |    435 | 851 | 48.884 | 51.116 |

**Visualización y justificación:** Barras apiladas al 100% comparan la composición Sí/No dentro de cada grupo, independientemente de su tamaño; etiquetas y N explicitan el denominador.

![acceso_por_cobertura.png](../outputs/figuras/relaciones/acceso_por_cobertura.png)

Frecuencias esperadas bajo independencia:

| Cobertura_Salud | Sí esperado | No esperado |
| --------------- | ----------: | ----------: |
| Privada         |     571.554 |     271.446 |
| Pública         |     546.468 |     259.532 |
| Sin cobertura   |     576.978 |     274.022 |

**Chi-cuadrado:** χ²=255.798, gl=2, p < 0.001, N=2500. **V de Cramér=0.3199**. Mínimo esperado=259.532; celdas esperadas <5: 0; mínimo observado=126. Se usan conteos, categorías excluyentes y una celda por paciente. Se cumple el control de frecuencias; la independencia entre pacientes sigue siendo un supuesto de trabajo. Se aplica χ² de independencia sin corrección de continuidad (tabla 3×2, gl=2). [Supuestos y cálculo: SciPy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.chi2_contingency.html).

**Significación:** hay evidencia de asociación al nivel nominal 0.05. **Magnitud:** V=0.3199 en escala 0–1, sin dirección ni interpretación de porcentaje de varianza. Se interpreta junto con las proporciones observadas, sin umbrales universales de importancia. Fórmula sin corrección por sesgo: V = √[χ² / (N × min(r−1,c−1))]; aquí min(r−1,c−1)=1. [Verificación de V: SciPy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.contingency.association.html).

## 5. Condición de salud y acceso a medicación

N efectivo: **2500**; excluidos por NA: **0**. Porcentajes dentro de cada grupo.

| Condicion_Salud | Sí (n) | No (n) | N   | Sí (%) | No (%) |
| --------------- | -----: | -----: | --: | -----: | -----: |
| Saludable       |    589 |    239 | 828 | 71.135 | 28.865 |
| Aguda           |    592 |    237 | 829 | 71.411 | 28.589 |
| Crónica         |    514 |    329 | 843 | 60.973 | 39.027 |

**Visualización y justificación:** Barras apiladas al 100% comparan la composición Sí/No dentro de cada grupo, independientemente de su tamaño; etiquetas y N explicitan el denominador.

![acceso_por_condicion.png](../outputs/figuras/relaciones/acceso_por_condicion.png)

Frecuencias esperadas bajo independencia:

| Condicion_Salud | Sí esperado | No esperado |
| --------------- | ----------: | ----------: |
| Saludable       |     561.384 |     266.616 |
| Aguda           |     562.062 |     266.938 |
| Crónica         |     571.554 |     271.446 |

**Chi-cuadrado:** χ²=27.170, gl=2, p < 0.001, N=2500. **V de Cramér=0.1042**. Mínimo esperado=266.616; celdas esperadas <5: 0; mínimo observado=237. Se usan conteos, categorías excluyentes y una celda por paciente. Se cumple el control de frecuencias; la independencia entre pacientes sigue siendo un supuesto de trabajo. Se aplica χ² de independencia sin corrección de continuidad (tabla 3×2, gl=2). [Supuestos y cálculo: SciPy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.chi2_contingency.html).

**Significación:** hay evidencia de asociación al nivel nominal 0.05. **Magnitud:** V=0.1042 en escala 0–1, sin dirección ni interpretación de porcentaje de varianza. Se interpreta junto con las proporciones observadas, sin umbrales universales de importancia. Fórmula sin corrección por sesgo: V = √[χ² / (N × min(r−1,c−1))]; aquí min(r−1,c−1)=1. [Verificación de V: SciPy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.contingency.association.html).

Comparación de magnitudes en tablas del mismo tamaño: V cobertura=0.3199 frente a V condición=0.1042. La asociación marginal de cobertura con acceso es mayor en este dataset, aunque ambas pruebas pueden arrojar p-values pequeños. Esto no compara efectos independientes ni importancia clínica.

## 6. Cobertura + condición y acceso a medicación

N efectivo: **2500**; excluidos por NA: **0**. Se describen las nueve combinaciones, sin pruebas separadas.

| Cobertura     | Condición | N   | Acceso Sí (n) | Acceso Sí (%) |
| ------------- | --------- | --: | ------------: | ------------: |
| Privada       | Saludable | 272 |           242 |        88.971 |
| Privada       | Aguda     | 269 |           240 |        89.219 |
| Privada       | Crónica   | 302 |           235 |        77.815 |
| Pública       | Saludable | 266 |           193 |        72.556 |
| Pública       | Aguda     | 280 |           208 |        74.286 |
| Pública       | Crónica   | 260 |           161 |        61.923 |
| Sin cobertura | Saludable | 290 |           154 |        53.103 |
| Sin cobertura | Aguda     | 280 |           144 |        51.429 |
| Sin cobertura | Crónica   | 281 |           118 |        41.993 |

**Visualización y justificación:** Un único heatmap 3×3 permite comparar las nueve proporciones simultáneamente; escala fija 0–100%, porcentajes y N en cada celda evitan depender solo del color.

![acceso_cobertura_condicion.png](../outputs/figuras/relaciones/acceso_cobertura_condicion.png)

Mayor acceso observado: Privada / Aguda, 240/269 (89.22%); menor: Sin cobertura / Crónica, 118/281 (41.99%). No se asignan etiquetas de vulnerabilidad ni se evalúa una interacción estadística.

## 7. Tiempo de espera y satisfacción

N efectivo: **2357**; filas excluidas por NA en cualquiera de las dos variables: **143**. Hay 74 NA en espera y 72 en satisfacción, con 3 coincidentes: 74 + 72 − 3 = 143 exclusiones. No se imputan valores.

**Spearman bilateral:** ρ=-0.7402, p < 0.001, N=2357. Dirección negativa: los rangos de espera mayores tienden a acompañar niveles de satisfacción menores. La magnitud absoluta |ρ|=0.7402 indica una relación monotónica negativa marcada, sin equivaler a porcentaje de varianza explicada. Hay evidencia estadística al nivel nominal 0.05; no implica causalidad ni ajuste por acceso o cobertura. Se usa la aproximación asintótica del p-value con N>500 y rangos medios ante empates; no se utiliza Pearson como análisis principal. [Método e interpretación: SciPy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.spearmanr.html).

| Satisfacción | N   | Media espera min | Mediana min | Q1 min  | Q3 min  |
| -----------: | --: | ---------------: | ----------: | ------: | ------: |
|            1 | 134 |          148.358 |     155.000 | 129.250 | 171.750 |
|            2 | 321 |          117.480 |     115.000 |  92.000 | 149.000 |
|            3 | 561 |           81.474 |      83.000 |  54.000 | 109.000 |
|            4 | 765 |           46.282 |      34.000 |  21.000 |  72.000 |
|            5 | 576 |           24.326 |      21.000 |  12.000 |  29.000 |

**Visualización y justificación:** Boxplots en orden lógico comparan mediana, intervalo intercuartílico, dispersión y solapamiento. Bigotes de 1.5 × IQR; puntos exteriores, si existen, se conservan y no se consideran errores automáticamente.

![espera_por_satisfaccion.png](../outputs/figuras/relaciones/espera_por_satisfaccion.png)

## 8. Acceso a medicación y satisfacción

N efectivo total: **2428**; excluidos por NA de satisfacción: **72**.

| Acceso | N disponible | NA  | Mediana | Moda | Nivel 1 % | Nivel 2 % | Nivel 3 % | Nivel 4 % | Nivel 5 % |
| ------ | -----------: | --: | ------: | ---- | --------: | --------: | --------: | --------: | --------: |
| Sí     |         1640 |  55 |   4.000 | 4    |     0.610 |     6.159 |    18.232 |    39.695 |    35.305 |
| No     |          788 |  17 |   3.000 | 3    |    16.371 |    28.807 |    35.152 |    18.147 |     1.523 |

**Visualización y justificación:** Barras agrupadas por nivel 1–5 conservan el orden ordinal y comparan porcentajes con denominadores específicos para Sí y No; no convierten satisfacción en continua.

![satisfaccion_por_acceso.png](../outputs/figuras/relaciones/satisfaccion_por_acceso.png)

Con acceso: mediana 4, moda 4, N=1640; sin acceso: mediana 3, moda 3, N=788. La comparación es descriptiva. No se agrega una prueba: la distribución por niveles, mediana y moda responden la pregunta solicitada sin aumentar la familia de contrastes.

## 9. Resumen estadístico de relaciones

| Relación                         | N efectivo | Método estadístico                           | Resultado principal                                                                                          | p-value     | Medida de efecto/asociación                              | Interpretación breve                                      |
| -------------------------------- | ---------: | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ----------- | -------------------------------------------------------- | --------------------------------------------------------- |
| Condición–frecuencia             |       2500 | Kruskal-Wallis                               | H=2042.640                                                                                                   | < 0.001     | No aplicada (estandarizada); medianas 1 / 4 / 13         | Diferencias globales de rangos; dispersión desigual.      |
| Cobertura–espera                 |       2426 | Kruskal-Wallis                               | H=1684.378                                                                                                   | < 0.001     | No aplicada (estandarizada); medianas 18 / 71 / 105 min  | Diferencias globales; no solo medias.                     |
| Cobertura–medicación             |       2500 | Chi-cuadrado                                 | χ²=255.798; gl=2                                                                                             | < 0.001     | V=0.3199                                                 | Asociación nominal; magnitud separada del p-value.        |
| Condición–medicación             |       2500 | Chi-cuadrado                                 | χ²=27.170; gl=2                                                                                              | < 0.001     | V=0.1042                                                 | Asociación nominal; magnitud separada del p-value.        |
| Cobertura + condición–medicación |       2500 | No aplicada (objetivo descriptivo)           | Mayor acceso observado: Privada / Aguda, 240/269 (89.22%); menor: Sin cobertura / Crónica, 118/281 (41.99%). | No aplicada | No aplicada (sin contraste); porcentajes por combinación | Nueve perfiles; no mide efectos ajustados ni interacción. |
| Espera–satisfacción              |       2357 | Spearman bilateral                           | ρ=-0.7402                                                                                                    | < 0.001     | ρ=-0.7402                                                | Asociación monotónica negativa marcada.                   |
| Medicación–satisfacción          |       2428 | No aplicada (descripción ordinal suficiente) | Con acceso: mediana 4, moda 4, N=1640; sin acceso: mediana 3, moda 3, N=788.                                 | No aplicada | No aplicada; porcentajes, medianas y modas               | Comparación descriptiva; no se afirma significación.      |

En Kruskal-Wallis no se añade un índice estandarizado: se informa magnitud descriptiva con medianas, IQR y distribuciones, evitando traducir H o p a porcentaje explicado. Las dos secciones descriptivas indican No aplicada porque no plantean un contraste adicional. V y ρ cuantifican magnitud en sus análisis respectivos; no son medidas intercambiables.

## 10. Hallazgos principales

### Hallazgo 1

**RESULTADO:** Medianas 1, 4 y 13 consultas para Saludable, Aguda y Crónica; H=2042.640, p < 0.001, N=2500.

**INTERPRETACIÓN:** Se observan diferencias globales de rangos y separación descriptiva de las distribuciones.

**LIMITACIÓN:** Sin post-hoc no se afirma significación de cada par; no es un efecto causal ni una prueba exclusiva de medianas.

### Hallazgo 2

**RESULTADO:** Medianas 18, 71 y 105 min; H=1684.378, p < 0.001, N=2426, 74 NA excluidos.

**INTERPRETACIÓN:** Las distribuciones de espera difieren entre coberturas en ubicación y dispersión.

**LIMITACIÓN:** El contraste global no prueba causalidad; las formas distintas impiden interpretarlo solo como prueba de medianas.

### Hallazgo 3

**RESULTADO:** Cobertura–medicación: χ²=255.798, gl=2, p < 0.001, V=0.3199, N=2500; acceso Sí entre 48.88% y 85.05%.

**INTERPRETACIÓN:** Se observa asociación; su magnitud se expresa con V y las diferencias de proporciones.

**LIMITACIÓN:** Es una asociación marginal, sin ajuste por la otra variable ni interpretación causal.

### Hallazgo 4

**RESULTADO:** Condición–medicación: χ²=27.170, gl=2, p < 0.001, V=0.1042, N=2500; acceso Sí entre 60.97% y 71.41%.

**INTERPRETACIÓN:** Se observa asociación; su magnitud se expresa con V y las diferencias de proporciones.

**LIMITACIÓN:** Es una asociación marginal, sin ajuste por la otra variable ni interpretación causal.

### Hallazgo 5

**RESULTADO:** Mayor acceso observado: Privada / Aguda, 240/269 (89.22%); menor: Sin cobertura / Crónica, 118/281 (41.99%). N total=2500.

**INTERPRETACIÓN:** Se observan combinaciones con porcentajes relativos distintos.

**LIMITACIÓN:** No se hicieron nueve pruebas; no se concluye interacción, vulnerabilidad ni efecto independiente.

### Hallazgo 6

**RESULTADO:** ρ=-0.7402, p < 0.001, N=2357, 143 exclusiones por NA.

**INTERPRETACIÓN:** Se observa una asociación monotónica negativa marcada entre espera y satisfacción ordinal.

**LIMITACIÓN:** No es causal ni mide una relación ajustada; faltantes y empates limitan la interpretación inferencial.

### Hallazgo 7

**RESULTADO:** Con acceso: mediana 4, moda 4, N=1640; sin acceso: mediana 3, moda 3, N=788. Se excluyeron 72 NA.

**INTERPRETACIÓN:** La satisfacción disponible se concentra en niveles distintos según acceso.

**LIMITACIÓN:** No se realizó contraste adicional ni ajuste por espera; no se atribuyen causas.

## 11. Limitaciones

Los datos son ficticios y las relaciones fueron incorporadas intencionalmente según el caso de uso; los resultados no validan hechos sobre la población real. La independencia se supone, no se demuestra con IDs únicos. No se documenta un diseño muestral. Los análisis son exploratorios y los cinco p-values no están ajustados por multiplicidad; no se formulan conclusiones confirmatorias conjuntas. Los p-values no son probabilidades de que la hipótesis sea verdadera ni medidas de tamaño del efecto.

El mecanismo de los NA es desconocido: cada resultado se limita a sus casos disponibles y puede tener selección no evaluada. Kruskal-Wallis detecta diferencias globales de rangos y puede responder a cambios de forma o dispersión, no exclusivamente a medianas. Spearman es monotónico, trata empates mediante rangos medios y usa un p-value asintótico. Chi-cuadrado se sustenta en los controles de frecuencias esperadas y en el supuesto de independencia. V no tiene dirección y sus umbrales de magnitud no son universales. Los análisis marginales no controlan otras variables; el heatmap no estima interacción ni efectos independientes. No se realizan afirmaciones causales ni recomendaciones finales.

## 12. Preguntas para la etapa de vulnerabilidad

- ¿Qué dimensión de vulnerabilidad acordará el equipo y con qué fundamento, dado que no existe una etiqueta directa?
- ¿Cómo distinguirá el equipo una dificultad observada de acceso o atención de una definición operacional de vulnerabilidad?
- ¿Qué papel tendrán la disponibilidad de datos y el tamaño de cada combinación en una evaluación posterior?

Estas preguntas quedan abiertas. No se define una regla, no se clasifica a pacientes ni se crean variables nuevas.

**Control final:** N efectivos y porcentajes reconciliados; frecuencias esperadas verificadas; χ², V y Spearman contrastados con fórmulas independientes; p-values de Kruskal-Wallis contrastados con la cola χ²₂. Se preservaron satisfacción ordinal, NA, datos y todos los archivos anteriores, verificando igualdad exacta del DataFrame y hashes SHA-256. Siete figuras no vacías y sin nuevas columnas en el dataset. Reproducción: notebooks/05_relaciones.ipynb.

SHA-256 del procesado intacto: 6707074a0d805b2fce33f461c10c9335adcb5ab302d960bc0e963db868b983bd.
