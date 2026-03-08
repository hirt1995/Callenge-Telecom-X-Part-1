# 📊 Telecom X — Análisis de Evasión de Clientes (Churn)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12%2B-4C72B0)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?logo=googlecolab)
![Status](https://img.shields.io/badge/Status-Completado-brightgreen)

---

## 📌 Descripción del Proyecto

**Telecom X** enfrenta una alta tasa de cancelaciones y necesita comprender los factores que llevan a la pérdida de clientes. Este proyecto realiza un análisis completo de evasión de clientes (Churn) utilizando Python, desde la extracción de datos hasta la generación de insights y recomendaciones estratégicas.

> 🎯 **Objetivo:** Identificar patrones de comportamiento que permitan predecir y reducir la evasión de clientes.

---

## 🗂️ Estructura del Proyecto

```
telecomx-churn-analysis/
│
├── TelecomX_Analisis.ipynb      # Notebook principal con todo el análisis
├── README.md                    # Este archivo
└── assets/                      # Gráficas exportadas (opcional)
```

---

## 🔄 Flujo del Análisis

```
1. Extracción de Datos (API)
        ↓
2. Comprobación de Incoherencias
        ↓
3. Manejo de Inconsistencias
        ↓
4. Creación de Columna Cuentas_Diarias
        ↓
5. Estandarización y Transformación
        ↓
6. Análisis Descriptivo
        ↓
7. Distribución de Evasión
        ↓
8. Informe Final + Recomendaciones
```

---

## 📥 Fuente de Datos

Los datos fueron obtenidos desde la API pública del proyecto:

```
https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/main/TelecomX_Data.json
```

El dataset contiene información de **~7.000 clientes** con variables demográficas,
tipo de servicios contratados y estado de evasión.

---

## 🧹 Limpieza y Tratamiento de Datos

| Problema detectado | Acción aplicada |
|---|---|
| Nulos disfrazados (`'none'`, `'null'`, `'-'`) | Reemplazados por `NaN` real |
| Columna `Churn` con 224 NaN | Filas eliminadas — no se imputa la variable objetivo |
| `Charges.Total` almacenado como texto | Convertida a numérico — NaN → mediana |
| Espacios en blanco en columnas de texto | Eliminados con `.str.strip()` |
| Capitalización inconsistente | Estandarizada con `.str.capitalize()` |
| Filas duplicadas | Eliminadas con `drop_duplicates()` |

---

## 🔠 Transformaciones Aplicadas

- ✅ Columnas renombradas al español para mayor claridad
- ✅ Valores categóricos traducidos (`Fiber optic` → `Fibra Optica`, etc.)
- ✅ Variables binarias convertidas a `1 / 0`
- ✅ Nueva columna **`Cargo_Diario`** = `Cargo_Mensual ÷ 30`

---

## 📊 Principales Hallazgos

### Variables Numéricas

| Variable | Clientes que se quedaron | Clientes que se fueron |
|---|---|---|
| 💰 Cargo mensual promedio | Menor | **Mayor** |
| 📅 Permanencia promedio | Mayor (más meses) | **Menor (clientes nuevos)** |

### Variables Categóricas

- 🔴 **Contrato mes a mes** → Mayor tasa de evasión
- 🔴 **Sin servicios adicionales** (seguridad, soporte, backup) → Mayor riesgo
- 🔴 **Pago por cheque electrónico** → Asociado a mayor abandono
- 🟢 **Contratos anuales / bianuales** → Alta retención
- 🟢 **Múltiples servicios contratados** → Mayor fidelización

---

## 🚀 Recomendaciones Estratégicas

1. **Incentivar contratos anuales** con descuentos para reducir la evasión por contratos mes a mes
2. **Programa de onboarding** en los primeros 3 meses — los clientes nuevos son los más vulnerables
3. **Revisar precios altos** — ofrecer planes personalizados a clientes en riesgo
4. **Promover servicios adicionales** — más servicios = mayor vinculación = menor evasión
5. **Modelo predictivo de Churn** como siguiente paso (Random Forest, XGBoost, Regresión Logística)

---

## 🛠️ Tecnologías Utilizadas

| Librería | Uso |
|---|---|
| `Pandas` | Manipulación y limpieza de datos |
| `NumPy` | Operaciones numéricas |
| `Matplotlib` | Visualizaciones base |
| `Seaborn` | Visualizaciones estadísticas |
| `Requests` | Extracción de datos desde la API |
| `IPython` | Renderizado de informe en Markdown |

---

## ▶️ Cómo ejecutar el proyecto

1. Abre el notebook en **Google Colab**:

   [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

2. Ejecuta las celdas en orden — cada paso está claramente documentado.

3. No requiere instalaciones adicionales. Todas las librerías están disponibles en Google Colab.

---

## 📁 Variables del Dataset

| Variable | Descripción |
|---|---|
| `ID_Cliente` | Identificador único del cliente |
| `Genero` | Género del cliente |
| `Adulto_Mayor` | Si el cliente es adulto mayor (1/0) |
| `Tiene_Pareja` | Si tiene pareja (1/0) |
| `Tiene_Dependientes` | Si tiene dependientes (1/0) |
| `Meses_Contratado` | Meses de permanencia en la empresa |
| `Tipo_Contrato` | Mes a Mes / Un Año / Dos Años |
| `Tipo_Internet` | DSL / Fibra Optica / Sin Internet |
| `Cargo_Mensual` | Cargo mensual en USD |
| `Cargo_Total` | Cargo total acumulado en USD |
| `Cargo_Diario` | Cargo diario calculado (Mensual ÷ 30) |
| `Evasion` | Variable objetivo — 1: se fue, 0: se quedó |

---

## 👤 Autor

Proyecto desarrollado como parte del **Challenge 2 — Data Science LATAM**

---

## 📄 Licencia

Este proyecto es de uso educativo y fue desarrollado con fines de aprendizaje y práctica en análisis de datos.
