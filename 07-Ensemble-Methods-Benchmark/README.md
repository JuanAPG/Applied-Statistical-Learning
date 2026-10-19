# Benchmarking Ensemble, Kernel and Neural Methods on National Birth Records

## Descripción General
Esta investigación compara cuatro familias de modelos de clasificación sobre el mismo escenario experimental, con el objetivo de contrastar no solo su desempeño predictivo sino también su costo computacional y su escalabilidad frente a un corpus de casi un millón de observaciones de entrenamiento. Se construyeron un **Random Forest**, un modelo de **Gradient Boosting** por histogramas, una **Máquina de Vectores de Soporte** con kernel radial y una **red neuronal feedforward implementada desde cero en NumPy**, con propagación hacia adelante, retropropagación y optimizador Adam programados manualmente, además de una referencia equivalente en Keras. El trabajo documenta explícitamente las decisiones de submuestreo forzadas por el costo cuadrático del SVM.

## Base de Datos
* **Fuente de los datos:** Base de microdatos **"Estadística de Nacimientos Registrados 2024"** del **Instituto Nacional de Estadística y Geografía (INEGI)**.
* **Acceso a los datos:** Por el volumen del archivo `.dbf` original (más de 140 MB), los microdatos no se alojan en este repositorio. Pueden descargarse directamente del portal oficial:
  * 📥 [INEGI - Estadística de Nacimientos (Microdatos)](https://www.inegi.org.mx/programas/natalidad/#microdatos)
* **Características del conjunto de datos:** 1,196,565 observaciones tras la limpieza, con una partición estratificada de 957,252 de entrenamiento y 239,313 de prueba. La matriz de diseño final consta de 40 variables: 4 cuantitativas y 36 variables dummy.
* **Variables:** La variable objetivo es `grupo_edad`, con las mismas tres clases desbalanceadas del proyecto anterior (72.92%, 14.05% y 13.04%). Las características predictoras incluyen escolaridad, actividad laboral, orden del parto, tamaño de localidad y codificaciones dummy de estado conyugal y entidad federativa.

## Resultados Principales
* **Boosting** obtuvo el mejor desempeño, con una exactitud balanceada de 0.6523, seguido del **Random Forest** con 0.6425 y del **SVM** con 0.6311.
* El **SVM** requirió submuestrear a 40,000 observaciones, apenas el 4% del conjunto de entrenamiento, y aun así generó 35,723 vectores de soporte, resultando el modelo más costoso y el de peor desempeño entre los tres compensados.
* La **red neuronal en NumPy** alcanzó la exactitud simple más alta (0.7288) pero una exactitud balanceada de 0.3343, equivalente al azar: colapsó sobre la clase mayoritaria al no compensar el desbalance. Es la demostración más clara del riesgo de evaluar un clasificador multiclase con exactitud simple.

## Índice de Archivos del Proyecto
* [`ensemble_svm_neural_networks.ipynb`](./ensemble_svm_neural_networks.ipynb): Construcción y evaluación comparada de Random Forest, Gradient Boosting, SVM con kernel radial y red neuronal implementada en NumPy, con métricas de sensibilidad, especificidad, precisión y F1 por clase.
* **Reporte HTML:** [Comparación de Ensambles, SVM y Redes Neuronales](https://juanapg.github.io/Applied-Statistical-Learning/07_ensemble_benchmark.html)
