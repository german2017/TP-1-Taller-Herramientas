# TP1 Salud Pública — Auditoría del dataset

Etapa 2 exclusivamente. Fuente: Excel ficticio y reports/01_objetivos.md. No se aplicaron limpieza, imputación, corrección, eliminación, gráficos, modelos ni análisis de asociaciones. Los porcentajes usan todas las filas como denominador, salvo indicación expresa. Los valores nulos son los reconocidos por pandas con los parámetros predeterminados de read_excel.

Entorno: Python 3.12.3, pandas 3.0.5, NumPy 2.5.3, openpyxl 3.1.5. Las versiones pueden afectar los tipos inferidos y el consumo de memoria.

## 1. Carga y estructura

Hoja: Salud Publica. Dimensiones reales: **2500 filas × 10 columnas**. Coincide con los 2500 registros declarados: **sí**.

| Columna             | Tipo pandas | Memoria bytes |
| ------------------- | ----------- | ------------: |
| ID_Paciente         | int64       |         20000 |
| Region              | str         |        137613 |
| Edad                | int64       |         20000 |
| Genero              | str         |        127481 |
| Condicion_Salud     | str         |        139998 |
| Cobertura_Salud     | str         |        145106 |
| Frecuencia_Atencion | int64       |         20000 |
| Tiempo_Espera_min   | float64     |         20000 |
| Acceso_Medicacion   | str         |        154620 |
| Satisfaccion        | float64     |         20000 |

Memoria profunda total, incluido índice: **804950 bytes (786.08 KiB)**. Índice: 132 bytes. Es memoria del DataFrame, no tamaño del archivo.

Primeras cinco filas, únicamente como control de carga:

| ID_Paciente | Region       | Edad | Genero | Condicion_Salud | Cobertura_Salud | Frecuencia_Atencion | Tiempo_Espera_min | Acceso_Medicacion | Satisfaccion |
| ----------: | ------------ | ---: | ------ | --------------- | --------------- | ------------------: | ----------------: | ----------------- | -----------: |
|           1 | CABA         |   23 | Otro   | Aguda           | Sin cobertura   |                   3 |          158.0000 | Sí                |       2.0000 |
|           2 | Sur          |   58 | M      | Cronica         | Privada         |                  12 |           20.0000 | Sí                |       4.0000 |
|           3 | Sur          |   49 | F      | Aguda           | Privada         |                   3 |           11.0000 | Sí                |       4.0000 |
|           4 | Buenos Aires |   83 | Otro   | Cronica         | Sin cobertura   |                  16 |          140.0000 | Sí                |       3.0000 |
|           5 | Norte        |   18 | F      | Saludable       | Sin cobertura   |                   0 |          175.0000 | No                |       1.0000 |

## 2. Identificadores

| Control                        | Cantidad |
| ------------------------------ | -------: |
| Valores presentes              |     2500 |
| Valores únicos no nulos        |     2500 |
| Repeticiones adicionales de ID |        0 |
| Filas en grupos de ID repetido |        0 |
| Valores nulos                  |        0 |

Repeticiones adicionales excluye la primera aparición; filas involucradas incluye todas las apariciones. Los nulos se cuentan por separado. El ID se trata como identificador nominal.

## 3. Valores faltantes

| Columna             | Nulos | Porcentaje |
| ------------------- | ----: | ---------: |
| ID_Paciente         |     0 |     0.0000 |
| Region              |     0 |     0.0000 |
| Edad                |     0 |     0.0000 |
| Genero              |     0 |     0.0000 |
| Condicion_Salud     |     0 |     0.0000 |
| Cobertura_Salud     |     0 |     0.0000 |
| Frecuencia_Atencion |     0 |     0.0000 |
| Tiempo_Espera_min   |    74 |     2.9600 |
| Acceso_Medicacion   |     0 |     0.0000 |
| Satisfaccion        |    72 |     2.8800 |

Columnas con faltantes: Tiempo_Espera_min, Satisfaccion.

Filas con al menos un faltante: **143 (5.72%)**. Con más de uno: **3 (0.12%)**.

Patrones exactos de coincidencia (incluye filas completas):

| Columnas faltantes en la misma fila | Filas | Porcentaje |
| ----------------------------------- | ----: | ---------: |
| Sin faltantes                       |  2357 |    94.2800 |
| Tiempo_Espera_min                   |    71 |     2.8400 |
| Satisfaccion                        |    69 |     2.7600 |
| Tiempo_Espera_min, Satisfaccion     |     3 |     0.1200 |

