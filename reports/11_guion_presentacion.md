# Etapa 11A - Guion de presentación

## 1. Concepto narrativo

**PULSO Analytics es un equipo ficticio de consultoría en análisis de datos, utilizado exclusivamente como recurso narrativo académico.** Los cuatro integrantes representan ese equipo en una exposición de la **Universidad de la Ciudad de Buenos Aires**, para **TP1 - Salud Pública**, materia **Herramientas de Análisis de Datos**. La identidad institucional es la principal. Los nombres de los cuatro integrantes quedan como campos por completar; no se infieren de la presentación anterior.

La convocatoria es parte de la ficción: “Una organización vinculada a la gestión sanitaria nos entrega información ficticia de 2500 pacientes y nos pregunta si todos experimentan la atención de la misma manera”. No se inventan clientes reales, hospitales, organismos, contratos ni políticas. Cada resultado describe este dataset ficticio.

**Idea que sostiene la historia:** una primera fotografía global resulta insuficiente; al segmentar aparecen diferencias que permiten formular preguntas más precisas. La satisfacción conecta esas diferencias con la experiencia declarada. El índice organiza dimensiones concurrentes y el modelo explora capacidad predictiva. El dashboard permite consultar lo aprendido y el cierre recupera exclusivamente las cuatro líneas de acción de Etapa 10.

Arco: nos convocan → recibimos y auditamos datos → primera fotografía → los promedios ocultan diferencias → segmentamos → leemos satisfacción → describimos acumulación → exploramos predicción → hacemos consultables los resultados → proponemos dónde profundizar → cierre.

Cada lámina sigue **pregunta → evidencia → interpretación → nueva pregunta**. El pipeline de la diapositiva 3 ubica el recorrido, pero la exposición avanza por preguntas, sin enumerar técnicas como hitos aislados. Las frases de entrada y salida son parte del tiempo asignado y no deben repetirse al leer las notas.

**Fuentes leídas y utilizadas:** [Etapa 1](01_objetivos.md), [Etapa 2](02_auditoria_dataset.md), [Etapa 3](03_limpieza.md), [Etapa 4](04_eda.md), [Etapa 5](05_relaciones.md), [Etapa 6](06_vulnerabilidad.md), [Etapa 7](07_modelado.md), [Etapa 8](08_seleccion_hallazgos.md), [Etapa 9](09_dashboard.md) y [Etapa 10](10_conclusiones_recomendaciones.md). Las alternativas de Etapa 8 se actualizan editorialmente según las decisiones ya documentadas en Etapas 9 y 10. No se recalculan resultados.

La referencia visual localizada es `C:/Users/Germán/Desktop/TP_FINAL_Fortunesky_Scarafilo.pptx`. Se inspeccionaron sus elementos de formato y la presencia del recurso institucional dentro del archivo; no se reutilizan contenidos, gráficos, resultados ni conclusiones del trabajo anterior. Esta etapa produce únicamente el presente guion, sin crear PPTX, imágenes ni otros artefactos.

## 2. Distribución de tiempos e integrantes

**Plan principal: 18:40 minutos, incluida una demo de 1:15. Margen hasta 20:00: 1:20.** Los tiempos incluyen explicación, lectura guiada de figuras, pausas breves y transiciones previstas. Son objetivos de ensayo, no una duración medida. Los cuatro backups se reservan para preguntas y quedan fuera de los 20 minutos.

| Diapositiva | Integrante | Tiempo | Acumulado |
| --- | --- | ---: | ---: |
| 1 | 1 | 1:10 | 1:10 |
| 2 | 1 | 1:35 | 2:45 |
| 3 | 1 | 1:50 | 4:35 |
| 4 | 2 | 1:10 | 5:45 |
| 5 | 2 | 1:35 | 7:20 |
| 6 | 2 | 1:50 | 9:10 |
| 7 | 3 | 1:30 | 10:40 |
| 8 | 3 | 1:35 | 12:15 |
| 9 | 3 | 1:40 | 13:55 |
| 10 | 4 | 1:35 | 15:30 |
| 11 | 4 | 1:40, incluye demo 1:15 | 17:10 |
| 12 | 4 | 1:30 | 18:40 |

| Responsable | Bloque | Total |
| --- | --- | ---: |
| Integrante 1 | Convocatoria, preguntas y confianza en los datos; 1–3 | 4:35 |
| Integrante 2 | Primera fotografía y segmentación; 4–6 | 4:35 |
| Integrante 3 | Satisfacción y acumulación; 7–9 | 4:45 |
| Integrante 4 | Predicción, herramienta y cierre; 10–12 | 4:45 |

## 3. Diapositiva 1

**Título:** “2500 pacientes. Una pregunta: ¿todos experimentan la atención de la misma manera?”

**A. Objetivo.** Captar atención con la pregunta que motiva la convocatoria ficticia. Una idea: necesitamos mirar si las experiencias son distintas.

**B. Qué debe aparecer visualmente.** Portada clara; pregunta protagonista y 2500 destacado. Logo institucional existente de la referencia, con mayor jerarquía que la mención tipográfica PULSO Analytics. No requiere figura estadística. No usar fotografías de pacientes ni ilustraciones nuevas.

**C. Texto mínimo visible.** Título; “TP1 - Salud Pública”; “Universidad de la Ciudad de Buenos Aires”; “Herramientas de Análisis de Datos”; “[Nombre integrante 1] · [Nombre integrante 2] · [Nombre integrante 3] · [Nombre integrante 4]”; “PULSO Analytics · equipo ficticio”; “Dataset ficticio · ejercicio académico”.

**D. Guion oral sugerido.**

“Somos PULSO Analytics, un equipo de consultoría que representamos como parte de este trabajo académico. En esta historia, una organización vinculada a la gestión sanitaria nos entrega información ficticia de 2500 pacientes. Nos plantea una pregunta: ¿todos experimentan la atención de la misma manera?”

“Antes de responder, vale la pena detenerse en la palabra experiencia. Un resumen general puede ser útil, pero quizá no describe de la misma forma a todos los perfiles. Nuestro trabajo fue recorrer esa pregunta con los datos disponibles y reconocer hasta dónde podíamos llegar.”

Hacer una pausa mirando al público. No solicitar respuestas que abran un debate ni comenzar con variables o metodología.

**E. Frase de entrada.** “Les proponemos acompañarnos en una consulta ficticia, pero con una pregunta concreta.”

**F. Frase de salida/transición.** “Para poder responderla, primero tuvimos que convertir esa inquietud en preguntas que los datos permitieran abordar.”

**G. Tiempo estimado.** 1:10.

**H. Integrante responsable.** Integrante 1.

## 4. Diapositiva 2

**Título:** “El desafío: transformar registros en información para decidir”

**A. Objetivo.** Delimitar el encargo en tres preguntas conectadas. Una idea: comparar perfiles ayuda a organizar la lectura de la experiencia.

**B. Qué debe aparecer visualmente.** Dos bloques conceptuales, PERFIL y EXPERIENCIA, unidos por una flecha rotulada “comparar y relacionar”. Es una composición de texto a maquetar en 11B, no una figura analítica existente. La flecha no representa un mecanismo causal.

**C. Texto mínimo visible.** “¿Dónde se espera más?”; “¿Qué segmentos tienen menor acceso a medicación?”; “¿Cómo se relaciona con la satisfacción?”. PERFIL: “Cobertura · Condición · Región” → EXPERIENCIA: “Espera · Medicación · Satisfacción”. Pie: “Relaciones observadas, no causas”.

**D. Guion oral sugerido.**

“El pedido era amplio. Lo ordenamos en tres preguntas: dónde aparecen mayores tiempos de espera, qué segmentos tienen más dificultades de acceso a medicación y cómo se relacionan esas condiciones con la satisfacción.”

“De un lado tenemos características que permiten describir perfiles: cobertura, condición de salud y región. Del otro, aspectos de la experiencia registrada. La flecha significa que vamos a comparar y relacionar; no que esas características determinen por sí solas el resultado.”

“La región queda disponible para explorar en la herramienta. En el relato principal vamos a concentrarnos en cobertura y condición, porque permiten mostrar los contrastes seleccionados sin perder el hilo. Eso no significa que hayamos demostrado ausencia de diferencias regionales.”

“La información puede orientar dónde profundizar. Para recomendar una intervención concreta o estimar su efecto harían falta elementos que este ejercicio no tiene. Primero necesitábamos saber qué podíamos sostener con estos registros.”

**E. Frase de entrada.** “La pregunta inicial se volvió más manejable cuando la dividimos en tres.”

