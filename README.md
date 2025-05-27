# Bitcoin Price Prediction using LSTM and Genetic Algorithm

## 📌 Descripción del Proyecto
Este proyecto implementa un modelo de predicción de precios de Bitcoin utilizando una red neuronal LSTM (Long Short-Term Memory) combinada con un algoritmo genético para optimizar los hiperparámetros del modelo. El código carga datos históricos de Bitcoin, los preprocesa, entrena un modelo LSTM y utiliza un algoritmo genético para encontrar los mejores hiperparámetros.

---

## ✨ Características Principales
- **Preprocesamiento de datos**: Normalización de los precios de cierre de Bitcoin usando `MinMaxScaler`.
- **Generación de secuencias**: Creación de secuencias temporales para el entrenamiento del modelo LSTM.
- **Modelo LSTM**: Implementación de una red neuronal recurrente para predecir precios futuros.
- **Algoritmo genético**: Optimización de hiperparámetros como longitud de secuencia, tamaño de capa oculta, número de capas, `dropout` y tasa de aprendizaje.
- **Entrenamiento y evaluación**: División de datos en conjuntos de entrenamiento y validación, y cálculo de pérdida (`loss`).

---

## 📁 Estructura del Código

### 1. Preprocesamiento de Datos
- Carga el dataset `btcusd_1-min_data.csv`.
- Convierte la columna `Timestamp` a formato `datetime` y selecciona solo la columna `Close`.
- Normaliza los datos usando `MinMaxScaler`.

### 2. Creación de Secuencias
- La función `create_sequences` genera secuencias de datos para entrenar el modelo LSTM.
- Cada secuencia contiene `seq_len` valores históricos y el valor siguiente como etiqueta.

### 3. Modelo LSTM
- La clase `BitcoinLSTM` define la arquitectura de la red:
  - Capa LSTM configurable (tamaño de entrada, capas ocultas, `dropout`).
  - Capa lineal final para la predicción.

### 4. Algoritmo Genético
- La función `genetic_algorithm` busca los mejores hiperparámetros para el modelo:
  - **Población inicial**: Genera individuos con valores aleatorios para `seq_len`, `hidden_size`, `num_layers`, `dropout`, y `lr`.
  - **Fitness**: Entrena el modelo y calcula la pérdida en validación.
  - **Selección y reproducción**: Mejores individuos reproducen por cruce y mutación.

### 5. Entrenamiento del Modelo Final
- Se entrena el modelo usando los mejores hiperparámetros encontrados.
- Se evalúa el rendimiento del modelo en validación.

---

## 📊 Resultados
- El algoritmo genético encuentra la combinación óptima de hiperparámetros que minimiza la pérdida en el conjunto de validación.
- El modelo LSTM entrenado con estos parámetros mejora la capacidad de predecir precios futuros de Bitcoin con mayor precisión.

## Predicción de Series Temporales con LSTM y Optimización con Optuna
📌 1. Objetivo del proyecto
Predecir el precio futuro de Bitcoin utilizando una red LSTM, entrenada con datos históricos, y optimizar sus hiperparámetros para mejorar la precisión del modelo. Se usa Optuna como motor de optimización automática.

## 🧠 2. Contexto de Series Temporales
Una serie temporal es una secuencia de datos medidos en intervalos de tiempo constantes. En este caso:

El precio de Bitcoin está disponible por minuto, lo que forma una serie ordenada cronológicamente.

El modelo necesita capturar tendencias, patrones y dependencia temporal en los datos. Por eso se utiliza una red LSTM, que es capaz de recordar información a largo plazo y es ideal para series temporales.

## 🔧 3. Estructura del Código y Flujo General
## 3.1. 📦 Importación de librerías
torch, nn: Para construir y entrenar el modelo LSTM.

optuna: Para optimizar automáticamente los hiperparámetros.

sklearn: Para escalado, división de datos y métricas de error.

matplotlib: Para visualización.

pandas, numpy: Para manipulación de datos.

## 3.2. 📥 Carga y procesamiento de datos

Se cargan los precios de cierre de Bitcoin por minuto.

Se transforma la columna de tiempo UNIX a formato de fecha legible.

Se toma solamente el precio de cierre para la predicción.

## 3.3. 🔃 Normalización de datos

## 3.4. 🧩 Generación de secuencias

Se generan pares de entradas/salidas:

X: ventana de seq_len precios pasados.

y: el siguiente valor de la serie.

## 🧠 4. Modelo: BitcoinLSTM

## 🧪 5. Optuna: Optimización de Hiperparámetros

Se define la función objetivo para que Optuna explore automáticamente combinaciones de:

seq_len: longitud de la ventana temporal.

hidden_size: número de unidades en la LSTM.

num_layers: capas LSTM.

dropout: regularización.

lr: tasa de aprendizaje.

batch_size: tamaño de lote.

El modelo es entrenado por 20 épocas y evaluado por su error cuadrático medio (MSE) en validación.

## 🎯 6. Entrenamiento final con los mejores parámetros

Entrenamiento de modelo final
Se utilizan los mejores hiperparámetros encontrados (ya definidos manualmente).

Se divide el dataset en train/val/test (70%-15%-15%).

Aquí se busca que el modelo aprenda las regularidades temporales del precio de Bitcoin.

## 📈 7. Evaluación y visualización
## 7.1. Evaluación en el conjunto de prueba
Se utiliza RMSE para evaluar precisión:

## 📊 8. Métricas Finales
Se reportan tres métricas comunes en regresión:

MAE: 18.7345
RMSE: 38.9452
R² Score: 0.9854
MAE: Error absoluto medio.

RMSE: Raíz del error cuadrático medio.

R²: Cuánto del comportamiento del precio real es explicado por el modelo.
