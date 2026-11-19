# Subgrupos moleculares de cáncer de hígado

Análisis de expresión génica TCGA-LIHC con agrupamiento, estabilidad, características clínicas y supervivencia.

## Datos y reproducción

Los datos son de TCGA-LIHC, disponibles en [UCSC Xena](https://xenabrowser.net/datapages/). Coloca los cuatro archivos suministrados en `dataset/` junto al notebook. La matriz `TCGA-LIHC.star_tpm.tsv.gz` debe obtenerse por separado debido a su tamaño. El análisis incluye datos clínicos, supervivencia y el mapa de genes GENCODE v36.

## Archivos

- [Notebook](liver_cancer_subtypes.ipynb)
- [Reporte HTML](https://juanapg.github.io/Applied-Statistical-Learning/10_liver_cancer_subtypes.html)
