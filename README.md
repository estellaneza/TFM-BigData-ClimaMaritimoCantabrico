# TFM-BigData-ClimaMaritimoCantabrico
Análisis de series temporales de clima marítimo mediante Python y Big Data aplicado a la gestión portuaria en Gijón y Bilbao.
# TFM-BigData-ClimaMaritimoCantabrico

Repositorio del Trabajo Fin de Máster centrado en la aplicación de técnicas de Big Data al análisis de clima marítimo y gestión portuaria en el litoral cantábrico.

## Descripción

El proyecto analiza series temporales históricas procedentes de boyas de Puertos del Estado para estudiar variables de oleaje y viento en el entorno de Gijón y Bilbao.

El objetivo principal es transformar datos océano-meteorológicos en indicadores útiles para la gestión portuaria, incluyendo análisis exploratorio, indicadores estacionales, episodios potencialmente adversos y modelos predictivos exploratorios.

## Datasets utilizados

- Gijón costera 1117
- Cabo de Peñas 2242
- Bilbao costera 1103
- Bilbao-Vizcaya 2136

## Variables principales

- Altura significativa de ola, Hs
- Altura máxima de ola, Hmax
- Periodo de pico, Tp
- Dirección del oleaje

## Variable complementaria

- Viento en boyas exteriores

## Metodología

La metodología se inspira en CRISP-DM y se adapta al alcance del TFM:

1. Comprensión del problema portuario.
2. Comprensión de los datos disponibles.
3. Preparación y limpieza de datos.
4. Análisis exploratorio.
5. Generación de indicadores de clima marítimo.
6. Predicción exploratoria de Hs.
7. Clasificación exploratoria de episodios adversos.
8. Interpretación desde la gestión portuaria.

## Estructura del repositorio

```text
notebooks/       Notebooks de análisis en Google Colab
data/raw/        Datos originales
data/processed/  Datos procesados
outputs/figures/ Figuras generadas
outputs/tables/  Tablas generadas
outputs/models/  Modelos entrenados
docs/            Documentación metodológica
