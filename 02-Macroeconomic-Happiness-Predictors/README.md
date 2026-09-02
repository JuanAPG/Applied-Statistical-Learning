# Macroeconomic and Social Predictors of Global Happiness

## Descripción General
Este estudio analiza la relación subyacente entre el índice de felicidad de diversas naciones y una serie de variables económicas, de salud e institucionales[cite: 2, 5]. Se evaluaron modelos de regresión lineal simple y múltiple para demostrar que el PIB transformado logarítmicamente, en conjunto con factores sociales, aproxima con alta precisión el ingreso per cápita como el predictor dominante del bienestar global[cite: 2, 5].

## Base de Datos
Los datos se encuentran en el directorio `/data/`.
* **Fuente original:** Indicadores del *World Happiness Report* y portal oficial de datos abiertos del *World Bank*[cite: 2, 5].
* **Características del conjunto de datos:** La muestra abarca 141 países a nivel global[cite: 2]. El dataset fue enriquecido mediante la integración de 3 variables complementarias: población total, esperanza de vida al nacer y un puntaje de control de corrupción, resultando en un entorno de 8 variables finales tras aplicar transformaciones logarítmicas[cite: 2, 5].

## Índice de Archivos del Proyecto
* [`regression_models.ipynb`](./regression_models.ipynb): Experimentación de modelos de regresión (simple y múltiple), evaluación de colinealidad e interpretación de coeficientes estandarizados.
* [`whr_2022_gdp.csv`](./data/whr_2022_gdp.csv): Base de datos base inicial.
* [`world_bank_extended.csv`](./data/world_bank_extended.csv): Base de datos extendida con variables macroeconómicas.
* **Reporte HTML:** [Resultados de Regresión](URL_A_TU_GITHUB_PAGES/02_macroeconomic_happiness.html)
