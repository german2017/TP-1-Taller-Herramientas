# Etapa 9 - Dashboard interactivo

## 1. Objetivo

Comunicar tiempos de espera, acceso a medicación, satisfacción e Índice operacional de vulnerabilidad en el acceso y la atención mediante una página interactiva. Se leyeron los informes de Etapas 1–8 antes de construirla.

La consigna de Etapa 9 resuelve las decisiones pendientes de selección: cinco gráficos, cuatro KPIs, satisfacción promedio acompañada de mediana y distribución, y exclusión del modelado. No se modifican retrospectivamente los informes anteriores ni se elaboran recomendaciones o presentación.

## 2. Arquitectura

Python lee el Excel y genera un único HTML UTF-8 con Plotly JS, estilos, datos JSON y lógica JavaScript embebidos. Al cambiar un filtro se seleccionan registros, se recalculan KPIs y agregaciones y se actualizan las cinco vistas mediante Plotly.react(). No se precalculan todas las combinaciones.

La documentación oficial respalda la [exportación autocontenida de Plotly](https://plotly.com/python/interactive-html-export/) y la [actualización mediante Plotly.react](https://plotly.com/javascript/plotlyjs-function-reference/). Estos enlaces son referencias de este informe, no dependencias del HTML.

El [notebook reproducible](../notebooks/09_dashboard.ipynb) contiene carga, controles globales, plantilla completa, lógica JavaScript, pruebas independientes en pandas y navegador, y generación de este informe. Para reproducir y validar se requieren Python, pandas, openpyxl, plotly, nbformat, playwright y un navegador compatible. Chrome o Edge instalado se detectan automáticamente; alternativamente puede instalarse Chromium de Playwright. La prueba se ejecuta en un hilo separado para convivir con el bucle de eventos de Jupyter. Ninguna de estas herramientas es requerida por quien abre el HTML.

## 3. Fuente de datos

Se utiliza exclusivamente data/analysis/dataset_salud_vulnerabilidad.xlsx: 2500 filas × 14 columnas. Se conserva intacto el archivo y se leen sus scores preexistentes sin volver a calcular dimensiones, umbrales ni reglas.

El HTML incluye los 2500 registros con siete campos necesarios: Region, Cobertura_Salud, Condicion_Salud, Tiempo_Espera_min, Acceso_Medicacion, Satisfaccion y Score_Vulnerabilidad. No incorpora ID_Paciente ni campos ajenos a las vistas. Los NA se serializan como null; no se convierten en cero.

## 4. Filtros

Selectores combinables de Region, Cobertura_Salud y Condicion_Salud, todos inicialmente en “Todas”, con botón “Restablecer filtros”. Se usa intersección de condiciones: cada registro debe cumplir todos los filtros activos. Una cobertura específica conserva la pregunta del gráfico de espera y muestra una única barra.

Los KPIs, cinco gráficos, denominadores, notas de casos no disponibles y tablas desplegables se actualizan conjuntamente. Una selección vacía muestra “Sin datos para la selección”, sin divisiones por cero ni errores JavaScript. Los selectores usan categorías reales; el caso vacío se comprueba mediante una llamada de prueba al mismo renderizador.

## 5. KPIs

| KPI                       | Resultado global | Denominador / complemento         |
| ------------------------- | ---------------- | --------------------------------- |
| Registros                 | 2500             | Todos los registros seleccionados |
| Tiempo promedio de espera | 64.58 min        | N=2426; mediana=54 min            |
| Acceso a medicación       | 67.80%           | Sí / acceso observable; N=2500    |
| Satisfacción promedio     | 3.56 / 5         | N=2428; mediana=4 / 5             |

**Satisfacción promedio global calculada para este KPI:** 3.564250411862 / 5. Se muestra redondeada a 3,56 / 5. Esta incorporación está autorizada expresamente en Etapa 9; no sustituye la mediana ni presupone intervalos iguales entre categorías. La nota ordinal se mantiene visible inmediatamente debajo de las tarjetas.

## 6. Visualizaciones

| Vista                            | Tipo                                      | Denominador reactivo                             | Información accesible                                     |
| -------------------------------- | ----------------------------------------- | ------------------------------------------------ | --------------------------------------------------------- |
| Espera por cobertura             | Barras                                    | Espera observable en cada cobertura              | Promedio, mediana y N válido                              |
| Acceso por cobertura y condición | Heatmap                                   | Acceso observable en cada combinación            | Porcentaje Sí, cantidad Sí, N válido y N del grupo        |
| Distribución de satisfacción     | Barras ordenadas 1–5                      | Satisfacción observable del filtro               | Nivel, cantidad, porcentaje y N válido                    |
| Acumulación por cobertura        | Barras apiladas al 100%; score 0–3        | Score observable en cada cobertura               | Score, cantidad, porcentaje y N de cobertura              |
| Satisfacción según acumulación   | Barras apiladas al 100%; satisfacción 1–5 | Ambas variables observables dentro de cada score | Score, nivel, cantidad, porcentaje, N y mediana del score |

Se utilizan paletas consistentes para satisfacción y score, leyendas ordenadas, porcentajes y tooltips. Las tablas desplegables brindan una alternativa al color y permiten consultar categorías con frecuencia cero. Las celdas sin denominador válido se muestran sin porcentaje, no como 0%. Los porcentajes se recalculan desde conteos, no desde cifras globales redondeadas.

La página tiene fondo claro, tarjetas, separación entre bloques y adaptación a escritorio y móvil. Se verificó a 1440 y 390 píxeles de ancho, sin desbordamiento horizontal de la página. Las leyendas no ocultan segmentos al pulsarlas: se preserva la lectura de distribuciones completas al 100%.

## 7. Tratamiento de NA

Los 74 NA de espera y 72 de satisfacción permanecen ausentes. El score conserva 74 NA. Cada KPI excluye únicamente ausencias de su propia variable; acceso usa respuestas Sí/No observables. El gráfico conjunto exige score y satisfacción, con N global=2357 y 143 registros sin alguna de ambas variables.

Un NA no se interpreta como score 0, satisfacción 0 o falta de acceso. Las medias, medianas, porcentajes y N válidos se calculan sobre el subconjunto actual. Cuando no hay observables, se presenta “Sin datos”; una categoría con observables pero cero casos del nivel sí conserva porcentaje cero.

## 8. Índice operacional

Se mantiene el nombre **Índice operacional de vulnerabilidad en el acceso y la atención**. Score 0–3 significa cantidad de dimensiones operacionales: condición crónica, falta de acceso a medicación y espera ≥99 minutos. El umbral es el Q3 original y permanece fijo al filtrar.

No se crea una clasificación binaria ni categorías de gravedad. El índice no es una escala clínica; la asociación con satisfacción no implica causalidad ni validación clínica. La cobertura solo segmenta; no se incorpora a la fórmula.

## 9. Validación sin filtros

La referencia independiente en pandas reproduce las cifras anteriores con tolerancia de 0.005 para valores publicados con dos decimales. Se compara además toda la estructura de agregaciones JavaScript con pandas, con tolerancia numérica de 1e-9 absoluta o 1e-10 relativa.

| Control                                         | Resultado                  | Estado   |
| ----------------------------------------------- | -------------------------- | -------- |
| Registros                                       | 2500                       | APROBADO |
| Espera: N / media / mediana                     | 2426 / 64.58079143 / 54    | APROBADO |
| Acceso: N / Sí (%)                              | 2500 / 67.80               | APROBADO |
| Satisfacción: N / media / mediana               | 2428 / 3.564250411862 / 4  | APROBADO |
| Score: N / frecuencias 0,1,2,3                  | 2426 / 904, 937, 471, 114  | APROBADO |
| Score y satisfacción: N                         | 2357                       | APROBADO |
| Espera media: Privada / Pública / Sin cobertura | 17.60 / 70.19 / 106.11 min | APROBADO |
| Acceso: Privada-Aguda / Sin cobertura-Crónica   | 89.22% / 41.99%            | APROBADO |
| Score 3: Privada / Pública / Sin cobertura      | 0.00% / 3.09% / 10.90%     | APROBADO |
| Mediana satisfacción por score 0,1,2,3          | 4 / 4 / 3 / 2              | APROBADO |

## 10. Validación de filtros

Se accionaron los selectores reales en Chrome/Chromium headless, con red deshabilitada, y se compararon las filas seleccionadas con pandas en contenido y orden. Se verificaron todos los KPIs, N válidos, cinco agregaciones y los datos efectivamente entregados a los cinco gráficos. Ningún registro fuera de la selección participó.

| Prueba | Selección                | Registros | N espera | N acceso | N satisfacción | N score | N conjunto | Estado   |
| ------ | ------------------------ | --------: | -------: | -------: | -------------: | ------: | ---------: | -------- |
| A      | CABA                     |       498 |      479 |      498 |            480 |     479 |        463 | APROBADO |
| B      | Pública                  |       806 |      777 |      806 |            780 |     777 |        752 | APROBADO |
| C      | Crónica                  |       843 |      824 |      843 |            820 |     824 |        802 | APROBADO |
| D      | CABA / Pública / Crónica |        41 |       41 |       41 |             38 |      41 |         38 | APROBADO |

Cada distribución con denominador positivo suma aproximadamente 100% antes del redondeo. Para grupos sin observables, los porcentajes son null. Se verificaron también reset a 2500 registros, estado vacío, grupo de prueba con todas las variables descriptivas ausentes, tooltips y diseño responsive. El grupo artificial se usa únicamente en la función de prueba; no se agrega al HTML ni al dataset.

## 11. Portabilidad

| Control                                    | Resultado                                           |
| ------------------------------------------ | --------------------------------------------------- |
| HTML                                       | outputs/dashboard/dashboard_salud.html              |
| Tamaño                                     | 5278162 bytes (5.03 MiB)                            |
| Plotly JS                                  | Embebido íntegramente                               |
| Datos                                      | JSON embebido: 2500 registros × 7 campos necesarios |
| Recursos externos de HTML                  | 0                                                   |
| Solicitudes HTTP/HTTPS al abrir y filtrar  | 0                                                   |
| Errores JavaScript                         | 0                                                   |
| Apertura                                   | Archivo local con navegador offline, sin servidor   |
| Dependencia de Excel o notebook para abrir | Ninguna                                             |
| Reset y cinco gráficos                     | APROBADOS                                           |
| Política de red                            | connect-src 'none'; recursos externos bloqueados    |

**Búsqueda explícita de referencias:**

| Texto buscado | Apariciones en HTML | Interpretación                                                            |
| ------------- | ------------------: | ------------------------------------------------------------------------- |
| http://       |                  20 | Solo dentro del bundle Plotly; no usado como dependencia por estas vistas |
| https://      |                  55 | Solo dentro del bundle Plotly; no usado como dependencia por estas vistas |
| cdn.plot.ly   |                   1 | Solo dentro del bundle Plotly; no usado como dependencia por estas vistas |
| file://       |                   2 | Solo dentro del bundle Plotly; no usado como dependencia por estas vistas |
| localhost     |                   0 | Ausente                                                                   |
| 127.0.0.1     |                   0 | Ausente                                                                   |

Los literales HTTP/HTTPS y cdn.plot.ly pertenecen al código y referencias internas de la biblioteca completa, incluidas funciones ajenas a estas vistas; no todos son texto documental. Los literales file:// también pertenecen al bundle y no apuntan a archivos del proyecto. No hay atributos externos src/href ni referencias a XLSX o notebook. La plantilla propia, los datos y la lógica del dashboard no requieren ninguna de esas direcciones.

Además de la inspección estática se probó apertura directa por URI local, con el contexto del navegador offline, filtros y reset. No se registró ninguna solicitud HTTP/HTTPS. La política de contenido bloquea conexiones de red; las cinco vistas usan barras y heatmap, sin mapas, servicios externos ni fuentes remotas. Por ello la presencia de literales internos del bundle no representa una dependencia funcional.

Para compartir: entregar únicamente el HTML y abrirlo con doble clic en un navegador moderno. La vista previa de GitHub o de algunos clientes de correo puede no ejecutar JavaScript: descargar el archivo y abrirlo en el navegador.

## 12. Limitaciones

Los datos son ficticios y las asociaciones descriptivas no establecen causalidad ni representan la población real. Filtrar puede producir grupos pequeños; se muestran sus N, sin asignar umbrales ni etiquetas nuevas. Los valores faltantes tienen mecanismo desconocido. El promedio de satisfacción es un KPI solicitado sobre una variable ordinal y debe leerse con sus complementos.

El HTML incorpora la información necesaria para explorar los 2500 registros; es una copia estática de la fuente al generarlo. Cambios posteriores en el Excel requieren regeneración con el notebook. La biblioteca completa aumenta el tamaño a favor de portabilidad offline.

Las únicas advertencias técnicas son los literales de URL internos del bundle y la necesidad de descargar el HTML para ejecutarlo fuera de visores que bloquean scripts. No hay errores funcionales en las pruebas realizadas. No se incluyeron modelado, pruebas inferenciales, recomendaciones ni presentación.

**Integridad:** todos los archivos anteriores conservaron su SHA-256. Fuente analítica: 62f99797abe3dfc926cdc59a54b953346a1db83b16da930d47b2d5286d1af9c5.

Entorno de generación: Python 3.12.3, pandas 3.0.5, Plotly Python 7.1.0.
