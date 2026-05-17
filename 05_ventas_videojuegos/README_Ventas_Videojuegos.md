# Análisis de Ventas Globales de Videojuegos con Clustering

Exploración y segmentación de un dataset histórico de ventas de videojuegos a nivel global. El análisis identifica patrones de ventas por plataforma, género y región, y aplica clustering para agrupar títulos con perfiles de distribución de ventas similares.

## ¿Qué problema resuelve?

Entender qué combinaciones de plataforma y género generan mayores ventas por región, y si existen grupos naturales de videojuegos con comportamientos de venta homogéneos que puedan orientar decisiones de distribución.

## Técnicas y herramientas

- **EDA completo**: dimensiones, tipos de datos, valores nulos, estadísticas descriptivas
- **Análisis de frecuencias**: géneros y plataformas más populares con `seaborn.countplot`
- **Análisis de ventas por región**: distribución entre NA, EU, JP y otras regiones
- **Correlación**: heatmap de correlación entre variables de ventas regionales
- **Normalización**: `MinMaxScaler` para preparar datos para clustering
- **Reducción de dimensionalidad**: PCA estándar y Kernel PCA (`rbf`) para capturar relaciones no lineales
- **Clustering**: K-Means sobre componentes principales

## Estructura del proyecto

```
Ventas_Videojuegos/
├── Ventas_de_video_juegos.ipynb   # Notebook principal
├── data/
│   └── vgsales.csv
└── README.md
```

## Cómo ejecutar

```bash
pip install pandas numpy scikit-learn seaborn matplotlib
jupyter notebook Ventas_de_video_juegos.ipynb
```

El dataset `vgsales.csv` está disponible en [Kaggle — Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales).

## Flujo del análisis

```
Carga → EDA (shape, info, nulos) → Limpieza (dropna)
→ Análisis de género y plataforma → Ventas por región
→ Filtrado (2014–2020) → MinMaxScaler
→ PCA / Kernel PCA → K-Means → Visualización de clusters
```

## Resultados principales

- Géneros más vendidos: Action, Sports, Shooter
- Norteamérica concentra la mayor proporción de ventas globales
- Kernel PCA captura patrones no lineales no visibles con PCA estándar
- Clusters de videojuegos con perfiles de venta regionales diferenciados

## Fuente de datos

Kaggle — Video Game Sales with Ratings  
[https://www.kaggle.com/datasets/gregorut/videogamesales](https://www.kaggle.com/datasets/gregorut/videogamesales)

## Librerías

`pandas` `numpy` `scikit-learn` `seaborn` `matplotlib`
