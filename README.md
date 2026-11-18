# Workshop3:

**Curso:** ETL – Ingeniería de Datos e Inteligencia Artificial  
**Institución:** Universidad Autónoma de Occidente 
**Estudiante:** Juliana Toro Serrano  

---

## Descripción del Proyecto
Este proyecto implementa una tubería ETL completa combinando ingesta de datos en streaming y Machine Learning para predecir los puntajes de felicidad mundial (*World Happiness Report*). El flujo comprende las siguientes fases:

1. **Consumo en Streaming (Fase 1):** Conexión segura a un clúster de Apache Kafka (kafka-classroom-2026.westus.cloudapp.azure.com:9092) utilizando autenticación `SASL_SSL` (`SCRAM-SHA-512`) para consumir registros del tópico etl.records.
2. **Análisis Exploratorio y Limpieza (Fase 2):** Aplanamiento de estructuras JSON anidadas (metadata y data) y unificación de columnas históricas de múltiples años en un dataset consolidado de 782 registros.
3. **Preparación de Características (Fase 3):** Selección de variables predictoras socioeconómicas clave (PIB, apoyo social, expectativa de vida, libertad, generosidad y corrupción) y división de datos (80/20) con escalado estándar para evitar sesgos (data leakage).
4. **Entrenamiento del Modelo (Fase 4):** Implementación de un modelo de Regresión Lineal supervisado mediante `scikit-learn`.
5. **Evaluación y Visualización (Fase 5):** Cálculo de métricas de rendimiento (MAE, MSE, RMSE y $R^2$) y generación de gráficas estilizadas en tonos morados para analizar la relación entre los valores reales y las predicciones.
6. **Persistencia (Fase 6):** Carga y almacenamiento final de los resultados estructurados en una base de datos relacional local (SQLite).

---

## Tecnologías y Librerías Utilizadas
* **Python 3.x**
* **Apache Kafka** (confluent-kafka)
* **Manipulación de Datos:** pandas, numpy
* **Machine Learning & Preprocesamiento:** scikit-learn (LinearRegression, StandardScaler, métricas de evaluación)
* **Visualización:** matplotlib, seaborn
* **Almacenamiento:** sqlite3
