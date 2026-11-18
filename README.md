# Workshop3:

**Curso:** ETL – Ingeniería de Datos e Inteligencia Artificial  
**Institución:** Universidad Autónoma de Occidente 

**Estudiante:** Juliana Toro Serrano  

## Descripción General
Este proyecto implementa una tubería ETL (*Extract, Transform, Load*) robusta e integrada con un modelo de Machine Learning. El objetivo principal es procesar y predecir los puntajes de felicidad global a partir del histórico del **World Happiness Report**. 

El flujo de trabajo se compone de los siguientes momentos clave:

1. **Ingesta en Streaming (Fase 1):** Conexión segura a un clúster de Apache Kafka (etl.records) mediante autenticación SASL_SSL para la recolección de registros en tiempo real.
2. **Exploración y Limpieza de Datos (Fase 2):** Procesamiento de estructuras JSON anidadas y unificación armónica de variables históricas de múltiples años.
3. **Ingeniería de Características (Fase 3):** Selección de factores socioeconómicos determinantes (PIB, apoyo social, expectativa de vida, libertad, generosidad y percepción de corrupción) y partición de datos (80/20) con escalado estándar para evitar sesgos (*data leakage*).
4. **Modelado Predictivo (Fase 4):** Entrenamiento de un modelo de Regresión Lineal supervisado con scikit-learn.
5. **Evaluación y Visualización (Fase 5):** Análisis de rendimiento mediante métricas clave (MAE, MSE, RMSE y $R^2$) y representación visual estilizada de los resultados.
6. **Persistencia Final (Fase 6):** Almacenamiento estructurado de las predicciones en una base de datos relacional local (SQLite).

## Tecnologías y Librerías
* **Lenguaje:** Python 3.x
* **Streaming:** Apache Kafka (confluent-kafka)
* **Procesamiento:** pandas, numpy
* **Modelado:** scikit-learn
* **Visualización:** matplotlib, seaborn
* **Base de Datos:** sqlite3
  
