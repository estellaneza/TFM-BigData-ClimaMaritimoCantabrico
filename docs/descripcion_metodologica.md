# Descripción metodológica

Este documento resume la metodología técnica seguida en el Trabajo Fin de Máster `TFM-BigData-ClimaMaritimoCantabrico`.

El proyecto aplica técnicas de procesamiento y análisis de datos a series temporales históricas de oleaje del litoral cantábrico. El objetivo es transformar observaciones horarias procedentes de boyas de Puertos del Estado en indicadores que permitan caracterizar el clima marítimo y aportar información de apoyo a la planificación estacional en los entornos portuarios de Gijón y Bilbao.

## Enfoque metodológico

La metodología se inspira en las fases de comprensión, preparación, análisis y evaluación de CRISP-DM, adaptadas al alcance aplicado del TFM. El flujo de trabajo se organiza en siete notebooks ejecutables de forma secuencial:

1. Carga, limpieza, normalización y control de calidad de los datos.
2. Análisis exploratorio de las principales variables de oleaje.
3. Cálculo de indicadores temporales mensuales, estacionales y anuales.
4. Identificación y descripción de episodios potencialmente adversos mediante umbrales exploratorios de altura significativa.
5. Análisis de la dirección de procedencia del oleaje y su relación con la intensidad.
6. Predicción estadística mensual de la altura significativa del oleaje para 2027.
7. Priorización mensual de la exposición marítima prevista como apoyo a la planificación portuaria.

El análisis no emplea técnicas de clasificación ni modelos de *machine learning*. La componente predictiva utiliza métodos estadísticos de series temporales con una estructura sencilla e interpretable.

## Datos utilizados

Los datos proceden de la red de boyas de Puertos del Estado. El periodo de estudio comprende, de forma general, los años 2005 a 2024 y reúne 610.438 registros horarios.

Se analizan cuatro estaciones:

* Bilbao costera (1103).
* Bilbao-Vizcaya exterior (2136).
* Gijón costera (1117).
* Cabo de Peñas exterior (2242).

La utilización conjunta de boyas costeras y exteriores permite describir las diferencias entre los registros disponibles en cada entorno. No se plantea una comparación competitiva entre los puertos de Gijón y Bilbao.

## Dataset principal

Tras la limpieza y normalización de los archivos originales, las observaciones se integran en el archivo `dataset_principal_oleaje.csv`. El dataset mantiene la trazabilidad de cada registro mediante variables temporales e identificativas de la boya.

Las principales variables empleadas son:

* fecha y hora de la observación;
* código, nombre, zona y tipo de boya;
* altura significativa del oleaje (`Hs_m`);
* altura máxima de ola (`Hmax_m`);
* periodo medio espectral (`Tm02_s`);
* periodo de pico (`Tp_s`);
* dirección media y dirección de pico del oleaje;
* dispersión angular en el pico.

La altura significativa del oleaje constituye la variable central del estudio por su disponibilidad homogénea en las cuatro boyas y por su utilidad para describir la intensidad del estado de la mar.

## Tratamiento y análisis de los datos

El proceso de preparación incluye la conversión de los códigos de ausencia a valores nulos, la normalización de los nombres de las variables, la transformación de la fecha al formato temporal adecuado y la revisión de duplicados, cobertura temporal y discontinuidades.

Posteriormente, se realizan análisis descriptivos y gráficos para estudiar la distribución de las variables, las diferencias entre boyas y la evolución temporal de Hs. También se calculan medias, percentiles, máximos e indicadores mensuales, estacionales y anuales.

Los episodios potencialmente adversos se identifican a partir de umbrales exploratorios de Hs. Estos indicadores permiten estudiar su frecuencia, duración y distribución temporal, pero no representan límites oficiales de operatividad portuaria.

El análisis direccional agrupa la procedencia del oleaje en sectores y evalúa tanto su frecuencia como la relación entre cada dirección y los valores de Hs registrados.

## Predicción estadística y priorización para 2027

La predicción se realiza a escala mensual, ya que el objetivo es caracterizar la exposición marítima esperada a medio plazo y no generar predicciones meteorológicas diarias.

Para cada boya se construye una serie mensual de Hs media. Los meses con una cobertura horaria inferior al 70 % se identifican como incompletos y se imputan mediante la mediana histórica del mismo mes únicamente para disponer de una serie regular que pueda utilizarse en el modelo.

La selección del método predictivo se realiza mediante una validación cronológica. Se utilizan los datos disponibles entre 2005 y 2021 para estimar los 36 meses de 2022 a 2024. Se comparan una referencia estacional sencilla y un modelo Holt-Winters aditivo con tendencia amortiguada, seleccionando para cada boya la alternativa con menor error absoluto medio.

Finalmente, el método seleccionado se ajusta con toda la serie histórica disponible entre 2005 y 2024 y se genera una proyección mensual para el periodo 2025–2027. La dirección de oleaje se presenta como el sector históricamente más frecuente para cada mes, por lo que constituye una referencia climatológica y no un pronóstico direccional.

Los resultados se sintetizan en una priorización mensual de la exposición marítima. Esta priorización puede servir de apoyo para la planificación estacional de trabajos, recursos y actividades sensibles al oleaje. No sustituye las predicciones oficiales de corto plazo, los estudios de agitación portuaria ni los criterios técnicos aplicables a cada operación.
