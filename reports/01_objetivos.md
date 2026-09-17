# TP1 Salud Pública

## 1. Problemática general

El caso de uso plantea que el acceso a los servicios de salud, la calidad de la atención, los tiempos de espera y la disponibilidad de medicamentos son dimensiones relevantes para la equidad del sistema sanitario. Propone estudiar experiencias de pacientes para identificar desigualdades, evaluar el servicio, detectar poblaciones vulnerables y orientar la asignación de recursos.

Los problemas y dimensiones explícitos son:

- Desigualdades en el acceso a la atención y a la medicación.
- Diferencias en los tiempos de espera según la cobertura de salud.
- Relación de la espera y del acceso a medicación con la satisfacción.
- Diferencias en la frecuencia de atención según la condición de salud.
- Identificación de grupos vulnerables.
- Evaluación del sistema y propuestas de mejora, con segmentación por región, cobertura y condición de salud.

Estos son problemas planteados por el documento: todavía no se comprobó su manifestación en el archivo. El dataset es ficticio y no constituye evidencia sobre la población real.

**Fuentes utilizadas:** “Salud Publica Caso de uso G7.pdf”, páginas 1–2, y “Consignas para la presentacion TP-parcial 1 2cuat2026.pdf”, página 1. Ambos se encontraron en la raíz del proyecto, al igual que el Excel, en lugar de las rutas `docs/` y `data/raw/` indicadas en el pedido. No se movieron los archivos.

## 2. Objetivo del análisis

El objetivo general explícito del caso es analizar patrones de atención, evaluar el sistema de salud y generar propuestas de mejora a partir de un dataset ficticio de 2500 pacientes.

Para el proyecto, se propone estudiar cómo varían la espera, el acceso a medicación, la frecuencia de atención y la satisfacción entre perfiles de pacientes, para aportar criterios a la discusión de equidad y mejora del servicio. La identificación de vulnerabilidad y los objetivos de modelado requieren definiciones posteriores.

Las actividades solicitadas se organizan de la siguiente manera. Se documentan para etapas futuras; no se ejecutan en esta etapa.

| Categoría                            | Actividades indicadas                                                                                                                                                                            | Fuente                              |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------- |
| Análisis exploratorio                | Examinar la distribución de tipos de cobertura y el promedio del tiempo de espera por sistema. La correspondencia entre “sistema” y `Cobertura_Salud` deberá explicitarse.                       | Caso, p. 2, nivel 1                 |
| Análisis de relaciones               | Estudiar tiempo de espera frente a satisfacción y cobertura frente a acceso a medicación.                                                                                                        | Caso, p. 2, nivel 2                 |
| Identificación de grupos vulnerables | Identificar grupos vulnerables; el documento no establece un criterio operacional.                                                                                                               | Caso, p. 2, nivel 2                 |
| BI / dashboard                       | KPI sugeridos: tiempo promedio de espera, porcentaje de acceso a medicación y satisfacción promedio. Segmentar por región, tipo de cobertura y condición de salud.                               | Caso, p. 2, nivel 3                 |
| Modelado                             | Predecir satisfacción, detectar riesgo de mala atención y clasificar pacientes vulnerables. Los dos últimos objetivos requieren definir qué resultado se pretende identificar.                   | Caso, p. 2, nivel 4                 |
| Presentación de resultados           | Elaborar una presentación con conclusiones; presentar tema, problemática, problemas y actividades; justificar las visualizaciones; comunicar hallazgos y sugerencias para la toma de decisiones. | Caso, p. 2, nivel 5; consigna, p. 1 |

La consigna fija entrega final el lunes 28 de septiembre de 2026, por un integrante mediante correo electrónico desde el campus. Las exposiciones comienzan el miércoles 30 de septiembre, con orden aleatorio: 20 minutos de exposición y 10 de preguntas, con participación equitativa de todos los integrantes. Permite elegir entre PowerPoint, Google Slides, Canva, Mentimeter, Genially y Prezi. Evalúa diseño, contenido relacionado con la materia, estrategia comunicacional, claridad, disertación individual y cumplimiento del tiempo; contempla una nota grupal y otra individual.

## 3. Dataset disponible

