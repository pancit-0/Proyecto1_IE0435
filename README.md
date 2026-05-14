# Proyecto1_IE0435
Construir un sistema completo, que incluye datos, modelos, evaluación y exportación del modelo, para cumplir con lo siguiente: Detectar elementos anómalos (contaminaciones) en imágenes, usando aprendizaje automático clásico.

Autor: Juan Chacón Bermúdez   Carné: C32009
Universidad de Costa Rica 
IE0435 - Inteligencia Artificial Aplicada a la Ingeniería Eléctrica

## Descripción del proyecto

La simulación se realizó utilizando imágenes capturadas sobre un fondo blanco uniforme. Las imágenes con presencia de granos de arroz se clasifican como **muestras positivas**, mientras que las imágenes del fondo vacío o con otros elementos se clasifican como **muestras negativas**.

Cada imagen fue procesada para convertirse en una representación numérica vectorial:
* **Transformación:** Escala de grises y redimensionamiento.
* **Vectorización:** Cada imagen se convirtió en un vector fila de características numéricas.
* **Codificación de etiquetas:**
    * **Etiqueta 1:** Presencia de arroz (Imagen positiva).
    * **Etiqueta 0:** Sin arroz / Fondo / Aros (anillos y clips) (Imagen negativa).

## Estructura del repositorio

```text
Proyecto1_IE0435/
|
├── data/
│   ├── group_dataset/
|   |       ├── arroz_1(me).csv            
|   |       |── arroz_2.csv                
│   |       ├── arroz_3.csv                
│   |       ├── arroz_4.csv                 
│   |       ├── arroz_5.csv                 
│   |       └── arroz_6.csv                 
|   |
|   └── processed/
│           └── dataset_total.csv 
│
├── models/
│   ├── modelo_knn_80.joblib          # Mejor modelo exportado
│   └── escalador_80.joblib           # Escalador de datos (StandardScaler)
│
├── notebooks/
│   ├── Procesamiento.ipynb           # Unificación y limpieza
│   ├── Modelos_experimento.ipynb     # Entrenamiento y comparativa
│   └── exportar_modelo.ipynb         # Generación de archivos finales
│
├── DATASET.md                        # Documentación de los datos
├── MODEL_CARD.md                     # Ficha técnica del modelo
├── README.md                         # Guía general del proyecto
├── requirements.txt                  # Librerías necesarias
└── LICENSE                           # Licencia MIT
```

## Modelos Evaluados

Se realizó una comparativa utilizando una división de datos de 80% para entrenamiento (144 muestras) y 20% para pruebas (36 muestras). Los resultados obtenidos fueron:
| Modelo | Exactitud (Accuracy) |
| :--- | :--- | 
| **K-Nearest Neighbors (KNN)** |  **0.7222 (72.2%)** |
| Naive Bayes | 0.6944 (69.4%) |
| Random Forest |  0.6667 (66.7%)  |
| SVM (Lineal) |  0.5556 (55.5%) |

## Mejor modelo obtenido

El mejor desempeño fue alcanzado por el algoritmo K-Nearest Neighbors (KNN) con un valor de k=3, logrando una exactitud de 0.7222.Este resultado indica que el modelo clasifica correctamente el 72.22% de las muestras del conjunto de prueba. 
El uso de KNN se justifica por la naturaleza de los descriptores de píxeles, donde la cercanía geométrica entre muestras de la misma clase permite una frontera de decisión más efectiva que modelos lineales como SVM.

## Instalación y ejecución

Los scripts fueron desarrollados para ejecutarse en Google Colab. Para instalar las dependencias necesarias en un entorno local, ejecute: 

``` text
Bashpip install -r requirements.txt
```
## Orden de ejecución

Para reproducir el flujo completo del experimento, ejecute los notebooks en el siguiente orden:

``` text
1. notebooks/Procesamiento.ipynb            
2. notebooks/Modelos_experimento.ipynb      
3. notebooks/exportar_modelo.ipynb          
```

## Archivos de documentación (DATASET.md): 

Describe la recolección, estructura, procesamiento y limitaciones del conjunto de datos.

* MODEL_CARD.md: Documenta el modelo seleccionado, métricas, análisis crítico y reproducibilidad.
* LICENSE: Indica las condiciones de uso (Licencia MIT).
