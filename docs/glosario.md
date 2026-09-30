---
tags:
  - Glosario
  - Geoestadística
---

# Glosario

Definiciones cortas de los conceptos que se repiten entre tutoriales y ramos.
Ordenadas por tema; usa el buscador para saltar directo a una.

## Datos y muestreo

**Sondaje**
:   Perforación que recupera muestras del subsuelo. *Diamantina*: recupera testigo (núcleo de roca).
    *Aire reverso (RC)*: recupera detritos; más barato, menos información geológica.

**Compósito**
:   Muestra regularizada a un largo constante (por ejemplo, 5 m) a partir de los intervalos
    originales del sondaje. Se composita para que todas las muestras tengan el **mismo soporte**.
    Contra: reduce la variabilidad (suaviza).

**Soporte**
:   Tamaño, forma y orientación del volumen sobre el que se mide una variable. Una muestra de 2 m y
    un bloque de 20 m de la misma zona **no tienen la misma varianza**: a mayor soporte, menor
    dispersión.

**QA/QC**
:   Aseguramiento y control de calidad del muestreo y del laboratorio. Se insertan **blancos**
    (material estéril, detecta contaminación), **estándares o CRM** (ley certificada, mide
    exactitud) y **duplicados** (mide precisión). Criterio usado en clase: entre 2 y 3 desviaciones
    estándar del valor esperado es cuestionable; más de 3 se rechaza.

**Límite de detección**
:   Valor mínimo que el laboratorio puede medir (por ejemplo, 0,01 % Cu).

## Estadística (AED)

**Variable regionalizada**
:   Variable que depende de su ubicación en el espacio, \(z(x)\): por ejemplo, la ley de cobre.
    Tiene una parte aleatoria y una parte estructurada (leyes cercanas se parecen más que las lejanas).

**Media vs mediana**
:   En leyes con asimetría positiva, **media > mediana**. Reportar solo la media, sin mirar su
    sensibilidad a los valores altos, puede sobreestimar el depósito.

**Coeficiente de variación (CV)**
:   Desviación estándar dividida por la media. CV > 1 indica una distribución errática, donde
    conviene revisar capping y dominios.

**Asimetría (skewness) y curtosis**
:   Asimetría positiva: la mayoría de los datos son bajos y hay una cola de valores altos.
    Curtosis alta (leptocúrtica): colas pesadas, muchos valores extremos.

**Pearson vs Spearman**
:   Pearson mide relación **lineal** entre dos variables y es sensible a los extremos. Spearman
    usa rangos y mide relación **monótona**; es más robusto con leyes asimétricas.

**Agrupamiento y desagrupamiento (declustering)**
:   Los sondajes se concentran en las zonas ricas, así que la media simple queda inflada.
    Desagrupar da menos peso a las muestras agrupadas (por ejemplo, por celdas) para obtener una
    media representativa.

**Capping (recorte de altos)**
:   Recortar los valores extremos a un umbral justificado (quiebre del gráfico de probabilidad,
    percentil alto) para que no contaminen la estimación. Se reporta el porcentaje de metal perdido.

## Dominios

**Dominio de estimación**
:   Volumen donde la ley se comporta como una sola población: misma media, variabilidad y
    continuidad. Se define con geología (litología, alteración, oxidación) y estadística.

**Estacionariedad**
:   Supuesto de que las propiedades estadísticas (media, variograma) no cambian de un lugar a otro
    dentro del dominio. Es lo que permite usar un solo variograma por dominio.

**Contacto duro**
:   Límite entre dominios que **no** se cruza al estimar: cada dominio usa solo sus muestras.
    Se usa cuando las leyes cambian bruscamente en el contacto.

**Contacto blando**
:   Se permite usar muestras del dominio vecino hasta cierta distancia del contacto (por ejemplo,
    ~25 m). Se usa cuando la ley cambia gradualmente.

**Modelamiento implícito (RBF)**
:   Construye los sólidos de los dominios interpolando una función de distancia a partir de los
    datos, en vez de digitalizarlos a mano sección por sección. Ver
    [el lab de modelo de bloques](icmi222/lab-modelo-bloques-id2.md#3-dominios-con-modelamiento-implicito-rbf).

## Variografía

**Variograma**
:   Mide cuánto difieren, en promedio, dos leyes separadas por una distancia \(h\):

    \[ \gamma(h) = \frac{1}{2N(h)} \sum_{i=1}^{N(h)} \left[ z(x_i + h) - z(x_i) \right]^2 \]

    donde \(N(h)\) es el número de pares a esa distancia. Leyes cercanas se parecen
    (γ bajo); leyes lejanas no (γ alto).

**Efecto pepita (nugget, \(C_0\))**
:   Valor del variograma en el origen: variabilidad a distancia casi cero. Refleja errores de
    muestreo y variabilidad a escala menor que la malla. Compositar lo reduce.

**Meseta (sill)**
:   Valor donde el variograma se estabiliza. Es aproximadamente la **varianza** de los datos.

**Alcance (range, \(a\))**
:   Distancia a la que el variograma llega a la meseta. Más allá, las muestras ya no están
    correlacionadas. En modelos asintóticos (exponencial, gaussiano) se usa el alcance práctico,
    al 95 % de la meseta.

**Modelos de variograma**
:   *Esférico*: sube casi lineal y llega a la meseta en \(a\). *Exponencial*: asintótico.
    *Gaussiano*: parabólico en el origen (muy continuo); en la práctica debe acompañarse de pepita.

**Anisotropía**
:   El alcance cambia según la dirección, con la misma meseta (anisotropía geométrica).
    Se describe con un elipsoide: dirección principal, semi-principal y menor.

**Lag, tolerancias y ancho de banda**
:   *Lag*: paso de distancia con que se agrupan los pares; conviene que sea múltiplo del largo de
    compósito. *Tolerancia de lag*: por defecto, la mitad del lag. *Tolerancia angular* y *ancho de
    banda*: cuánto se puede desviar un par de la dirección calculada. Reglas prácticas: al menos 30
    pares por punto y no interpretar más allá de la mitad del campo.

## Estimación

**Inverso a la distancia (ID)**
:   Promedio ponderado con pesos \(\lambda_i \propto 1/d_i^{\,p}\). Geométrico: no usa el
    variograma ni entrega varianza. Ver
    [el lab](icmi222/lab-modelo-bloques-id2.md#5-estimacion-de-cu-por-inverso-a-la-distancia-id2).

**Kriging ordinario**
:   Estimador que calcula los pesos usando el variograma, de modo que la estimación sea **insesgada**
    y de **mínima varianza**. Considera la redundancia entre muestras y entrega la varianza de
    kriging.

**Discretización**
:   Dividir el bloque en puntos internos (por ejemplo, 4 × 4 × 1) para estimar la ley **promedio**
    del bloque y no la de su centro.

**Suavizamiento**
:   Toda estimación tiene menos varianza que los datos reales: los bloques altos se subestiman y los
    bajos se sobreestiman. Afecta a la curva tonelaje-ley.

**Validación cruzada**
:   Se quita cada muestra, se estima en su posición con las demás y se compara estimado vs real.
    Mide sesgo y precisión del plan de estimación.

**Modelo de bloques**
:   Discretización del yacimiento en celdas regulares que guardan atributos (dominio, ley,
    densidad). El tamaño de bloque depende de la malla de sondajes y de la selectividad minera (SMU).