**F. Frase de salida/transición.** “Pero antes de comparar experiencias, había una condición: entender qué calidad tenía la información recibida.”

**G. Tiempo estimado.** 1:35.

**H. Integrante responsable.** Integrante 1.

## 5. Diapositiva 3

**Título:** “Antes de buscar respuestas, tuvimos que confiar en los datos”

**A. Objetivo.** Explicar por qué los denominadores cambian y qué se conservó. Una idea: preparar los datos también implica preservar sus límites.

**B. Qué debe aparecer visualmente.** 2500 registros y 10 variables originales; recorrido textual “Auditoría → Limpieza → EDA → Relaciones → Índice → Modelado → Dashboard” en franja secundaria. Tres notas breves sobre NA, casos disponibles y normalización. No hay figura de pipeline existente: maquetación conceptual pendiente en 11B, sin crear una imagen ahora.

**C. Texto mínimo visible.** “2500 registros · 10 variables originales”; “74 NA en espera · 72 NA en satisfacción”; “Sin eliminación global”; “Casos disponibles + N válido”; “Normalización mínima”. El pipeline completo va en segundo plano.

**D. Guion oral sugerido.**

“Recibimos 2500 registros y diez variables originales. En la auditoría encontramos faltantes en dos variables importantes para nuestras preguntas: 74 en espera y 72 en satisfacción. Eso no significaba que tuviéramos que descartar toda la información de esas personas.”

“Conservamos los registros y los faltantes. Para las descripciones y relaciones usamos los casos disponibles en las variables necesarias y mostramos cuántos participaron. Por eso van a ver distintos N: el total del archivo y la cantidad válida para una comparación no siempre coinciden.”

“La limpieza fue mínima: normalizamos las categorías Crónica y Pública, que venían sin tilde. No modificamos extremos ni completamos respuestas que no estaban. La ausencia de un dato tampoco se convirtió en cero.”

“El recorrido de abajo muestra cómo organizamos el trabajo. No hace falta recorrer cada técnica ahora: van a aparecer cuando la pregunta las necesite. En el modelo hubo un tratamiento específico de la espera faltante dentro del entrenamiento, documentado por separado; eso no cambió el dataset.”

Fuente: Etapas 2 y 3. El detalle de duplicados, intersección de NA e imputación del modelo se reserva para backups A y D.

**E. Frase de entrada.** “Confiar en los datos no fue suponer que estaban completos, sino reconocer qué había y qué faltaba.”

**F. Frase de salida/transición.** “Con los datos preparados, hicimos una primera fotografía del problema. Ahora vamos a ver qué mostraba y qué dejaba fuera.”

**G. Tiempo estimado.** 1:50, incluida transición 1 → 2.

**H. Integrante responsable.** Integrante 1.

## 6. Diapositiva 4

**Título:** “La primera fotografía parecía simple...”

**A. Objetivo.** Dar una referencia global y abrir la tensión entre resumen y diferencias. Una idea: los KPIs son un punto de partida.

**B. Qué debe aparecer visualmente.** Cuatro tarjetas tipográficas grandes a maquetar en 11B. No se requiere gráfico. Valores de Etapa 9, sección 5; no se extraen resultados nuevos del dashboard.

**C. Texto mínimo visible.** “2500 · Registros”; “64.58 min · Espera promedio · N=2426”; “67.80% · Acceso a medicación · N=2500”; “3.56/5 · Satisfacción promedio · Mediana=4 · N=2428”. Pie: “Satisfacción ordinal 1–5; leer junto con mediana y distribución”.

**D. Guion oral sugerido.**

“La primera fotografía resume el conjunto: 2500 registros, una espera promedio de 64.58 minutos y acceso a medicación en el 67.80%. El dashboard también muestra una satisfacción promedio de 3.56 sobre 5, acompañada por una mediana de 4.”

“Los N de cada tarjeta nos recuerdan qué información está disponible. Y la satisfacción tiene niveles ordenados: no suponemos que la distancia entre dos niveles sea siempre equivalente. Por eso el promedio no se interpreta solo.”

“Estos indicadores responden cómo se ve el conjunto. Todavía no responden cómo se distribuye la experiencia entre sus distintos perfiles.”

Señalar las tarjetas sin leer todos los pies en voz alta; dejar una pausa para observarlas.

**E. Frase de entrada.** “Esta fue nuestra primera fotografía.”

**F. Frase de salida/transición.** “¿Qué ocurre si estos promedios están ocultando experiencias diferentes?”

**G. Tiempo estimado.** 1:10.

**H. Integrante responsable.** Integrante 2.

## 7. Diapositiva 5

**Título:** “El promedio ocultaba experiencias de espera muy diferentes”

**A. Objetivo.** Mostrar qué agrega segmentar la espera. Una idea: el promedio global no describe por igual a las tres coberturas.

**B. Qué debe aparecer visualmente.** Figura existente `outputs/figuras/eda/espera_promedio_cobertura.png`, Etapa 4. Mantener las tres barras, escala desde cero, N y NA. Solo ajustar tamaño y márgenes exteriores en la futura diapositiva; no recolorear ni redibujar el gráfico.

**C. Texto mínimo visible.** Título y gráfico: “Privada 17.60 min · N=823”; “Pública 70.19 min · N=777”; “Sin cobertura 106.11 min · N=826”. Referencia pequeña: “Global: 64.58 min”. Pie: “Diferencias observadas; sin interpretación causal”. No sumar otra tabla de medianas al cuerpo.

**D. Guion oral sugerido.**

“Al separar por cobertura, la fotografía cambia. La espera media es 17.60 minutos en Privada, 70.19 en Pública y 106.11 en Sin cobertura. El promedio general sigue siendo correcto, pero no representa de la misma forma a estos tres grupos.”

“Las barras comparan la misma medida y cada una informa su cantidad de esperas disponibles. Los faltantes no se trataron como esperas de cero minutos. Tampoco estamos diciendo que todas las personas de una cobertura tengan la misma experiencia: una media resume variación interna.”

“La lectura que podemos sostener es que las esperas observadas difieren. No que la falta de cobertura provoque por sí sola una demora. Eso requeriría conocer mecanismos y otros factores que no están medidos.”

“Para el encargo, esta diferencia aporta algo concreto: nos indica dónde tendría sentido profundizar la revisión de procesos. Pero la espera era solo una parte de la experiencia.”

Fuente: Etapa 4, sección 8; Etapa 5, sección 3. Medianas 18/71/105 quedan disponibles en backup B.

**E. Frase de entrada.** “La primera diferencia apareció cuando dejamos de mirar a todos como un único grupo.”

**F. Frase de salida/transición.** “¿La medicación también mostraría diferencias si mirábamos las combinaciones de cobertura y condición de salud?”

**G. Tiempo estimado.** 1:35.

**H. Integrante responsable.** Integrante 2.

## 8. Diapositiva 6

**Título:** “La medicación mostró otra diferencia que el promedio no veía”

**A. Objetivo.** Mostrar cómo las combinaciones detallan el acceso. Una idea: los perfiles conjuntos aportan información que el porcentaje global oculta.

**B. Qué debe aparecer visualmente.** Heatmap completo `outputs/figuras/relaciones/acceso_cobertura_condicion.png`, Etapa 5. Conservar las nueve celdas, sus N y la escala 0–100%. Señalar dos celdas con el puntero o un énfasis de maquetación futuro, sin ocultar el resto.

**C. Texto mínimo visible.** “Privada / Aguda: 89.22% · 240/269”; “Sin cobertura / Crónica: 41.99% · 118/281”; “Global: 67.80% · N=2500”. Las etiquetas del PNG están redondeadas a un decimal; las dos cifras destacadas recuperan la precisión del informe, sin modificar la imagen.

**D. Guion oral sugerido.**

“Acá combinamos cobertura y condición de salud. Cada celda muestra el porcentaje de acceso dentro de esa combinación, no sobre el total del dataset. Primero miremos la matriz completa: permite conservar el contexto antes de concentrarnos en dos extremos.”

“Privada con condición aguda presenta 89.22% de acceso. Sin cobertura con condición crónica presenta 41.99%. Las cantidades debajo de cada porcentaje importan: no todas las combinaciones contienen el mismo número de registros.”

“El acceso global de 67.80% no permitía ver esas diferencias. El grupo Sin cobertura / Crónica se vuelve un segmento que vale la pena investigar. Todavía no sabemos qué obstáculos explican su menor acceso.”

