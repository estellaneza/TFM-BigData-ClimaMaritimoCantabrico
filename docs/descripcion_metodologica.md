# Descripción metodológica

Este documento resume la metodología técnica seguida en el Trabajo Fin de Máster `TFM-BigData-ClimaMaritimoCantabrico`.

El trabajo aplica técnicas de Big Data y análisis de series temporales a datos históricos de clima marítimo del litoral cantábrico, con especial atención a los entornos portuarios de Gijón y Bilbao.

## Enfoque metodológico

La metodología se inspira en CRISP-DM y se adapta al alcance del TFM. Las fases principales son:

1. Comprensión del problema portuario.
2. Comprensión de los datos disponibles.
3. Preparación, limpieza y normalización de datos.
4. Construcción de datasets de trabajo.
5. Análisis exploratorio.
6. Generación de indicadores temporales, estacionales y direccionales.
7. Predicción exploratoria de Hs.
8. Clasificación exploratoria de episodios adversos.
9. Interpretación desde la gestión portuaria.

## Datasets previstos

- Gijón costera 1117
- Cabo de Peñas 2242
- Bilbao costera 1103
- Bilbao-Vizcaya 2136

## Dataset principal

El dataset principal estará centrado en variables de oleaje:

- Fecha y hora
- Código de boya
- Nombre de boya
- Tipo de boya
- Altura significativa de ola
- Altura máxima
- Periodo de pico
- Dirección del oleaje

## Dataset complementario

El dataset complementario estará centrado en variables de viento y solo se construirá para las boyas exteriores:

- Cabo de Peñas 2242
- Bilbao-Vizcaya 2136

## Enfoque de análisis

El análisis se estructura en:

- limpieza y control de calidad;
- análisis descriptivo;
- análisis temporal y estacional;
- análisis de episodios adversos;
- análisis direccional;
- análisis complementario del viento;
- predicción exploratoria de Hs;
- clasificación exploratoria de episodios adversos.
