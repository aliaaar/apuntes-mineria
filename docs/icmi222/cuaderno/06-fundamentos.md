---
tags:
  - ICMI222
  - Cuaderno
---

# Fundamentos de geoestadística (semana 6 · 07/09)

!!! quote "Cuaderno de clases"
    Mis apuntes de esa clase, ordenados y corregidos. Las capturas son de Vulcan y de los laboratorios.
    Las 8 diapositivas del curso que acompañaban estas notas no se publican: su contenido está resumido en [el apunte de clase](../clases/04-variable-regionalizada.md).

- Leyes **cercanas** se parecen; leyes **lejanas** no se parecen.
- Si no hay una herramienta que cuantifique esa relación según la distancia (el **variograma**), no se habla de geoestadística.

## 5.1 Crítica a los métodos tradicionales

- **Polígonos:** método geométrico basado en un área de influencia alrededor de cada muestra.
- **Inverso de la distancia:** pondera cada muestra según su distancia al punto a estimar.
- **Defectos:** son empíricos y muy geométricos, y no consideran el agrupamiento. Con datos agrupados (por sondajes) hay sobreestimación; a los datos agrupados se les debe bajar la ponderación.
- La **geoestadística** entrega un valor **y un rango de error**; los métodos tradicionales generan **sesgo** (sobreestimación o subestimación).

## 5.2 Misma estadística, distinta continuidad

- La idea es mostrar que los mismos valores estadísticos pueden venir de comportamientos espaciales distintos.
- En los gráficos primero se revisan los ejes x e y.
- En el sondaje A, de 0 a 10 m baja la ley, de 10 a 30 m sube y de 30 a 60 m se nota más estable. Las leyes van de ~30 % Fe a ~45 % Fe (en hierro, los concentrados llegan a ~60 % Fe).
- El sondaje B tiene un comportamiento mucho **más errático**.
- Ambos tienen **igual varianza pero distinta continuidad**: la desviación estándar mide la dispersión respecto de la media, no cómo se ordenan los valores en el espacio.

## 5.3 Variable regionalizada

**Ejemplos de variables regionalizadas vistos en clase:** una playa, un monte en Lirquén y la potencia de agua en napas subterráneas.

En la galería se saca una **tajada** de material (se "tajea") y de ahí se obtiene una muestra.

## 5.4 Soporte, aditividad y variable aleatoria

Las **variables no aditivas** no sirven para la estimación directa.

!!! note "Complemento · Variables aditivas y no aditivas"
    - Una variable es **aditiva** si el valor de la unión de dos volúmenes es el promedio ponderado por volumen: **leyes, potencias, acumulaciones, densidad**.
    - **No aditivas:** índice de trabajo (WI), recuperación metalúrgica, razón de solubilidad CuS/CuT. Promediarlas no tiene sentido físico, aunque el software lo permita.
    - En vetas se estiman la **potencia** y la **acumulación** (ley × potencia), y la ley se recupera al final como su cociente.

- Ejemplo de dominios: **óxidos, sulfuros** y una tercera unidad.
- El **valor esperado** en cualquier punto debe ser el **valor medio** del dominio: es la hipótesis de **estacionariedad**.

!!! note "Complemento · Función aleatoria y estacionariedad"
    - Como hay un solo yacimiento, se supone que z(x) es **una realización** de una **función aleatoria** Z(x). Es un modelo de cálculo, no describe cómo se formó el depósito.
    - **Estacionariedad de segundo orden:** media constante en el dominio y covarianza que depende solo de la distancia h.
    - **Hipótesis intrínseca:** basta con que las diferencias Z(x+h) − Z(x) sean estacionarias. De ahí nace el variograma.
