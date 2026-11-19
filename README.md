# Explorador de Aleaciones de Alta Entropía

Herramienta web para **buscar y comparar aleaciones de alta entropía (HEA) y multicomponentes** por sus propiedades mecánicas, y para **estudiar cómo la composición se relaciona con la fase** que forman.

Etapa 3 del proyecto de Python · Ingeniería de Materiales · Facultad de Ingeniería, UNAM · Dataset 3 (aleaciones multicomponentes).

**Página publicada:** `https://<usuario>.github.io/<repositorio>/`

## Para quién es

- **Ingeniería y diseño:** encontrar aleaciones que cumplan requisitos de resistencia, ductilidad, densidad o temperatura de servicio, y revisar la calidad de cada dato antes de usarlo.
- **Estudiantes:** ver con datos reales el compromiso resistencia-ductilidad, el efecto de la temperatura, la relación de Hall-Petch y las reglas empíricas para anticipar la fase (VEC, δ y entropía de mezcla).

## Qué incluye

| Vista | Función |
|---|---|
| **Explorador** | Filtros por familia de fase, sistema de aleación, tipo de ensayo, temperatura, procesamiento, rangos de propiedades, elementos y calidad del dato. Gráfica con ejes y color configurables, seis vistas guiadas, tabla ordenable y ficha de cada registro con su DOI. |
| **Calculadora de composición** | A partir de una fórmula calcula ΔS<sub>mix</sub>, δ, VEC, densidad por regla de mezclas y sistema; predice la fase con la regla del VEC; ubica la aleación en el mapa VEC–δ del dataset y busca las composiciones más parecidas. |
| **Guía** | Definiciones, glosario de procesamiento, criterios de calidad y limitaciones. |

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
6. Exporta todo a `datos.js`.

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
