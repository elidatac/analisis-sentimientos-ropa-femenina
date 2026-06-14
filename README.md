# Análisis de Sentimientos en Reseñas de Ropa Femenina con Modelos Preentrenados de Hugging Face

## Descripción del proyecto

Este proyecto implementa un prototipo en Colab de análisis de sentimientos utilizando modelos preentrenados del ecosistema Hugging Face sobre el conjunto de datos **Women's Clothing E-Commerce Reviews**. de la fuente Kaggle. 

El objetivo es identificar automáticamente si una reseña expresa un sentimiento positivo o negativo a partir de la calificación otorgada por el usuario. Para ello, la variable objetivo se construyó a partir de la columna **Rating** de acuerdo al siguiente criterio:

* Positivo (1): Rating ≥ 4
* Negativo (0): Rating < 4
Las reseñas con puntuación mayor o igual a 4 fueron clasificadas como positivas, mientras que las reseñas con puntuación menor a 4 fueron clasificadas como negativas. 
---

# Ecosistema Hugging Face

Hugging Face es una plataforma especializada en Inteligencia Artificial y Procesamiento de Lenguaje Natural (NLP) que proporciona:

* Modelos preentrenados.
* Tokenizadores.
* Pipelines de inferencia.
* Herramientas de entrenamiento y evaluación.
* Repositorios de modelos y datasets.

Para este proyecto se evaluaron tres diferentes modelos Transformer preentrenados para determinr cual presenta el mejor desempeño en la tarea de clasificación de sentimientos.

---

# Dataset

# # Women's Clothing E-Commerce Reviews

Variables utilizadas:

* Review Text
* Rating
* label y (variable objetivo)

# Selección y análisis de modelos preentrenados

Los modelos fueron elegidos por su capacidad para comprender mejor el contexto de las reseñas-

### Modelos evaluados

| Modelo                      | Descripción                                               |
| --------------------------- | --------------------------------------------------------- |
| DistilBERT SST-2            | Modelo optimizado y ligero para análisis de sentimientos. |
| RoBERTa Twitter Sentiment   | Modelo especializado en clasificación de sentimientos.    |
| BERT Multilingual Sentiment | Modelo multilingüe basado en clasificación por estrellas. |

---

# Entorno de ejecución

## Plataforma

Google Colab

## Hardware

* GPU de Google Colab

## Librerías principales

* pandas
* numpy
* scikit-learn
* transformers
* torch
* datasets
* accelerate
* matplotlib
* seaborn

---

# Estructura del repositorio

```text
.
├── README.md
├── requirements.txt
├── data/
├── notebooks/
├── results/
```

## Descripción de carpetas

### data/

Contiene el conjunto de datos original utilizado para el proyecto.

### notebooks/

Contiene el notebook principal desarrollado en Google Colab. Y los resultados. 

### results/

Contiene los resultados obtenidos:

* Comparación de modelos.


# Pasos de ejecución
1. Cargar el dataset.
2. Limpiar registros nulos.
2. Crear la variable objetivo *sentimiento*.
3. Dividir datos en 80% entrenamiento y 20% prueba.
4. Ejecutar los modelos preentrenados.
5. Calcular Accuracy, Precision, Recall y F1-score.
6. Comparar métricas.
7. Realizar predicciones sobre nuevas reseñas.

---

## Resultados

Los modelos fueron comparados utilizando las siguientes métricas de clasificación:

* Accuracy
* Precision
* Recall
* F1-score

Estas métricas permiten evaluar tanto la precisión general como la capacidad del modelo para clasificar correctamente ambas clases. El mejor modelo fue seleccionado considerando principalmente el F1-score. 

---

# Resultados

Los resultados completos se encuentran en la carpeta results.

## Comparación de modelos

| Modelo            | Accuracy | Precision | Recall | F1-score |
| ----------------- | -------- | --------- | ------ | -------- |
| DistilBERT SST-2  |  0.860   | 0.9158    | 0.8963 | 0.9059   |
| RoBERTa Twitter   |  0.840   | 0.8834    | 0.9069 | 0.8950   |
| BERT Multilingual |  0.876   | 0.9645    | 0.8670 | 0.9132   |

---

# Justificación de la selección final

El modelo seleccionado fue **[BERT Multilingual Stars]**.

La decisión se tomó considerando:

* El mayor valor de F1-score.
* El equilibrio entre precisión y recall.
* El desempeño general en la clasificación de reseñas.
* El tiempo de inferencia y facilidad de implementación.

Este modelo presente el mejor desempeño para cumplir con el objetivo de clasificar automáticamente sentimientos en reseñas de comercio electrónico.

---


# Conclusiones

Los modelos Transformer preentrenados permiten implementar soluciones de análisis de sentimientos con alta precisión sin necesidad de entrenar modelos desde cero, bajo el ecosistema Hugging Face. La implementación se llevó a cabo en Google colab mediante el uso de pipelines de inferencia listos para producción, reduciendo significativamente la complejidad técnica, el tiempo de desarrollo y los recursos computacionales requeridos. La comparación experimental entre los tres modelos, permitió identificar la alternativa con mejor desesmpeño a partir de métricas como  Accuracy, Precision, Recall y F1-score.
Desde la perspectiva del caso de uso, los resultados confirman que los modelos evaluados son capaces de automatizar el análisis de sentimientos de clientes en plataformas de comercio electrónico a partir del contenido textual en las nuevas reseñas de clientes dentro de las categorías positivo y negativo.
Las predicciones realizadas sobre reseñas nuevas en el conjunto de datos demostraron la capacidad del modelo final para identificar opiniones favorables asociados con altos niveles de satisfacción y detectar comentarios negativados relacionados con malas experiencias de compra. 
El uso de modelos preentrenados permite obtener una solucion funcional, escalable y de rápida implementación. Esta aproximación reduce los costos y tiempos asociados al entrenamiento especializado de modelos, manteniendo niveles de desempeño adecuados para apoyar la toma de decisiones basada en la percepción y satisfacción de los clientes.

# Autor 

Carmen Elizabeth Juárez Mortera

6. Los resultados demuestran que la Inteligencia Artificial puede apoyar la toma de decisiones basada en la voz del cliente y mejorar la comprensión de la satisfacción de los usuarios.
