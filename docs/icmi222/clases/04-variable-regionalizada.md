---
tags:
  - ICMI222
  - Apuntes de clase
  - Geoestadística
  - Estacionariedad
---

# PPT 04 · Variable regionalizada y función aleatoria

!!! quote "Fuente"
    Resumen propio de la presentación **PPT 04** del curso ICMI222 (semana 6).
    Lectura: Alfaro (2007), cap. II; Isaaks & Srivastava (1989), cap. 1; Rossi & Deutsch (2014), cap. 2.

## Dónde estamos

La estadística descriptiva **ignora dónde está cada muestra**: si se reordenan los datos, el
histograma no cambia. Pero en un yacimiento la posición es información. Se necesita un modelo que
**mida la continuidad** y permita **estimar con un error asociado**: la teoría de las variables
regionalizadas.

## La crítica a los métodos tradicionales

Media aritmética, polígonos e inverso de la distancia comparten las mismas debilidades:

- son **empíricos y geométricos**: los pesos dependen de la distancia o el área, no del
  comportamiento del mineral;
- **no consideran la estructura**: ni la continuidad de las leyes ni la anisotropía;
- **no corrigen el agrupamiento** de datos;
- **no entregan un error**: dan un número sin medida de confianza;
- producen **sesgo condicional**: sobrestiman los bloques ricos y subestiman los pobres.

!!! example "Dos sondajes, la misma estadística"
    Dos sondajes pueden tener igual media e igual varianza y, sin embargo, uno muestra leyes que
    cambian suavemente y el otro leyes que saltan de un tramo a otro. La estadística clásica no los
    distingue; la geoestadística sí, porque mide la **continuidad espacial**.

!!! info "Conexión con el lab"
    El laboratorio de esta semana fue justamente estimar por **inverso de la distancia por
    dominios**: ver el [tutorial del lab](../lab-modelo-bloques-id2.md). Sus limitaciones son
    las de esta lista.

## Variable regionalizada

Función \(z(x)\) que representa la variación en el espacio de una magnitud asociada a un fenómeno
natural. \(x\) es un punto (en 1, 2 o 3 dimensiones), escrito con una sola letra.

- Es **irregular**: no es derivable ni se puede escribir como un polinomio.
- **"Regionalizada"** significa que el valor está anclado a una posición.
- Ojo con la notación: \(z\) también se usa para la cota. Hay que declarar qué significa.

## Campo, dominio y soporte

| Concepto | Definición |
|---|---|
| **Campo** | Zona del espacio donde se estudia la variable. Sus límites salen del modelo geológico, no son arbitrarios |
| **Dominio** | Subdivisión del campo: unidades \(D_1, D_2, \dots, D_k\), en general disjuntas, cada una con su propio tratamiento |
| **Soporte** | Volumen, forma y orientación de la muestra. La compositación lleva los tramos a un soporte común |

**Fronteras duras:** para estimar dentro de una unidad se usan solo datos de esa unidad. Se
justifican cuando las leyes de ambas unidades son independientes, y eso se comprueba con el
análisis de contactos.

## Variables aditivas y no aditivas

Una variable es **aditiva** si el valor de la unión de dos soportes es el promedio ponderado por
volumen de sus valores:

\[ z(v_1 \cup v_2) = \frac{|v_1|\, z(v_1) + |v_2|\, z(v_2)}{|v_1| + |v_2|} \]

| Aditivas (se pueden estimar directo) | No aditivas (no se promedian) |
|---|---|
| Leyes, potencias, acumulaciones, densidad | Índice de trabajo (WI), recuperación metalúrgica, razón de solubilidad CuS/CuT |

!!! note "Caso de las vetas"
    En una veta de potencia variable la ley no es aditiva. Se estiman la **potencia** \(p\) y la
    **acumulación** \(a = p \cdot z\), y la ley se recupera al final como \(z^* = a^* / p^*\).

!!! warning "Antes de estimar cualquier variable, pregúntate si es aditiva"
    El software promedia lo que le pidas, aunque no tenga sentido físico.

## Los dos objetivos de la teoría

1. **Describir la estructura**: cuantificar la continuidad y la anisotropía → **variograma**.
2. **Estimar con error**: asignar a cada estimación una medida de su precisión → **kriging**.

Están ligados: mientras más irregular es la variable, mayor es el error de estimación.

## La función aleatoria

**Problema:** hay un solo yacimiento y no se puede repetir el experimento.

**Solución de Matheron:** suponer que \(z(x)\) es **una realización** de una **función aleatoria**
\(Z(x)\), que asigna a cada punto del espacio una variable aleatoria. El yacimiento real es una de
las infinitas realizaciones posibles.

!!! warning "Enunciado correcto"
    "\(z(x)\) es una realización de la función aleatoria \(Z(x)\)". Decir que el yacimiento "es
    aleatorio" es como decir que el número 6 es una variable aleatoria. La función aleatoria es un
    **modelo**, no describe cómo se formó el depósito.

Esta idea reaparece en **simulación geoestadística**: cada simulación es otra realización
igualmente compatible con los datos.

## Estacionariedad

Con una sola realización, para inferir los parámetros de \(Z(x)\) hace falta una hipótesis más.

**Estacionariedad de segundo orden**

\[ E[Z(x)] = m \quad \forall x
   \qquad
   \operatorname{Cov}\big(Z(x), Z(x+h)\big) = C(h) \]

La media es la misma en todo el dominio y la covarianza depende solo del vector \(h\) que separa los
puntos, no de dónde están.

**Hipótesis intrínseca** (más débil): basta con que los **incrementos** sean estacionarios.

\[ E[Z(x+h) - Z(x)] = 0
   \qquad
   \operatorname{Var}[Z(x+h) - Z(x)] = 2\gamma(h) \]

De aquí nace el **variograma** \(\gamma(h)\). Si además hay estacionariedad de segundo orden,
\(\gamma(h) = C(0) - C(h)\).

!!! info "Es una decisión, no una propiedad de la roca"
    La estacionariedad se **decide, se justifica y se documenta**. Si hay una tendencia sistemática
    (deriva), no se sostiene: hay que acotar el dominio, trabajar localmente o modelar la deriva.

## Errores conceptuales frecuentes

- Decir que la variable regionalizada "es aleatoria".
- Confundir campo con dominio.
- Suponer estacionariedad global en un depósito con zonación evidente, en vez de trabajar por dominios.
- Estimar directamente variables no aditivas.
- Mezclar soportes distintos en un mismo análisis.
- Creer que el modelo probabilístico describe la génesis del depósito.

## Preguntas de repaso

??? question "¿Por qué no se puede promediar la recuperación metalúrgica de dos bloques?"
    Porque no es aditiva: la recuperación de la mezcla depende de cuánto metal aporta cada bloque,
    no solo de su volumen. Se estiman las variables aditivas (ley de cabeza, metal recuperado) y la
    recuperación se calcula al final.

??? question "¿Qué diferencia hay entre estacionariedad de segundo orden e hipótesis intrínseca?"
    La de segundo orden pide media constante y covarianza que depende solo de \(h\) (varianza
    finita). La intrínseca solo pide que las diferencias \(Z(x+h)-Z(x)\) tengan media cero y
    varianza que dependa de \(h\). Es más general y es la que justifica el variograma, incluso sin
    meseta.

??? question "Nombra tres limitaciones del inverso de la distancia frente al kriging."
    No usa la continuidad medida por el variograma, no corrige el agrupamiento de muestras (la
    redundancia) y no entrega error de estimación. Además produce sesgo condicional.
