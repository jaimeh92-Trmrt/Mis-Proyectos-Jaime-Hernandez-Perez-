🗺️ Análisis Espacial Avanzado: Efecto Borde y Sesgos de Muestreo en la Biodiversidad de Canarias (2000 - 2026)
📌 Descripción del Proyecto
Este proyecto de investigación personal evalúa de forma cuantitativa la proximidad de la biodiversidad registrada en las Islas Canarias respecto a la infraestructura viaria principal y secundaria. El objetivo inicial era medir el impacto del "Efecto Borde" (edge effect) sobre tres grupos taxonómicos (Aves, Artrópodos y Plantas Vasculares).

Sin embargo, tras procesar Big Data espacial (+1.1 millones de registros), el análisis evolucionó hacia una auditoría metodológica crítica. Mediante el uso de un modelo nulo de control geográfico y una comparativa inter-taxonómica, el proyecto demuestra cómo la fragmentación del territorio insular y los sesgos inherentes a la ciencia ciudadana pueden enmascarar o distorsionar los patrones ecológicos reales si los datos se analizan de forma ingenua.

🛠️ Stack Tecnológico y Herramientas GIS
Para optimizar los recursos computacionales y garantizar la precisión cartográfica, el pipeline de datos se dividió de forma híbrida:

R (v4.x) & RStudio: Tratamiento de Big Data, optimización de memoria RAM mediante filtrado por bloques (chunk processing), manipulación de datos espaciales (sf, tidyverse) y análisis estadístico y gráfico descriptivo avanzado (ggplot2).

QGIS (v3.x): Inspección de geometrías, control de calidad cartográfica mediante el filtrado de registros erróneos en el mar (spatial clip) y validación visual de la red viaria.

Geodatasets Utilizados:

GBIF (Global Biodiversity Information Facility): Datos de presencia biológica filtrados temporalmente desde el año 2000 hasta la actualidad (2026).

Geofabrik / OpenStreetMap: Capa vectorial de carreteras completas del archipiélago (canary-islands-260607-free.shp / subcapa gis_osm_roads_free_1).

📁 Estructura del Repositorio
Para garantizar la replicabilidad del análisis, el proyecto se organiza de la siguiente manera:
├── data/
│   ├── raw/                 # Archivos originales de GBIF y Geofabrik (No subidos por peso)
│   └── processed/           # Capas espaciales intermedias filtradas (.gpkg)
├── scripts/
│   ├── 01_data_cleaning.R   # Pipeline de lectura por chunks, filtrado temporal y espacial
│   ├── 02_hub_distance.R    # Cálculo geométrico de proximidad a carreteras (CRS: 32628)
│   └── 03_control_model.R   # Generación del modelo nulo aleatorio y analítica final
├── outputs/
│   ├── tables/              # Matrices estadísticas de resumen exportadas
│   └── plots/               # Gráficos de densidad generados (PNG de alta resolución)
└── README.md                # Documentación principal del proyecto
