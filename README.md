# Omicron: Predicción de Demanda de Taxis

## Descripción del Proyecto

La compañía **Sweet Lift Taxi** busca anticipar la demanda de taxis en los aeropuertos para atraer un número adecuado de conductores durante los períodos de alta actividad. El objetivo de este proyecto es desarrollar un modelo de aprendizaje automático capaz de predecir la cantidad de pedidos de taxis para la próxima hora utilizando datos históricos de solicitudes.

## Objetivo

Construir un modelo de series temporales que permita predecir la cantidad de pedidos de taxis por hora, cumpliendo con el requisito del proyecto:

**RMSE < 48**

---

## Objetivo de Negocio

Una estimación precisa de la demanda futura permite:

- Mejorar la disponibilidad del servicio.
- Reducir tiempos de espera para los clientes.
- Optimizar la asignación de conductores.
- Anticipar períodos de alta demanda.

---

## Tecnologías Utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Statsmodels
- Scikit-Learn
- LightGBM
- XGBoost

---

## Metodología

### 1. Preparación de Datos

- Conversión de fechas al formato `datetime`.
- Ordenamiento cronológico de la serie temporal.
- Configuración de `datetime` como índice.
- Remuestreo de datos en intervalos de una hora mediante:

```python
data.resample("1h").sum()
```

---

### 2. Análisis Exploratorio de Datos

Se realizó un análisis de la serie temporal para identificar:

- Tendencia.
- Estacionalidad.
- Variabilidad.
- Posibles valores atípicos.

Además, se utilizó la descomposición temporal para analizar:

- Componente de tendencia.
- Componente estacional.
- Componente residual.

---

### 3. Ingeniería de Características

Se generaron nuevas variables temporales:

- Hora
- Día
- Mes
- Día de la semana
- Año

También se crearon características basadas en el comportamiento histórico de la serie:

#### Variables de desfase (lags)

```python
lag_1
lag_24
```

#### Media móvil

```python
rolling_mean
```

Estas variables permitieron capturar patrones temporales y estacionalidades presentes en los datos.

---

### 4. División de Datos

Se utilizó una división temporal respetando el orden cronológico:

```python
test_size = 0.10
shuffle = False
```

- Entrenamiento: 90%
- Prueba: 10%

---

## Modelos Evaluados

### Modelo Base

**DummyRegressor**

RMSE:

```text
84.69
```

---

### Regresión Lineal

RMSE:

```text
47.71
```

✅ Cumple el requisito.

---

### Árbol de Decisión

RMSE:

```text
50.09
```

❌ No cumple el requisito.

---

### Random Forest

RMSE:

```text
46.40
```

✅ Cumple el requisito.

---

### LightGBM

RMSE:

```text
46.19
```

✅ Cumple el requisito.

---

### XGBoost

RMSE:

```text
41.79
```

✅ Mejor resultado obtenido.

---

## Comparación de Resultados

| Modelo | RMSE |
|----------|----------:|
| DummyRegressor | 84.69 |
| Decision Tree | 50.09 |
| Linear Regression | 47.71 |
| Random Forest | 46.40 |
| LightGBM | 46.19 |
| XGBoost | **41.79** |

---

## Mejor Modelo

### XGBoost

```text
RMSE = 41.79
```

Este modelo obtuvo el menor error en el conjunto de prueba, superando ampliamente el requisito mínimo establecido para el proyecto.

---

## Conclusiones

Se desarrolló un sistema de predicción de demanda horaria de taxis utilizando técnicas de series temporales y modelos de aprendizaje automático.

El análisis exploratorio permitió identificar una tendencia creciente y una estacionalidad diaria en la demanda, lo que justificó la creación de variables temporales, desfases y medias móviles.

Se evaluaron múltiples modelos de regresión, observándose mejoras significativas respecto al modelo base. El mejor desempeño fue obtenido por **XGBoost**, alcanzando una **RMSE de 41.79**, resultado que cumple satisfactoriamente el criterio de éxito del proyecto (**RMSE < 48**).

Los resultados demuestran que la información histórica de la serie y las características temporales aportan valor para anticipar la demanda de taxis con una hora de anticipación, proporcionando una herramienta útil para la planificación operativa de Sweet Lift Taxi.

---

## Autor

**Santiago Rodríguez Zaraza**

Proyecto Omicron - Forecasting de Demanda de Taxis
