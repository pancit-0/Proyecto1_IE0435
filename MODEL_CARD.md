# Model Card: Clasificador de Arroz KNN

Este Model Card proporciona información técnica detallada sobre el modelo de aprendizaje automático desarrollado para la clasificación de granos de arroz, garantizando la transparencia, la reproducibilidad y el análisis crítico del sistema.

## 1. Detalles del Modelo
* **Autor:** Juan Chacón Bermúdez
* **Fecha:** Mayo 2026
* **Tipo de Modelo:** K-Nearest Neighbors (KNN)
* **Versión:** 1.0 (Basada en entrenamiento de 144 muestras)
* **Librerías:** Scikit-learn, Joblib, Pandas.

## 2. Uso Previsto
* **Casos de uso primarios:** Clasificación binaria automatizada para identificar la presencia de granos de arroz en imágenes de control de calidad (tipo de contaminante positivo).
* **Fuera de alcance:** No debe utilizarse en entornos de producción real sin una validación de hardware industrial o para la detección de patógenos.

## 3. Modelos usados

A continuación se detalla la comparativa técnica entre los algoritmos evaluados durante la fase de experimentación:

| Algoritmo | Hiperparámetros Clave | Exactitud (Accuracy) | Estado |
| :--- | :--- | :--- | :--- |
| **K-Nearest Neighbors (KNN)** | `n_neighbors=3`, `metric='euclidean'` | **0.7222 (72.2%)** | **Ganador** |
| Naive Bayes | `var_smoothing=1e-9` (Gaussian) | 0.6944 (69.4%) | Evaluado |
| Random Forest | `n_estimators=100`, `max_depth=None` | 0.6667 (66.7%) | Evaluado |
| SVM (Lineal) | `kernel='linear'`, `C=1.0` | 0.5556 (55.5%) | Evaluado |

## 4. Métricas
El modelo fue evaluado mediante la técnica de validación *Hold-out* (80/20).

* **Exactitud (Accuracy):** 0.7222 (72.22%)
* **Conjunto de Entrenamiento:** 144 muestras (80% de 180).
* **Conjunto de Prueba:** 36 muestras (20% de 180).
* **Hiperparámetros:**
    * `n_neighbors`: 3
    * `metric`: Euclidean
    * `weights`: Uniform

## 5. Datos de Entrenamiento
El entrenamiento se realizó utilizando una base de datos unificada de 180 muestras, provenientes de 6 sesiones de captura distintas (archivos CSV).
* **Preprocesamiento:** Se aplicó `StandardScaler` para normalizar las características morfológicas y de color antes del ajuste del modelo.
* **Reproducibilidad:** Se utilizó la semilla `random_state=42` para asegurar que el conjunto de entrenamiento de 144 muestras sea consistente en cada ejecución.

## 6. Análisis Crítico y Limitaciones
* **Sensibilidad a la iluminación:** El modelo presenta variaciones en su precisión si las condiciones lumínicas de la nueva imagen difieren de las del dataset original.
* **Oclusión:** El modelo no es capaz de separar granos de arroz que se encuentran amontonados, clasificándolos como un solo objeto anómalo.
* **Comparativa Técnica:** Se seleccionó KNN sobre SVM y Random Forest debido a que la distribución de los píxeles mostró una agrupación local más fuerte, permitiendo una frontera de decisión más efectiva en este tamaño de muestra.

## 7. Consideraciones Éticas y de Seguridad
* **Privacidad:** El dataset no contiene datos de identificación personal.
* **Seguridad:** El modelo no toma decisiones críticas que afecten la salud humana; su uso es estrictamente académico y de monitoreo técnico.

## 8. Reproducibilidad

El proyecto fue desarrollado y probado en el entorno de **Google Colab**, asegurando un entorno de ejecución estandarizado.

Para reproducir el flujo completo del experimento, se deben ejecutar los cuadernos (notebooks) en el siguiente orden jerárquico:

```text
1. notebooks/Procesamiento.ipynb            # Realización de 1´s y 0´s en las imágenes.
2. notebooks/Modelos_experimento.ipynb      # Entrenamiento y comparativa de los 4 algoritmos.
3. notebooks/exportar_modelo.ipynb          # Generación de archivos .joblib finales.
```
## 9. Mejor modelo

El modelo con mejor desempeño (KNN) ha sido exportado para su uso inmediato en la carpeta de modelos:

```text
models/C32009_Juan_Chacon.joblib
```
## 10. Hardware

El hardware como tal no es específico ya que los scripts fueron ejecutados en Google Colab, usando el entorno estandarizado.
