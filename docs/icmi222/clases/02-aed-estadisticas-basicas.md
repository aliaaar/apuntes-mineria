---
tags:
  - ICMI222
  - Apuntes de clase
  - Análisis exploratorio
---

# PPT 02 · AED I: estadísticas y gráficos básicos

!!! quote "Fuente"
    Resumen propio de la presentación **PPT 02** del curso ICMI222 (semana 3).
    Lectura: Isaaks & Srivastava (1989), caps. 2-4; Rossi & Deutsch (2014), cap. 3.

## Para qué sirve el AED

Antes de estimar hay que **conocer los datos**. El análisis exploratorio de datos (AED):

- detecta errores, duplicados y valores imposibles que el QA/QC no filtró;
- describe la distribución de leyes: centro, dispersión, forma y extremos;
- muestra relaciones entre variables (Cu-Au, ley-litología, ley-densidad);
- revela el agrupamiento de los sondajes y posibles dominios;
- fundamenta las decisiones siguientes: compósitos, extremos y plan de estimación.

!!! warning "Lo que no se detecta en el AED se arrastra hasta el modelo de recursos."

## Medidas de posición

Con \(n\) datos \(z_1, \dots, z_n\):

\[ m = \frac{1}{n}\sum_{i=1}^{n} z_i
   \qquad
   m_w = \frac{\sum_{i=1}^{n} w_i z_i}{\sum_{i=1}^{n} w_i} \]

| Medida | Qué dice | Cuidado |
|---|---|---|
| **Media** \(m\) | Valor esperado de la ley | Muy sensible a los valores altos |
| **Media ponderada** \(m_w\) | Promedio con pesos (largo, área, volumen) | Base de la compositación y del desagrupamiento |
| **Mediana** (P50) | Valor central de los datos ordenados | Robusta frente a la cola alta |
| **Cuantiles** (P10, P25, P75, P90) | Describen toda la distribución | Cuartiles = 4 partes; deciles = 10; quintiles = 5 |
| **Moda** | Valor más frecuente | Dos modas → posible mezcla de poblaciones |
| **Mínimo, máximo, rango** | Control de valores imposibles | Leyes negativas, ceros, unidades mezcladas |

!!! info "Media > mediana"
    En leyes con asimetría positiva la media supera a la mediana. Reportar solo la media, sin
    analizar la cola alta, **sobrestima** el depósito.

## Medidas de dispersión y forma

\[ \sigma^2 = \frac{1}{n}\sum_{i=1}^{n}(z_i - m)^2
   \qquad
   \sigma = \sqrt{\sigma^2}
   \qquad
   CV = \frac{\sigma}{m} \]

\[ \text{asimetría} = \frac{\frac{1}{n}\sum (z_i - m)^3}{\sigma^3}
   \qquad
   \text{curtosis} = \frac{\frac{1}{n}\sum (z_i - m)^4}{\sigma^4} - 3 \]

!!! note "Vulcan usa la varianza poblacional"
    El *Data Analyser* divide por \(n\), no por \(n-1\). Con muchos datos da lo mismo, pero en
    dominios chicos se nota.

### Coeficiente de variación (CV)

Variabilidad **relativa**, sin unidades: permite comparar depósitos y campañas.

| CV | Lectura |
|---|---|
| < 0,5 | Variable bien comportada |
| ~0,7 | Típico de un pórfido de cobre |
| ~1,5 | Variabilidad media; revisar extremos |
| > 1,5 | Alerta: valores extremos, mezcla de dominios o varias poblaciones |
| ~4,5 | Muy errático (por ejemplo, oro en vetas) |

El CV condiciona el método de estimación y la densidad de muestreo que se necesita.

!!! example "En el dataset ICMI222"
    Cu tiene un CV de 0,90 con todos los datos juntos, pero 0,72 dentro de R102 y 0,84 dentro de
    R101. R112 (óxidos, halo) llega a 1,19: es el dominio más errático.

### Asimetría y curtosis

- **Asimetría positiva** (lo habitual en leyes): la mayoría de los datos son bajos y hay una cola
  de valores altos. La distribución se parece a una **lognormal**.
- **Curtosis > 0** (leptocúrtica): colas pesadas, muchos valores extremos.
  **≈ 0**: mesocúrtica (como la normal). **< 0** (platicúrtica): distribución aplanada.

## Gráficos del AED

| Gráfico | Qué muestra | Para qué decisión sirve |
|---|---|---|
| **Histograma** | Forma de la distribución | Una sola moda o varias (dominios); cola alta |
| **Box-plot** | Mediana, cuartiles y extremos en una caja | Comparar dominios lado a lado |
| **Frecuencia acumulada** | Proporción de datos bajo o sobre un valor | Base de la curva tonelaje-ley |
| **Gráfico Q-Q** | Cuantiles de una población contra los de otra | ¿Dos dominios o campañas tienen la misma distribución? |
| **Gráfico de probabilidad** | Datos contra una distribución de referencia (normal, lognormal) | Quiebres = poblaciones distintas o umbral de capping |
| **Dispersión (scatter)** | Relación entre dos variables | Correlación Cu-Au, densidad-ley |
| **Mapa de datos (planta)** | Ubicación de las muestras | Cobertura, agrupamiento, zonas de alta ley |
| **Curva tonelaje-ley** | Tonelaje y ley media sobre cada ley de corte | Referencial con datos; la definitiva va sobre el modelo de bloques |

!!! tip "Número de clases del histograma"
    Demasiadas clases muestran solo ruido; muy pocas esconden la cola alta. Un histograma con
    pocos datos no sirve de mucho.

!!! note "Box-plot en Vulcan"
    Los bigotes del box-plot de Vulcan van a los percentiles 2,5 y 97,5, no a la regla de Tukey
    (1,5 veces el rango intercuartil). Por eso no dibuja los valores atípicos uno por uno.

## Buenas prácticas

- Analizar **por dominio**: mezclar poblaciones distorsiona toda la estadística.
- No eliminar extremos sin justificación: primero verificar el dato y después decidir.
- Considerar el **soporte**: muestras de distinto largo no se comparan (se resuelve compositando).
- **Desagrupar** antes de informar estadísticas globales.
- Reportar siempre **n**, unidades y criterio de selección de los datos.
- Documentar cada decisión: el AED debe ser reproducible por un tercero.

## Preguntas de repaso

??? question "¿Por qué no basta con reportar la media de los compósitos?"
    Porque las leyes son asimétricas: unos pocos valores altos suben la media por sobre lo que
    tiene la mayor parte del depósito. Hay que mirar también la mediana, los percentiles y la cola
    alta, y desagrupar si los sondajes se concentran en zonas ricas.

??? question "Un dominio tiene CV = 1,8. ¿Qué revisas primero?"
    Si hay valores extremos (y si son errores) y si el dominio mezcla poblaciones: histograma
    bimodal o quiebres en el gráfico de probabilidad. Con CV alto también conviene revisar el
    capping y esperar una estimación menos precisa.

??? question "¿Para qué sirve un gráfico Q-Q?"
    Para comparar dos distribuciones cuantil a cuantil, por ejemplo dos dominios o dos campañas de
    muestreo. Si los puntos siguen la diagonal, tienen la misma distribución. Si se apartan, son
    poblaciones distintas o hay sesgo entre campañas.
