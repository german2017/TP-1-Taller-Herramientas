# Etapa 6 - Índice operacional de vulnerabilidad

## 1. Objetivo

Construir y describir el **Índice operacional de vulnerabilidad en el acceso y la atención**, definido por el equipo para estudiar la acumulación de dimensiones observables en el dataset ficticio. El dataset no contiene una variable original de vulnerabilidad. Este índice no es una verdad clínica, diagnóstico ni definición oficial, y no debe generalizarse a población real. Un registro con score X presenta X dimensiones según esta definición operacional; no se etiqueta al paciente como vulnerable.

Se leyeron los cinco informes anteriores. Esta etapa es descriptiva: no se agregan pruebas estadísticas, modelos, dashboard ni recomendaciones. Los porcentajes se calculan con casos evaluables en las variables requeridas; pueden sumar 99.99% o 100.01% por redondeo.

## 2. Definición operacional

| Dimensión      | 1 punto                   | 0 puntos               | Si falta información |
| -------------- | ------------------------- | ---------------------- | -------------------- |
| Dim_Necesidad  | Condicion_Salud = Crónica | Otra condición         | NA                   |
| Dim_Medicacion | Acceso_Medicacion = No    | Acceso_Medicacion = Sí | NA                   |
| Dim_Espera     | Tiempo_Espera_min ≥ 99    | Tiempo_Espera_min < 99 | NA                   |

Score_Vulnerabilidad es la suma de las tres dimensiones **solo cuando todas son observables**, con valores 0, 1, 2, 3 o NA. Cada dimensión pesa un punto. El umbral se fija en 99 minutos por decisión del equipo, correspondiente al Q3 del EDA; no se recalcula por región o cobertura. Se incluye el valor exacto 99. Cobertura, región y satisfacción no participan en la fórmula. No se crean categorías bajo/medio/alto ni una clasificación binaria.

## 3. Manejo de datos faltantes

| Estado              | N    | Porcentaje sobre 2500 |
| ------------------- | ---: | --------------------: |
| Score calculable    | 2426 |                 97.04 |
| Score no calculable |   74 |                  2.96 |

Los 74 NA de espera se conservan como NA en Dim_Espera y Score_Vulnerabilidad. Dim_Necesidad y Dim_Medicacion tienen 2500 valores observables, y Dim_Espera tiene 2426. Un score NA no equivale a cero dimensiones. La suma exige tres componentes presentes (min_count=3); no se imputa. Los 72 NA de satisfacción no impiden calcular el score si las tres dimensiones están presentes; sí se excluyen al describir satisfacción. No se eliminan filas de la copia analítica.

## 4. Distribución del score

Pregunta: ¿cuántas dimensiones operacionales se acumulan en los registros evaluables? N efectivo=2426; NA del score=74.

| Score | Frecuencia | Porcentaje evaluable |
| ----: | ---------: | -------------------: |
|     0 |        904 |                37.26 |
|     1 |        937 |                38.62 |
|     2 |        471 |                19.41 |
|     3 |        114 |                 4.70 |

**Visualización:** Barras ordenadas 0–3 comparan la frecuencia de cada cantidad de dimensiones; los NA quedan fuera del denominador y se informan aparte.

![score_vulnerabilidad_distribucion.png](../outputs/figuras/vulnerabilidad/score_vulnerabilidad_distribucion.png)

## 5. Composición del score

| Dim_Necesidad | Dim_Medicacion | Dim_Espera | Score | N   | Porcentaje de evaluables |
| ------------: | -------------: | ---------: | ----: | --: | -----------------------: |
|             0 |              0 |          0 |     0 | 904 |                    37.26 |
|             0 |              0 |          1 |     1 | 237 |                     9.77 |
|             0 |              1 |          0 |     1 | 285 |                    11.75 |
|             1 |              0 |          0 |     1 | 415 |                    17.11 |
|             0 |              1 |          1 |     2 | 176 |                     7.25 |
|             1 |              0 |          1 |     2 |  87 |                     3.59 |
|             1 |              1 |          0 |     2 | 208 |                     8.57 |
|             1 |              1 |          1 |     3 | 114 |                     4.70 |