Coincidencias por par de columnas:

| Columna A         | Columna B    | Filas con ambos nulos |
| ----------------- | ------------ | --------------------: |
| Tiempo_Espera_min | Satisfaccion |                     3 |

Estos conteos describen coincidencias; no identifican el mecanismo ni la causa de ausencia.

## 4. Duplicados

| Control                                     | Cantidad |
| ------------------------------------------- | -------: |
| Filas completamente duplicadas, adicionales |        0 |
| Filas involucradas en duplicación completa  |        0 |
| IDs repetidos, apariciones adicionales      |        0 |
| Filas involucradas en IDs repetidos         |        0 |

La duplicación completa compara las diez columnas, incluido ID_Paciente. No se eliminaron registros.

## 5. Variables categóricas y escala ordinal

Las tablas enumeran todos los valores únicos, incluyendo NA si existe; porcentajes sobre todas las filas. repr conserva visibles los espacios en los textos. Satisfaccion es conceptualmente ordinal 1–5, aunque pandas infiera un tipo numérico. Genero no tiene catálogo documentado: sus categorías observadas no pueden declararse fuera de dominio sin una definición adicional. Los dominios de las demás columnas se toman de la Etapa 1.

### Region

| Valor literal  | Frecuencia | Porcentaje |
| -------------- | ---------: | ---------: |
| 'CABA'         |        498 |    19.9200 |
| 'Sur'          |        505 |    20.2000 |
| 'Buenos Aires' |        518 |    20.7200 |
| 'Norte'        |        484 |    19.3600 |
| 'Centro'       |        495 |    19.8000 |

### Genero

| Valor literal | Frecuencia | Porcentaje |
| ------------- | ---------: | ---------: |
| 'Otro'        |        827 |    33.0800 |
| 'M'           |        833 |    33.3200 |
| 'F'           |        840 |    33.6000 |

### Condicion_Salud

| Valor literal | Frecuencia | Porcentaje |
| ------------- | ---------: | ---------: |
| 'Aguda'       |        829 |    33.1600 |
| 'Cronica'     |        843 |    33.7200 |
| 'Saludable'   |        828 |    33.1200 |

### Cobertura_Salud

| Valor literal   | Frecuencia | Porcentaje |
| --------------- | ---------: | ---------: |
| 'Sin cobertura' |        851 |    34.0400 |
| 'Privada'       |        843 |    33.7200 |
| 'Publica'       |        806 |    32.2400 |

### Acceso_Medicacion

| Valor literal | Frecuencia | Porcentaje |
| ------------- | ---------: | ---------: |
| 'Sí'          |       1695 |    67.8000 |
| 'No'          |        805 |    32.2000 |

### Satisfaccion

| Valor literal | Frecuencia | Porcentaje |
| ------------: | ---------: | ---------: |
|           2.0 |        328 |    13.1200 |
|           4.0 |        794 |    31.7600 |
|           3.0 |        576 |    23.0400 |
|           1.0 |        139 |     5.5600 |
|           5.0 |        591 |    23.6400 |
|            NA |         72 |     2.8800 |

### Escritura y dominios

| Columna           | Filas con espacios anómalos | Variantes por espacios/caja/tildes |
| ----------------- | --------------------------: | ---------------------------------- |
| Region            |                           0 | []                                 |
| Genero            |                           0 | []                                 |
| Condicion_Salud   |                           0 | []                                 |
| Cobertura_Salud   |                           0 | []                                 |
| Acceso_Medicacion |                           0 | []                                 |
| Satisfaccion      |                           0 | []                                 |

Comparar claves sin espacios exteriores, mayúsculas ni tildes se usa solo para diagnóstico; no se asigna al dataset. La comparación exacta con el dominio también detecta variantes únicas de escritura.

| Columna           | Fuera del dominio literal | Porcentaje | Valores     |
| ----------------- | ------------------------: | ---------: | ----------- |
| Region            |                         0 |     0.0000 | []          |
| Condicion_Salud   |                       843 |    33.7200 | ['Cronica'] |
| Cobertura_Salud   |                       806 |    32.2400 | ['Publica'] |
| Acceso_Medicacion |                         0 |     0.0000 | []          |
| Satisfaccion      |                         0 |     0.0000 | []          |

