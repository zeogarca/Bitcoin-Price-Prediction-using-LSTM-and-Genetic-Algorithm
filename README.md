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

## 🌱 Mejoras Futuras
- Incluir más características como volumen, medias móviles o indicadores técnicos.
- Implementar early stopping para evitar sobreentrenamiento.
- Usar más generaciones y población en el algoritmo genético para una mejor optimización.
