# Predicción de Rotación de Personal con SQLite + Random Forest + SHAP

Caso de consultoría simulado: modelo de clasificación para predecir qué empleados tienen mayor probabilidad de renunciar, combinando exploración de datos con SQL y Machine Learning interpretable con SHAP values.

---

## ¿Qué problema resuelve?

Reemplazar a un empleado cuesta entre el 50% y el 200% de su salario anual. Este proyecto ayuda al área de Recursos Humanos a identificar empleados en riesgo **antes de que renuncien**, priorizando intervenciones de retención donde más impactan.

## Preguntas de negocio respondidas

- ¿Qué departamentos tienen la mayor tasa de rotación?
- ¿Qué perfil de empleado tiene mayor riesgo de irse?
- ¿Qué variables impactan más en la decisión de renunciar?
- ¿Con qué precisión puede predecirse la rotación?

---

## Flujo del proyecto

```
CSV → SQLite → Consultas de negocio (SQL)
→ Visualización → Random Forest → Evaluación → SHAP → Recomendaciones
```

---

## Hallazgos principales

- **Sales** es el departamento con mayor tasa de rotación (>20%)
- Los empleados con **horas extra + baja satisfacción + menos de 3 años** en la empresa representan el grupo de mayor riesgo
- Las variables con mayor impacto según SHAP: `OverTime`, `MonthlyIncome`, `Age`, `JobSatisfaction`, `YearsAtCompany`
- El modelo alcanza un **ROC-AUC > 0.80**, con buena capacidad para identificar renuncias antes de que ocurran

## Recomendaciones de negocio

1. Programa de retención focalizado en empleados de Sales con horas extra
2. Revisión salarial en los 3 puestos con menor ingreso promedio
3. Encuesta de clima a empleados con menos de 2 años y satisfacción ≤ 2
4. Monitoreo mensual con score de riesgo por empleado generado por el modelo

---

## Técnicas y herramientas

| Etapa | Herramienta |
|---|---|
| Base de datos | SQLite (`sqlite3`) |
| Consultas de negocio | SQL (7 queries con agregaciones, CASE WHEN, filtros) |
| Limpieza y EDA | pandas |
| Visualización | Seaborn, Matplotlib |
| Modelo | Random Forest (`scikit-learn`) con `class_weight="balanced"` |
| Evaluación | Classification Report, Matriz de Confusión, ROC-AUC |
| Interpretabilidad | SHAP TreeExplainer — summary plot por importancia |

## Métricas del modelo

| Métrica | Valor |
|---|---|
| ROC-AUC | > 0.80 |
| Clase mayoritaria (Se quedó) | Alta precisión |
| Clase minoritaria (Se fue) | Balanceada con `class_weight` |

---

## Estructura del repositorio

```
07_rotacion_personal_ibm/
├── IBM_HR_Attrition_SQLite_ML.ipynb   # Notebook principal
├── data/
│   └── instrucciones_descarga.md      # El CSV se descarga desde Kaggle
├── img/
│   ├── rotacion_departamento.png
│   ├── confusion_matrix.png
│   └── shap_importancia.png
└── README.md
```

## Cómo ejecutar

1. Descarga el dataset desde [Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
2. Sube el archivo `WA_Fn-UseC_-HR-Employee-Attrition.csv` a tu entorno
3. Ejecuta las celdas en orden — no requiere instalaciones adicionales en Google Colab

## Dataset

IBM HR Analytics Employee Attrition & Performance  
Kaggle — [Ver dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)  
1,470 registros · 35 variables · Dataset sintético generado por IBM

---

## Librerías

`sqlite3` `pandas` `numpy` `scikit-learn` `shap` `matplotlib` `seaborn`
