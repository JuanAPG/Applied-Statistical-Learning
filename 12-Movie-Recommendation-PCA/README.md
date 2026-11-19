# Proyector — Recomendación de películas con PCA

Aplicación interactiva que construye recomendaciones a partir de calificaciones de MovieLens. Usa componentes principales obtenidos de una matriz usuario-película centrada por espectador y proyecta un perfil nuevo mediante reconstrucción iterativa.

## Datos y modelo

El modelo incorporado usa un catálogo de 7,805 películas con al menos 300 calificaciones y cinco componentes que explican en conjunto 6.93 % de la variación. La aplicación solicita al menos ocho calificaciones con variación suficiente y recomienda películas que la persona aún no ha calificado, con al menos 1,000 votos. Los resultados se calculan en el navegador.

La evaluación incluida informa un RMSE de 0.953 y un MAE de 0.7315 sobre 3,000 espectadores de evaluación. Los resultados y parámetros proceden del archivo proporcionado. La implementación de entrenamiento y los datos originales no están incluidos en este repositorio.

- [Abrir aplicación](https://juanapg.github.io/Applied-Statistical-Learning/12_movie_recommender.html)
- [Código de la aplicación y modelo incorporado](../docs/12_movie_recommender.html)
- [MovieLens — GroupLens](https://grouplens.org/datasets/movielens/)
