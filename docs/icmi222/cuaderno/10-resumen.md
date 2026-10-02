---
tags:
  - ICMI222
  - Cuaderno
---

# Resumen de conceptos

!!! quote "Cuaderno de clases"
    Mis apuntes de esa clase, ordenados y corregidos. Las capturas son de Vulcan y de los laboratorios.

| Concepto | Definición |
|---|---|
| **Varianza** | Cuantifica la dispersión de los datos respecto de la media. |
| **Desviación estándar** | Raíz cuadrada de la varianza: cuánto se aleja una ley típica del yacimiento de la media. |
| **Skewness (asimetría)** | Mide qué tan simétrica es la distribución respecto de una campana de Gauss. Positiva: cola de valores altos. |
| **Curtosis** | Qué tan pesadas son las colas de la distribución (cuántos valores extremos hay). |
| **Sondaje vs. compósito** | El sondaje es la perforación real hecha en terreno; el compósito es una regularización matemática de sus muestras a un largo fijo. |
| **Pearson** | Mide qué tan relacionadas están linealmente dos variables (por ejemplo, Mo y Cu). Va de −1 a +1. |
| **Spearman** | Mide la correlación entre los rangos de los datos. Es más robusto frente a valores atípicos que Pearson. |
| **Soporte** | Volumen, forma y orientación geométrica con que se toma y mide una muestra. |
| **Variograma** | Mide la continuidad espacial: la diferencia promedio al cuadrado entre pares de muestras según la distancia que las separa. Dice a qué distancia dos muestras dejan de parecerse. |
| **Efecto pepita** | El salto del variograma en el origen. Puede venir de vetillas de alta ley o de errores de muestreo. Si es muy alto, los datos son erráticos y la estimación tendrá mucho suavizamiento. |
| **Alcance** | Distancia de influencia máxima de una muestra: donde el variograma se estabiliza. Define el radio de búsqueda para estimar los bloques. |
| **Meseta** | Valor constante máximo del variograma. Al llegar a ella se pierde la estructura espacial y la variabilidad entre puntos es igual a la varianza global. |
| **Anisotropía** | La continuidad cambia según la dirección. Se detecta calculando variogramas en distintas direcciones (azimut y manteo): cambia el alcance o la forma de la curva. |
| **Isotropía** | La propiedad es igual sin importar la dirección desde la que se mire. |

## Preguntas que quedaron abiertas

!!! note "Complemento · ¿Qué pasa si el variograma no llega a tocar la meseta?"
    - Tu respuesta: ocurre en modelos que nunca dejan de correlacionarse a la escala del yacimiento. Es una de las causas; conviene revisar estas tres, en este orden:
    - **Deriva (tendencia):** la ley media cambia sistemáticamente dentro del dominio (por ejemplo, con la profundidad). El variograma sigue subiendo. Hay que acotar el dominio o modelar la tendencia.
    - **El campo es más chico que el alcance:** no hay pares a distancia suficiente para ver la meseta.
    - **Comportamiento sin meseta real:** se modela con un modelo **potencia** o **lineal**, válidos bajo la hipótesis intrínseca.
    - Los modelos asintóticos (exponencial, gaussiano) tampoco tocan la meseta: ahí se usa el alcance práctico, al 95 %.

!!! note "Complemento · ¿Qué relación tiene el efecto pepita con la meseta?"
    - Tu respuesta: **se complementan para sumar la varianza total**. Si el efecto pepita se lleva gran parte de la meseta, el depósito es tan desordenado que es difícil de predecir con exactitud.
    - Eso se mide con el **efecto pepita relativo**:
    *C₀ / (C₀ + C)*
    
    - < 0,15: variable muy continua, kriging preciso · 0,15–0,30: buena · 0,30–0,50: moderada, suavizamiento notorio · > 0,50: errática, revisar QA/QC y compósitos.
    - Con pepita baja, la muestra más cercana domina los pesos del kriging. Con pepita alta, los pesos se igualan y la estimación se acerca a un promedio simple.

## Tipos de gráficos: los modelos de variograma

| Modelo | Qué identifica | Cómo se reconoce en el gráfico |
|---|---|---|
| **Esférico** | El más usado en geología de minas. Fenómenos con continuidad espacial **moderada y bien comportada**. | Cerca del origen sube en **línea recta**. Llega a la meseta de forma nítida justo en el alcance, con un "hombro" bien marcado antes de aplanarse. |
| **Exponencial** | Fenómenos más **erráticos**, discontinuos o con cambios bruscos a corta distancia (vetillas complejas, mineralización muy alterada). | Cerca del origen sube **muy empinado** (más rápido que el esférico). Nunca toca la meseta: se acerca lentamente, por eso se usa el **alcance práctico** al 95 %. |
| **Gaussiano** | Fenómenos de continuidad **extremadamente suave y regular** (algunos depósitos de hierro, mantos sedimentarios amplios, potencias, topografía). | Forma de **S**: arranca casi horizontal, se acelera en la zona media y frena para tocar la meseta. |

!!! warning "Ojo · corrección · Ojo con el gaussiano"
    - Es muy exigente: si los datos no son realmente tan suaves como indica la curva, genera **inestabilidad numérica** en la estimación. Siempre se usa con un pequeño efecto pepita.
