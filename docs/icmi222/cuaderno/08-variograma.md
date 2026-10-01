---
tags:
  - ICMI222
  - Cuaderno
---

# Variograma experimental (semana 8 · 21/09)

!!! quote "Cuaderno de clases"
    Mis apuntes de esa clase, ordenados y corregidos. Las capturas son de Vulcan y de los laboratorios.
    Las 17 diapositivas del curso que acompañaban estas notas no se publican: su contenido está resumido en [el apunte de clase](../clases/06-variograma-experimental.md).

En esta clase se construyeron los dominios a lo largo del sondaje y se calculó el variograma sobre el mismo sondaje.

## 8.1 La idea del variograma

- El variograma compara pares de muestras y mide cuánto varían las leyes a cierta distancia: a medida que se alejan, son más diferentes.
- Se calcula con muchos pares de muestras y se aplica sobre **compósitos**.
- Las leyes de cada par se **restan**; como la resta puede dar negativa, se **eleva al cuadrado**.
- Se **promedian** los cuadrados y el promedio se **divide por 2**: ese es el valor de gamma (γ).

Se toma una muestra conocida en x y otra a una distancia x + h; se saca la diferencia, se eleva al cuadrado y luego se divide por 2.

\[ \gamma(h) = \frac{1}{2N(h)} \sum_{i=1}^{N(h)} \big[z(x_i) - z(x_i + h)\big]^2 \]

Se suman todos los pares separados por la distancia h, y eso es la sumatoria. N(h) es el número de pares.

- Cada muestra tiene su ley asociada, y cada distancia tiene su propio grupo de pares.
- Con 8 muestras hay **7 pares** a 5 m: se saca la diferencia de cada par y se eleva al cuadrado.
- A **menor distancia, menor variación**; a **mayor distancia, mayor variación**.
- **Para qué sirve en minería:** traduce la continuidad de las leyes en información para estimar el recurso.

## 8.2 Partes del variograma

- **Comportamiento en el origen:** el desplazamiento sobre el eje y en h ≈ 0 es variabilidad que existe incluso entre muestras casi pegadas.
- Ese salto se llama **efecto pepita** (por las pepitas de oro).
- La **meseta** es el valor máximo de variabilidad, donde la curva se estabiliza.
- El **alcance** es la distancia donde se llega a la meseta: más allá, las muestras se comportan como independientes.

- El efecto pepita se relaciona con el **QA/QC**: los errores de muestreo y análisis lo aumentan.
- **Compositar reduce el efecto pepita.**
- En esta clase también se hizo una estimación con inverso de la distancia en un modelo de bloques.

- **Alcance:** distancia a la que el variograma se estabiliza.
- **Meseta:** es un valor estadístico, aproximadamente igual a la **varianza** de los datos usados en el cálculo.
- Para estimar puntos se define un radio de búsqueda. Un variograma **omnidireccional** mira en todas las direcciones a la vez.

## 8.3 Cómo se eligen los pares

En la realidad los datos no están ordenados en una grilla perfecta, así que se definen **tolerancias**: la **tolerancia angular** y el **ancho de banda**. El **paso** (lag) es la distancia h entre clases.

El variograma puede parecerse a distintas funciones matemáticas según lo errática que sea la variable.

A medida que la distancia aumenta se pueden evaluar menos pares, y el variograma es **menos representativo**.

## 8.4 Reglas prácticas

- Los variogramas se hacen **siempre sobre compósitos**.
- Cada **dominio** tiene su propio variograma.
- Mínimo **30 pares** para cada punto del variograma.
- No graficar a distancias mayores que la **mitad del campo**.

## 8.5 Anisotropía

**Anisotropía:** un alcance distinto según la dirección, con la misma meseta. Si todo es igual en cualquier dirección, el depósito es **isótropo**.
