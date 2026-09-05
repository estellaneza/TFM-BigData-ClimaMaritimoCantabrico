# TFM Big Data: clima marítimo y gestión portuaria cantábrica

Repositorio asociado al Trabajo Fin de Máster sobre el análisis de series temporales de oleaje y su aplicación como apoyo a la planificación portuaria en los entornos de Gijón y Bilbao.

## Objetivo

Transformar datos históricos horarios de boyas de Puertos del Estado en indicadores temporales, direccionales y predictivos que permitan caracterizar la exposición al oleaje.

## Datos

* Fuente: Puertos del Estado.
* Periodo analizado: 2005–2024.
* Registros: 610.438 observaciones horarias.
* Boyas: Bilbao costera, Bilbao-Vizcaya, Gijón costera y Cabo de Peñas.
* Variables principales: altura significativa de ola (`Hs_m`), altura máxima, periodo medio, periodo de pico y dirección de oleaje.

## Notebooks

1. `01_carga_limpieza_datos.ipynb`: carga, limpieza y creación del dataset principal.
2. `02_analisis_exploratorio.ipynb`: estadísticos descriptivos y distribuciones.
3. `03_indicadores_temporales.ipynb`: análisis mensual, estacional y anual.
4. `04_episodios_potencialmente_adversos.ipynb`: episodios de oleaje elevado mediante umbrales exploratorios.
5. `05_analisis_direccional.ipynb`: frecuencia y relación entre dirección e intensidad.
6. `06_prediccion_estadistica_Hs_2027.ipynb`: proyección estadística mensual de Hs para 2027.
7. `07_priorizacion_exposicion_portuaria_2027.ipynb`: priorización mensual de la exposición marítima prevista.

## Estructura

```text
data/raw/          Datos originales
data/processed/    Dataset procesado
notebooks/         Notebooks de análisis
outputs/figures/   Figuras generadas
outputs/tables/    Tablas generadas
outputs/models/    Resultados de modelización
docs/              Documentación del proyecto
```

## Reproducibilidad

Los notebooks deben ejecutarse en orden numérico. Cada notebook utiliza los datos procesados generados en las etapas anteriores y guarda automáticamente sus figuras y tablas en `outputs/`.


