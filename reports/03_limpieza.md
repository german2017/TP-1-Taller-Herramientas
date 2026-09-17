# Etapa 3 - Preparación y limpieza

## 1. Decisiones adoptadas

Se aplicaron las decisiones del equipo sobre la base de reports/01_objetivos.md y reports/02_auditoria_dataset.md: conservar los 2500 registros, sin eliminar filas ni imputar faltantes, y normalizar exclusivamente las dos categorías indicadas. Se preservaron el orden de las filas, las diez columnas, los identificadores y los valores extremos.

No se crearon grupos etarios, variables derivadas, indicadores, variables de vulnerabilidad o mala atención ni targets. Esta etapa no incluye EDA, gráficos, análisis de relaciones ni modelos.

## 2. Transformaciones realizadas

Las sustituciones se aplicaron por coincidencia exacta sobre una copia en memoria del original.

| Variable        | Antes   | Después | Motivo                                                   |
| --------------- | ------- | ------- | -------------------------------------------------------- |
| Condicion_Salud | Cronica | Crónica | Consistencia con documentación, gráficos y presentación. |
| Cobertura_Salud | Publica | Pública | Consistencia con documentación, gráficos y presentación. |

| Variable        | Celdas modificadas |
| --------------- | -----------------: |
| Condicion_Salud |                843 |
| Cobertura_Salud |                806 |

Se modificaron **1649 celdas** en total. Este conteo corresponde a celdas, no necesariamente a pacientes distintos. El resto de las categorías permaneció intacto.

## 3. Tratamiento de valores faltantes

**Los valores faltantes se conservaron como NA, sin imputación ni eliminación de filas.** En el Excel se almacenan como celdas vacías y se recuperan como NA mediante pandas.

| Variable          | NA originales | NA conservados |
| ----------------- | ------------: | -------------: |
| Tiempo_Espera_min |            74 |             74 |
| Satisfaccion      |            72 |             72 |

Se preservaron las 146 celdas faltantes en sus posiciones originales: 143 filas tienen al menos un NA y 3 tienen ambos. No se introdujeron faltantes nuevos.

**En los análisis posteriores se utilizarán casos disponibles según las variables involucradas y se informará el N efectivo utilizado en cada análisis.** Esta decisión no implica eliminar registros del dataset procesado.

## 4. Validaciones

Los controles se ejecutaron sobre el archivo procesado después de guardarlo y volverlo a cargar. Todas las comprobaciones se implementaron con aserciones.

| Validación                        | Esperado | Obtenido | Resultado |
| --------------------------------- | -------- | -------- | --------- |
| Filas                             | 2500     | 2500     | OK        |
| Columnas                          | 10       | 10       | OK        |
| ID_Paciente únicos                | 2500     | 2500     | OK        |
| IDs nulos                         | 0        | 0        | OK        |
| Filas completamente duplicadas    | 0        | 0        | OK        |
| NA en Tiempo_Espera_min           | 74       | 74       | OK        |
| NA en Satisfaccion                | 72       | 72       | OK        |
| Apariciones de Cronica            | 0        | 0        | OK        |
| Presencia de Crónica              | True     | True     | OK        |
| Apariciones de Crónica            | 843      | 843      | OK        |
| Apariciones de Publica            | 0        | 0        | OK        |
| Presencia de Pública              | True     | True     | OK        |
| Apariciones de Pública            | 806      | 806      | OK        |
| Celdas modificadas autorizadas    | 1649     | 1649     | OK        |
| Celdas modificadas no autorizadas | 0        | 0        | OK        |
| Cambios en ubicación de NA        | 0        | 0        | OK        |

También se verificó igualdad exacta de valores y tipos detectados por pandas entre la copia preparada en memoria y el archivo vuelto a cargar.

## 5. Integridad respecto del dataset original

Se compararon programáticamente las 25000 celdas del original y del procesado, en el mismo orden, considerando iguales los NA coincidentes. La máscara de diferencias coincidió exactamente con las posiciones originales de Cronica en Condicion_Salud y Publica en Cobertura_Salud; se comprobaron además sus destinos Crónica y Pública.

Se verificó igualdad exacta de las otras ocho columnas: ID_Paciente, Region, Edad, Genero, Frecuencia_Atencion, Tiempo_Espera_min, Acceso_Medicacion y Satisfaccion. No cambió ningún otro valor, la ubicación de los NA, el orden de los registros ni los encabezados. Los valores extremos quedaron intactos.

Los cuatro archivos protegidos mantuvieron sus hashes SHA-256 antes y después de la ejecución:

| Archivo protegido               | SHA-256 antes y después                                          |
| ------------------------------- | ---------------------------------------------------------------- |
| dataset_salud_publica_2500.xlsx | 06449a4ada23692fe43b173198d4d46e05c28a29b5fe796e72eb6926bd1f5100 |
| reports/01_objetivos.md         | 845f2358abe8bfd478dd8ccdf7ead2a45df38c46fb8332bc664ed0b2853663d5 |
| reports/02_auditoria_dataset.md | e6005884fc9cc6f4059dd7fe20a5ae35aca533f5965e9a76a96b2a91c56ee72e |
| notebooks/02_auditoria.ipynb    | a3c654515d3e3d498d1a5fa8a724a1e630b10776d9b01efcdf9e060cf9b68319 |

## 6. Dataset resultante

- **Archivo:** data/processed/dataset_salud_publica_limpio.xlsx.
- **Hoja:** Salud Publica.
- **Dimensiones:** 2500 filas y 10 columnas, sin columna adicional de índice.
- **Origen preservado:** dataset_salud_publica_2500.xlsx.
- **Notebook reproducible:** notebooks/03_limpieza.ipynb. Ejecutar todas las celdas desde la raíz del repositorio o notebooks/ regenera el procesado y este informe.
- **Entorno de ejecución:** Python 3.12.3, pandas 3.0.5, openpyxl 3.1.5.
- **SHA-256 del procesado de esta ejecución:** 6707074a0d805b2fce33f461c10c9335adcb5ab302d960bc0e963db868b983bd.

La preparación y limpieza finaliza con las dos normalizaciones autorizadas y la conservación de todos los registros y NA.
