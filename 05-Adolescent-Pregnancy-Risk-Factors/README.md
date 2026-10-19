# Logistic Classification of Adolescent Pregnancy Risk

## Descripción General
Esta investigación traslada el estudio de la maternidad temprana de un enfoque inferencial a uno de clasificación binaria, prediciendo si un nacimiento corresponde a una madre adolescente a partir de condiciones sociodemográficas. El modelo de regresión logística se implementó **desde cero** mediante el método de Newton-Raphson con mínimos cuadrados reponderados iterativamente (IRLS), sin recurrir a librerías de modelado; lo mismo aplica para la validación cruzada estratificada de 10 particiones, la construcción de la curva ROC y el cálculo del AUC. El análisis cierra con la interpretación de los coeficientes como razones de momios y con el desplazamiento del umbral de decisión para privilegiar la sensibilidad sobre la exactitud, dada la naturaleza desbalanceada del problema.

## Base de Datos
* **Fuente de los datos:** Base de microdatos **"Estadística de Nacimientos Registrados 2024"** del **Instituto Nacional de Estadística y Geografía (INEGI)**.
* **Acceso a los datos:** Por el volumen del archivo `.dbf` original (más de 140 MB), los microdatos no se alojan en este repositorio. Pueden descargarse directamente del portal oficial:
  * 📥 [INEGI - Estadística de Nacimientos (Microdatos)](https://www.inegi.org.mx/programas/natalidad/#microdatos)
* **Características del conjunto de datos:** El corpus original contiene 1,672,227 registros. Tras filtrar los códigos centinela de "no especificado" se retuvieron 1,196,565 observaciones, divididas de forma estratificada en 957,252 de entrenamiento y 239,313 de prueba.
* **Variables:** La variable objetivo es `embarazo_adolescente`, construida como una dicotomía a partir de la edad materna al nacimiento (1 si es menor o igual a 19 años). Presenta un desbalance de 85.95% contra 14.05%. Las características predictoras son el nivel de escolaridad de la madre, su actividad laboral, el orden del parto y el estado conyugal codificado como variable dummy.

## Resultados Principales
* **Validación cruzada (10 particiones estratificadas):** AUC de 0.8697 con una desviación estándar de 0.0025, y sensibilidad media de 0.7811.
* **Conjunto de prueba:** AUC de 0.8701. Ajustando el umbral de 0.5 a 0.2 se alcanza una sensibilidad de 0.7795 y una especificidad de 0.8053.
* **Interpretación:** cada nivel adicional de escolaridad de la madre multiplica los momios de embarazo adolescente por 0.57, y cada orden de parto adicional los multiplica por 0.14.

## Índice de Archivos del Proyecto
* [`logistic_regression_classification.ipynb`](./logistic_regression_classification.ipynb): Pipeline completo con limpieza de códigos centinela, implementación propia de la regresión logística por IRLS, validación cruzada estratificada, curva ROC y análisis de razones de momios.
* **Reporte HTML:** [Clasificación de Riesgo de Embarazo Adolescente](https://juanapg.github.io/Applied-Statistical-Learning/05_adolescent_pregnancy.html)
