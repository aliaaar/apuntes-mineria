---
tags:
  - ICMI222
  - Apuntes de clase
  - QA/QC
---

# PPT 01 · Introducción a la geoestadística

!!! quote "Fuente"
    Resumen propio de la presentación **PPT 01** del curso ICMI222 (semanas 1 y 2).

## Qué es la geoestadística

La palabra junta dos ideas: **geo**, el campo de estudio (las ciencias de la Tierra), y
**estadística**, el uso de métodos probabilísticos. Nació en la minería:

- **Danie Krige (1952)**, en las minas de oro de Sudáfrica, mostró que estimar un bloque con la
  media de sus muestras no basta y que las muestras vecinas aportan información.
- **Georges Matheron (1962)** formalizó la teoría de las **variables regionalizadas**.

Definición operativa (Alfaro, 2007): aplicar la teoría de las variables regionalizadas al
reconocimiento y la estimación de un fenómeno natural.

## Variable regionalizada

Una función \(z(x)\) que describe cómo varía en el espacio una magnitud de un fenómeno natural.
La idea clave es que **el valor está amarrado a una posición**: la ley en un punto se parece a la
ley en los puntos cercanos.

Ejemplos: ley de Cu en un pórfido, potencia de una veta, cota de una superficie, calidad de la
roca (RQD). Se profundiza en [PPT 04](04-variable-regionalizada.md).

## Sondajes

Perforaciones que extraen muestras físicas y registran información geológica.

| Tipo | Qué recupera | Uso típico |
|---|---|---|
| **Diamantina (DDH)** | Testigo de roca intacto | Geología detallada, estructuras, estimación |
| **Aire reverso (RC)** | Detritos (*chips*) | Más rápido y barato; relleno de malla |

Con los sondajes se construyen los modelos geológicos, la interpretación de la mineralización y
la estimación de recursos. Todo lo que viene en el curso parte de esta base de datos.

## Persona competente e informes bancables

- La **persona competente** es el profesional calificado que firma la estimación de recursos y
  reservas, y responde por ella. En Chile la acredita la **Comisión Minera**
  ([buscador](https://www.comisionminera.cl/busca-personas-competentes/)).
- Los códigos nacionales (JORC, NI 43-101, código chileno…) se alinean bajo
  [CRIRSCO](https://www.crirsco.com/).
- Un **informe bancable** (por ejemplo, un NI 43-101) es el documento con el que se financia un
  proyecto. Su capítulo de recursos sigue el mismo orden del curso: compositación, AED, valores
  extremos, variografía, modelo de bloques y estimación.

## QA/QC: aseguramiento y control de calidad

- **QA (aseguramiento)**: los procedimientos que **previenen** errores: protocolos de muestreo,
  preparación y análisis.
- **QC (control)**: las mediciones que **detectan** errores, insertando muestras de control en
  cada lote.

| Muestra de control | Qué es | Qué mide |
|---|---|---|
| **Blanco** | Material estéril (por ejemplo, sílice) | Contaminación entre muestras. Se inserta después de una muestra de ley alta |
| **Estándar (CRM)** | Material con ley certificada | **Exactitud**: si el laboratorio tiene sesgo |
| **Duplicado** | Segunda parte de la misma muestra | **Precisión**: si el resultado se repite |

**Regla de aceptación de estándares** (vista en clase):

- dentro de ±2 desviaciones estándar del valor certificado: aceptado;
- entre 2 y 3 desviaciones: **cuestionable** (se revisa);
- fuera de ±3 desviaciones: **rechazado** (se reanaliza el lote).

!!! info "Límite de detección"
    El valor más bajo que el laboratorio puede medir con confianza (por ejemplo, 0,01 % Cu).
    Los resultados bajo ese límite se registran con una convención y no como cero real.

!!! note "Por qué importa para el resto del curso"
    Los errores de muestreo y análisis aparecen después como **efecto pepita** en el variograma
    ([PPT 06](06-variograma-experimental.md)). Un mal QA/QC termina en una estimación imprecisa.

## Preguntas de repaso

??? question "¿Qué mide un estándar y qué mide un duplicado?"
    El estándar (CRM) mide **exactitud**: compara el resultado con un valor conocido y detecta
    sesgo. El duplicado mide **precisión**: si la misma muestra entrega el mismo valor dos veces.

??? question "¿Por qué el blanco se inserta justo después de una muestra de ley alta?"
    Porque ahí es más probable la contaminación (restos en el chancador, el pulverizador o el
    instrumento). Si el blanco sale con ley, el equipo arrastró material de la muestra anterior.

??? question "Un estándar cae a 2,5 desviaciones del valor certificado. ¿Qué se hace?"
    Es **cuestionable**: se revisan el lote y los estándares vecinos. Si cayera a más de 3
    desviaciones, se rechaza y se reanaliza el lote.
