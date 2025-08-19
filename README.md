# CLima - Modelo de Predicción Climática

Este proyecto implementa un modelo de predicción climática utilizando PatchTST (Patch Time Series Transformer) para predecir variables meteorológicas como temperatura, humedad, velocidad del viento y precipitación.

## Descripción

CLima es una herramienta que utiliza aprendizaje profundo para realizar predicciones meteorológicas basadas en datos históricos. El modelo está implementado utilizando la arquitectura PatchTST, que es especialmente eficaz para el análisis y predicción de series temporales.

## Características

- Predicción de múltiples variables meteorológicas (temperatura, humedad, velocidad del viento, precipitación)
- Preprocesamiento y normalización automática de datos
- Visualización comparativa de valores reales vs. predichos
- Fácil adaptación a diferentes conjuntos de datos climáticos

## Requisitos

Para utilizar este proyecto, necesitarás instalar las siguientes dependencias:

```bash
pip install pandas numpy torch transformers scikit-learn
```

Versiones recomendadas:
- pandas >= 1.3.0
- numpy >= 1.20.0
- torch >= 1.9.0
- transformers >= 4.18.0
- scikit-learn >= 1.0.0

## Estructura de datos

El modelo espera un archivo CSV con el siguiente formato:

```
Fecha,Temperatura,Humedad,Velocidad del Viento,Precipitacion
2025-01-01 00:00:00,28.5,85,5.2,0.0
2025-01-01 01:00:00,28.1,86,6.0,0.0
...
```

Donde:
- `Fecha`: Timestamp en formato 'YYYY-MM-DD HH:MM:SS'
- `Temperatura`: Valor numérico (°C)
- `Humedad`: Valor numérico (%)
- `Velocidad del Viento`: Valor numérico (km/h)
- `Precipitacion`: Valor numérico (mm)

## Uso

1. Prepara tu archivo CSV con datos climáticos siguiendo el formato especificado.
2. Ejecuta el notebook `main.ipynb` en un entorno Jupyter.
3. El notebook cargará automáticamente los datos, entrenará el modelo y realizará predicciones.

## Funcionamiento del modelo

El modelo funciona en los siguientes pasos:

1. **Carga de datos**: Lee el archivo CSV con datos climáticos históricos.
2. **Preprocesamiento**: Normaliza los datos utilizando StandardScaler.
3. **División de datos**: Separa los datos en valores pasados (para entrenamiento) y futuros (para validación).
4. **Configuración del modelo**: Inicializa el modelo PatchTST con parámetros específicos.
5. **Entrenamiento**: Realiza un paso de entrenamiento con los datos históricos.
6. **Predicción**: Genera predicciones para las próximas horas/días.
7. **Visualización**: Muestra una comparación entre valores reales y predichos.

## Configuración del modelo

El modelo PatchTST se configura con los siguientes parámetros:

- `num_input_channels`: Número de variables a predecir (4 en este caso)
- `prediction_length`: Longitud de la predicción (4 horas en este caso)
- `context_length`: Longitud del contexto histórico (20 horas en este caso)
- `patch_length`: Longitud de cada parche para el procesamiento (4 en este caso)
- `patch_stride`: Paso entre parches consecutivos (2 en este caso)

Estos parámetros pueden ajustarse según las necesidades específicas de predicción.

## Personalización

Para adaptar el modelo a tus propios datos o necesidades:

1. Modifica el archivo CSV de entrada con tus propios datos climáticos.
2. Ajusta los parámetros de configuración del modelo en la sección 4 del notebook.
3. Cambia la longitud de predicción según tus necesidades.

## Limitaciones

- El modelo actual está configurado para predicciones a corto plazo (4 horas).
- La precisión depende de la calidad y cantidad de los datos históricos disponibles.
- Se recomienda reentrenar el modelo periódicamente con datos actualizados.

## Licencia

Este proyecto está disponible como código abierto bajo la licencia MIT.