“Por ejemplo, disponibilidad o dificultades administrativas serían preguntas posteriores, no resultados del dataset. La variable registra Sí o No; no identifica esos mecanismos. Tampoco hicimos pruebas separadas entre las nueve celdas ni estimamos una interacción estadística.”

Pausa breve para recorrer visualmente filas y columnas; no leer las nueve proporciones. Fuente: Etapa 5, sección 6.

**E. Frase de entrada.** “Para la medicación necesitábamos cruzar dos características del perfil.”

**F. Frase de salida/transición.** “Ya vimos diferencias en espera y medicación. Pero faltaba una pregunta: ¿también aparecen en la experiencia reportada por los pacientes?”

**G. Tiempo estimado.** 1:50, incluida transición 2 → 3.

**H. Integrante responsable.** Integrante 2.

## 9. Diapositiva 7

**Título:** “Mayor espera se asocia con menor satisfacción”

**A. Objetivo.** Conectar las condiciones de atención con la experiencia declarada. Una idea: existe una asociación negativa, con límites claros.

**B. Qué debe aparecer visualmente.** `outputs/figuras/relaciones/espera_por_satisfaccion.png`, Etapa 5. Boxplots completos y grandes. Orientar la lectura: eje horizontal, satisfacción 1–5; vertical, espera en minutos. No convertir la figura en un gráfico causal ni invertir sus ejes.

**C. Texto mínimo visible.** “Spearman ρ=−0.7402 · N=2357”; “ASOCIACIÓN ≠ CAUSALIDAD”. El gráfico conserva los N por nivel. El p-value queda en backup B.

**D. Guion oral sugerido.**

“En el eje horizontal están los niveles de satisfacción y en el vertical, los minutos de espera. Las cajas permiten ver distribución y solapamiento, no solo un valor por grupo. Al recorrerlas, los niveles mayores de satisfacción tienden a acompañarse de esperas menores.”

“La asociación de Spearman fue negativa, con un valor de menos 0.7402, usando 2357 registros con ambas variables disponibles. Elegimos una lectura por rangos porque la satisfacción es ordinal; el detalle del cálculo queda para preguntas.”

“Este patrón conecta la espera con la experiencia declarada, pero no explica por sí solo su causa. No permite prometer cuánto aumentaría la satisfacción si redujéramos cierta cantidad de minutos. Además, no estamos ajustando por todas las otras variables.”

“Hasta acá veníamos mirando relaciones entre aspectos específicos. Una misma persona, sin embargo, puede presentar más de una dimensión a la vez.”

Fuente: Etapa 5, sección 7. No afirmar que ρ representa un porcentaje explicado.

**E. Frase de entrada.** “La siguiente pregunta fue si las diferencias también se reflejaban en la satisfacción.”

**F. Frase de salida/transición.** “¿Qué ocurre cuando una misma persona acumula varias dimensiones?”

**G. Tiempo estimado.** 1:30.

**H. Integrante responsable.** Integrante 3.

## 10. Diapositiva 8

**Título:** “Necesitábamos observar la acumulación de dificultades”

**A. Objetivo.** Definir el índice antes de mostrar sus resultados. Una idea: score significa cantidad de dimensiones operacionales.

**B. Qué debe aparecer visualmente.** Tres componentes textuales con signos de suma y un resultado 0–3. No existe una imagen de esta fórmula: **VISUAL PENDIENTE DE DECISIÓN**, a resolver como composición textual en 11B desde la definición de Etapa 6, sin crear un gráfico estadístico ni un logo. Aclarar oralmente que la condición crónica representa necesidad según la definición y no una barrera por sí misma.

**C. Texto mínimo visible.** “Índice operacional de vulnerabilidad en el acceso y la atención”; “Condición crónica + Sin acceso a medicación + Espera ≥99 min → SCORE 0–3”; “1 punto por dimensión · 99=Q3 original”; “Cobertura no integra la fórmula”. Franja visible: “NO es diagnóstico · NO es riesgo clínico · NO significa baja/media/alta vulnerabilidad · NO clasifica vulnerable Sí/No”.

**D. Guion oral sugerido.**

“Para describir la concurrencia definimos un índice operacional. Suma un punto por condición crónica, uno por falta de acceso a medicación y otro por espera de 99 minutos o más. Ese umbral corresponde al tercer cuartil original; no es un límite clínico y no cambia cuando filtramos.”

“La condición crónica representa una dimensión de necesidad por decisión del equipo. No estamos diciendo que sea en sí misma una barrera ni que otras condiciones no necesiten atención.”

“El score responde cuántas de esas tres dimensiones están presentes. No responde qué gravedad tiene una persona, no hace un diagnóstico ni la clasifica como vulnerable o no vulnerable. Un mismo score puede reunir perfiles distintos.”

“La cobertura no se suma: la usamos después para comparar. Y si falta información para una dimensión, dejamos el score sin calcular. Un dato ausente no significa que esa dimensión no exista.”

Fuente: Etapa 6, secciones 2, 3 y 9. No leer las cuatro negaciones como una lista extensa; mantenerlas visibles y explicar el significado central.

**E. Frase de entrada.** “Necesitábamos un resumen de la concurrencia, con una definición explícita.”

**F. Frase de salida/transición.** “Con esa definición, pudimos preguntar dónde se acumulan las dimensiones y cómo se ve allí la satisfacción.”

**G. Tiempo estimado.** 1:35.

**H. Integrante responsable.** Integrante 3.

## 11. Diapositiva 9

**Título:** “Cuando se acumulan dimensiones, la experiencia también cambia”

**A. Objetivo.** Unir distribución del índice y satisfacción bajo una sola idea: la acumulación operacional coincide con diferencias en la experiencia declarada.

**B. Qué debe aparecer visualmente.** Dos figuras existentes de Etapa 6: `outputs/figuras/vulnerabilidad/score_por_cobertura.png` y `outputs/figuras/vulnerabilidad/satisfaccion_por_score.png`. Planificar dos apariciones sucesivas dentro de la misma diapositiva: primero cobertura, después satisfacción, usando el mismo espacio amplio. No crear otra lámina ni reducir ambas a miniaturas. Mantener escalas, leyendas, N y todos los niveles; el énfasis cambia con la explicación.

**C. Texto mínimo visible.** Primer momento: “Score 3: Privada 0.00% · Pública 3.09% · Sin cobertura 10.90%” y N=823/777/826. Segundo: “Mediana de satisfacción: score 0 → 4; 1 → 4; 2 → 3; 3 → 2”, N=874/912/457/114; N conjunto=2357. Pie persistente: “Asociación descriptiva · No valida clínicamente el índice”.

**D. Guion oral sugerido.**

“Primero miremos dónde coinciden las tres dimensiones. El score 3 representa 0.00% en Privada, 3.09% en Pública y 10.90% en Sin cobertura, siempre entre registros con score disponible. Son porcentajes dentro de cada cobertura. La ausencia en Privada es coherente con que sus esperas no alcanzan el umbral; no significa ausencia de toda dificultad.”

Cambiar de figura en la misma lámina.

“Ahora miremos la experiencia declarada. Las medianas de satisfacción son 4, 4, 3 y 2 al recorrer los scores de cero a tres. Las distribuciones también importan: cero y uno comparten mediana, pero no tienen una composición idéntica.”

“La acumulación operacional coincide con diferencias en satisfacción. No demuestra que el score cause satisfacción ni que sea una escala clínica validada. Aunque satisfacción está fuera de la fórmula, los datos provienen del mismo ejercicio sintético.”

Fuente: Etapa 6, secciones 6 y 8; cifras corroboradas en Etapa 9. Dedicar aproximadamente la mitad del bloque visual a cada figura.

**E. Frase de entrada.** “El índice nos permitió mirar la concurrencia de dos maneras complementarias.”

**F. Frase de salida/transición.** “Ya pudimos describir relaciones y acumulación. La siguiente pregunta fue si esas variables también contenían información para predecir satisfacción.”

**G. Tiempo estimado.** 1:40, incluida transición 3 → 4.

**H. Integrante responsable.** Integrante 3.

## 12. Diapositiva 10

**Título:** “El modelo encuentra estructura predictiva, pero no explica causas”

**A. Objetivo.** Comunicar aporte y alcance del modelo frente a una referencia simple. Una idea: predicción útil dentro del ejercicio no equivale a explicación causal.

**B. Qué debe aparecer visualmente.** KPIs tipográficos de Decision Tree frente al baseline, con dos porcentajes protagonistas. No requiere una figura nueva: se transcriben métricas de Etapa 7. La figura existente `outputs/figuras/modelado/comparacion_modelos.png` se reserva para backup D porque reúne tres métricas y tres estrategias. No añadirla como miniatura a esta lámina.

