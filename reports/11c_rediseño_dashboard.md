# Etapa 11C - Unificación visual del dashboard, versión 2

## 1. Entregables y conservación de la versión anterior

Se creó [dashboard_salud_v2.html](../outputs/dashboard/dashboard_salud_v2.html) a partir del HTML existente. La instrucción de crear una versión 2 prevalece sobre la actualización del archivo original planteada en el texto adjunto.

- Versión anterior conservada, sin modificaciones: [dashboard_salud.html](../outputs/dashboard/dashboard_salud.html).
- Copia de respaldo creada porque no existía: [dashboard_salud_original.html](../outputs/dashboard/dashboard_salud_original.html).
- Captura real para la presentación: [dashboard_salud_presentacion.png](../outputs/dashboard/dashboard_salud_presentacion.png).
- Informe: `reports/11c_rediseño_dashboard.md`.

El HTML anterior y su respaldo tienen el mismo SHA-256: `1d20b6dd75ba349a28bebec64555107de4fd62be99ef99cacc4805e93ee57497`.

No se modificaron la presentación, datasets, notebooks, gráficos anteriores ni informes previos. La versión 2 conserva exactamente el bloque JSON de los 2500 registros y el código embebido de Plotly. No se reconstruyó el dashboard desde cero.

## 2. Referencia visual y paleta

Se inspeccionó el archivo real `C:/Users/Germán/Downloads/TP1_Salud_Publica_PULSO_Analytics_sin_ficticio.pptx`: colores y propiedades tipográficas de sus diapositivas, su layout compartido y sus imágenes. Los códigos siguientes provienen del PPTX, sin inferir una especificación institucional ajena al archivo.

| Color | Procedencia en la presentación | Uso en la versión 2 |
| --- | --- | --- |
| `#B2388D` | Título SALUD PÚBLICA y acentos de diapositivas | Título, acentos KPI, foco de controles y encabezados de sección |
| `#632575` | Identidad secundaria y destacados | Botón secundario, filtros activos, enlaces a tablas y notas metodológicas |
| `#24272C` | Texto principal | Texto y etiquetas Plotly |
| `#384355` | Franja superior del layout y panel de portada | Línea institucional superior, títulos de sección y valores KPI |
| `#666A73` | Textos secundarios | Etiquetas, denominadores y notas |
| `#F7F7F8` | Fondo del layout compartido | Fondo general |
| `#FFFFFF` | Superficies claras | Tarjetas, paneles y controles |
| `#D7D9DE` | Bordes de elementos | Contornos suaves y separadores |
| `#F2E8F1` | Destacados claros | Estado visual de filtro seleccionado y hover del botón |
| `#F0EDF3` | Superficies secundarias | Notas metodológicas |
| `#F0F1F3` | Grises claros de apoyo | Grillas y separadores discretos |

La presentación utiliza Aptos Display en títulos y Aptos en elementos del layout. El dashboard solicita esas fuentes locales, con equivalentes Segoe UI y Arial cuando no están instaladas. No descarga ni incorpora fuentes remotas. Las sombras mínimas son transparencias del color oscuro, no efectos tridimensionales ni degradados de fondo.

## 3. Logos e identidad

**Logo PULSO Analytics encontrado: sí, embebido en la presentación definitiva.** No había un archivo independiente del logo en el proyecto. La imagen de portada tiene la descripción `pulso_analytics_logo_cropped.png` y se resuelve mediante la relación de `ppt/slides/slide1.xml` a `ppt/media/image1.png`.

El logo de Universidad de la Ciudad también se recuperó del PPTX: `ppt/media/image-1002-1.png`, referenciado desde `ppt/slideLayouts/slideLayout2.xml`. Ambos recursos se inspeccionaron y se incorporaron en el HTML como imágenes PNG Base64, sin alterar sus bytes ni proporciones.

La Universidad encabeza la identidad institucional mediante logo, nombre y materia; PULSO Analytics acompaña en una posición secundaria. Su PNG se integra sobre un contenedor blanco y se escala con `height:auto`, sin recorte destructivo ni nuevo diseño. El original del PPTX permanece intacto.

La cabecera comunica SALUD PÚBLICA, Análisis de acceso y experiencia de atención, Universidad de la Ciudad de Buenos Aires y Herramientas de Análisis de Datos. Conforme a la consigna, la versión 2 omite las referencias textuales a “ficticio/ficticia” de la cabecera y de la primera frase metodológica. Se conservan las aclaraciones de no representatividad poblacional, ausencia de causalidad, naturaleza ordinal de satisfacción y carácter no clínico del índice. No se modifican resultados ni interpretaciones analíticas restantes.

