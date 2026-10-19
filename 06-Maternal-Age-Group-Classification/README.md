# Discriminant Analysis and Decision Trees for Maternal Age Stratification

## Descripción General
Esta investigación extiende el problema de la edad materna a una clasificación multiclase, contrastando dos familias de modelos con supuestos opuestos. Por un lado, un **Análisis Discriminante Lineal implementado desde cero**, incluyendo el cálculo de la matriz de covarianza ponderada, la descomposición en eigenvalores y la proyección sobre los discriminantes LD1 y LD2. Por el otro, un **árbol de decisión** optimizado mediante poda por costo-complejidad, donde el hiperparámetro de penalización se selecciona con validación cruzada estratificada. El eje del trabajo es evaluar cómo los supuestos de cada modelo —normalidad multivariada y homocedasticidad frente a particiones recursivas del espacio— condicionan su desempeño sobre clases desbalanceadas.

## Base de Datos
* **Fuente de los datos:** Base de microdatos **"Estadística de Nacimientos Registrados 2024"** del **Instituto Nacional de Estadística y Geografía (INEGI)**.
* **Acceso a los datos:** Por el volumen del archivo `.dbf` original (más de 140 MB), los microdatos no se alojan en este repositorio. Pueden descargarse directamente del portal oficial:
  * 📥 [INEGI - Estadística de Nacimientos (Microdatos)](https://www.inegi.org.mx/programas/natalidad/#microdatos)
* **Características del conjunto de datos:** 1,196,565 observaciones tras la limpieza, particionadas de forma estratificada en 957,252 de entrenamiento y 239,313 de prueba.
* **Variables:** La variable objetivo es `grupo_edad`, una recodificación cualitativa de tres clases a partir de la edad materna: *Adolescente* (hasta 19 años, 14.05%), *Adulta joven* (de 20 a 34 años, 72.92%) y *Adulta mayor* (35 años o más, 13.04%). Para el LDA se seleccionaron únicamente las variables cuantitativas compatibles con sus supuestos —escolaridad y orden del parto—, mientras que el árbol incorporó además la actividad laboral, el tamaño de localidad y variables dummy de estado conyugal y entidad.

## Resultados Principales
* Se evaluaron 5,211 valores candidatos del parámetro de poda; el seleccionado por validación cruzada fue 0.001302.
* **Exactitud:** 0.7239 para el LDA contra 0.7370 para el árbol podado.
* **Hallazgo central:** la exactitud balanceada del LDA cae a 0.3700, apenas por encima del azar en tres clases. El modelo prácticamente ignora a las clases minoritarias, con una sensibilidad de 0.0430 para *Adolescente*, mientras que el árbol alcanza 0.6046 en esa misma clase. El contraste demuestra que una exactitud alta puede encubrir un modelo inservible cuando las clases están desbalanceadas.
* **Importancia de variables en el árbol:** orden del parto (0.4897), escolaridad (0.4494) y estado conyugal (0.0610).

## Índice de Archivos del Proyecto
* [`discriminant_analysis_trees.ipynb`](./discriminant_analysis_trees.ipynb): Implementación propia del LDA con proyección sobre discriminantes, árbol de decisión con poda por costo-complejidad validada por K-Fold, y comparación de métricas por clase.
* **Reporte HTML:** [Discriminantes Lineales y Árboles de Decisión](https://juanapg.github.io/Applied-Statistical-Learning/06_maternal_age_groups.html)
