# Proyecto-Machine-Learning-Final
Proyecto Machine Learning — Análisis de los documentos desclasificados del 23F
Equipo: Jorge Barbancho Justo · Alexandro Barbancho Almedina
Asignatura: Machine Learning · Curso 2025-2026 · Máster en Big Data y Data Science · Universidad de Navarra
Descripción
Análisis de los 167 documentos desclasificados sobre el 23F publicados por RTVE en el Buscador 23F. El trabajo aplica técnicas de machine learning sobre el corpus para extraer conocimiento estructurado, articuladas en cuatro casos de uso complementarios:

Caso 1 — Análisis temporal del flujo documental. Reconstrucción del eje temporal mediante extracción de fechas con regex, detección de meses atípicos por z-score y modelado de temas con LDA.
Caso 2 — Clasificación supervisada del tipo documental. Derivación del target a partir del título y comparación de cinco clasificadores (baseline, Naive Bayes, regresión logística, SVM lineal y Random Forest) con validación cruzada estratificada y F1-macro.
Caso 3 — Red de actores (grafo de personas). Normalización difusa de entidades con rapidfuzz, grafo de co-aparición ponderado, centralidades (grado, betweenness, eigenvector) y detección de comunidades con Louvain.
Caso 4 — Grafo de lugares y red bipartita actores–lugares. Clasificación de lugares en geografía / institución / rol, geocodificación con Nominatim, mapa interactivo con Folium y grafo bipartito comparado con el Caso 3 mediante el índice de Rand ajustado.

Contenido del repositorio

ProyMachineLearning.ipynb — Notebook principal con todo el análisis.
documentos_23f.csv — Dataset de partida con los 167 documentos.
README.md — Este fichero.

Al ejecutar el notebook se generan dos carpetas adicionales: data/, con una copia actualizada del CSV producida por el scraping, y outputs/, donde se guardan las figuras y los archivos de salida de cada caso (caso1_serie_temporal.png, caso1_temas_tiempo.png, caso2_matriz_confusion.png, caso3_red_actores.png, caso3_actores.gexf, caso4_mapa_lugares.html, caso4_bipartita.png).
Ejecución
El análisis se ejecuta desde ProyMachineLearning.ipynb de principio a fin sin necesidad de modificar nada. Todas las rutas son relativas. El notebook se encarga de descargar los 167 documentos del Buscador 23F mediante web scraping, ejecutar los cuatro casos de uso secuencialmente y guardar las figuras y resultados.
Las dependencias específicas que no vienen instaladas por defecto en un entorno estándar de Python o en Google Colab (rapidfuzz, networkx, python-louvain, folium, geopy) se instalan automáticamente desde las propias celdas del notebook. El resto (pandas, numpy, scikit-learn, matplotlib, nltk, requests, beautifulsoup4) son librerías estándar disponibles en cualquier entorno habitual.
La ejecución completa requiere conexión a internet (para el scraping inicial de RTVE y la geocodificación con Nominatim del Caso 4) y tarda aproximadamente 3-5 minutos.
Dataset
El dataset contiene 167 documentos con sus metadatos, resumen, entidades (personas y lugares), palabras clave y transcripción OCR completa. Las 15 columnas se agrupan en cuatro bloques: identificadores (id, detalle_url, original_url), metadatos de la digitalización (tipo, estado, paginas, kb, modelo_ocr, proveedor_ocr), contenido textual (titulo, resumen, texto_completo) y entidades (personas, lugares, palabras_clave).
Fuente: RTVE (2024). Buscador 23F — Documentos desclasificados del intento de golpe de Estado.
Resultados destacados

Caso 1: se recuperan fechas en el 72,5% de los documentos. Marzo y abril de 1982 emergen como meses atípicos por exceso de documentación (z = +2,6 y +2,4). El LDA identifica cinco temas interpretables con un desplazamiento progresivo del foco documental hacia el proceso judicial.
Caso 2: la regresión logística sobre TF-IDF + variables estructurales alcanza un F1-macro de 0,72 sobre cinco clases, frente al 0,12 del baseline.
Caso 3: el grafo de co-aparición consta de 886 nodos y 4.573 aristas, con 35 comunidades detectadas por Louvain (modularidad 0,697). Las centralidades recuperan una jerarquía coherente con el rol histórico de cada actor.
Caso 4: se geocodifican 262 lugares y se construye un grafo bipartito de 1.604 nodos y 9.260 aristas. El ARI de 0,196 frente al Caso 3 confirma que la dimensión espacial aporta una redistribución diferente de los actores.

Autores

Jorge Barbancho Justo
Alexandro Barbancho Almedina
