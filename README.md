Descripción del Script de Entrenamiento y Evaluación (División 50/50)

Este script entrena y evalúa un modelo de Regresión Logística para predecir la presencia de enfermedad cardiovascular utilizando un dataset previamente preprocesado. Su particularidad es que realiza una división del dataset en partes iguales (50% para entrenamiento y 50% para prueba), lo que permite analizar cómo se comporta el modelo bajo un esquema de validación más exigente.

Proceso del Script
1. Carga del dataset

Se monta Google Drive y se carga un archivo CSV que contiene los datos ya preprocesados. Se limpian los nombres de columnas para evitar errores durante el procesamiento.

2. Separación de variables

El conjunto de datos se divide en:

X: características que se utilizarán como entrada del modelo

y: variable objetivo correspondiente a la presencia o ausencia de enfermedad cardiovascular

3. División del dataset (50/50)

A diferencia del enfoque tradicional (80/20), este script divide el dataset en dos partes iguales:

50% para entrenamiento

50% para prueba

La división se hace con estratificación para mantener la proporción original de clases.

4. Construcción y entrenamiento del modelo

Se utiliza un pipeline que incluye un único componente:

Regresión Logística, configurada con:

solver="liblinear" para tareas de clasificación binaria

class_weight="balanced" para corregir posibles desbalances entre clases

random_state=42 para asegurar resultados reproducibles

El modelo se ajusta utilizando únicamente el conjunto de entrenamiento.

5. Predicciones con threshold ajustado

En lugar de utilizar el umbral estándar de 0.5, se emplea un threshold de 0.4.
El objetivo de este ajuste es mejorar el recall, favoreciendo la detección de casos positivos en escenarios clínicos.

6. Evaluación del modelo

El rendimiento se evalúa utilizando varias métricas esenciales:

Exactitud (Accuracy)

Sensibilidad (Recall)

F1-Score

Área bajo la curva ROC (ROC AUC)

También se genera la matriz de confusión para analizar los verdaderos positivos, verdaderos negativos y errores del modelo.

7. Visualización de la curva ROC

El script muestra la curva ROC correspondiente al modelo entrenado, permitiendo examinar gráficamente la relación entre la tasa de verdaderos positivos y la tasa de falsos positivos.