- **Archivo examinado:** `dataset_salud_publica_2500.xlsx`, ubicado en la raíz.
- **Formato:** libro Excel con una hoja, denominada `Salud Publica`.
- **Estructura declarada por la hoja:** rango `A1:J2501`, con diez encabezados en la primera fila y espacio para 2500 filas de datos. Esto es consistente con los 2500 registros descritos por el caso; no verifica completitud ni unicidad.
- **Unidad de observación según el caso:** cada fila representa la experiencia de un paciente en el sistema de salud.
- **Origen según el caso:** datos ficticios con relaciones incorporadas intencionalmente.
- **Contenido general:** identificación, características demográficas, condición y cobertura de salud, frecuencia de atención, espera, acceso a medicación y satisfacción.
- **Alcance de esta revisión:** lectura de documentos, metadatos del libro, dimensiones de la hoja y encabezados. No se calcularon estadísticas ni se inspeccionaron distribuciones, faltantes, duplicados, rangos observados o calidad de los registros.

Los nombres de las columnas se verificaron en el Excel. Los significados, unidades y categorías que siguen provienen del caso, salvo las limitaciones expresamente indicadas. Los tipos conceptuales no equivalen a tipos de almacenamiento verificados. Las categorías documentadas tampoco se presentan como valores observados.

## 4. Diccionario de variables