## 4. Layout, controles y KPIs

La cabecera se compactó y se organizó en identidad institucional y título del producto. El contenido tiene un ancho máximo de 1580 px, fondo claro y paneles blancos. Se mantiene el orden de lectura de las cinco visualizaciones.

Los tres filtros conservan sus IDs, opciones, categorías y eventos. Se presentan como una barra de control con etiquetas pequeñas, selectores claros, foco magenta y un estado de selección distinguible mediante borde y fondo. Restablecer filtros conserva su comportamiento y se muestra como acción secundaria violeta.

Los cuatro KPIs conservan íntegramente texto dinámico, valores, unidades y denominadores. Se mejoró su jerarquía mediante valores grandes, acento magenta breve, títulos discretos y detalles visibles. Los N válidos mantienen una jerarquía secundaria sin ocultarse.

En 1920×1080 y 1366×768, la parte inferior de las tarjetas KPI queda aproximadamente a 422 px y el primer gráfico comienza aproximadamente a 585 px: se ven todos los KPIs sin desplazamiento y el gráfico está a continuación. En pantallas menores se apilan controles y paneles, y las tarjetas se distribuyen en dos columnas; se conserva el desplazamiento vertical normal.

## 5. Plotly: cambios estrictamente visuales

Se realizaron seis sustituciones explícitas de configuración visual en el JavaScript propio:

1. Familia tipográfica, tamaño general de 14 px y color de texto `#24272C`.
2. Fondo de papel transparente sobre panel blanco.
3. Márgenes de gráfico de 64/24/20/72 px, en orden izquierda/derecha/arriba/abajo.
4. Fondo, borde y tipografía del tooltip.
5. Color de grilla `#F0F1F3`.
6. Color secundario de la anotación de selección sin datos.

Al revertir únicamente esas seis sustituciones, el JavaScript propio coincide exactamente con el original. Se conservan agregación, selección de filas, fórmulas, N, tratamiento de NA, score, series, límites de escalas, leyendas, texto de tooltips, tablas, `Plotly.react`, configuración interactiva y manejadores de filtros/reset. No se agregó lógica analítica.

Los títulos permanecen alineados a la izquierda dentro de sus paneles. El fondo de trazado es blanco, las grillas son discretas y las leyendas conservan categorías y comportamiento. Se mantienen las cinco vistas: espera por cobertura; acceso por cobertura y condición; distribución de satisfacción; score por cobertura; satisfacción por score.

**Color de marca y color de datos permanecen separados.** Se conservaron las paletas analíticas originales:

- Coberturas: `#386d83`, `#548d94`, `#8a718e`.
- Acceso, escala 0–100%: `#edf3f7`, `#82acb9`, `#24536a`.
- Satisfacción 1–5, idéntica en sus dos vistas: `#924434`, `#bf7250`, `#b6a46c`, `#548d94`, `#24536a`.
- Score 0–3: `#dde6ef`, `#9cb8d2`, `#537fa3`, `#254965`, secuencia azul neutral sin semáforo de riesgo.

Las etiquetas siguen siendo Score 0, Score 1, Score 2, Score 3 y los niveles de satisfacción 1–5. No se incorporan categorías clínicas ni valoraciones nuevas.

## 6. Validación numérica y funcional

Se reutilizaron las funciones de referencia independiente en pandas y las comprobaciones de navegador de `notebooks/09_dashboard.ipynb`, sin ejecutar sus celdas de generación ni sobrescribir entregables. Se leyó el mismo Excel analítico exclusivamente para validar. La comparación recursiva usa tolerancia absoluta de 1e-9 o relativa de 1e-10; los controles de cifras publicadas mantienen la tolerancia de la Etapa 9.

| Control global | Resultado comprobado | Estado |
| --- | --- | --- |
| Registros | 2500 | APROBADO |
| Espera: N / media / mediana | 2426 / 64.580791426216 / 54 | APROBADO |
| Acceso: N / cantidad Sí / porcentaje | 2500 / 1695 / 67.80% | APROBADO |
| Satisfacción: N / media / mediana | 2428 / 3.5642504118616145 / 4 | APROBADO |
| Score: N | 2426 | APROBADO |
| Score 0 / 1 / 2 / 3 | 904 / 937 / 471 / 114 | APROBADO |
| Score y satisfacción: N conjunto | 2357 | APROBADO |
| Espera media por cobertura | 17.60 / 70.19 / 106.11 min, redondeadas | APROBADO |
| Acceso Privada/Aguda y Sin cobertura/Crónica | 89.22% / 41.99%, redondeados | APROBADO |
| Medianas de satisfacción por score | 4 / 4 / 3 / 2 | APROBADO |

