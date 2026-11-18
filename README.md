# Workshop3:

ETL – Ingeniería de Datos e Inteligencia Artificial  
Universidad Autónoma de Occidente 

**Estudiante:** Juliana Toro Serrano  

## Descripción General
Este proyecto implementa una tubería ETL (*Extract, Transform, Load*) robusta e integrada con un modelo de Machine Learning. El objetivo principal es procesar y predecir los puntajes de felicidad global a partir del histórico del **World Happiness Report**. 

Estructura y Fases del Proyecto

El desarrollo del taller se encuentra organizado de forma secuencial en las siguientes fases técnicas dentro del cuaderno:

* **Fase 1: Conexión a Apache Kafka y Consumo**
  * Se establece una conexión segura con el clúster de Kafka de la universidad (kafka-classroom-2026.westus.cloudapp.azure.com:9092) utilizando autenticación SASL_SSL (SCRAM-SHA-512).
  * Se realiza la suscripción al tópico etl.records para consumir y extraer un total de 782 registros en formato JSON.

* **Fase 2: Análisis Exploratorio de Datos (EDA) y Limpieza**
  * Se procesan y aplanan las estructuras de datos anidadas (metadata y data) convirtiéndolas en un DataFrame tabular de pandas.
  * Se unifican armónicamente las columnas históricas que variaban entre los distintos reportes anuales (como el puntaje de felicidad, PIB, apoyo social y expectativa de vida) y se genera una matriz de correlación estilizada.

* **Fase 3: Preparación de Características (Feature Engineering)**
  * Se seleccionan las variables predictoras independientes clave (PIB, apoyo social, expectativa de vida, libertad, generosidad y corrupción) frente a la variable objetivo (Unified_Happiness_Score).
  * Se realiza la partición aleatoria del dataset en conjuntos de entrenamiento (80%) y prueba (20%), aplicando un escalador estándar (StandardScaler) ajustado únicamente sobre el conjunto de entrenamiento para evitar fugas de datos (*data leakage*).

* **Fase 4: Entrenamiento del Modelo de Regresión**
  * Se inicializa y entrena un modelo de **Regresión Lineal** supervisado utilizando scikit-learn con los datos escalados, obteniendo los coeficientes y el intercepto óptimos del modelo.

* **Fase 5: Evaluación, Métricas y Visualización**
  * Se evalúa el rendimiento predictivo calculando métricas clave como el Error Absoluto Medio (MAE), Error Cuadrático Medio (MSE), Raíz del Error Cuadrático Medio (RMSE) y el Coeficiente de Determinación ($R^2$).
  * Se genera una gráfica de dispersión estilizada comparando los valores reales frente a los valores predichos por el modelo.

* **Fase 6: Carga y Persistencia en Base de Datos (SQLite)**
  * Se consolida un DataFrame final con las características de prueba, los valores reales y las predicciones generadas.
  * Se almacenan los resultados de forma estructurada en una base de datos relacional local llamada **happiness_warehouse.db** dentro de la tabla model_predictions.

## Tecnologías y Librerías
* **Lenguaje:** Python 3.x
* **Streaming:** Apache Kafka (confluent-kafka)
* **Procesamiento:** pandas, numpy
* **Modelado:** scikit-learn
* **Visualización:** matplotlib, seaborn
* **Base de Datos:** sqlite3
  