**C. Texto mínimo visible.** “Target: satisfacción 1–5”; “Decision Tree: ≈50.4% exactas · ≈96.5% dentro de ±1”; “Baseline: siempre 4 · ≈32.7% exactas · ≈80.7% dentro de ±1”; “N test=486 · ±1 incluye exactas”. Secundario: “Macro F1=0.5071 · MAE ordinal=0.5309”; “Variables más utilizadas por el modelo: espera ≈63.1% · medicación ≈26.2%”. Pie: “PREDICCIÓN ≠ CAUSALIDAD · Sin validación externa; test usado en selección”.

**D. Guion oral sugerido.**

“Probamos predecir satisfacción entre uno y cinco, comparando el árbol con una referencia que siempre responde cuatro. El Decision Tree seleccionado acertó exactamente alrededor del 50.4% y quedó dentro de un nivel de diferencia en aproximadamente el 96.5%. El baseline obtuvo alrededor de 32.7% y 80.7%, respectivamente.”

“Estar dentro de un nivel incluye los aciertos exactos. No significa que acertemos exactamente en el 96.5% ni que tengamos esa probabilidad de acierto para cada persona.”

“Las variables más utilizadas por el árbol fueron espera y acceso a medicación. Esos porcentajes describen su uso en el modelo, no causas de la satisfacción.”

“Hay estructura predictiva en este dataset, que ya contiene relaciones sintéticas. El mismo test participó en la selección y no tenemos validación externa. Tampoco es un pronóstico previo a la atención: requiere conocer espera y acceso. Su función acá es complementar la descripción.”

Fuentes exactas: Etapa 7, secciones 5, 8–11. Exactas/±1: árbol 50.4115%/96.5021%; baseline 32.7160%/80.6584%. Importancias: 63.1003% y 26.1623%. La aproximación de pantalla sigue la consigna; el backup conserva la precisión publicada.

**E. Frase de entrada.** “Describir un patrón y predecir un resultado son preguntas diferentes.”

**F. Frase de salida/transición.** “Nos faltaba que todo este recorrido pudiera consultarse sin recorrer los notebooks y los informes.”

**G. Tiempo estimado.** 1:35.

**H. Integrante responsable.** Integrante 4.

## 13. Diapositiva 11

**Título:** “Convertimos el análisis en una herramienta para explorar decisiones”

**A. Objetivo.** Mostrar cómo consultar los resultados segmentados. Una idea: la herramienta hace explorables los hallazgos y sus denominadores.

**B. Qué debe aparecer visualmente.** Captura real del dashboard existente, con filtros y KPIs legibles. **VISUAL PENDIENTE DE DECISIÓN:** no se encontró una captura entre los artefactos del proyecto. Su fuente verificada es `outputs/dashboard/dashboard_salud.html` (Etapa 9). En 11B deberá capturarse ese HTML real, sin reconstruir ni inventar una pantalla. No se crea la imagen en 11A ni se asigna una ruta ficticia de captura.

**C. Texto mínimo visible.** “Región · Cobertura · Condición”; “4 KPIs · 5 visualizaciones”; “Offline · HTML autocontenido”; “Sin Python ni Excel para consultar”. Los KPIs visibles en la captura: registros, espera, acceso a medicación y satisfacción. Los filtros recalculan sus indicadores con los casos seleccionados.

**D. Guion oral sugerido.**

Introducción breve: “El análisis no debía quedar solamente en notebooks e informes. Construimos una herramienta para explorar los mismos resultados por región, cobertura y condición, conservando los N válidos. Funciona offline y se consulta abriendo un HTML, sin Python ni Excel.”

Realizar la demo de 75 segundos de la sección 16: vista global → cobertura Pública → KPIs → espera por cobertura y acceso por condición → restablecer → volver. La locución de esa sección reemplaza cualquier explicación adicional durante la demo.

No recorrer las cinco vistas: existen espera por cobertura, acceso por cobertura y condición, distribución de satisfacción, acumulación por cobertura y satisfacción por acumulación; solo se muestran las dos previstas. El dashboard no contiene el modelo ni estima efectos de decisiones.

**E. Frase de entrada.** “Para que la información se pudiera explorar, la llevamos a un dashboard interactivo.”

**F. Frase de salida/transición.** “La herramienta permite mirar los perfiles; el paso final es distinguir qué preguntas y propuestas están respaldadas por lo que vimos.”

**G. Tiempo estimado.** 1:40: 0:25 para introducción y transición, más 1:15 de demo con cambio de ventana y regreso incluidos.

**H. Integrante responsable.** Integrante 4; también opera el dashboard.

## 14. Diapositiva 12

**Título:** “Los datos nos mostraron dónde vale la pena mirar”

**A. Objetivo.** Responder al encargo con las cuatro líneas de Etapa 10. Una idea: la evidencia orienta dónde profundizar, sin demostrar efectos de intervención.

**B. Qué debe aparecer visualmente.** Cuatro líneas breves y una frase de cierre grande. No requiere figura estadística. Evitar repetir gráficos o sumar recomendaciones. Al final puede aparecer “Gracias / Preguntas” dentro de la misma diapositiva.

**C. Texto mínimo visible.**

- **TIEMPOS DE ESPERA:** Revisar procesos en segmentos con mayores demoras.
- **ACCESO A MEDICACIÓN:** Investigar barreras en combinaciones con menor acceso.
- **ACUMULACIÓN:** Utilizar el índice para orientar dónde profundizar.
- **SATISFACCIÓN:** Monitorearla junto con condiciones de acceso y atención.

Frase grande: **“Los datos no nos dijeron qué decisión tomar. Nos mostraron dónde vale la pena mirar.”** Pie: “Dataset ficticio · Resultados no generalizables automáticamente a Argentina · Asociación ≠ causalidad”. Final: “Gracias / Preguntas”.

**D. Guion oral sugerido.**

“Volvemos al encargo inicial con cuatro líneas para profundizar, ya desarrolladas en nuestras conclusiones. Las diferencias de espera justifican revisar procesos en los segmentos con mayores demoras. El contraste de acceso a medicación orienta a investigar barreras, especialmente en Sin cobertura con condición crónica.”

“La acumulación permite organizar qué segmentos mirar con más detalle, siempre recordando que el índice cuenta dimensiones. No debe usarse para decidir prestaciones individuales. Y la satisfacción conviene monitorearla junto con espera, medicación y perfiles, porque el valor global no alcanza para describir toda la experiencia.”

“Podemos seguir esas preguntas con indicadores que ya tenemos: media y mediana de espera, porcentaje de acceso, distribución del score y distribución de satisfacción, siempre con sus N.”

“No evaluamos políticas ni efectos de una intervención. Trabajamos con datos ficticios y no generalizamos a Argentina.”

Pausa y frase de cierre; no leer de nuevo las cuatro líneas. Fuente exclusiva de sugerencias: Etapa 10, secciones 3–6 y 8–10.

**E. Frase de entrada.** “¿Con qué información volvemos entonces a la organización de nuestra historia?”

**F. Frase de salida/transición.** “Los datos no nos dijeron qué decisión tomar. Nos mostraron dónde vale la pena mirar. Muchas gracias; los escuchamos.”

**G. Tiempo estimado.** 1:30.

**H. Integrante responsable.** Integrante 4.

## 15. Transiciones entre integrantes

Las tres transiciones se ensayan como un diálogo continuo; el siguiente integrante retoma la pregunta sin volver a presentarse ni resumir todo el bloque anterior.

| Pase | Cierre del integrante saliente | Entrada del siguiente |
| --- | --- | --- |
| 1 → 2, entre 3 y 4 | “Con los datos preparados, hicimos una primera fotografía del problema. Ahora vamos a ver qué mostraba y qué dejaba fuera.” | “Esta fue nuestra primera fotografía.” |
| 2 → 3, entre 6 y 7 | “Ya vimos diferencias en espera y medicación. Pero faltaba una pregunta: ¿también aparecen en la experiencia reportada por los pacientes?” | “La siguiente pregunta fue si las diferencias también se reflejaban en la satisfacción.” |
| 3 → 4, entre 9 y 10 | “Ya pudimos describir relaciones y acumulación. La siguiente pregunta fue si esas variables también contenían información para predecir satisfacción.” | “Describir un patrón y predecir un resultado son preguntas diferentes.” |

