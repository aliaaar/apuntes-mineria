---
tags:
  - ICMI222
  - Apuntes de clase
  - Análisis exploratorio
  - Capping
---

# PPT 03 · AED II: de la descripción a la decisión

!!! quote "Fuente"
    Resumen propio de la presentación **PPT 03** del curso ICMI222 (semana 4).
    Lectura: Isaaks & Srivastava (1989), caps. 2-4; Rossi & Deutsch (2014), cap. 3.

## Las cinco preguntas

La semana anterior se describieron los datos. Ahora esa descripción se usa para **decidir**:

| Pregunta | Herramienta | Decisión |
|---|---|---|
| ¿Los datos vienen de una o de varias poblaciones? | Histograma, gráfico de probabilidad, Q-Q | **Dominios** |
| ¿La media representa al dominio? | Mapa de datos, desagrupamiento | **Media desagrupada** |
| ¿Los valores extremos son reales o errores? | Gráfico de probabilidad, revisión del dato | **Capping** |
| ¿Las muestras son comparables entre sí? | Largos de muestra | **Compositación** |
| ¿Puedo apoyarme en una variable para estimar otra? | Dispersión, correlación, regresión | **Coestimación o regresión** |

Cada respuesta se documenta: es parte de la trazabilidad del modelo de recursos.

## Por qué la estadística clásica no basta

La estadística clásica supone muestras **independientes**. En un yacimiento no lo son: las muestras
vecinas se parecen (**correlación espacial**). Consecuencias:

1. La **ubicación** de las muestras importa tanto como su valor.
2. \(n\) muestras agrupadas aportan **menos información** que \(n\) muestras repartidas.
3. Los intervalos de confianza clásicos **subestiman** la incertidumbre real.

Por eso el análisis estadístico se acompaña siempre del análisis espacial (variografía).

## Soporte

**Soporte** = volumen, forma y orientación sobre los que se mide la variable. Un testigo de 2 m,
un compósito de 10 m y un bloque de 25 m **no son la misma variable**.

!!! note "Efecto del soporte"
    Al aumentar el soporte, **la media se conserva y la varianza disminuye**. Consecuencia: el
    tonelaje sobre una ley de corte depende del tamaño de bloque. Nunca se comparan estadísticas
    de soportes distintos sin corregir.

## Agrupamiento preferencial y desagrupamiento

Los sondajes se concentran donde la ley es alta, así que la muestra **no es aleatoria** y la media
simple **sobrestima** la del dominio.

**Solución:** ponderar cada dato por el área o volumen que representa. En el **método de celdas**
se divide el dominio en celdas y cada dato recibe un peso inverso al número de datos de su celda:

\[ m_d = \sum_{i=1}^{n} w_i\, z_i
   \qquad
   w_i = \frac{1/n_{c(i)}}{\sum_j 1/n_{c(j)}}
   \qquad
   \sum w_i = 1 \]

donde \(n_{c(i)}\) es la cantidad de datos en la celda del dato \(i\). El **tamaño de celda** se
elige donde la media desagrupada se estabiliza o llega a su mínimo (cuando las zonas ricas están
sobremuestreadas). Toda estadística global del dominio se reporta desagrupada.

## Mezcla de poblaciones y contactos

- Un **histograma bimodal** avisa que hay dos poblaciones. Separarlas por unidad geológica
  devuelve distribuciones interpretables.
- El **análisis de contactos** grafica la ley media a distintas distancias del contacto:
  un salto brusco indica un contacto **duro** (no se comparten datos) y una transición suave, uno
  **blando**. Más detalle en [PPT 05](05-dominios-compositacion.md).

## Valores extremos y capping

En el gráfico de probabilidad (log), el punto donde la nube **se despega de la recta** da un umbral
de capping defendible.

!!! warning "Antes de recortar, verificar"
    Primero se comprueba que el valor no sea un error de laboratorio o de digitación. Recién
    después se decide recortarlo. Se reporta cuántas muestras se recortaron y cuánto metal se pierde.

!!! example "En el dataset ICMI222"
    El Cu máximo es 12,51 % (sondaje 154, dominio R101), con solo 0,46 g/t de Au. Duplica al
    segundo valor más alto (6,02 %) y coincide dígito a dígito con el máximo de Au de R111.
    Es candidato a revisión de QA/QC antes que a capping.

## Relación entre dos variables

