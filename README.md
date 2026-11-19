# Explorador de Aleaciones de Alta Entropía

Herramienta web para **buscar y comparar aleaciones de alta entropía (HEA) y multicomponentes** por sus propiedades mecánicas, y para **estudiar cómo la composición se relaciona con la fase** que forman.

Etapa 3 del proyecto de Python · Ingeniería de Materiales · Facultad de Ingeniería, UNAM · Dataset 3 (aleaciones multicomponentes).

**Página publicada:** `https://<usuario>.github.io/<repositorio>/`

## Para quién es

- **Ingeniería y diseño:** encontrar aleaciones que cumplan requisitos de resistencia, ductilidad, densidad o temperatura de servicio, y revisar la calidad de cada dato antes de usarlo.
- **Estudiantes:** ver con datos reales el compromiso resistencia-ductilidad, el efecto de la temperatura, la relación de Hall-Petch y las reglas empíricas para anticipar la fase (VEC, δ y entropía de mezcla).

## Qué incluye

| Sección | Para qué sirve |
|---|---|
| **Inicio** | Explica qué es una aleación de alta entropía, resume el dataset y da tres recomendaciones antes de usar los datos. |
| **Buscar aleaciones** | Preguntas sencillas (tipo de carga, temperatura, estructura, resistencia mínima, ductilidad mínima y densidad máxima). Los resultados se agrupan por composición en tarjetas, y una gráfica muestra en qué zona caen. Cada aleación abre un panel con todos sus registros, avisos de calidad y DOI de los artículos. |
| **Lo que dicen los datos** | Siete preguntas respondidas con gráficas interactivas: la revisión de calidad de la Etapa 1, los análisis de la Etapa 2 (estructura cristalina, procesamiento y Hall-Petch), el efecto de la temperatura, el compromiso resistencia-ductilidad y la regla del VEC. |
| **Diseñar una aleación** | Eliges elementos y proporciones; responde si es de alta entropía (ΔS<sub>mix</sub>), si formará solución sólida (δ) y qué estructura se espera (VEC), estima su resistencia con los grupos de la Etapa 2 y muestra las aleaciones reales más parecidas. |
| **Glosario** | Definiciones, procesamiento, criterios de calidad, limitaciones y fuentes. |

## Estructura del repositorio

```
├── index.html                       Página (HTML + CSS + JavaScript, sin librerías externas)
├── datos.js                         Datos procesados, generados por el notebook
├── preparar_datos.ipynb             Limpieza y procesamiento en Python
├── Dataset_3 - Dataset_3.csv        Dataset original del curso
└── README.md
```

## Cómo se generan los datos

`preparar_datos.ipynb` (Python, pandas y numpy):

1. Separa valor, incertidumbre y tipo (exacto, límite o rango) en las columnas numéricas que venían como texto, y normaliza fase y procesamiento (Etapa 1).
2. Clasifica cada registro por familia de fase y sistema de aleación, y marca las unidades con varios registros (Etapa 2).
3. Lee las fórmulas con paréntesis como porcentaje cuando los coeficientes suman 100, y encuentra que las 672 fórmulas corresponden a 631 composiciones.
4. Calcula ΔS<sub>mix</sub>, δ, VEC y densidad por regla de mezclas. La densidad calculada coincide con la del dataset (error mediano de −0.02 %), y la regla del VEC acierta en el 74.3 % de las aleaciones.
5. Asigna un indicador de **calidad del dato** (Alta, Media, Baja) con avisos como elongación plástica mayor que la total, razón YS/HV fuera de lo esperado o valores corregidos por los compiladores.
6. Repite los análisis de la Etapa 2 (grupos por estructura, pares de procesamiento, series de Hall-Petch) y el resumen de calidad de la Etapa 1 para mostrarlos en la página. Al hacerlo se encontraron dos ajustes: una aleación cambia de sistema con la lectura corregida de paréntesis, y la comparación colada-recocido de la Etapa 2 tenía las etiquetas invertidas. Ninguno cambia sus conclusiones.
7. Exporta todo a `datos.js`.

Para regenerar los datos: abrir el notebook en Google Colab, ejecutar todas las celdas y reemplazar `datos.js` con el archivo descargado.

## Limitaciones

- Datos recopilados de 265 artículos con métodos distintos; son asociaciones, no un experimento controlado.
- Compresión y tensión no son comparables; la mayoría de los ensayos es a temperatura ambiente.
- La regla del VEC y el criterio de δ son empíricos. Los radios, densidades y VEC de los elementos son valores tabulados aproximados.
- La calculadora no considera la entalpía de mezcla ni el procesamiento.

## Fuentes

- Borg, C. K. H. et al. (2020). *Expanded dataset of mechanical properties and observed phases of multi-principal element alloys*. Scientific Data, 7, 430.
- Guo, S., Ng, C., Lu, J. y Liu, C. T. (2011). Effect of valence electron concentration on stability of fcc or bcc phase in high entropy alloys. Journal of Applied Physics, 109, 103505.
- Yang, X. y Zhang, Y. (2012). Prediction of high-entropy stabilized solid-solution in multi-component alloys. Materials Chemistry and Physics, 132, 233–238.

## Equipo

- Integrante 1 —
- Integrante 2 —
- Integrante 3 —
- Integrante 4 —