| Nombre real de columna | Significado y dominio documentado                                                                                               | Tipo conceptual                                                                      | Posibles usos analíticos posteriores                                                                                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ID_Paciente`          | Identificador del paciente. No se documentan formato ni garantía de unicidad.                                                   | Identificador nominal, sin magnitud cuantitativa.                                    | Trazabilidad y futura revisión de identificación/unicidad; no representa una característica explicativa de salud.                                                                          |
| `Region`               | Región del paciente. El caso enumera Norte, Centro, Sur, CABA y Buenos Aires, sin precisar delimitaciones geográficas.          | Cualitativa nominal.                                                                 | Segmentar indicadores y comparar diferencias territoriales en atención y acceso.                                                                                                           |
| `Edad`                 | Edad del paciente. No se explicitan unidad, rango ni forma de registro.                                                         | Cuantitativa; carácter discreto o continuo pendiente de precisar.                    | Describir el perfil etario y estudiar diferencias en las experiencias de atención.                                                                                                         |
| `Genero`               | Género del paciente. No se enumeran categorías ni codificación.                                                                 | Cualitativa nominal.                                                                 | Describir la composición y explorar diferencias en acceso y atención.                                                                                                                      |
| `Condicion_Salud`      | Condición de salud: Saludable, Crónica o Aguda.                                                                                 | Cualitativa nominal; no implica una escala de gravedad documentada.                  | Comparar frecuencia de atención, acceso a medicación y satisfacción; discutir necesidades diferenciadas.                                                                                   |
| `Cobertura_Salud`      | Cobertura de salud: Pública, Privada o Sin cobertura.                                                                           | Cualitativa nominal.                                                                 | Comparar espera y acceso a medicación; segmentar indicadores y explorar desigualdades.                                                                                                     |
| `Frecuencia_Atencion`  | Cantidad de consultas anuales, según el caso.                                                                                   | Cuantitativa discreta de conteo.                                                     | Describir utilización de servicios y su relación con la condición de salud.                                                                                                                |
| `Tiempo_Espera_min`    | Tiempo de espera en minutos. No se especifica el punto de inicio/fin ni si corresponde a una atención o a un resumen de varias. | Cuantitativa de duración, conceptualmente continua; precisión de registro pendiente. | Comparar espera por cobertura y región; estudiar su relación con satisfacción; KPI sugerido.                                                                                               |
| `Acceso_Medicacion`    | Acceso a medicación, documentado como Sí/No. No se define período ni si distingue falta de necesidad de falta de acceso.        | Cualitativa nominal dicotómica.                                                      | Estudiar acceso por cobertura y condición; calcular posteriormente el KPI de porcentaje de acceso una vez definido su denominador.                                                         |
| `Satisfaccion`         | Nivel de satisfacción en una escala de 1 a 5. No se detallan las etiquetas de cada nivel.                                       | Cualitativa ordinal expresada con números.                                           | Describir satisfacción, relacionarla con espera y medicación y considerar su predicción. El caso sugiere un promedio, cuyo uso deberá justificarse por la naturaleza ordinal de la escala. |

## 5. Relaciones incorporadas en el dataset

**Son relaciones declaradas por el caso de uso (pp. 1–2), incorporadas al dataset ficticio. No son hallazgos del análisis, resultados estadísticos ni evidencia causal.** Su expresión concreta y su intensidad en el archivo no se evaluaron.

| Relación declarada                          | Descripción proporcionada por el caso                                                                                                                         | Columnas correspondientes                                 |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| Condición de salud → frecuencia de atención | Crónica: más consultas; Aguda: consultas intermedias; Saludable: pocas consultas.                                                                             | `Condicion_Salud`, `Frecuencia_Atencion`                  |
| Cobertura → tiempo de espera                | Privada: menor espera; Pública: mayor espera; Sin cobertura: mayor dificultad. “Mayor dificultad” no viene acompañada de una medida ni de un tiempo concreto. | `Cobertura_Salud`, `Tiempo_Espera_min`                    |
| Cobertura + condición → acceso a medicación | Privada: mayor acceso; Sin cobertura: menor acceso; crónicos: más dificultad. No especifica todos los cruces de categorías.                                   | `Cobertura_Salud`, `Condicion_Salud`, `Acceso_Medicacion` |
| Tiempo de espera + acceso → satisfacción    | Mayor espera: menor satisfacción; sin medicación: fuerte caída en satisfacción. No cuantifica la caída.                                                       | `Tiempo_Espera_min`, `Acceso_Medicacion`, `Satisfaccion`  |

## 6. Preguntas analíticas

Las siguientes preguntas se derivan de los documentos y de las columnas disponibles. Son propuestas para intentar responder posteriormente, sujetas a la auditoría del dataset y a las decisiones del equipo. No presuponen resultados.

### 6.1 Descriptivas

| Pregunta / qué queremos conocer                                                                                                 | Variables involucradas                 | Relevancia para el problema                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- | -------------------------------------------------------------------------------------------------- |
| D1. ¿Cómo se distribuyen las experiencias registradas entre tipos de cobertura y regiones? Conocer la composición del conjunto. | `Cobertura_Salud`, `Region`            | Contextualizar las comparaciones de acceso y la segmentación territorial propuesta.                |
| D2. ¿Cuál es el perfil de edad, género y condición de salud de los pacientes representados?                                     | `Edad`, `Genero`, `Condicion_Salud`    | Comprender a quiénes describen los indicadores y las necesidades de atención representadas.        |
| D3. ¿Cómo se distribuye el tiempo de espera y cuál es su promedio por cobertura?                                                | `Tiempo_Espera_min`, `Cobertura_Salud` | Caracterizar una dimensión de calidad del servicio y cumplir la actividad exploratoria explícita.  |
| D4. ¿Qué proporción registra acceso a medicación, en total y por región?                                                        | `Acceso_Medicacion`, `Region`          | Describir el acceso y preparar uno de los KPI sugeridos.                                           |
| D5. ¿Cómo se distribuyen los niveles de satisfacción?                                                                           | `Satisfaccion`                         | Caracterizar la valoración de la experiencia de atención sin anticipar umbrales de insatisfacción. |
| D6. ¿Cómo se distribuye la cantidad de consultas anuales?                                                                       | `Frecuencia_Atencion`                  | Describir utilización del servicio como contexto para discutir recursos.                           |

### 6.2 Relaciones

| Pregunta / qué queremos conocer                                                                                       | Variables involucradas                                                                                   | Relevancia para el problema                                                              |
| --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| R1. ¿Qué asociación se observa entre tiempo de espera y satisfacción?                                                 | `Tiempo_Espera_min`, `Satisfaccion`                                                                      | Examinar una actividad explícita y una relación declarada de la experiencia de atención. |
| R2. ¿Cómo varía el acceso a medicación entre coberturas?                                                              | `Cobertura_Salud`, `Acceso_Medicacion`                                                                   | Examinar desigualdades de acceso y la relación solicitada en el nivel 2.                 |
| R3. ¿Cómo varía la frecuencia de atención según la condición de salud?                                                | `Condicion_Salud`, `Frecuencia_Atencion`                                                                 | Examinar el patrón de utilización que el caso declara haber incorporado.                 |
| R4. ¿Cómo se relacionan conjuntamente cobertura y condición de salud con el acceso a medicación?                      | `Cobertura_Salud`, `Condicion_Salud`, `Acceso_Medicacion`                                                | Considerar diferencias de acceso en perfiles con distintas necesidades de atención.      |
| R5. ¿Cómo cambia la satisfacción según el acceso a medicación al considerar también el tiempo de espera?              | `Acceso_Medicacion`, `Tiempo_Espera_min`, `Satisfaccion`                                                 | Examinar conjuntamente las dos dimensiones vinculadas con satisfacción en el caso.       |
| R6. ¿Qué diferencias de espera, acceso y satisfacción aparecen entre regiones al segmentar por cobertura y condición? | `Region`, `Cobertura_Salud`, `Condicion_Salud`, `Tiempo_Espera_min`, `Acceso_Medicacion`, `Satisfaccion` | Orientar la comparación territorial propuesta para el dashboard.                         |

### 6.3 Vulnerabilidad

Estas preguntas exploran posibles situaciones desfavorables. No asignan una condición de “vulnerable”, no establecen una regla y no anticipan qué grupos lo serían.

| Pregunta / qué queremos conocer                                                                                                      | Variables involucradas                                                                                   | Relevancia para el problema                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| V1. ¿Qué combinaciones de cobertura y condición presentan menor proporción de acceso a medicación?                                   | `Cobertura_Salud`, `Condicion_Salud`, `Acceso_Medicacion`                                                | Aportar evidencia futura a la discusión sobre barreras de acceso y necesidades de salud.                                 |
| V2. ¿En qué perfiles de región, cobertura y condición coinciden comparativamente mayores esperas, menor acceso y menor satisfacción? | `Region`, `Cobertura_Salud`, `Condicion_Salud`, `Tiempo_Espera_min`, `Acceso_Medicacion`, `Satisfaccion` | Explorar la concurrencia de dificultades en las dimensiones del caso, sin fijar cortes ni etiquetas.                     |
| V3. ¿Existen diferencias de espera y acceso asociadas con edad o género dentro de las coberturas y condiciones de salud?             | `Edad`, `Genero`, `Cobertura_Salud`, `Condicion_Salud`, `Tiempo_Espera_min`, `Acceso_Medicacion`         | Explorar posibles desigualdades entre perfiles disponibles, sin asumir que una edad o un género implique vulnerabilidad. |

### 6.4 Modelado

| Pregunta / qué queremos conocer                                                                                                                             | Variables involucradas                                                                                                                                                                                                                                                    | Relevancia para el problema                                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| M1. ¿Hasta qué punto podría predecirse el nivel de satisfacción a partir de la espera y el acceso a medicación, considerando cobertura, condición y región? | Objetivo: `Satisfaccion`. Candidatas: `Tiempo_Espera_min`, `Acceso_Medicacion`, `Cobertura_Salud`, `Condicion_Salud`, `Region`.                                                                                                                                           | Corresponde al objetivo explícito de predecir satisfacción y podría ayudar a estudiar factores asociados con la experiencia del servicio.                                    |
| M2. Una vez definido “mala atención”, ¿podría identificarse su riesgo con las variables disponibles?                                                        | No existe una variable objetivo directa. Para discutir el concepto: `Tiempo_Espera_min`, `Acceso_Medicacion`, `Satisfaccion`. Posibles variables de contexto: `Region`, `Edad`, `Genero`, `Cobertura_Salud`, `Condicion_Salud`, `Frecuencia_Atencion`. Roles por decidir. | Atiende al objetivo de detectar riesgo de mala atención, cuya factibilidad depende de una definición y del momento de predicción.                                            |
| M3. Si el equipo acuerda una definición y dispone de una etiqueta válida, ¿podría clasificarse la vulnerabilidad con los datos disponibles?                 | No existe una etiqueta directa. Variables a discutir: `Region`, `Edad`, `Genero`, `Condicion_Salud`, `Cobertura_Salud`, `Frecuencia_Atencion`, `Tiempo_Espera_min`, `Acceso_Medicacion`, `Satisfaccion`. Roles por decidir.                                               | Retoma la clasificación solicitada sin inventar una definición. Deberá distinguirse entre aprender una clasificación y reproducir una regla creada con las mismas variables. |

La disponibilidad de estas columnas no garantiza viabilidad predictiva. No se eligieron algoritmos, objetivos derivados ni particiones de datos.

## 7. Decisiones pendientes

**Concepto de paciente vulnerable**

- **¿Existe una variable que lo defina directamente?** No. Ninguno de los diez encabezados corresponde a vulnerabilidad ni a una etiqueta equivalente documentada.
- **¿La consigna ofrece una definición operacional?** No. La consigna regula la presentación; el caso propone identificar grupos y clasificar pacientes vulnerables, pero no fija criterios, umbrales ni una etiqueta de referencia.
- **¿Qué variables podrían estar relacionadas?** Cobertura, condición de salud y acceso a medicación son candidatas por las dificultades descritas en el caso. Espera y satisfacción podrían caracterizar experiencias desfavorables; frecuencia de atención puede aportar contexto de utilización, sin equivaler por sí misma a necesidad insatisfecha. Región, edad y género permiten explorar diferencias entre perfiles, sin suponer que alguna categoría sea vulnerable.
- **¿Qué debe resolver el equipo?** Qué dimensión de vulnerabilidad pretende estudiar, si la unidad será el paciente o un grupo, qué fundamento tendrá su definición y cómo la distinguirá de insatisfacción o mala atención. No se propone aquí una regla ni se crea una columna `Vulnerable`.

**Otras decisiones y aclaraciones antes de la auditoría**

| Tema pendiente                          | Qué debe acordarse o confirmarse                                                                                                                                                                                                                                                  |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Significado y alcance de las mediciones | Unidad y registro de edad; categorías de género; delimitación de regiones; significado concreto de la espera y del acceso a medicación; etiquetas de satisfacción. Los documentos no precisan estos aspectos.                                                                     |
| Unidad y referencia temporal            | Confirmar el alcance de “experiencia de un paciente”, la expectativa de unicidad del ID y el período de referencia de las variables. Solo la frecuencia se describe como anual; no hay columna de fecha.                                                                          |
| Cobertura y “sistema”                   | Explicitar si los promedios “por sistema” se calcularán por `Cobertura_Salud` y cómo se interpretará “Sin cobertura” respecto del acceso al sistema público.                                                                                                                      |
| Mala atención                           | Definir qué significa y cómo se observaría; no hay etiqueta directa ni definición operacional. No equipararla automáticamente con satisfacción baja.                                                                                                                              |
| Indicadores                             | Acordar denominadores, tratamiento futuro de registros no válidos y justificación del promedio de una escala ordinal, aunque esté sugerido en el caso.                                                                                                                            |
| Segmentaciones                          | Decidir si hacen falta grupos etarios u otras agrupaciones y con qué fundamento. No se fijan cortes en esta etapa.                                                                                                                                                                |
| Modelado                                | Definir objetivo, momento de predicción y variables disponibles en ese momento. Evitar usar como predictores información que define la etiqueta o que no estaría disponible al predecir. Aclarar con la cátedra el alcance esperado de los niveles propuestos si fuera necesario. |
| Alcance de las conclusiones             | Mantener las conclusiones dentro del ejercicio ficticio. No hay columnas de costos, dotación, establecimientos ni fechas para estimar directamente presupuestos, capacidad o evolución temporal; las propuestas de recursos deberán reconocer esas limitaciones.                  |
| Organización del proyecto y entrega     | Acordar si más adelante se adoptarán las carpetas previstas; elegir herramienta de presentación y distribuir participación y tiempos. En esta etapa se conservan las ubicaciones originales.                                                                                      |

La auditoría posterior deberá contrastar la estructura documentada con los datos efectivos. En esta etapa no se diagnosticaron problemas de calidad ni se adoptaron decisiones de limpieza.

## 8. Pregunta general del proyecto

**¿Cómo varían los tiempos de espera, el acceso a medicación y la satisfacción según la cobertura, la condición de salud y la región en este dataset ficticio, y qué diferencias podrían orientar propuestas de mejora de la equidad en la atención e identificar posibles grupos vulnerables, una vez acordada su definición?**

Esta pregunta conecta las actividades descriptivas, de relaciones, segmentación y presentación, y deja abierta una etapa de modelado si se acuerdan objetivos válidos. No presupone desigualdades comprobadas ni una definición de vulnerabilidad.