## 6. Variables numéricas

Estadísticas calculadas sobre valores presentes, sin imputar. Desviación estándar muestral (ddof=1); cuartiles con interpolación lineal predeterminada de pandas. El porcentaje de alertas usa las 2500 filas.

| Variable            | count | Media   | Mediana | Desv. estándar | Mínimo | Q1      | Q3      | Máximo   | IQR     |
| ------------------- | ----: | ------: | ------: | -------------: | -----: | ------: | ------: | -------: | ------: |
| Edad                |  2500 | 45.3996 | 45.0000 |        26.4906 | 0.0000 | 22.0000 | 69.0000 |  90.0000 | 47.0000 |
| Frecuencia_Atencion |  2500 |  6.1884 |  4.0000 |         5.5810 | 0.0000 |  2.0000 | 10.0000 |  20.0000 |  8.0000 |
| Tiempo_Espera_min   |  2426 | 64.5808 | 54.0000 |        47.7098 | 5.0000 | 23.0000 | 99.0000 | 180.0000 | 76.0000 |

Regla diagnóstica: valores estrictamente menores que Q1 − 1.5 × IQR o mayores que Q3 + 1.5 × IQR. Los límites son estadísticos, no límites de validez del dominio.

| Variable            | Límite inferior | Límite superior | Alertas IQR | Porcentaje |
| ------------------- | --------------: | --------------: | ----------: | ---------: |
| Edad                |        -48.5000 |        139.5000 |           0 |     0.0000 |
| Frecuencia_Atencion |        -10.0000 |         22.0000 |           0 |     0.0000 |
| Tiempo_Espera_min   |        -91.0000 |        213.0000 |           0 |     0.0000 |

### Interpretación de las alertas numéricas

- **Imposible:** edad o duración negativas, consultas negativas o fraccionarias y valores no finitos contradicen sus conceptos. No se encontraron.
- **Sospechoso:** un valor requiere verificación contextual o documental; la regla IQR no basta para llamarlo error. No aparecieron alertas IQR ni otras infracciones numéricas objetivas en estos controles.
- **Extremo pero plausible:** los máximos observados de 90 en Edad, 20 consultas anuales y 180 minutos de espera no contradicen un límite documentado y no activan IQR. Se consideran extremos del archivo potencialmente plausibles, no errores; no se certifica su exactitud.

El caso no fija un máximo válido de edad ni de espera. No se inventa un umbral superior; Edad=0 no es automáticamente imposible. La interpretación de edad en años no está confirmada por el documento.

## 7. Consistencia lógica

| Control                              | Filas afectadas | Porcentaje |
| ------------------------------------ | --------------: | ---------: |
| Edad: negativos                      |               0 |     0.0000 |
| Edad: no finitos                     |               0 |     0.0000 |
| Frecuencia_Atencion: negativos       |               0 |     0.0000 |
| Frecuencia_Atencion: no finitos      |               0 |     0.0000 |
| Tiempo_Espera_min: negativos         |               0 |     0.0000 |
| Tiempo_Espera_min: no finitos        |               0 |     0.0000 |
| Frecuencia_Atencion: no entera       |               0 |     0.0000 |
| Satisfaccion: fuera de 1–5 entero    |               0 |     0.0000 |
| Acceso_Medicacion: distinto de Sí/No |               0 |     0.0000 |

No se detectaron infracciones en estos controles. Los faltantes se informan por separado y no se consideran valores fuera de dominio. No hay una restricción determinista documentada que obligue a una combinación específica entre condición, consultas, cobertura, acceso, espera y satisfacción. Por ello no se interpreta una combinación inusual como inconsistencia. En particular, cero consultas anuales junto con espera o satisfacción no prueba un error sin conocer los períodos de referencia. No se contrastaron las asociaciones incorporadas al dataset.

## 8. Reporte de calidad

Criterios: CRÍTICO impediría o invalidaría análisis posteriores; IMPORTANTE requiere una decisión previa; MENOR conviene documentarlo pero probablemente no altera el análisis; SIN PROBLEMAS DETECTADOS se limita a los controles realizados.

