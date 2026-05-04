# 🏦 Predicción de Abandono de Clientes Bancarios con Deep Learning

Proyecto final del curso **Modelos de Deep Learning: Aplicaciones Prácticas**  
Especialización en Inteligencia Artificial Aplicada a los Negocios | Centrum PUCP

---

## 📌 Objetivo del Proyecto

El abandono de clientes (*churn*) es uno de los principales problemas de rentabilidad en la industria bancaria. Adquirir un cliente nuevo cuesta hasta 5 veces más que retener a uno actual. Sin embargo, la mayoría de bancos actúan de forma reactiva — se enteran del abandono cuando el cliente ya tomó la decisión.

Este proyecto construye una **Red Neuronal Multicapa (MLP)** con TensorFlow/Keras que predice la probabilidad de abandono de cada cliente, permitiendo al banco actuar de forma **proactiva** antes de que el cliente decida irse.

---

## 📊 Dataset

- **Fuente:** [Kaggle — Churn for Bank Customers](https://www.kaggle.com/datasets/mathchi/churn-for-bank-customers)
- **Registros:** 10,000 clientes de un banco europeo
- **Variables:** 11 variables predictoras
- **Tasa de abandono:** 20% (dataset desbalanceado)

| Variable | Descripción |
|---|---|
| CreditScore | Puntaje crediticio del cliente |
| Geography | País del cliente (Francia, Alemania, España) |
| Gender | Género del cliente |
| Age | Edad del cliente |
| Tenure | Años como cliente del banco |
| Balance | Saldo en cuenta |
| NumOfProducts | Número de productos contratados |
| HasCrCard | Si tiene tarjeta de crédito (1/0) |
| IsActiveMember | Si es miembro activo (1/0) |
| EstimatedSalary | Salario estimado |
| **Exited** | **Variable objetivo: 1 = abandonó, 0 = se quedó** |

---

## 🛠️ Tecnologías Utilizadas

- **Python 3**
- **TensorFlow / Keras** — construcción y entrenamiento de la red neuronal
- **Scikit-learn** — preprocesamiento, división de datos y métricas
- **Pandas / NumPy** — manipulación de datos
- **Matplotlib / Seaborn** — visualizaciones
- **Google Colab** — entorno de desarrollo

---

## ⚙️ Pipeline del Proyecto

```
1. Carga de datos        →  Descarga del dataset desde Kaggle via API
2. Exploración (EDA)     →  Análisis de distribuciones y balance de clases
3. Preprocesamiento      →  Encoding de variables categóricas y escalado
4. División 80/20        →  Train/Test split con estratificación
5. Entrenamiento MLP     →  Red neuronal con Dropout y Early Stopping
6. Evaluación            →  Métricas: Accuracy, AUC-ROC, Precision, Recall, F1
7. Interpretación        →  Permutation Importance para variables clave
```

---

## 🧠 Arquitectura del Modelo

```
Capa de Entrada   →  10 neuronas (una por variable)
Capa Oculta 1     →  64 neuronas | Activación: ReLU | Dropout: 30%
Capa Oculta 2     →  32 neuronas | Activación: ReLU | Dropout: 20%
Capa Oculta 3     →  16 neuronas | Activación: ReLU
Capa de Salida    →   1 neurona  | Activación: Sigmoid
```

**Configuración de entrenamiento:**
- Optimizador: Adam
- Función de pérdida: Binary Crossentropy
- Épocas máximas: 50
- Batch size: 32
- Early Stopping: patience=10

---

## 📈 Resultados

| Métrica | Valor |
|---|---|
| **Accuracy** | 86.05% |
| **AUC-ROC** | 85.66% |
| **Precision** | 77.35% |
| **Recall** | 44.47% |
| **F1-Score** | 56.47% |

El AUC-ROC de 0.857 confirma que el modelo tiene una capacidad sólida para distinguir entre clientes que abandonan y los que se quedan, muy por encima del 0.5 que representaría una predicción aleatoria.

---

## 🔍 Variables Más Influyentes

Analizadas mediante **Permutation Importance** — mide cuánto empeora el modelo al desordenar cada variable:

| Variable | Impacto | Interpretación |
|---|---|---|
| **NumOfProducts** | 12.8 | Pocos productos = menos vínculos con el banco = mayor riesgo |
| **Age** | 11.3 | Clientes mayores tienden a irse por cambios en sus necesidades |
| **IsActiveMember** | 3.1 | Clientes inactivos no usan el banco, no les cuesta irse |

---

## 🚀 Cómo Ejecutar el Notebook

1. Abre el archivo `.ipynb` en **Google Colab**
2. Ejecuta las celdas en orden de arriba hacia abajo (`Shift + Enter`)
3. En la celda de carga de datos, asegúrate de tener tus credenciales de Kaggle configuradas
4. Todos los outputs — gráficos, métricas y resultados — se generan automáticamente

> **Nota:** El notebook ya incluye todos los outputs ejecutados. No es necesario volver a ejecutarlo para ver los resultados.

---

## 💡 Conclusión y Valor para el Negocio

El modelo transforma al banco de **reactivo a proactivo**. En lugar de esperar a que el cliente cierre su cuenta, el modelo asigna una probabilidad de abandono a cada cliente, permitiendo:

- **Alertas tempranas** integradas al CRM del banco
- **Campañas personalizadas** dirigidas a clientes de alto riesgo
- **Optimización de recursos** — enfocando retención donde más se necesita
- **Fidelización preventiva** — especialmente para clientes mayores con pocos productos

---

## 👤 Arturo Correa L.

**Guillermo Arturo Correa Lama**  
Especialización en IA Aplicada a los Negocios | Centrum PUCP  
Mayo 2026