| Selección mediante controles reales | Registros | N espera | N acceso | N satisfacción | N score | N conjunto | Estado |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | --- |
| CABA | 498 | 479 | 498 | 480 | 479 | 463 | APROBADO |
| Pública | 806 | 777 | 806 | 780 | 777 | 752 | APROBADO |
| Crónica | 843 | 824 | 843 | 820 | 824 | 802 | APROBADO |
| CABA / Pública / Crónica | 41 | 41 | 41 | 38 | 41 | 38 | APROBADO |

Para Pública se confirmó además media de espera aproximadamente 70.19 minutos y mediana 71. Se compararon las filas seleccionadas en contenido y orden, todas las agregaciones y los valores efectivamente enviados a las cinco figuras. Los KPIs visibles contienen los valores formateados correspondientes a la selección.

También aprobaron reset a 2500 registros y filtros Todas; selección vacía; grupo de prueba sin observables; sumas de conteos y porcentajes; hover real sobre la primera barra; foco de teclado magenta e imágenes embebidas cargadas correctamente. Los casos artificiales de validación solo se pasan a las funciones de prueba y no se agregan al HTML ni al dataset.

## 7. Validación técnica, responsive y offline

Pruebas en Chrome sin ventana, apertura directa mediante archivo local y contexto de navegador con red deshabilitada. Playwright se instaló en una carpeta temporal como herramienta de verificación; no es una dependencia de consulta del dashboard.

| Comprobación | Resultado |
| --- | --- |
| Apertura local sin servidor | APROBADO |
| Recursos externos declarados en atributos del HTML | 0 |
| Solicitudes HTTP/HTTPS registradas | 0 |
| Errores JavaScript | 0 |
| Errores de consola | 0 |
| Imágenes PNG Base64 cargadas | 2 |
| Actualización de las cinco vistas y filtros | APROBADO |
| Reset, selección vacía y NA | APROBADO |
| 1920×1080, 1366×768, 768×1024 y 390×844 | Sin scroll horizontal de la página |
| Tarjetas KPI completas sin scroll en los dos tamaños de escritorio | APROBADO |
| Desbordamiento de textos en KPIs, cabecera y controles | No detectado |

Se revisaron capturas reales de escritorio y móvil para comprobar disposición, etiquetas, leyendas y ausencia de superposiciones visibles. Las tablas conservan su propio contenedor desplazable cuando su ancho lo requiere; eso no genera scroll horizontal en la página.

El HTML conserva la biblioteca Plotly embebida y la política `connect-src 'none'`. No incorpora CDN, fuentes web, CSS/JS externos, APIs ni imágenes remotas. Los literales de URL internos del bundle Plotly preexistente no son dependencias de las vistas: la biblioteca se mantuvo byte por byte y las pruebas no registraron solicitudes HTTP/HTTPS.

## 8. Captura para la presentación

`outputs/dashboard/dashboard_salud_presentacion.png` es una captura **real de 1920×1080**, tomada del HTML v2 abierto en Chrome, después de esperar la actualización de Plotly y pulsar Restablecer filtros. Región, Cobertura y Condición están en Todas; los KPIs corresponden a los 2500 registros.

La captura incluye cabecera, filtros, KPIs y los dos primeros gráficos completos. Es un encuadre del viewport para la diapositiva 11, no una imagen reconstruida ni una captura de toda la página. No se modificó el PowerPoint.

## 9. Limitaciones y mantenimiento

La familia tipográfica exacta depende de las fuentes locales disponibles; las alternativas funcionan sin conexión. El logo PULSO conserva la textura y fondo de su PNG original, integrado mediante contenedor blanco. El HTML aumenta de tamaño al incorporar los dos logos Base64 y sigue siendo autocontenido.

En móvil se necesita desplazamiento vertical para recorrer los cuatro KPIs y las cinco vistas. En 1366×768 el primer gráfico comienza dentro del viewport, aunque para verlo completo se requiere un desplazamiento breve. La captura de 1920×1080 prioriza el recorrido de la demo y no intenta mostrar las cinco visualizaciones a la vez.

El notebook de Etapa 9 permanece sin cambios y genera la versión anterior. La versión 2 es una adaptación visual del HTML entregado; volver a ejecutar aquel notebook no reproduce este rediseño. Para compartir la v2 solo se necesita su HTML, sin los logos por separado, Python, Excel ni los scripts temporales de validación.