Las frases de entrada pueden acortarse en ensayo para evitar repetir la pregunta textual. El pase de voz y el cambio de diapositiva forman parte del bloque saliente; el margen general absorbe retrasos, no una segunda explicación.

## 16. Demo del dashboard

**Duración elegida: 75 segundos**, dentro del intervalo solicitado de 60–90 y dentro del bloque del integrante 4. Fuente: [dashboard existente](../outputs/dashboard/dashboard_salud.html). Esta etapa solo planifica; no ejecuta filtros ni calcula resultados nuevos.

Preparación para el ensayo: abrir previamente el HTML local en el navegador, dejar todos los filtros en “Todas” y ubicar la ventana junto a la presentación. Probar la alternancia de ventanas en el equipo de exposición. No depender de internet ni abrir notebooks. La futura captura real de 11B funcionará también como respaldo estático.

| Segundo | Acción exacta | Locución o foco |
| --- | --- | --- |
| 0–10 | Cambiar al navegador y mostrar vista sin filtros | “Partimos de los 2500 registros y de los indicadores globales que ya vimos.” |
| 10–20 | Elegir únicamente Cobertura = Pública; Región y Condición siguen en Todas | “Ahora miramos una sola cobertura, manteniendo las demás selecciones abiertas.” |
| 20–35 | Señalar cambio de KPIs y sus denominadores | “La selección contiene 806 registros. Cada indicador usa los datos disponibles para su variable.” No improvisar cifras de los demás KPIs. |
| 35–50 | Señalar espera por cobertura y su información de media/mediana/N | “La vista conserva el segmento elegido: media de espera 70.19 minutos, mediana 71, N=777.” |
| 50–60 | Mostrar el heatmap de acceso por condición, con desplazamiento breve si hace falta | “Dentro de la selección también podemos distinguir las condiciones de salud.” No abrir otros cruces ni leer todas las celdas. |
| 60–68 | Pulsar Restablecer filtros | “Volvemos al conjunto completo.” Verificar que reaparecen 2500 registros. |
| 68–75 | Volver inmediatamente a la presentación | Retomar el cierre de la diapositiva 11 y avanzar a la 12. |

La selección Pública es significativa porque retoma la comparación de espera y permite mostrar que los denominadores cambian. Ya fue validada en Etapa 9, sección 10: N registros=806, N espera=777, N acceso=806, N satisfacción=780, N score=777 y N conjunto=752. Las cifras de espera proceden de Etapas 4–5; no se obtienen nuevos resultados para preparar este guion.

**Contingencia:** si falla la apertura o alternancia, volver a la captura real prevista para 11B y explicar el recorrido con ella, sin simular que es interactiva. No dedicar el margen a resolver problemas técnicos en público. Si la captura aún no existe, la preparación de 11B queda pendiente; el guion no la presenta como entregada. La demo podrá reducirse a 60 segundos en ensayo suprimiendo el comentario del segundo gráfico, conservando restablecer y regresar.

## 17. Identidad visual

**Referencia revisada:** `C:/Users/Germán/Desktop/TP_FINAL_Fortunesky_Scarafilo.pptx`. La inspección del paquete PPTX confirma imágenes recurrentes con descripción `Logos-3-png_Logo-secundario-1-1024x496.png`, fondos claros y formatos tipográficos con Play, Arial y Calibri. En los elementos inspeccionados aparecen blanco, grises y tonos violeta como `#522263` y `#7A2D87`. Estos últimos son colores observados en la referencia, no una certificación del código institucional magenta. No se renderizó una presentación nueva ni se trasladó contenido temático.

Para 11B mantener **Universidad de la Ciudad como identidad principal**: logo institucional original, proporciones preservadas, sin redibujarlo. En el paquete de referencia, la imagen asociada al logo de la primera diapositiva se localiza mediante su relación a `ppt/media/image10.png`; es un recurso interno del PPTX, no un PNG creado en el proyecto. Verificar visualmente su variante y legibilidad al incorporarlo en 11B. No reutilizar otras imágenes de la referencia.

Usar fondo predominantemente claro, títulos grandes, texto oscuro, KPIs destacados, poco texto y espacio suficiente para que los gráficos sean protagonistas. El **magenta institucional solicitado** será el acento en títulos cortos, líneas o destacados; el tono exacto deberá verificarse contra el recurso institucional disponible al maquetar, sin inventar un código oficial. Conservar las paletas de los gráficos existentes para no alterar su lectura; el acento pertenece a la composición de la diapositiva.

Como pauta de maquetación futura, priorizar títulos de aproximadamente 30–36 pt y texto de apoyo de 20–24 pt, ajustando según proyección. Son recomendaciones de diseño, no tamaños atribuidos a toda la referencia. No copiar los textos pequeños detectados en ella si perjudican la lectura.

**PULSO Analytics, identidad secundaria:** concepto de observación y lectura de indicadores; usar por ahora únicamente el nombre tipográfico con “equipo ficticio”. Ubicación propuesta: área inferior o esquina opuesta al logo institucional, con menor tamaño y peso visual. No usar un trazo de electrocardiograma que sugiera diagnóstico ni diseñar un logo en esta etapa. La marca académica no compite con la Universidad ni se presenta como una empresa real.

## 18. Visualizaciones existentes a reutilizar

Rutas relativas a la raíz del proyecto, verificadas en disco. Los identificadores F corresponden al inventario de Etapa 8. “Adaptación” significa planificación de escala, posición, márgenes o énfasis de exposición dentro del futuro PPTX; no regeneración de gráficos ni modificación de archivos existentes.

| Diapositiva / recurso | Archivo existente o estado | Origen | Qué comunica | Recorte o adaptación prevista |
| --- | --- | --- | --- | --- |
| 1 | Recurso institucional dentro del PPTX de referencia indicado en sección 17; sin figura estadística | Referencia visual | Identidad de la Universidad | Preservar logo original; no extraído a disco en 11A |
| 2 | No requiere figura estadística; composición textual PERFIL → EXPERIENCIA pendiente de maquetación | Etapa 1 | Preguntas y variables conceptuales | Rotular la flecha como comparación, sin sentido causal |
| 3 | No existe figura del pipeline; composición textual pendiente de maquetación | Etapas 2–3 y recorrido 4–9 | Calidad y continuidad del trabajo | Franja secundaria; no sumar detalle técnico |
| 4 | No requiere figura; tarjetas con valores ya documentados | Etapa 9, sección 5 | Referencia global | Mantener N y nota ordinal |
| 5 · F11 | [outputs/figuras/eda/espera_promedio_cobertura.png](../outputs/figuras/eda/espera_promedio_cobertura.png) | Etapa 4 | Medias de espera por cobertura | Ajustar escala y solo márgenes vacíos; conservar ejes, N y NA |
| 6 · F16 | [outputs/figuras/relaciones/acceso_cobertura_condicion.png](../outputs/figuras/relaciones/acceso_cobertura_condicion.png) | Etapa 5 | Nueve combinaciones de acceso | Matriz completa; no recortar celdas ni escala; destacados externos con precisión del informe |
| 7 · F17 | [outputs/figuras/relaciones/espera_por_satisfaccion.png](../outputs/figuras/relaciones/espera_por_satisfaccion.png) | Etapa 5 | Distribución de espera por satisfacción | Mantener ejes y N por nivel; añadir ρ como texto externo |
| 8 | VISUAL PENDIENTE DE DECISIÓN: no existe imagen de la fórmula; usar composición textual futura | Etapa 6, sección 2 | Tres dimensiones sumadas, score 0–3 | Sin nuevo gráfico estadístico; fórmula completa y exclusiones visibles |
| 9 · F20 | [outputs/figuras/vulnerabilidad/score_por_cobertura.png](../outputs/figuras/vulnerabilidad/score_por_cobertura.png) | Etapa 6 | Distribución completa del score por cobertura | Primera aparición; conservar leyenda 0–3, N y porcentajes |
| 9 · F22 | [outputs/figuras/vulnerabilidad/satisfaccion_por_score.png](../outputs/figuras/vulnerabilidad/satisfaccion_por_score.png) | Etapa 6 | Distribución de satisfacción por score | Segunda aparición en la misma lámina; mantener leyenda y N; medianas como texto externo |
| 10 | No requiere PNG; tarjetas de métricas existentes | Etapa 7, secciones 5 y 8–11 | Exactitud y cercanía frente al baseline | Mantener ±1 incluye exactas y N; F23 queda solo en backup D |
| 11 | [outputs/dashboard/dashboard_salud.html](../outputs/dashboard/dashboard_salud.html); captura: VISUAL PENDIENTE DE DECISIÓN | Etapa 9 | Herramienta real y filtros | Captura real pendiente de 11B; encuadrar filtros y KPIs, sin inventar pantalla ni ruta |
| 12 | No requiere figura; composición textual | Etapa 10 | Cuatro líneas de acción ya formuladas | Frase final protagonista |
| Backup A | No requiere PNG; tabla documental ya existente en reports/03_limpieza.md, secciones 3–4 | Etapas 2–3 | Conservación de filas y NA | Maquetar selección de filas de la tabla, sin recalcular |
| Backup B · F13 | [outputs/figuras/relaciones/espera_por_cobertura_boxplot.png](../outputs/figuras/relaciones/espera_por_cobertura_boxplot.png) | Etapa 5 | Distribuciones más allá de las medias | Mostrar solo si la pregunta requiere la distribución; tabla de pruebas en otra aparición de la misma lámina |
| Backup C · F19 | [outputs/figuras/vulnerabilidad/score_vulnerabilidad_distribucion.png](../outputs/figuras/vulnerabilidad/score_vulnerabilidad_distribucion.png) | Etapa 6 | Frecuencias de scores 0–3 | Alternar con fórmula y tabla de combinaciones, sin multiplicar backups |
| Backup D · F23 | [outputs/figuras/modelado/comparacion_modelos.png](../outputs/figuras/modelado/comparacion_modelos.png) | Etapa 7 | Comparación de tres estrategias y métricas | Figura completa; explicar un panel por vez |
| Backup D · F26 | [outputs/figuras/modelado/importancia_variables_modelo.png](../outputs/figuras/modelado/importancia_variables_modelo.png) | Etapa 7 | Importancias agregadas de los ocho predictores | Aparición alternativa según pregunta, con límite no causal |

