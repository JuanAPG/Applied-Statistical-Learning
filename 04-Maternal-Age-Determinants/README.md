# Socio-demographic Predictors of Maternal Age at Birth

## Descripción General
Este proyecto aborda el fenómeno de la maternidad temprana, una prioridad de salud pública, a través de la inferencia estadística sobre microdatos a nivel nacional. La investigación incluye técnicas de limpieza de datos masivos (identificación y filtrado de códigos centinela), resolución de problemas de colinealidad y un algoritmo de *Backward Feature Selection*. Finalmente, se contrasta un modelo lineal estándar contra una especificación no lineal (regresión polinomial) para capturar la curvatura real en variables como el nivel de escolaridad y su impacto en la edad materna.

## Base de Datos
* **Fuente de los datos:** Los registros provienen de la base de microdatos **"Estadística de Nacimientos Registrados 2024"**, publicada oficialmente por el **Instituto Nacional de Estadística y Geografía (INEGI)**.
* **Acceso a los datos:** Debido al alto volumen de la información (arquitectura de Big Data), el archivo `.dbf` original no se aloja en este repositorio. Los microdatos públicos para reproducir este análisis pueden descargarse directamente en el siguiente enlace:
  * 📥 [INEGI - Estadística de Nacimientos (Microdatos)](https://www.inegi.org.mx/programas/natalidad/#microdatos)
* **Características del conjunto de datos:** El corpus original consiste en un volumen masivo de 1,672,227 observaciones (representando el registro nacional de nacimientos). Tras aplicar procesos de limpieza y tratamiento de valores nulos disfrazados, se retuvo una muestra robusta de 1,196,565 registros.
* **Variables:** La variable objetivo es la edad materna al momento del nacimiento (cuantitativa continua). Las características predictoras incluyen factores sociodemográficos codificados estadísticamente, tales como escolaridad, estado conyugal (variables dummy), actividad laboral y orden del parto.

## Índice de Archivos del Proyecto
* [`maternal_age_modeling.ipynb`](./maternal_age_modeling.ipynb): Pipeline de análisis incluyendo extracción de datos `.dbf`, limpieza de Big Data, matriz de correlación, *Backward Selection* y modelado polinomial con análisis de varianza (ANOVA) y residuales.
* [`nacim24.dbf`](./data/nacim24.dbf): Archivo de microdatos crudos del INEGI.
* **Reporte HTML:** [Inferencia Estadística y Geográfica](URL_A_TU_GITHUB_PAGES/04_maternal_age_determinants.html)
