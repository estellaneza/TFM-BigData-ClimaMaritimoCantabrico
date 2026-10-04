# TFM Big Data: clima marítimo y gestión portuaria cantábrica

<<<<<<< HEAD
Repositorio asociado al Trabajo Fin de Máster centrado en el análisis de series temporales de oleaje y su aplicación como apoyo a la planificación portuaria en los entornos de Gijón y Bilbao.

El proyecto integra información oceanográfica procedente de boyas de Puertos del Estado con datos mensuales de actividad portuaria. El análisis estudia la exposición al oleaje, su relación exploratoria con los principales tráficos y su asociación con las restricciones operativas registradas en ambos puertos.

## Objetivo

Transformar datos históricos de oleaje en indicadores temporales, direccionales y operativos que permitan caracterizar la exposición marítima de Gijón y Bilbao.

De forma específica, el proyecto:

- analiza la evolución temporal, estacional y direccional del oleaje;
- identifica episodios de oleaje elevado mediante umbrales exploratorios de altura significativa de ola;
- integra los indicadores de oleaje con los tráficos portuarios y las horas de restricción operativa;
- examina la asociación entre las horas mensuales con Hs ≥ 3 m y las restricciones operativas;
- desarrolla una proyección estacional de las horas mensuales con Hs ≥ 3 m para 2027.

La proyección tiene carácter orientativo y está diseñada como apoyo a la planificación estacional. No sustituye la evaluación meteorológica u operativa en tiempo real.

## Datos

Los datos proceden de fuentes públicas de Puertos del Estado y cubren el periodo comprendido entre enero de 2005 y diciembre de 2024.

### Información oceanográfica

- Registros analizados: 610.438 observaciones horarias.
- Boyas: Gijón Costera, Cabo de Peñas, Bilbao Costera y Bilbao-Vizcaya.
- Variables principales: altura significativa de ola (`Hs_m`), altura máxima, periodo medio, periodo de pico y dirección del oleaje.
- Boyas empleadas en la integración portuaria: Gijón Costera y Bilbao Costera.
- Boyas exteriores utilizadas como contexto: Cabo de Peñas y Bilbao-Vizcaya.

### Información portuaria

- Registros analizados: 480 observaciones mensuales.
- Puertos: Gijón y Bilbao.
- Variables: horas de restricción operativa, granel sólido, granel líquido, mercancía general y contenedores expresados en TEU.

## Metodología resumida

El flujo de trabajo se organiza de acuerdo con una adaptación de CRISP-DM:

1. Carga, revisión y limpieza de las fuentes originales.
2. Normalización e integración de las series de oleaje.
3. Construcción de indicadores temporales, direccionales y de episodios elevados.
4. Preparación e integración mensual de los datos portuarios.
5. Análisis exploratorio de la relación entre oleaje, tráficos y restricciones.
6. Ajuste de modelos lineales simples entre horas con Hs ≥ 3 m y restricciones operativas.
7. Comparación y validación cronológica de modelos de series temporales.
8. Proyección estacional para 2027 y elaboración de indicadores de planificación.

El umbral Hs ≥ 3 m se utiliza como referencia analítica común para identificar periodos de oleaje elevado. No representa un límite operativo oficial aplicable de forma general a todas las maniobras, buques o zonas portuarias.

## Notebooks

1. `01_carga_limpieza_datos.ipynb`  
   Carga de las fuentes, revisión de estructura, tratamiento de valores ausentes y construcción del dataset principal de oleaje.

2. `02_analisis_exploratorio.ipynb`  
   Estadísticos descriptivos, distribuciones y revisión inicial de las variables oceanográficas.

3. `03_indicadores_temporales.ipynb`  
   Construcción de indicadores mensuales, estacionales y anuales de oleaje.

4. `04_episodios_adversos.ipynb`  
   Identificación de episodios continuados de oleaje elevado y cálculo de frecuencia, duración e intensidad.

5. `05_analisis_direccional.ipynb`  
   Caracterización de la procedencia del oleaje y relación descriptiva entre dirección e intensidad.

6. `06_caracterizacion_trafico.ipynb`  
   Preparación y análisis descriptivo de los indicadores mensuales de actividad portuaria.

7. `07_oleaje_elevado_restricciones.ipynb`  
   Integración de oleaje y actividad portuaria; análisis exploratorio de tráficos y ajuste de regresiones lineales para las restricciones operativas.

8. `08_prediccion_horas_hs3_restricciones_2027.ipynb`  
   Validación cronológica de modelos de series temporales, proyección de horas con Hs ≥ 3 m para 2027 y estimación orientativa de restricciones operativas.

## Estructura del repositorio

```text
data/
├── raw/                Datos originales
└── processed/          Datos tratados e indicadores generados

notebooks/              Notebooks de análisis secuencial

outputs/
├── figures/            Figuras generadas
└── tables/             Tablas y resultados exportados

docs/                   Documentación complementaria del proyecto
```

## Tecnologías utilizadas

El proyecto se ha desarrollado en Python mediante notebooks de Jupyter.

Principales librerías:

- `pandas` y `NumPy` para carga, transformación y análisis de datos;
- `Matplotlib` y `Seaborn` para visualización;
- `SciPy` y `scikit-learn` para análisis estadístico, regresión y métricas de evaluación;
- `statsmodels` para la modelización de series temporales.

## Reproducibilidad

Los notebooks deben ejecutarse en orden numérico, ya que las etapas posteriores utilizan los conjuntos de datos procesados y los indicadores generados anteriormente.

La organización del repositorio mantiene la trazabilidad entre los datos originales, las transformaciones aplicadas y los resultados obtenidos. Los archivos generados se almacenan en las carpetas `data/processed/` y `outputs/`.

## Limitaciones

Las observaciones de las boyas representan las condiciones registradas en la ubicación de cada sensor y no reproducen directamente la agitación existente dentro de las dársenas portuarias.

Asimismo, el análisis de los tráficos tiene carácter exploratorio: las variaciones de actividad portuaria pueden estar influidas por factores económicos, comerciales, industriales y logísticos no incluidos en el modelo.
=======
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
docs/              Documentación del proyecto
```

## Reproducibilidad

Los notebooks deben ejecutarse en orden numérico. Cada notebook utiliza los datos procesados generados en las etapas anteriores y guarda automáticamente sus figuras y tablas en `outputs/`.


>>>>>>> b84ab41a95d1ba3a51fdeaf71f0b744c97104551