Las figuras inspeccionadas usan en algunos casos menos decimales que los informes. Conservar las imágenes originales y sus redondeos; los destacados recuperan las cifras documentadas. No agregar líneas, barras, escalas o estadísticas nuevas a los PNG. Las composiciones textuales previstas son instrucciones para 11B, no archivos visuales creados en esta etapa.

## 19. Diapositivas backup

**Exactamente cuatro backups: A, B, C y D**, fuera del recorrido principal y del tiempo de exposición. La información extensa que sigue prepara las notas del presentador: no debe volcarse toda simultáneamente en pantalla. Usar apariciones dentro de cada backup según la pregunta; no producir backups adicionales. Respuestas iniciales de 30–60 segundos y ampliación solo si el docente lo pide.

### Backup A — Conservamos los registros y explicitamos la información disponible

**A. Objetivo.** Responder cómo se auditó y cómo se trataron los faltantes.

**B. Visual.** Tabla compacta a partir de Etapas 2–3; sin gráfico nuevo.

**C. Texto mínimo visible.** “2500 × 10”; “0 IDs repetidos · 0 filas duplicadas”; “74 NA espera · 72 NA satisfacción”; “143 filas con algún NA · 3 con ambos”; “Casos disponibles; sin eliminación global”.

**D. Guion oral sugerido.** “Conservamos los 2500 registros. Los faltantes de espera y satisfacción se superponen en tres casos, de modo que 143 filas tienen alguno. Cada análisis usa las variables que necesita: espera N=2426, satisfacción N=2428 y la relación entre ambas N=2357. La limpieza solo normalizó Cronica a Crónica y Publica a Pública. No inferimos el mecanismo de ausencia ni reemplazamos NA por cero. El tratamiento temporal dentro del modelo está separado y no alteró el archivo.”

Respaldo de notas: 843 celdas de condición y 806 de cobertura normalizadas; 1649 celdas, no pacientes distintos. Fuentes: Etapa 2, secciones 3–4 y 8–9; Etapa 3, secciones 2–5. La unicidad del ID no demuestra independencia estadística.

**E. Entrada.** “La decisión fue conservar información y hacer explícito el denominador de cada resultado.”

**F. Salida.** “El N efectivo responde qué información exige cada pregunta.”

**G. Tiempo.** 0:45 orientativo, solo en preguntas.

**H. Responsable.** Integrante 1.

### Backup B — Las pruebas acompañan las diferencias; no identifican causas

**A. Objetivo.** Defender métodos, N efectivos y diferencia entre significación y magnitud.

**B. Visual.** Tabla documental de Etapa 5, sección 9. F13, `outputs/figuras/relaciones/espera_por_cobertura_boxplot.png`, queda como aparición alternativa para preguntas sobre dispersión. No mostrar tabla y gráfico reducidos simultáneamente.

**C. Texto mínimo visible.** Filas pertinentes de la siguiente tabla y “Exploratorio · Sin ajuste por multiplicidad · Asociación ≠ causalidad”.

| Relación | Método y resultado documentado | N | Magnitud / lectura |
| --- | --- | ---: | --- |
| Condición–frecuencia | Kruskal-Wallis H=2042.640; gl=2; p < 0.001 | 2500 | Medianas 1/4/13; diferencias globales de rangos |
| Cobertura–espera | Kruskal-Wallis H=1684.378; gl=2; p < 0.001 | 2426 | Medianas 18/71/105 min; formas y dispersiones distintas |
| Cobertura–medicación | χ²=255.798; gl=2; p < 0.001 | 2500 | V de Cramér=0.3199 |
| Condición–medicación | χ²=27.170; gl=2; p < 0.001 | 2500 | V de Cramér=0.1042 |
| Espera–satisfacción | Spearman ρ=−0.7402; p < 0.001 | 2357 | Asociación monotónica negativa |

**D. Guion oral sugerido.** “Las pruebas respondieron preguntas distintas. Kruskal-Wallis compara rangos entre grupos sin asumir normalidad; con distribuciones de distinta forma no lo interpretamos como una prueba exclusiva de medianas. Chi-cuadrado evalúa asociación entre categorías y V de Cramér aporta magnitud. Spearman permite relacionar la espera con satisfacción ordinal mediante rangos. Los p-values son exploratorios y no miden relevancia práctica ni causas.”

Notas para ampliar: cinco pruebas principales, α=0.05 y p nominales sin ajuste por multiplicidad; independencia supuesta, sin diseño muestral documentado; no hubo post-hoc. En chi-cuadrado los mínimos esperados fueron 259.532 y 266.616, sin celdas esperadas menores que 5. V no tiene dirección ni representa varianza explicada. El heatmap y satisfacción por medicación son descriptivos, sin pruebas adicionales. Fuentes: Etapa 5, secciones 1–9 y 11.

**E. Entrada.** “Elegimos la prueba según la pregunta y el tipo de variable.”

**F. Salida.** “La evidencia estadística acompaña el patrón, pero no elimina sus límites.”

**G. Tiempo.** 0:60 orientativo sobre el método preguntado, no toda la tabla.

**H. Responsable.** Integrante 2; Integrante 3 amplía Spearman si corresponde.

### Backup C — El score cuenta dimensiones y conserva perfiles distintos

**A. Objetivo.** Defender definición, umbral, combinaciones y NA sin clasificación clínica.

**B. Visual.** Fórmula textual de Etapa 6, sección 2; tabla de combinaciones de sección 5; F19 `outputs/figuras/vulnerabilidad/score_vulnerabilidad_distribucion.png` como aparición alternativa. Nada se recalcula.

**C. Texto mínimo visible.** “Score = I(Crónica) + I(Sin acceso) + I(Espera ≥99)”; “Solo con las tres dimensiones observables”; “Q3 original=99”; “Cobertura fuera de la fórmula”; “No es escala clínica”. I significa 1 cuando se cumple la condición y 0 cuando no; si falta una dimensión, score NA.

| Necesidad / medicación / espera | Score | N documentado |
| --- | ---: | ---: |
| 0/0/0 | 0 | 904 |
| 0/0/1 | 1 | 237 |
| 0/1/0 | 1 | 285 |
| 1/0/0 | 1 | 415 |
| 0/1/1 | 2 | 176 |
| 1/0/1 | 2 | 87 |
| 1/1/0 | 2 | 208 |
| 1/1/1 | 3 | 114 |

**D. Guion oral sugerido.** “La suma cuenta dimensiones y pierde parte del perfil. Por ejemplo, el score uno puede corresponder a necesidad por condición crónica, falta de medicación o espera desde 99 minutos; no son experiencias equivalentes. El corte proviene del tercer cuartil original y los pesos son iguales por definición del ejercicio, no por calibración clínica. Tenemos 2426 scores observables y 74 NA. La asociación con satisfacción usa 2357 casos y no constituye validación externa.”