Orden de componentes: necesidad, medicación, espera. Combinaciones más frecuentes: (0,0,0): 904 (37.26%); (1,0,0): 415 (17.11%); (0,1,0): 285 (11.75%). La combinación (0,0,0) no activa ninguna de las tres dimensiones. Los scores 1 y 2 reúnen tres perfiles diferentes cada uno; no describen un mismo problema ni una gravedad clínica homogénea.

## 6. Score según cobertura

Cobertura se utiliza únicamente para segmentar. Los porcentajes se calculan dentro de cada cobertura con score observable.

| Cobertura_Salud | N evaluable | Sin score | Score 0 % | Score 1 % | Score 2 % | Score 3 % |
| --------------- | ----------: | --------: | --------: | --------: | --------: | --------: |
| Privada         |         823 |        20 |     56.99 |     35.12 |      7.90 |      0.00 |
| Pública         |         777 |        29 |     39.12 |     39.51 |     18.28 |      3.09 |
| Sin cobertura   |         826 |        25 |     15.86 |     41.28 |     31.96 |     10.90 |

**Visualización:** Barras apiladas al 100% comparan el reparto de scores 0–3 dentro de cada cobertura, conservando orden, colores y denominadores.

![score_por_cobertura.png](../outputs/figuras/vulnerabilidad/score_por_cobertura.png)

Privada: score 0=56.99%, score 3=0.00% (N=823); Pública: score 0=39.12%, score 3=3.09% (N=777); Sin cobertura: score 0=15.86%, score 3=10.90% (N=826). Son diferencias descriptivas. La ausencia de score 3 en Privada es coherente con que sus esperas observadas no alcanzan 99 minutos; no implica ausencia de toda dificultad.

## 7. Score según región

Porcentajes dentro de cada región evaluable; región no forma parte de la definición.

| Region       | N evaluable | Sin score | Score 0 % | Score 1 % | Score 2 % | Score 3 % |
| ------------ | ----------: | --------: | --------: | --------: | --------: | --------: |
| Norte        |         466 |        18 |     34.33 |     39.48 |     22.32 |      3.86 |
| Centro       |         484 |        11 |     38.64 |     34.50 |     21.69 |      5.17 |
| Sur          |         492 |        13 |     37.20 |     40.24 |     18.50 |      4.07 |
| CABA         |         479 |        19 |     38.00 |     42.80 |     13.78 |      5.43 |
| Buenos Aires |         505 |        13 |     38.02 |     36.24 |     20.79 |      4.95 |

| Score | Mínimo regional % | Máximo regional % | Amplitud (puntos porcentuales) |
| ----: | ----------------: | ----------------: | -----------------------------: |
|     0 |             34.33 |             38.64 |                           4.30 |
|     1 |             34.50 |             42.80 |                           8.29 |
|     2 |             13.78 |             22.32 |                           8.54 |
|     3 |              3.86 |              5.43 |                           1.57 |

Score 2: CABA=13.78% frente a Norte=22.32% (amplitud 8.54 puntos porcentuales). Se incluye una figura porque esta diferencia y la variación del score 1 aportan contraste descriptivo; la decisión es editorial, no un umbral de significación o relevancia clínica. No se afirma una desigualdad territorial demostrada.

**Visualización:** Barras apiladas al 100% permiten comparar las cuatro proporciones regionales con la misma escala; las diferencias se cuantifican en la tabla.

![score_por_region.png](../outputs/figuras/vulnerabilidad/score_por_region.png)

## 8. Score y satisfacción

Pregunta: ¿cómo cambia la distribución de satisfacción al acumular dimensiones? **N efectivo=2357**; excluidos por ausencia de score o satisfacción=143. Entre los 2426 registros evaluables del índice, 69 carecen de satisfacción. Son 74 sin score más 72 sin satisfacción, con 3 coincidentes: 143 exclusiones únicas.

| Score | N con satisfacción | NA satisfacción entre evaluables | Mediana | Moda | Nivel 1 % | Nivel 2 % | Nivel 3 % | Nivel 4 % | Nivel 5 % |
| ----: | -----------------: | -------------------------------: | ------: | ---- | --------: | --------: | --------: | --------: | --------: |
|     0 |                874 |                               30 |    4.00 | 5    |      0.00 |      0.00 |     12.24 |     43.48 |     44.28 |
|     1 |                912 |                               25 |    4.00 | 4    |      1.43 |     14.36 |     30.48 |     33.88 |     19.85 |
|     2 |                457 |                               14 |    3.00 | 3    |     15.97 |     31.95 |     33.70 |     16.63 |      1.75 |
|     3 |                114 |                                0 |    2.00 | 1    |     42.11 |     38.60 |     19.30 |      0.00 |      0.00 |

