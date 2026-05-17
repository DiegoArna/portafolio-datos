# Análisis Geoespacial y Temporal de Delitos en CDMX (2020–2023)

Análisis de la evolución de delitos por alcaldía en la Ciudad de México usando datos abiertos de la Fiscalía General de Justicia (FGJ). El proyecto combina series de tiempo, estadística descriptiva y mapas geoespaciales para identificar tendencias y zonas de mayor incidencia.

## ¿Qué problema resuelve?

Responder cómo ha evolucionado la incidencia delictiva por alcaldía entre 2020 y 2023, identificando qué zonas concentran más delitos, cómo se distribuyen por colonia y si existen patrones temporales significativos.

Caso de estudio específico: análisis a nivel colonia en la alcaldía Iztapalapa, la más poblada de CDMX.

## Técnicas y herramientas

- **Carga y limpieza de datos multi-año**: función parametrizada `cargar_delitos_anual` para procesar archivos CSV por año de forma consistente
- **Series de tiempo**: evolución de delitos por alcaldía y año con visualización multi-serie
- **Estadística descriptiva**: boxplots y histogramas de distribución por año (`seaborn`)
- **Análisis geoespacial**: lectura y procesamiento de shapefiles con `geopandas`
- **Georreferenciación**: asignación de puntos de delito (latitud/longitud) a polígonos de colonia con `shapely`
- **Visualización de mapas**: distribución espacial de delitos por colonia

## Estructura del proyecto

```
Serie_Tiempo_Delitos_CDMX/
├── Serie_de_tiempo_vs_Violencia.ipynb   # Notebook principal
├── data/
│   ├── victimasFGJ_2020.csv
│   ├── victimasFGJ_2021.csv
│   ├── victimasFGJ_2022.csv
│   ├── victimasFGJ_2023.csv
│   └── colonias_iecm2022/              # Shapefile de colonias CDMX
│       └── colonias_iecm2022_.shp
└── README.md
```

## Cómo ejecutar

```bash
pip install pandas matplotlib seaborn geopandas shapely itertools
jupyter notebook Serie_de_tiempo_vs_Violencia.ipynb
```

Actualizar las rutas de los archivos CSV y el shapefile en las celdas de carga de datos.

## Fuente de datos

- **Víctimas en carpetas de investigación FGJ CDMX**: [datos.cdmx.gob.mx](https://datos.cdmx.gob.mx/dataset/victimas-en-carpetas-de-investigacion-fgj)
- **Shapefile de colonias CDMX**: Instituto Electoral de la Ciudad de México (IECM), 2022

## Resultados principales

- Serie de tiempo de delitos por alcaldía: 2020–2023
- Distribución estadística por año (boxplot y histograma)
- Mapa de calor de delitos por colonia en Iztapalapa

## Librerías

`pandas` `matplotlib` `seaborn` `geopandas` `shapely`