Notas: frecuencias 0/1/2/3=904/937/471/114. Score 0 no equivale a ausencia de toda dificultad; cronicidad no es una barrera por sí misma. El umbral incluye exactamente 99 y no se recalcula al filtrar. Fuente: Etapa 6, secciones 2–5, 8–11.

**E. Entrada.** “El significado del score está en su definición, no en una etiqueta de gravedad.”

**F. Salida.** “Su uso propuesto es descriptivo y para orientar investigación de segmentos.”

**G. Tiempo.** 0:45 orientativo, solo en preguntas.

**H. Responsable.** Integrante 3.

### Backup D — La comparación predictiva tiene una referencia y límites de validación

**A. Objetivo.** Defender split, pipeline, CV, selección, errores e importancias.

**B. Visual.** F23 `outputs/figuras/modelado/comparacion_modelos.png` como figura principal. F26 `outputs/figuras/modelado/importancia_variables_modelo.png` y la tabla de métricas como apariciones alternativas en el mismo backup. Las notas técnicas siguientes no se proyectan todas a la vez.

**C. Texto mínimo visible.** “Target 1–5 · Train 1942 / Test 486”; “Pipeline ajustado en train”; “CV: 5 pliegues en train”; “Baseline: siempre 4”; “Seleccionado: Decision Tree”; “Test utilizado en selección · Sin validación externa”.

| Estrategia | Macro F1 | MAE ordinal | Exactas % | Dentro de ±1 % | Errores ≥2 % |
| --- | ---: | ---: | ---: | ---: | ---: |
| Baseline | 0.0986 | 0.9239 | 32.7160 | 80.6584 | 19.3416 |
| Decision Tree | 0.5071 | 0.5309 | 50.4115 | 96.5021 | 3.4979 |
| Random Forest | 0.4840 | 0.5412 | 49.1770 | 96.7078 | 3.2922 |

**D. Guion oral sugerido.** “Separamos los 2428 casos con satisfacción disponible en train y test estratificados. La codificación y la imputación de espera se aprendieron dentro del pipeline con train, también en cada pliegue de validación cruzada. Comparamos dos modelos con una referencia que siempre predice cuatro. El criterio combinó macro F1, MAE ordinal y errores de dos niveles o más; seleccionó el árbol. El bosque tuvo menos errores grandes, de modo que la elección no significa que el árbol gane en todo. Como usamos el test para elegir, no es una evaluación externa independiente.”

Notas técnicas, fuente exclusiva Etapa 7:

- Split estratificado por satisfacción, test_size=0.20, random_state=42; 1942/486, sin filas compartidas. Se excluyen 72 sin target; se retienen 71 con target y espera NA.
- Ocho predictores: Region, Edad, Genero, Condicion_Salud, Cobertura_Salud, Frecuencia_Atencion, Tiempo_Espera_min y Acceso_Medicacion. Sin ID, score, Dim_* ni derivados del target.
- ColumnTransformer y Pipeline: OneHotEncoder con categorías desconocidas ignoradas; mediana solo para espera; Edad y Frecuencia_Atencion pasan sin cambios; sin escalado. Mediana aprendida en train=55.00 min. No se altera el dataset.
- Decision Tree: profundidad máxima 6, mínimo 10 por hoja. Random Forest: 200 árboles, profundidad máxima 10, mínimo 3 por hoja. Configuraciones fijas; no se retocaron con test.
- CV de cinco pliegues en train: macro F1 medio/DE, árbol 0.4918/0.0214; bosque 0.4812/0.0260. MAE medio/DE: árbol 0.5268/0.0258; bosque 0.5428/0.0199. No son intervalos de confianza ni prueba de estabilidad externa.
- Selección: suma de rangos en macro F1, MAE y errores ≥2; árbol 4, bosque 5. Desempate previsto por menor DE de F1 en CV y luego interpretabilidad; no fue necesario. Accuracy no decidió.
- Árbol: 245 exactas, 224 errores de un nivel, 17 de ≥2; nivel 4 con menor recall=0.3082. ±1 incluye exactas; no confundir cercanía con exactitud.
- Importancias por variable original: espera 63.1003%, medicación 26.1623%, edad 4.0425%, frecuencia 2.2755%, género 2.0038%, condición 1.1943%, cobertura 0.7111%, región 0.5103%. Son reducciones de impureza agregadas, sujetas a sesgos; no efectos causales independientes.
- El modelo aprende clases nominales; MAE incorpora orden en la evaluación sin demostrar intervalos iguales. Exploración previa del dataset completo; selección con el mismo test; relaciones sintéticas; sin validación externa, análisis de despliegue ni garantía de uso prospectivo.

**E. Entrada.** “Para interpretar el desempeño, primero necesitamos saber contra qué se comparó y cómo se evaluó.”

**F. Salida.** “El aporte es predictivo dentro del ejercicio; su aplicación real no quedó validada.”

**G. Tiempo.** 0:60 orientativo, seleccionando el bloque pertinente.

**H. Responsable.** Integrante 4.

## 20. Preparación para preguntas

**15 preguntas de defensa.** Respuestas base de aproximadamente 20–40 segundos, para adaptar a la pregunta sin memorizar. Las propuestas sobre información adicional retoman Etapa 10; no se añaden recomendaciones sanitarias.

### 1. ¿Por qué usaron promedio para satisfacción si es ordinal?

“El caso solicitaba ese KPI y en Etapa 9 se incorporó el promedio de 3.56 sobre 5, acompañado de mediana 4 y distribución por niveles. No lo interpretamos como si la distancia entre todas las categorías fuera igual. La distribución y la mediana siguen siendo necesarias: el promedio sirve como resumen solicitado, pero no reemplaza la lectura ordinal.” Fuente: Etapa 9, sección 5; apoyo: diapositiva 4.

### 2. ¿Por qué eligieron 99 minutos?

“Era el tercer cuartil original de las esperas disponibles. El equipo lo adoptó como umbral operacional, incluyendo el valor 99 y manteniéndolo fijo al filtrar. No es un estándar clínico ni un plazo aceptable validado. Además, convertir una duración en una condición binaria pierde información y separa valores cercanos; por eso el score no se interpreta como gravedad.” Fuente: Etapa 6, secciones 2 y 9; backup C.

### 3. ¿Por qué esas tres dimensiones para vulnerabilidad?

“Son una definición acotada a variables disponibles: condición crónica como dimensión de necesidad, falta de acceso a medicación y espera desde el umbral. No existe una etiqueta original de vulnerabilidad. La cronicidad no es por sí sola una barrera y otras condiciones también requieren atención. Los pesos iguales simplifican la descripción; no tienen una calibración clínica ni abarcan todas las necesidades.” Fuente: Etapa 6; backup C.

### 4. ¿Por qué cobertura no forma parte del score?

“La definición acordada cuenta tres dimensiones concretas y reserva cobertura para segmentar. Por eso podemos describir cómo cambia la distribución del score entre coberturas sin asignar un punto automáticamente por pertenecer a una. Eso no demuestra independencia entre cobertura y componentes ni un efecto causal. Describe la función que cumple cada variable en este ejercicio.” Fuente: Etapa 6, secciones 2 y 6; backup C.

### 5. ¿Por qué score 3 no significa alta vulnerabilidad?

“Porque tres expresa cuántas dimensiones de nuestra definición están presentes. No calibramos severidad, no validamos categorías clínicas ni establecimos niveles bajo, medio y alto. Tampoco un score cero significa ausencia de toda dificultad. La suma pierde intensidad y otras dimensiones posibles; su interpretación válida es concurrencia operacional y su uso propuesto es orientar qué segmentos investigar.” Fuente: Etapas 6 y 10; backup C.

### 6. ¿Por qué utilizar Spearman?

“La satisfacción es ordinal y queríamos describir una tendencia monotónica: si las esperas mayores tienden a acompañarse de niveles menores. Spearman trabaja con rangos y permite conservar esa lectura, sin tomar satisfacción como una medición continua con intervalos iguales. Usamos rangos medios para los empates y los 2357 casos con ambas variables disponibles. No interpretamos el coeficiente como porcentaje explicado.” Fuente: Etapa 5, sección 7; backup B.

### 7. ¿Correlación implica causalidad?

“No. Encontramos asociación entre las variables observadas, pero no evaluamos una intervención ni aislamos todos los factores que podrían explicar el patrón. Además, el dataset es ficticio y contiene relaciones incorporadas en su generación. El resultado no permite prometer un cambio determinado de satisfacción al reducir la espera. Lo usamos para contextualizar la experiencia y formular preguntas.” Fuente: Etapas 5 y 10; backup B.

