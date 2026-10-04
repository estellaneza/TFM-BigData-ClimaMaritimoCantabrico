# Descripción metodológica

Este documento resume la metodología técnica aplicada en el Trabajo Fin de Máster `TFM-BigData-ClimaMaritimoCantabrico`.

<<<<<<< HEAD
El proyecto integra datos históricos de oleaje y actividad portuaria para analizar la exposición marítima de los puertos de Gijón y Bilbao. El trabajo se centra en la altura significativa de ola (Hs), los episodios de oleaje elevado, los indicadores mensuales de tráfico y las horas de restricción operativa.

El periodo de estudio abarca desde enero de 2005 hasta diciembre de 2024. A partir de esta información se desarrolla una proyección estacional de las horas mensuales con Hs ≥ 3 m para 2027 y una estimación orientativa del condicionamiento operativo asociado.

## Enfoque metodológico

La metodología se organiza mediante una adaptación de CRISP-DM al alcance del TFM. Las fases principales son:

1. Comprensión del problema y definición de los objetivos del análisis.
2. Recopilación y comprensión de los datos oceanográficos y portuarios.
3. Limpieza, normalización y control de calidad de las fuentes.
4. Construcción de datasets de trabajo e integración temporal de la información.
5. Análisis exploratorio de las variables oceanográficas y portuarias.
6. Generación de indicadores temporales, estacionales, direccionales y de oleaje elevado.
7. Análisis exploratorio de la relación entre oleaje y tráficos portuarios.
8. Ajuste de funciones lineales entre horas con Hs ≥ 3 m y restricciones operativas.
9. Comparación, validación cronológica y selección de modelos de series temporales.
10. Proyección estacional para 2027 e interpretación como apoyo a la planificación portuaria.

El estudio se basa en datos observacionales. Por ello, los análisis se orientan a identificar asociaciones, patrones temporales y coincidencias entre variables, sin establecer relaciones causales automáticas.

## Fuentes de datos
=======
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
>>>>>>> b84ab41a95d1ba3a51fdeaf71f0b744c97104551

La información procede de fuentes públicas de Puertos del Estado e incluye datos oceanográficos y registros mensuales de actividad portuaria.

<<<<<<< HEAD
### Series de oleaje

Se utilizaron cuatro series históricas de boyas:

- Gijón Costera (`1117`)
- Cabo de Peñas (`2242`)
- Bilbao Costera (`1103`)
- Bilbao-Vizcaya (`2136`)

El conjunto oceanográfico está formado por 610.438 registros horarios de oleaje. Las boyas costeras se emplean como referencia principal para la integración con los indicadores portuarios. Las boyas exteriores se utilizan para contextualizar las condiciones de oleaje en mar abierto y contrastar los patrones observados.

### Registros portuarios

Se utilizaron 480 registros mensuales de actividad portuaria:

- 240 registros correspondientes al puerto de Gijón.
- 240 registros correspondientes al puerto de Bilbao.

Las variables empleadas son:

- horas de restricción operativa;
- tráfico de granel sólido;
- tráfico de granel líquido;
- mercancía general;
- movimiento de contenedores expresado en TEU.

## Dataset oceanográfico principal

El dataset principal integra las series de oleaje en una estructura común, conservando la identificación y tipología de cada estación.

Las variables principales incluyen:

- fecha y hora;
- código y nombre de boya;
- tipo de boya;
- altura significativa de ola (`Hs_m`);
- altura máxima de ola;
- periodo medio;
- periodo de pico;
- dirección media y dirección de pico del oleaje.

La variable principal del estudio es la altura significativa de ola. A partir de ella se calculan indicadores mensuales, estacionales y de superación de umbrales.

## Preparación e integración de los datos

La preparación de los datos incluye las siguientes tareas:

- revisión de la estructura y de los tipos de datos;
- transformación de valores ausentes identificados con el código `-9999.9` a valores nulos;
- normalización de nombres de variables y formatos temporales;
- integración de las cuatro boyas en un dataset común;
- verificación de la cobertura temporal mensual;
- exclusión de los meses con una cobertura inferior al 70 % de las horas teóricas para los análisis históricos mensuales;
- agregación de los registros horarios de oleaje a escala mensual;
- organización de los registros portuarios mediante una fecha mensual común;
- integración de los indicadores de oleaje de cada boya costera con los datos de actividad del puerto correspondiente.

La unidad temporal común de análisis es el mes, ya que permite combinar la información horaria de oleaje con los registros mensuales de actividad portuaria.

## Indicadores construidos

A partir de las series horarias se generan indicadores de:

