# Proyecto Machine Learning — Análisis de los documentos desclasificados del 23F

Trabajo final de la asignatura de Machine Learning del Máster en Big Data y Data Science de la Universidad de Navarra (curso 2025-2026). Análisis de los 167 documentos desclasificados por el Gobierno de España en 2024 sobre el intento de golpe de Estado del 23 de febrero de 1981, publicados por RTVE en el Buscador 23F.

**Autores:** Jorge Barbancho Justo · Alexandro Barbancho Almedina

## Contenido del repositorio

- `ProyMachineLearning.ipynb` — Notebook principal. Ejecutable de principio a fin: descarga los documentos mediante web scraping del Buscador 23F y desarrolla los cuatro casos de uso.
- `documentos_23f.csv` — Dataset resultante del scraping (167 documentos × 15 columnas). Se genera automáticamente al ejecutar el notebook; se incluye también como respaldo.
- `README.md` — Este archivo.

## Casos de uso

1. **Análisis temporal del flujo documental** — Reconstrucción del eje temporal a partir de fechas embebidas en títulos y texto, detección de anomalías por z-score y modelado de temas con LDA.
2. **Clasificación supervisada del tipo documental** — Comparación de cinco familias de clasificadores (Dummy, Naive Bayes, regresión logística, SVM lineal, Random Forest) sobre TF-IDF más variables propias, con validación cruzada estratificada de 5 pliegues y métrica F1-macro.
3. **Red de actores (grafo de personas)** — Normalización difusa de entidades con rapidfuzz, construcción del grafo de co-aparición ponderado, cálculo de centralidades y detección de comunidades con Louvain.
4. **Grafo de lugares y red bipartita actores–lugares** — Clasificación de lugares en geografía/institución/rol, geocodificación con Nominatim, mapa interactivo con Folium y comparación de comunidades con el Caso 3 mediante el índice de Rand ajustado.

## Cómo ejecutarlo

Requisitos: Python 3.10+ y las librerías `pandas`, `numpy`, `requests`, `beautifulsoup4`, `scikit-learn`, `matplotlib`, `networkx`, `python-louvain`, `rapidfuzz`, `geopy` y `folium`.

```bash
pip install pandas numpy requests beautifulsoup4 scikit-learn matplotlib networkx python-louvain rapidfuzz geopy folium
```

Abrir `ProyMachineLearning.ipynb` en Jupyter o VS Code y ejecutar las celdas en orden. El notebook descarga los datos del Buscador 23F automáticamente; no se necesitan archivos externos.

## Fuente de datos

RTVE (2024). *Buscador 23F — Documentos desclasificados del intento de golpe de Estado*. https://23fbuscador.rtve.es/