### 8. ¿Por qué Decision Tree?

“Fue seleccionado por un criterio fijado antes de evaluar: sumar los rangos de macro F1, MAE ordinal y errores de dos niveles o más. Obtuvo una suma de 4 frente a 5 del bosque. No elegimos solo por accuracy ni únicamente por facilidad de explicación. El mismo test participó en esa comparación, así que la elección necesita una evaluación independiente para confirmar su desempeño fuera de este ejercicio.” Fuente: Etapa 7, sección 8; backup D.

### 9. ¿Por qué no eligieron Random Forest?

“Random Forest tuvo un porcentaje algo menor de errores grandes: 3.2922% frente a 3.4979%. Pero el árbol obtuvo mejor macro F1 y menor MAE ordinal, y ganó según el criterio conjunto acordado. No afirmamos que un algoritmo sea siempre superior ni hicimos una prueba de superioridad poblacional. El bosque se conserva como comparador y muestra que distintas métricas pueden favorecer estrategias diferentes.” Fuente: Etapa 7, sección 8; backup D.

### 10. ¿Qué significa 96.5% dentro de ±1?

“Que, en el test, aproximadamente el 96.5% de las predicciones del árbol coincidió con el nivel real o se alejó como máximo un nivel. Incluye las exactas, que fueron 50.4115%. No es 96.5% de acierto exacto ni una probabilidad individual. Hubo 17 errores de dos niveles o más. Esa distancia ayuda a describir los fallos, sin demostrar intervalos psicológicos iguales.” Fuente: Etapa 7, sección 9; backup D.

### 11. ¿El modelo podría utilizarse realmente en un hospital?

“El trabajo no valida ese uso. Se entrenó con datos ficticios, no tiene evaluación externa y el test participó en la selección. Además, necesita conocer espera y acceso, cuya disponibilidad temporal no está documentada como escenario prospectivo. No evaluamos despliegue, calibración ni equidad de uso. El resultado muestra estructura predictiva en el ejercicio, pero no constituye una herramienta clínica ni una recomendación individual.” Fuente: Etapa 7, secciones 1 y 13; backup D.

### 12. ¿Se pueden generalizar los resultados a Argentina?

“No. El dataset es ficticio, no tiene un diseño muestral que sustente representatividad y contiene relaciones incorporadas. Sus 2500 registros no convierten los resultados en estimaciones de la población argentina. Las conclusiones describen este archivo y permiten practicar un recorrido de análisis y comunicación. Incluso una asociación estadística marcada conserva esos límites de origen y de alcance.” Fuente: Etapas 1, 5 y 10.

### 13. ¿Qué harían con más datos?

“Retomaríamos las preguntas que quedaron abiertas en Etapa 10: etapas del proceso de espera, capacidad, disponibilidad y continuidad de medicación, obstáculos administrativos y accesibilidad, además de aspectos de experiencia no relevados. Hoy esas dimensiones no están medidas. Para un seguimiento temporal harían falta fuentes comparables y fechas; para sostener el desempeño del modelo, una evaluación independiente. No asumiríamos que los nuevos datos confirman los patrones actuales.” Fuente: Etapa 10, secciones 3–7 y 9.

### 14. ¿Mantener NA en el análisis y luego imputar en el modelo no es contradictorio?

“Son decisiones para tareas distintas. El dataset conserva sus faltantes y los análisis descriptivos usan casos disponibles. El modelo excluye los 72 sin satisfacción y retiene 71 con target pero sin espera; para esos predictores aplica una imputación temporal dentro del pipeline. La mediana se aprende solo en train, también en cada pliegue. No se completó el archivo fuente ni se recuperó el valor verdadero ausente.” Fuente: Etapas 3 y 7; backups A y D.

### 15. ¿Un p-value pequeño demuestra que la diferencia es importante?

“No. El p-value no mide tamaño del efecto ni relevancia práctica. Por eso acompañamos las pruebas con proporciones, medianas y distribuciones; en las asociaciones categóricas usamos V de Cramér. Además, las cinco pruebas fueron exploratorias, sin ajuste por multiplicidad, y la independencia es un supuesto. No inferimos significación de cada par a partir de una prueba global ni convertimos significación en causalidad.” Fuente: Etapa 5, secciones 1, 9 y 11; backup B.

## 21. Control de tiempo

Los doce bloques suman **18:40**, con participación de **4:35 / 4:35 / 4:45 / 4:45**. La demo de **1:15** ya está dentro de los **1:40** de la diapositiva 11 y de los **4:45** del integrante 4. No se suma nuevamente al total. El margen de **1:20** absorbe retrasos breves hasta el máximo de **20:00**.

Las notas son una base para hablar y señalar evidencia, no un texto que deba leerse para llenar cada segundo. Ensayar con las figuras y las pausas previstas, sin agregar análisis, cifras ni conclusiones. Ajustar formulaciones orales si el tiempo real difiere; evitar prolongar la apertura con explicaciones que pertenecen a otras láminas.

| Punto de control | Objetivo acumulado | Si hay retraso |
| --- | ---: | --- |
| Fin del integrante 1 | 4:35 | Acortar la explicación del pipeline; conservar NA y N efectivo |
| Fin del integrante 2 | 9:10 | Señalar el contexto de la matriz sin recorrer cada celda |
| Fin del integrante 3 | 13:55 | Evitar repetir todas las advertencias; conservar significado del score y ausencia de validación |
| Fin de la demo y diapositiva 11 | 17:10 | Restablecer y regresar; no abrir nuevos filtros |
| Cierre | 18:40 | Mantener las cuatro líneas de acción y la frase final |

Si el ensayo se acerca a 20 minutos, reducir la demo a 60 segundos y comentarios secundarios antes de aumentar la velocidad de habla. No recortar denominadores esenciales, límites de interpretación o el cierre. Si la demo falla, utilizar el respaldo real previsto para 11B y continuar. Los backups solo se abren ante preguntas; no forman un segundo cierre.

## 22. Checklist previo a generar el PPTX

**Control de 11A:**

- [x] Exactamente 12 diapositivas principales, cada una con A–H y una idea principal.
- [x] Exactamente 4 backups definidos, con notas para preguntas y fuera del tiempo principal.
- [x] Cuatro integrantes, tres diapositivas por persona y tiempos aproximadamente equitativos.
- [x] Total planificado 18:40, demo incluida, margen 1:20 hasta 20:00.
- [x] Storytelling por preguntas, tres transiciones explícitas y cierre conectado con el encargo.
- [x] PULSO Analytics explícitamente ficticia; cliente genérico; Universidad como identidad principal.
- [x] Dataset ficticio explícito; sin generalización a Argentina ni afirmaciones causales.
- [x] Cifras recuperadas de informes anteriores; aproximaciones de pantalla identificadas y precisión exacta en notas y backup.
- [x] Score 0–3 sin categorías clínicas ni clasificación vulnerable Sí/No; cobertura fuera de fórmula.
- [x] Modelo sin interpretación causal ni validación externa; test usado en selección reconocido.
- [x] Cuatro líneas de acción tomadas de Etapa 10 y vinculadas con la evidencia expuesta.
- [x] Quince preguntas de defensa con respuestas basadas en el trabajo realizado.
- [x] Rutas de figuras y HTML existentes verificadas; ausencia de captura documentada sin inventar ruta.
- [x] Solo se genera este Markdown; sin estadísticas nuevas, gráficos, imágenes, notebooks, datasets, PPTX ni cambios de entregables anteriores.

**Pendientes concretos para 11B y ensayo, no ejecutados en 11A:**

- [ ] Completar los nombres reales de los cuatro integrantes en la portada.
- [ ] Incorporar el logo institucional original y verificar su variante; resolver el magenta exacto sin inventar una especificación oficial.
- [ ] Maquetar tarjetas, pipeline y fórmula con texto; mantener PULSO Analytics como identidad secundaria sin diseñar aquí un logo.
- [ ] Obtener la captura real del HTML existente para la diapositiva 11 y su contingencia estática.
- [ ] Comprobar legibilidad de figuras en proyección y las dos apariciones de la diapositiva 9, sin regenerar gráficos.
- [ ] Ensayar los 75 segundos de demo, el restablecimiento y el regreso inmediato.
- [ ] Cronometrar la exposición completa y ajustar la locución dentro del objetivo de 18:30–19:00.

La Etapa 11A termina con el guion. La construcción del PowerPoint queda para la etapa siguiente.