**Visualización:** Barras apiladas al 100% por score conservan el orden de satisfacción 1–5. Cada barra usa su N con ambas variables disponibles; no se calcula media de satisfacción.

![satisfaccion_por_score.png](../outputs/figuras/vulnerabilidad/satisfaccion_por_score.png)

score 0: mediana 4, moda 5 (N=874); score 1: mediana 4, moda 4 (N=912); score 2: mediana 3, moda 3 (N=457); score 3: mediana 2, moda 1 (N=114). Se observa desplazamiento descriptivo hacia niveles inferiores, aunque la mediana es igual para scores 0 y 1. Satisfacción no interviene en la fórmula: es un resultado externo al cálculo, pero no es evidencia externa independiente, pues procede del mismo dataset sintético y ya se relacionaba con espera y acceso en el caso. No constituye validación clínica ni causal.

## 9. Evaluación crítica del índice

| Aspecto             | Evaluación                                                                                                                                                                               |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Distribución        | Score 0: 904; 1: 937; 2: 471; 3: 114 (N=2426).                                                                                                                                           |
| Categorías pequeñas | Score 3 es el menor: 114 (4.70%). Permite descripción agregada, no garantiza precisión ni representatividad.                                                                             |
| N del score 3       | N=114, también 114 con satisfacción. Una observación equivale a 0.88 puntos porcentuales; subdividirlo reduce estabilidad.                                                               |
| Perfiles            | Distingue cantidad de dimensiones, pero combina perfiles diferentes dentro de scores 1 y 2. No está validado como escala de gravedad.                                                    |
| Cobertura           | Privada: score 0=56.99%, score 3=0.00% (N=823); Pública: score 0=39.12%, score 3=3.09% (N=777); Sin cobertura: score 0=15.86%, score 3=10.90% (N=826); no implica causalidad.            |
| Satisfacción        | score 0: mediana 4, moda 5 (N=874); score 1: mediana 4, moda 4 (N=912); score 2: mediana 3, moda 3 (N=457); score 3: mediana 2, moda 1 (N=114); patrón descriptivo, sin prueba ni media. |
| Umbral 99           | Q3 es relativo a esta muestra, no un estándar de oportunidad. La dicotomía separa valores cercanos como 98 y 99 y equipara todas las esperas ≥99.                                        |
| Pesos iguales       | Supone intercambiabilidad de las dimensiones y pierde identidad, intensidad y secuencia; un punto no tiene significado clínico calibrado.                                                |

Los subgrupos score 3 por cobertura tienen N=0 en Privada, N=24 en Pública y N=90 en Sin cobertura; no se debe trasladar automáticamente la estabilidad del total a cada segmento. Score 0 significa ausencia de estas tres condiciones operacionales, no ausencia de dificultades en general. La condición crónica representa aquí necesidad por decisión del equipo, no una barrera por sí misma; las condiciones agudas también pueden requerir atención, aspecto no recogido por ese componente. La definición no se modifica.

El umbral incluye 614 de 2426 esperas disponibles (25.31%). Hay 13 valores exactamente iguales a 99; el uso de ≥ y los empates implican que no tiene por qué activarse exactamente en el 25% de los casos.

## 10. Hallazgos

### Hallazgo 1

**RESULTADO:** Score calculable en 2426/2500 (97.04%); 74 sin score.

**INTERPRETACIÓN:** Se puede describir la acumulación en los casos con las tres dimensiones observables.

**LIMITACIÓN:** No se considera score 0 a los registros sin información ni se caracteriza su acumulación completa.

### Hallazgo 2

**RESULTADO:** Scores 0/1/2/3: 904/937/471/114 (N=2426); score 3=4.70%.

**INTERPRETACIÓN:** Los cuatro valores tienen representación; predomina score 1.

**LIMITACIÓN:** Frecuencia no equivale a gravedad clínica y el grupo 3 pierde precisión al subdividirse.

### Hallazgo 3