| Severidad  | Variable          | Problema                                               | Registros | Porcentaje | Posible impacto                                                                    | Alternativas, no aplicadas                                                                                                                  |
| ---------- | ----------------- | ------------------------------------------------------ | --------: | ---------: | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| IMPORTANTE | Tiempo_Espera_min | Valores faltantes                                      |        74 |     2.9600 | Reduce casos disponibles; el tratamiento puede cambiar denominadores y resultados. | Investigar origen; conservar NA y usar casos disponibles por análisis; evaluar exclusión específica o imputación justificada en otra etapa. |
| IMPORTANTE | Satisfaccion      | Valores faltantes                                      |        72 |     2.8800 | Reduce casos disponibles; el tratamiento puede cambiar denominadores y resultados. | Investigar origen; conservar NA y usar casos disponibles por análisis; evaluar exclusión específica o imputación justificada en otra etapa. |
| MENOR      | Condicion_Salud   | Diferencia literal respecto del documento: ['Cronica'] |       843 |    33.7200 | Filtros o cruces con el catálogo acentuado pueden omitir estos registros.          | Documentar correspondencia y conservar etiquetas; o acordar normalización posterior.                                                        |
| MENOR      | Cobertura_Salud   | Diferencia literal respecto del documento: ['Publica'] |       806 |    32.2400 | Filtros o cruces con el catálogo acentuado pueden omitir estos registros.          | Documentar correspondencia y conservar etiquetas; o acordar normalización posterior.                                                        |

**Problemas críticos detectados: 0.** Se registran dos incidencias IMPORTANTES por faltantes y dos MENORES de escritura. Las incidencias pueden afectar las mismas filas: no deben sumarse como pacientes distintos.

La discrepancia Cronica/Crónica afecta 843 filas (33.72%); Publica/Pública afecta 806 (32.24%). Son diferencias ortográficas frente al catálogo documental, no categorías semánticamente nuevas ni mezclas de etiquetas dentro de la columna. No hay valores distintos de Sí/No en acceso ni valores presentes fuera de 1–5 en satisfacción.

**SIN PROBLEMAS DETECTADOS:** dimensiones y encabezados esperados; integridad y unicidad del ID; duplicación completa; dominio de Region, Acceso_Medicacion y Satisfaccion; espacios anómalos y variantes internas de escritura en las categorías inspeccionadas; negativos, no finitos, consultas fraccionarias y alertas IQR. Cada uno afecta 0 registros (0%). Genero tiene F, M y Otro; al no existir catálogo documental, su validez externa no está verificada. No se propone recodificación por ese solo motivo.

## 9. Decisiones que debe tomar el equipo antes de limpiar

1. **Faltantes en Tiempo_Espera_min (74; 2.96%) y Satisfaccion (72; 2.88%):** decidir si se puede aclarar su origen y cómo se manejarán en cada análisis. Hay 143 filas con al menos uno (5.72%) y 3 con ambos (0.12%); eliminar toda fila incompleta excluiría 143, aunque 71 carecen solo de espera y 69 solo de satisfacción. Considerar mantener NA con denominadores explícitos, exclusión limitada a variables necesarias o una imputación fundamentada posteriormente. No hay evidencia aquí para elegir un mecanismo de ausencia o un método de imputación.
2. **Diferencias de tildes frente al documento:** acordar documentar Cronica ↔ Crónica y Publica ↔ Pública manteniendo las etiquetas originales, o normalizarlas en una futura copia de trabajo si se necesita compatibilidad con un catálogo. La normalización no es necesaria por sí sola para calcular resultados.

No se justifican eliminación de duplicados, recorte de extremos ni otras correcciones con los resultados de esta auditoría. No se creó una variable de vulnerabilidad ni un dataset procesado. La auditoría finaliza aquí.

## 10. Reproducibilidad e integridad

Todos los cálculos y tablas se reproducen ejecutando notebooks/02_auditoria.ipynb en orden. El notebook reúne este reporte en la variable informe sin escribir sobre las fuentes. Se verificó igualdad exacta del DataFrame con la copia de carga y SHA-256 de los dos archivos protegidos antes/después.

| Fuente protegida                | SHA-256                                                          |
| ------------------------------- | ---------------------------------------------------------------- |
| dataset_salud_publica_2500.xlsx | 06449a4ada23692fe43b173198d4d46e05c28a29b5fe796e72eb6926bd1f5100 |
| 01_objetivos.md                 | 845f2358abe8bfd478dd8ccdf7ead2a45df38c46fb8332bc664ed0b2853663d5 |
