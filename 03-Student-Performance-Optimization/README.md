# Predictive Modeling and Feature Selection for Student Performance

## Descripción General
El objetivo de este proyecto es construir un modelo de regresión lineal múltiple con alta capacidad de generalización para predecir métricas de desempeño[cite: 3, 4]. La investigación implementa una metodología de aprendizaje automático que incluye transformación de variables categóricas, *Standard Scaling*, y un algoritmo de *Forward Feature Selection* evaluado dinámicamente mediante validación cruzada (K-Fold) para prevenir el sobreajuste[cite: 3].

## Base de Datos
Los registros procesados se alojan en `/data/uci_student_data.csv`.
* **Fuente de los datos:** El corpus de datos original se obtuvo de la siguiente referencia: *Cortez, P. (2008). Student Performance [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5TG7T.*
* **Características del conjunto de datos:** El corpus contiene 395 registros con 10 características distintas (demográficas, ambientales y de desempeño histórico). No presenta valores nulos, y cuenta con variables de alta dispersión y desbalance que requirieron tratamiento estadístico riguroso antes del entrenamiento.

## Índice de Archivos del Proyecto
* [`feature_selection_cv.ipynb`](./feature_selection_cv.ipynb): Pipeline de Machine Learning completo, desde preprocesamiento y escalado hasta la evaluación de validación cruzada y residuales.
* [`uci_student_data.csv`](./data/uci_student_data.csv): Conjunto de datos analizado.
* **Reporte HTML:** [Modelado y Selección de Características](URL_A_TU_GITHUB_PAGES/03_student_performance.html)