- intensidad y distribución de la altura significativa de ola;
- evolución mensual, estacional y anual del oleaje;
- frecuencia de superación de los umbrales Hs ≥ 2 m, Hs ≥ 3 m y Hs ≥ 5 m;
- número, duración e intensidad de los episodios continuados de oleaje elevado;
- distribución direccional del oleaje;
- número de horas mensuales con Hs ≥ 3 m.

El umbral Hs ≥ 3 m se emplea como referencia analítica común para identificar periodos de oleaje elevado. No constituye un límite operativo oficial aplicable de forma general a todos los puertos, maniobras o zonas de operación.
=======
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
>>>>>>> b84ab41a95d1ba3a51fdeaf71f0b744c97104551

El proceso de preparación incluye la conversión de los códigos de ausencia a valores nulos, la normalización de los nombres de las variables, la transformación de la fecha al formato temporal adecuado y la revisión de duplicados, cobertura temporal y discontinuidades.

<<<<<<< HEAD
El análisis se estructura en los siguientes bloques:

- limpieza y control de calidad de los datos;
- análisis descriptivo de las series de oleaje;
- análisis temporal, mensual, estacional y anual;
- identificación de episodios continuados de oleaje elevado;
- análisis direccional;
- caracterización descriptiva de los indicadores de tráfico;
- análisis exploratorio de las coincidencias temporales entre oleaje elevado y tráficos;
- regresión lineal simple entre las horas mensuales con Hs ≥ 3 m y las horas de restricción operativa;
- comparación de modelos de series temporales para estimar las horas mensuales con Hs ≥ 3 m.

Los ajustes lineales se realizan de forma independiente para Gijón y Bilbao. La variable explicativa es el número de horas mensuales con Hs ≥ 3 m y la variable respuesta son las horas mensuales de restricción operativa.

## Validación y proyección para 2027

La validación de los modelos de series temporales se realiza de forma cronológica:

- periodo de entrenamiento: 2005–2021;
- periodo de evaluación: 2022–2024.

Tras comparar el comportamiento de los modelos mediante métricas de error, se selecciona el modelo con mejor desempeño y se reajusta con la serie completa disponible entre 2005 y 2024.

La proyección mensual resultante para 2027 se utiliza como referencia para estimar las horas con Hs ≥ 3 m y, mediante las funciones lineales ajustadas, generar una estimación orientativa de las restricciones operativas asociadas. Esta salida está destinada a apoyar la planificación estacional de recursos, maniobras y trabajos exteriores; no constituye una previsión operativa en tiempo real.
=======
Posteriormente, se realizan análisis descriptivos y gráficos para estudiar la distribución de las variables, las diferencias entre boyas y la evolución temporal de Hs. También se calculan medias, percentiles, máximos e indicadores mensuales, estacionales y anuales.

Los episodios potencialmente adversos se identifican a partir de umbrales exploratorios de Hs. Estos indicadores permiten estudiar su frecuencia, duración y distribución temporal, pero no representan límites oficiales de operatividad portuaria.

El análisis direccional agrupa la procedencia del oleaje en sectores y evalúa tanto su frecuencia como la relación entre cada dirección y los valores de Hs registrados.

## Predicción estadística y priorización para 2027

La predicción se realiza a escala mensual, ya que el objetivo es caracterizar la exposición marítima esperada a medio plazo y no generar predicciones meteorológicas diarias.

Para cada boya se construye una serie mensual de Hs media. Los meses con una cobertura horaria inferior al 70 % se identifican como incompletos y se imputan mediante la mediana histórica del mismo mes únicamente para disponer de una serie regular que pueda utilizarse en el modelo.

La selección del método predictivo se realiza mediante una validación cronológica. Se utilizan los datos disponibles entre 2005 y 2021 para estimar los 36 meses de 2022 a 2024. Se comparan una referencia estacional sencilla y un modelo Holt-Winters aditivo con tendencia amortiguada, seleccionando para cada boya la alternativa con menor error absoluto medio.

Finalmente, el método seleccionado se ajusta con toda la serie histórica disponible entre 2005 y 2024 y se genera una proyección mensual para el periodo 2025–2027. La dirección de oleaje se presenta como el sector históricamente más frecuente para cada mes, por lo que constituye una referencia climatológica y no un pronóstico direccional.

Los resultados se sintetizan en una priorización mensual de la exposición marítima. Esta priorización puede servir de apoyo para la planificación estacional de trabajos, recursos y actividades sensibles al oleaje. No sustituye las predicciones oficiales de corto plazo, los estudios de agitación portuaria ni los criterios técnicos aplicables a cada operación.
>>>>>>> b84ab41a95d1ba3a51fdeaf71f0b744c97104551
