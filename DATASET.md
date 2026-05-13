# Documentación del Conjunto de Datos (Dataset)

## Descripción general
El conjunto de datos utilizado en este proyecto corresponde a descriptores numéricos extraídos de imágenes de una línea de producción simulada. La captura se realizó utilizando una base de color blanco como fondo uniforme, sobre la cual se colocaron granos de arroz para su análisis morfológico y de color.

Las imágenes que presentan granos de arroz se consideran **muestras positivas**, mientras que aquellas que contienen otros objetos o están vacías se consideran **muestras negativas**.

## Recolección de datos
Cada registro en los archivos CSV fue clasificado según la presencia o ausencia de granos de arroz en la imagen original:

* **Clase 1:** Imagen positiva, contiene granos de arroz.
* **Clase 0:** Imagen negativa, no contiene granos de arroz (vacía o con objetos no deseados).

El archivo `arroz_1(me).csv` corresponde al conjunto de datos generado a partir de las imágenes propias del estudiante. Posteriormente, este archivo fue integrado con 5 archivos CSV adicionales generados por otros compañeros para construir un **conjunto de datos grupal de 180 muestras**.

## Organización de los datos
La carpeta `data/` del repositorio está estructurada de la siguiente manera para garantizar la reproducibilidad total:

```text
data/
├── group_dataset/
│   ├── arroz_1(me).csv             # Datos propios 
|   ├── arroz_2.csv                 # Datos compartidos por compañero
│   ├── arroz_3.csv                 # Datos compartidos por compañero
│   ├── arroz_4.csv                 # Datos compartidos por compañero
│   ├── arroz_5.csv                 # Datos compartidos por compañero
│   └── arroz_6.csv                 # Datos compartidos por compañero
└── processed/
    └── dataset_total.csv  # Unión de las 180 muestras
```
## Limitaciones y consideraciones éticas

Condiciones de Iluminación: El dataset es altamente dependiente de la iluminación utilizada en la simulación. Cambios en la temperatura de color o sombras pueden afectar la precisión de las características extraídas.
Instrumentación: Los datos dependen de la resolución de la cámara y la calibración del sensor utilizado por cada compañero de la clase.
