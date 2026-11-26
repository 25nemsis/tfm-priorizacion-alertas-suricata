# Priorización de alertas de Suricata mediante Isolation Forest

Repositorio del Trabajo Fin de Estudio en Inteligencia Artificial de la Universidad Internacional de La Rioja (UNIR).

El objetivo del trabajo es evaluar si una puntuación de anomalía obtenida mediante aprendizaje automático no supervisado ayuda a decidir qué alertas de Suricata revisar primero en un centro de operaciones de seguridad (SOC).

## Qué contiene el notebook

[`Priorizacion_alertas_suricata.ipynb`](./Priorizacion_alertas_suricata.ipynb) documenta el procedimiento experimental, desde la lectura de las alertas de `eve.json` hasta la comparación de los rankings:

1. Extrae y prepara las características de las alertas.
2. Separa cronológicamente el entrenamiento y la evaluación.
3. Ajusta Isolation Forest con y sin los puertos de origen y destino.
4. Genera dos rankings de referencia basados en la severidad de Suricata y la frecuencia histórica de cada firma.
5. Prepara las alertas para la revisión experta, consolida las etiquetas y calcula la precisión en las primeras 5, 10 y 20 posiciones.
6. Analiza cómo cambia la selección al excluir tres firmas internas y genera las tablas y la gráfica del Anexo H.

## Cómo ejecutarlo

El notebook utiliza Python y Jupyter, con NumPy, pandas, scikit-learn y Matplotlib. La entrada del análisis es un archivo `eve.json` generado por Suricata.

1. Descargar o clonar el repositorio y abrir el notebook en Jupyter.
2. Ajustar las rutas de trabajo en la primera celda y el intervalo de captura en la sección de división cronológica.
3. Ejecutar las celdas en orden. Para calcular la precisión operativa se necesita también las valoraciones y las etiquetas consensuadas que correspondan a los rankings evaluados.

## Resultado principal

En las primeras diez posiciones, la severidad de Suricata obtuvo la mayor precisión, con siete alertas relevantes. En las primeras veinte, Isolation Forest con puertos igualó la precisión de la severidad (35 %). Cada método situó siete alertas relevantes en ese corte y las dos selecciones de alertas relevantes fueron distintas. El piloto muestra así el potencial de la puntuación de anomalía como criterio complementario de priorización.

## Disponibilidad de los datos

La captura original, el archivo `eve.json` derivado y los archivos internos de revisión y consenso se conservan bajo custodia por motivos de confidencialidad. El repositorio permite consultar el código y la metodología. La reproducción exacta de las cifras del piloto requiere los datos originales y el etiquetado experto. El Anexo H de la memoria recoge las tablas anonimizadas que permiten comprobar las métricas publicadas.
