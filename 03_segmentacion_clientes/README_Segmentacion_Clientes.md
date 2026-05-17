# Segmentación de Clientes con PCA y K-Means — Wholesale Customers

Análisis de comportamiento de compra de clientes mayoristas para identificar segmentos con patrones de gasto similares. El proyecto aplica reducción de dimensionalidad y clustering no supervisado a un dataset real del repositorio UCI Machine Learning.

## ¿Qué problema resuelve?

Un proveedor mayorista necesita entender qué tipos de clientes tiene para personalizar su oferta comercial. El análisis transforma 6 variables de gasto anual (productos frescos, lácteos, abarrotes, congelados, detergentes, delicatessen) en segmentos accionables.

## Técnicas y herramientas

- **EDA**: distribución de variables, análisis por canal (HoReCa vs. Retail) y región (Lisboa, Oporto)
- **Visualización**: histogramas, pairplots con `seaborn`, gráficas de barras comparativas
- **Preprocesamiento**: `StandardScaler` para normalización, manejo de columnas categóricas
- **Reducción de dimensionalidad**: PCA con análisis de varianza explicada por componente
- **Clustering**: K-Means con visualización interactiva de clusters en espacio PCA

## Estructura del proyecto

```
Segmentacion_Clientes/
├── Segmentacion_de_clientes.ipynb   # Notebook principal
├── data/
│   └── Wholesale customers data.csv
└── README.md
```

## Cómo ejecutar

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
jupyter notebook Segmentacion_de_clientes.ipynb
```

## Flujo del análisis

```
Carga de datos (UCI) → Limpieza y mapeo de variables
→ EDA (distribuciones, pairplot) → StandardScaler
→ PCA (varianza explicada) → K-Means
→ Visualización e interpretación de segmentos
```

## Resultados principales

- Segmentación de clientes en grupos con perfiles de gasto diferenciados
- Identificación de los componentes principales que explican mayor varianza
- Perfiles de segmento: clientes con alto gasto en frescos vs. clientes con alto gasto en abarrotes y detergentes

## Fuente de datos

UCI Machine Learning Repository — Wholesale Customers Dataset  
Cardoso, M. (2014). [https://archive.ics.uci.edu/dataset/292/wholesale+customers](https://archive.ics.uci.edu/dataset/292/wholesale+customers)

## Librerías

`pandas` `numpy` `scikit-learn` `matplotlib` `seaborn`