**RESULTADO:** (0,0,0): 904 (37.26%); (1,0,0): 415 (17.11%); (0,1,0): 285 (11.75%); N=2426.

**INTERPRETACIÓN:** La suma reúne perfiles distintos; interpretar sus componentes evita tratarlos como problemas idénticos.

**LIMITACIÓN:** Los pesos iguales no cuantifican severidad ni establecen equivalencia clínica.

### Hallazgo 4

**RESULTADO:** Privada: score 0=56.99%, score 3=0.00% (N=823); Pública: score 0=39.12%, score 3=3.09% (N=777); Sin cobertura: score 0=15.86%, score 3=10.90% (N=826).

**INTERPRETACIÓN:** La composición del índice cambia descriptivamente entre coberturas.

**LIMITACIÓN:** La cobertura no participa en la fórmula y estas diferencias no prueban causalidad ni efectos independientes.

### Hallazgo 5

**RESULTADO:** Score 2: CABA=13.78% frente a Norte=22.32% (amplitud 8.54 puntos porcentuales).; N regional: Norte=466, Centro=484, Sur=492, CABA=479, Buenos Aires=505.

**INTERPRETACIÓN:** La figura regional aporta una comparación descriptiva adicional.

**LIMITACIÓN:** No se evaluó significación, incertidumbre ni relevancia territorial externa.

### Hallazgo 6

**RESULTADO:** score 0: mediana 4, moda 5 (N=874); score 1: mediana 4, moda 4 (N=912); score 2: mediana 3, moda 3 (N=457); score 3: mediana 2, moda 1 (N=114).

**INTERPRETACIÓN:** Hay un patrón descriptivo de satisfacción distinto a medida que se acumulan dimensiones.

**LIMITACIÓN:** No prueba que el índice cause satisfacción ni lo valida como instrumento; las relaciones sintéticas previas contribuyen al patrón.

## 11. Limitaciones

Definición operacional creada para el ejercicio: no es oficial, diagnóstica ni generalizable a población real. El índice incluye solo tres dimensiones disponibles y omite otras necesidades y barreras. Q3=99 depende del dataset; no es un límite validado y su uso en otras muestras no conservaría necesariamente el mismo significado. La dicotomización y la suma con pesos iguales pierden magnitudes y composición; no justifican categorías de gravedad.

Los 74 registros sin score quedan fuera de los porcentajes del índice; el mecanismo de ausencia es desconocido y puede afectar comparabilidad. Satisfacción se describe en N=2357 con ambas variables disponibles. Las proporciones regionales o de cobertura no establecen diferencias significativas. Los subgrupos pequeños o vacíos requieren cautela descriptiva. Las relaciones incorporadas al dataset limitan cualquier interpretación como validación independiente.

## 12. Decisiones pendientes

El equipo deberá revisar si la utilidad descriptiva, la heterogeneidad de los componentes y el N de los subgrupos justifican una eventual clasificación posterior. No se eligen cortes ni etiquetas en esta etapa. Si se planteara revisar pesos o umbral, debería justificarse y documentarse en otra etapa; aquí se conserva íntegramente la definición autorizada.

Entregables: notebooks/06_vulnerabilidad.ipynb, reports/06_vulnerabilidad.md, cuatro figuras en outputs/figuras/vulnerabilidad/ y data/analysis/dataset_salud_vulnerabilidad.xlsx. La copia analítica conserva 2500 filas y agrega únicamente Dim_Necesidad, Dim_Medicacion, Dim_Espera y Score_Vulnerabilidad.

**Control final aprobado:** copia analítica de 2500 × 14, con solo cuatro columnas añadidas; valores y NA verificados celda a celda, incluido el límite ≥99. Score completo igual a la suma exacta; NA si falta alguna dimensión. Se comprobó que cambios en copias de cobertura, región y satisfacción no alteran la fórmula. La lectura del Excel exportado reproduce los valores y NA, y las diez columnas originales permanecen exactamente iguales. Todos los archivos de etapas anteriores conservaron su SHA-256; cuatro figuras verificadas. No se crearon etiquetas, clasificación binaria, modelos ni afirmaciones causales.

SHA-256 del procesado intacto: 6707074a0d805b2fce33f461c10c9335adcb5ab302d960bc0e963db868b983bd. Entorno: Python 3.12.3, pandas 3.0.5, matplotlib 3.11.2.