\[ \operatorname{Cov}(X,Y) = \frac{1}{n}\sum (x_i - m_X)(y_i - m_Y)
   \qquad
   r = \frac{\operatorname{Cov}(X,Y)}{\sigma_X\,\sigma_Y}
   \qquad
   R^2 = r^2 \]

- La **covarianza** indica el sentido de la relación, pero su valor depende de las unidades.
- **Pearson (\(r\))** es la covarianza normalizada: sin unidades, entre −1 y 1. Solo detecta
  relaciones **lineales** y es sensible a los extremos.
- **Spearman (\(\rho\))** calcula Pearson sobre los **rangos**: detecta cualquier relación
  monótona y es robusto con leyes asimétricas.
- **\(R^2\)**: fracción de la variabilidad de una variable explicada por la otra (en regresión
  lineal simple, \(R^2 = r^2\)).

### Cómo leer \(|r|\) o \(|\rho|\) (orientativo)

| Valor | Lectura | Consecuencia |
|---|---|---|
| 0,0 – 0,3 | Despreciable | Estimar por separado |
| 0,3 – 0,5 | Débil | Ver si mejora separando por dominio |
| 0,5 – 0,7 | Moderada | Explorar dominio por dominio |
| 0,7 – 0,9 | Fuerte | Evaluar coestimación o regresión auxiliar |
| > 0,9 | Muy fuerte | Revisar que una variable no se calcule a partir de la otra |

### Comparar \(r\) con \(\rho\)

| Se observa | Significa | Qué hacer |
|---|---|---|
| \(r \approx \rho\), ambos altos | Relación lineal limpia | Usar la regresión con confianza |
| \(r\) bajo, \(\rho\) alto | Relación fuerte pero curva | Transformar (log) o usar rangos |
| \(r\) alto, \(\rho\) bajo | Unos pocos extremos fabrican la correlación | Revisar esos datos |
| Ambos ≈ 0 | Sin relación monótona | Mirar el gráfico: puede haber relación en U |
| Signos opuestos | Alarma | Buscar extremos o mezcla de dominios |

!!! example "En el dataset ICMI222"
    Cu-Au: Spearman 0,82–0,91 contra Pearson 0,55–0,78 según el dominio. Es el caso
    "\(\rho\) mayor que \(r\)": relación fuerte pero no lineal, típica de leyes lognormales.

**Regresión lineal:** sirve para estimar una variable difícil de medir (por ejemplo, la densidad)
a partir de otra bien muestreada (Fe), **solo dentro del rango observado**. La correlación puede ser
alta dentro de cada dominio y baja en el conjunto, o al revés.

## Otros chequeos

- **Matriz de correlación**: todas las relaciones por pares, para decidir si estimar variables
  juntas o por separado.
- **Efecto proporcional**: en depósitos lognormales, la variabilidad local crece con la ley media
  local. Condiciona el capping por zona y el tipo de variograma.
- **Comparar campañas**: antes de juntar bases de datos se comparan con Q-Q o dispersión. Una nube
  sistemáticamente bajo la diagonal indica sesgo entre campañas.

## Errores frecuentes

- Calcular estadísticas mezclando dominios.
- Informar la media sin desagrupar cuando la exploración fue dirigida.
- Confundir correlación con causalidad, o extrapolar una regresión fuera del rango.
- Aplicar capping sin verificar si el extremo es un error.
- Juntar campañas sin analizar el sesgo.
- Reportar coeficientes sin \(n\), unidades ni dominio.

## Preguntas de repaso

??? question "¿Por qué la media desagrupada suele ser menor que la media simple?"
    Porque los sondajes se concentran en las zonas ricas. Al dar menos peso a los datos agrupados,
    las zonas pobres (con pocos sondajes) recuperan su importancia y la media baja.

??? question "Al pasar de compósitos de 2 m a bloques de 20 m, ¿qué pasa con la media y la varianza?"
    La media se mantiene y la varianza baja. Por eso la curva tonelaje-ley de los compósitos no
    sirve directamente para los bloques: sobre una ley de corte alta, los compósitos muestran más
    tonelaje rico del que la mina podrá separar.

??? question "Pearson Cu-Au = 0,55 y Spearman = 0,85. ¿Cómo lo interpretas?"
    La relación es fuerte y monótona, pero no lineal (o hay extremos que bajan a Pearson). Con
    leyes lognormales, conviene mirar la relación en escala logarítmica antes de usar una regresión.
