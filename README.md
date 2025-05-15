# Bitcoin Price Prediction using LSTM and Genetic Algorithm

Descripción del Proyecto
Este proyecto implementa un modelo de predicción de precios de Bitcoin utilizando una red neuronal LSTM (Long Short-Term Memory) combinada con un algoritmo genético para optimizar los hiperparámetros del modelo. El código carga datos históricos de Bitcoin, los preprocesa, entrena un modelo LSTM y utiliza un algoritmo genético para encontrar los mejores hiperparámetros.

Características Principales
Preprocesamiento de datos: Normalización de los precios de cierre de Bitcoin usando MinMaxScaler.

Generación de secuencias: Creación de secuencias temporales para el entrenamiento del modelo LSTM.

Modelo LSTM: Implementación de una red neuronal recurrente para predecir precios futuros.

Algoritmo genético: Optimización de hiperparámetros como longitud de secuencia, tamaño de capa oculta, número de capas, dropout y tasa de aprendizaje.

Entrenamiento y evaluación: División de datos en conjuntos de entrenamiento y validación, y cálculo de pérdida.

Estructura del Código
1. Preprocesamiento de Datos
Carga el dataset de precios históricos de Bitcoin (btcusd_1-min_data.csv).

Convierte la columna Timestamp a formato datetime y selecciona solo la columna Close.

Normaliza los datos usando MinMaxScaler.

2. Creación de Secuencias
La función create_sequences genera secuencias de datos para entrenar el modelo LSTM. Cada secuencia contiene seq_len valores históricos y el valor siguiente como etiqueta.

3. Modelo LSTM
La clase BitcoinLSTM define la arquitectura de la red LSTM:

Capa LSTM con parámetros configurables (tamaño de entrada, capas ocultas, dropout).

Capa lineal para la salida.

4. Algoritmo Genético
La función genetic_algorithm busca los mejores hiperparámetros para el modelo LSTM:

Población inicial: Genera individuos con valores aleatorios para seq_len, hidden_size, num_layers, dropout y lr.

Evaluación de fitness: Entrena el modelo con los hiperparámetros de cada individuo y calcula la pérdida en el conjunto de validación.

Selección y reproducción: Selecciona los mejores individuos y genera una nueva población mediante cruce y mutación.

5. Entrenamiento del Modelo Final
Usa los mejores hiperparámetros encontrados por el algoritmo genético para entrenar el modelo LSTM.

Evalúa el modelo en el conjunto de validación.

Uso
Preparación del entorno:

Instala las dependencias: pandas, numpy, torch, scikit-learn, matplotlib.

Descarga el dataset btcusd_1-min_data.csv y colócalo en la ruta especificada (/content/).

Ejecución:

Ejecuta el script completo para entrenar el modelo y optimizar los hiperparámetros.

El modelo final se entrena con los mejores hiperparámetros encontrados.

Salida:

Muestra los mejores hiperparámetros encontrados.

Gráfico de la predicción vs. valores reales (opcional, descomentar la línea correspondiente).

Hiperparámetros Optimizables
seq_len: Longitud de las secuencias de entrada.

hidden_size: Número de neuronas en la capa oculta LSTM.

num_layers: Número de capas LSTM.

dropout: Tasa de dropout para regularización.

lr: Tasa de aprendizaje.

Resultados
El algoritmo genético encuentra la combinación de hiperparámetros que minimiza la pérdida en el conjunto de validación. El modelo LSTM entrenado con estos hiperparámetros puede usarse para predecir precios futuros de Bitcoin.

Mejoras Futuras
Añadir más características al modelo (volumen, indicadores técnicos).

Implementar early stopping durante el entrenamiento.

Usar más generaciones en el algoritmo genético para una mejor optimización.

Licencia
Este proyecto es de código abierto y puede ser modificado y distribuido libremente.
