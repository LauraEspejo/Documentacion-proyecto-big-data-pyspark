# Proyecto Big Data en Colab: integración y análisis de smartphones

## Descripción
Este proyecto fue desarrollado en Google Colab y tiene como objetivo integrar un dataset de ventas de smartphones con un dataset de especificaciones técnicas.  
A partir de esa integración se genera un dataset consolidado, se corrigen coincidencias problemáticas entre modelos y se realiza un análisis exploratorio de los datos.

## Objetivo
Construir un flujo de trabajo en Colab que permita:
- unir ventas y especificaciones de smartphones
- mejorar la calidad del cruce entre datasets
- generar un dataset final procesado
- analizar ventas por marca, ciudad y año
- analizar la relación entre características técnicas y comportamiento comercial

## Archivo principal
- `proyecto_big.py`

## Archivos de entrada
El script utiliza:
- `sales_clean.csv`
- `specs_clean.csv`

## Archivos generados
Durante la ejecución se crean:
- `dataset_final_merged.csv`
- `dataset_final_merged_v2.csv`
- `dataset_processed_colab.csv`

## Librerías utilizadas
- `pandas`
- `numpy`
- `matplotlib`
- `google.colab.files`

## Flujo del código

### 1. Carga de archivos en Colab
El script usa `files.upload()` para subir manualmente archivos al entorno de Google Colab.

### 2. Lectura de datasets limpios
Se cargan:
- `sales_clean.csv`
- `specs_clean.csv`

### 3. Creación de la llave de unión
Se crea una variable llamada `merge_key` uniendo:
- `brand_norm`
- `model_norm`

Esto permite relacionar los registros de ventas con las especificaciones técnicas.

### 4. Unión entre ventas y especificaciones
Se realiza un `merge` tipo `left`, usando el dataset de ventas como base, para no perder registros aunque algunos modelos no tengan especificaciones.

### 5. Validación de coincidencias
Después del merge, el script calcula:
- total de registros
- cantidad de coincidencias exitosas
- porcentaje de match
- modelos que no encontraron especificaciones

### 6. Correcciones manuales
Se aplican ajustes puntuales para mejorar el cruce entre modelos:
- `Vivo Y51` → `y51 2020 september`
- `Samsung Galaxy A51` → `galaxy a51 5g`
- `Samsung Galaxy S21` → `galaxy s21 5g`

### 7. Generación del dataset final
Luego del nuevo merge, se genera:
- `dataset_final_merged_v2.csv`

### 8. Preparación del dataset procesado
A partir del dataset final:
- se convierten columnas a tipo numérico
- se convierte `date` a tipo fecha
- se limpian espacios en columnas de texto
- se crean variables derivadas

Variables derivadas:
- `revenue_per_unit_sold`: ingreso por unidad vendida
- `has_specs`: indica si el modelo tiene especificaciones asociadas

### 9. Análisis exploratorio
El script calcula:
- total de registros
- total de unidades vendidas
- ingreso total
- cantidad de marcas, modelos y ciudades

Además genera:
- ventas por marca
- ingresos por marca
- modelos más vendidos
- ventas por ciudad
- ventas por año
- gráficos de precio vs ventas
- gráficos de batería vs ventas
- gráficos de RAM vs ventas
- matriz de correlación

### 10. Exportación final
El script guarda:
- `dataset_processed_colab.csv`

Este archivo representa la versión procesada final del dataset en Colab.

## Cómo ejecutar el proyecto en Colab
1. Abrir el notebook o script en Google Colab.
2. Subir `sales_clean.csv` y `specs_clean.csv`.
3. Ejecutar las celdas en orden.
4. Descargar los archivos generados:
   - `dataset_final_merged_v2.csv`
   - `dataset_processed_colab.csv`
   
## Posibles mejoras
- convertir el notebook en funciones reutilizables
- separar limpieza, merge y análisis en scripts diferentes
- agregar manejo de errores
- automatizar las homologaciones de nombres de modelos

## Autor
Laura Daniela Espejo Parada 
Yuli Valentina Andrade
Juan Francisco Prieto
