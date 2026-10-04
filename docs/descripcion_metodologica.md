# Descripción metodológica

Este documento resume la metodología técnica aplicada en el Trabajo Fin de Máster `TFM-BigData-ClimaMaritimoCantabrico`.

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

La información procede de fuentes públicas de Puertos del Estado e incluye datos oceanográficos y registros mensuales de actividad portuaria.

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

## Enfoque de análisis

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