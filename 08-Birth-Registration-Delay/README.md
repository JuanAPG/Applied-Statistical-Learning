# Classifying Delayed Birth Registration in Mexico

## Descripción General
Proyecto final del segundo parcial. Esta investigación aborda el registro tardío de nacimientos como problema de derecho a la identidad: en México una persona no existe legalmente hasta que su nacimiento se inscribe en el Registro Civil, y sin acta no puede acceder a educación, salud ni programas sociales. El trabajo construye y compara seis modelos de clasificación para caracterizar qué condiciones sociales, geográficas y del parto anticipan ese rezago.

El eje metodológico del proyecto son tres correcciones sin las cuales el modelo habría producido resultados espectaculares y falsos. Primero, la detección de **fuga de datos dura**: la diferencia entre la edad materna al registro y al nacimiento es exactamente la variable objetivo. Segundo, la detección de una **fuga suave** descubierta empíricamente, al comprobar que el número de hijos de la madre crece con el rezago porque está medido al momento del trámite. Tercero, la demostración de que los códigos de "no especificado" **no son ruido sino señal**, de modo que eliminarlos habría descartado el 79.6% de la base y destruido el fenómeno estudiado.

## Base de Datos
* **Fuente de los datos:** Base de microdatos **"Estadística de Nacimientos Registrados 2024"** del **Instituto Nacional de Estadística y Geografía (INEGI)**, acompañada de su descriptor oficial `DBD_Nacimientos_2024.pdf`.
* **Acceso a los datos:** Por el volumen del archivo `.dbf` original (más de 140 MB), los microdatos no se alojan en este repositorio. Pueden descargarse directamente del portal oficial:
  * 📥 [INEGI - Estadística de Nacimientos (Microdatos)](https://www.inegi.org.mx/programas/natalidad/#microdatos)
* **Características del conjunto de datos:** 1,672,227 registros y 44 variables. Una precisión importante sobre la unidad de análisis: cada fila es un **registro realizado durante 2024**, no un nacimiento ocurrido en 2024, ya que el 35% corresponde a nacimientos de años anteriores. Tras excluir los registros consulares del extranjero se retuvieron 1,651,829 observaciones y 125 variables.
* **Variables:** La variable objetivo se deriva de `EDAD_REG`, definida por el INEGI como la fecha de registro menos la fecha de nacimiento. Se construyeron tres clases cualitativas: *Oportuno* (menor de un año, 82.94%), *Tardío* (de 1 a 5 años, 10.80%) y *Muy tardío* (6 años o más, 6.26%). Las características predictoras se agrupan en condiciones del nacimiento (lugar y persona que atendió el parto, tipo y orden del parto, edad de los padres) y condiciones de la familia al momento del registro (escolaridad de ambos padres, estado conyugal, actividad y situación laboral, tamaño de localidad y entidad federativa).

## Resultados Principales
* **Modelo final: Gradient Boosting**, con una exactitud balanceada de 0.7378 y un AUC macro de 0.8847 sobre un conjunto de prueba independiente de 330,366 observaciones, usado una sola vez.
* El AUC por clase es de 0.968 para el rezago severo, de modo que **el modelo discrimina mejor justo el grupo que más urge identificar** para campañas de regularización.
* Un análisis de sensibilidad demuestra que retirar las variables administrativas cuesta menos de un punto porcentual, confirmando que el gradiente social explica prácticamente todo el poder predictivo.
* **Contraste con fuentes oficiales:** tres de las cinco entidades con mayor y con menor rezago coinciden con las identificadas por el CONAPO, pese a usar un criterio temporal y una fuente distintos.

## Índice de Archivos del Proyecto
* [`registration_delay_modeling.ipynb`](./registration_delay_modeling.ipynb): Reporte completo con planteamiento, diccionario de datos construido desde el descriptor oficial del INEGI, detección y demostración de fugas, tratamiento de valores no especificados, construcción y comparación de seis modelos, evaluación final y contraste con cifras oficiales.
* **Reporte HTML:** [Clasificación del Registro Tardío de Nacimientos](https://juanapg.github.io/Applied-Statistical-Learning/08_registration_delay.html)
