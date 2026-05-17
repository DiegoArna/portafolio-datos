# Segmentación de Zonas de Alta Incidencia Delictiva en México con K-Means

Aplicación de clustering no supervisado a datos de víctimas del fuero común en México para identificar grupos de estados con patrones delictivos similares. El análisis combina reducción de dimensionalidad con PCA y visualización geoespacial interactiva con Folium.

## ¿Qué problema resuelve?

Identificar qué entidades federativas comparten perfiles de victimización similares, con el objetivo de apoyar la priorización de recursos y políticas de seguridad pública diferenciadas por cluster.

La pregunta central: ¿existen grupos naturales de estados con comportamiento delictivo homogéneo que no sean evidentes a simple vista?

## Técnicas y herramientas

- **Análisis exploratorio**: correlación por pares (`seaborn.heatmap`), pairplot de variables clave
- **Limpieza de datos**: eliminación de valores nulos en columnas críticas, descarte de variables con baja varianza
- **Normalización**: `MinMaxScaler` de sklearn para escalar variables al rango [0, 1]
- **Reducción de dimensionalidad**: PCA a 2 componentes para visualización del espacio de características
- **Clustering**: K-Means con selección de K mediante método del codo
- **Visualización geoespacial**: mapas interactivos con `folium` y geocodificación automática con `geopy`
- **Visualización de clusters**: `plotly.graph_objects` para scatter plots interactivos

## Estructura del proyecto

```
Delitos_Clustering/
├── Delitos_vs_Clustering.ipynb   # Notebook principal
├── data/
│   └── TMod_Vic_Columnas_filtradas.csv
└── README.md
```

## Cómo ejecutar

```bash
pip install pandas numpy scikit-learn seaborn matplotlib plotly folium geopy
jupyter notebook Delitos_vs_Clustering.ipynb
```

Actualizar la ruta del archivo CSV en la segunda celda del notebook.

## Flujo del análisis

```
Carga de datos → EDA (correlaciones, pairplot) → Limpieza
→ Normalización MinMaxScaler → PCA (2 componentes)
→ K-Means (selección de K) → Visualización de clusters
→ Mapa interactivo Folium
```

## Resultados principales

- Identificación de K grupos de entidades con patrones de victimización similares
- Mapa interactivo con cada estado coloreado por cluster
- Perfiles descriptivos por cluster: variables dominantes en cada grupo

## Fuente de datos

Encuesta Nacional de Victimización y Percepción sobre Seguridad Pública (ENVIPE) — INEGI

## Librerías

`pandas` `numpy` `scikit-learn` `seaborn` `matplotlib` `plotly` `folium` `geopy`
