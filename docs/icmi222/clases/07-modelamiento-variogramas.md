---
tags:
  - ICMI222
  - Apuntes de clase
  - Variografía
---

# PPT 07 · Modelamiento de variogramas

!!! quote "Fuente"
    Resumen propio de la presentación **PPT 07** del curso ICMI222 (semana 9).
    Lectura: Alfaro (2007), cap. III; Isaaks & Srivastava (1989), cap. 16; Rossi & Deutsch (2014), cap. 6.

!!! tip "Materia de la Solemne 2"
    Según la PPT 07, la Solemne 2 cubre variogramas experimentales y modelamiento.

## Por qué modelar

El variograma experimental solo existe en las distancias donde había pares (5, 10, 15 m…) y además
tiene ruido. El kriging necesita \(\gamma\) en **cualquier** distancia. El modelo entrega una
función continua y filtra el ruido.

!!! info "Modelar no es copiar los puntos: es interpretarlos"
    Mandan los puntos cercanos al origen; los lejanos tienen pocos pares.

## No sirve cualquier curva

El modelo debe ser **definido positivo**; si no, el kriging puede entregar varianzas negativas. En la
práctica no se verifica a mano: se usan los modelos conocidos y se **suman**, porque la suma de
modelos válidos también es válida.

## Modelos con meseta

Con meseta \(C\) y alcance \(a\) (más el efecto pepita \(C_0\) cuando corresponde):

**Esférico** (el más usado en minería)

\[ \gamma(h) =
   \begin{cases}
   C\left[\dfrac{3}{2}\dfrac{h}{a} - \dfrac{1}{2}\left(\dfrac{h}{a}\right)^3\right] & h \le a \\[2mm]
   C & h > a
   \end{cases} \]

Sube casi recto y llega a la meseta **exactamente** en \(a\).

**Exponencial**

\[ \gamma(h) = C\left[1 - \exp\!\left(-\frac{3h}{a}\right)\right] \]

Se acerca a la meseta sin tocarla. \(a\) es el **alcance práctico**: el factor 3 hace que en
\(h = a\) llegue al 95 % de la meseta.

**Gaussiano**

\[ \gamma(h) = C\left[1 - \exp\!\left(-\frac{3h^2}{a^2}\right)\right] \]

Arranca **plano** (parabólico): fenómenos muy continuos, como potencias, cotas o espesores; rara vez
leyes.

!!! warning "Gaussiano siempre con un poco de efecto pepita"
    Sin pepita produce inestabilidad numérica en el kriging.

Con el mismo alcance y la misma meseta, lo único que los distingue es **el comportamiento junto al
origen**. Ahí se decide cuál usar.

## Modelos sin meseta

- **Efecto pepita puro:** salta a \(C_0\) y se queda ahí. **No hay correlación espacial**: la
  geoestadística no aporta nada sobre la media aritmética.
- **Potencia:** \(\gamma(h) = b\,h^{\omega}\) con \(0 < \omega < 2\); con \(\omega = 1\) es el
  **lineal**. Crece sin límite; válido bajo la hipótesis intrínseca.

Antes de aceptar un modelo sin meseta, descarta que sea una **deriva**.

## Estructuras anidadas

\[ \gamma(h) = C_0 + \gamma_1(h) + \gamma_2(h) + \dots \]

Dos alcances suelen reflejar **dos escalas geológicas**: vetillas o bandas a corta distancia y el
cuerpo mineralizado a larga distancia. Ejemplo:

\[ \gamma(h) = 0{,}05 + 0{,}10\,\text{Sph}_{30\,m}(h) + 0{,}15\,\text{Sph}_{150\,m}(h) \]

## Cómo ajustar un modelo, paso a paso

1. **Efecto pepita:** extrapolar los primeros puntos hasta el origen.
2. **Meseta:** identificarla y compararla con la varianza de los datos.
3. **Alcance:** leer dónde la curva se aplana.
4. **Forma:** elegirla según el comportamiento junto al origen.
5. **Anidar** estructuras si una sola no describe la curva.

El ajuste es **visual y con criterio**, no una regresión automática. Se ponderan más los puntos
cercanos al origen y se ignoran los que tienen pocos pares.

## Anisotropía en el modelo

- **Geométrica** (misma meseta, distinto alcance): se resuelve con un **elipsoide** de tres alcances
  y tres ángulos.
- **Zonal** (la meseta cambia con la dirección): se agrega una estructura que actúa solo en una
  dirección. Típica de depósitos estratificados.
- **Razón de anisotropía** = alcance mayor / alcance menor.
- La dirección de mayor continuidad debe coincidir con la geología (rumbo, manteo, control estructural).

!!! example "Conexión con el lab"
    Los elipsoides que usamos en el implícito y en el ID2 (por ejemplo, 400 / 200 / 100 m rotado
    180 / 0 / −70 para R101) son justamente elipsoides de este tipo. En un trabajo real saldrían de
    los alcances del variograma modelado. Ver el [tutorial del lab](../lab-modelo-bloques-id2.md).

## Efecto pepita relativo

\[ \text{pepita relativa} = \frac{C_0}{C_0 + C} \]

| Pepita relativa | Continuidad | Consecuencia |
|---|---|---|
| < 0,15 | Muy continua | Kriging preciso |
| 0,15 – 0,30 | Buena | Estimación confiable |
| 0,30 – 0,50 | Moderada | Suavizamiento notorio |
| > 0,50 | Errática | Revisar QA/QC y compósitos antes que el modelo |

Con pepita baja, la muestra más cercana domina los pesos del kriging. Con pepita alta, los pesos se
igualan y el kriging se acerca a un **promedio simple**.

## Del modelo al plan de estimación

| Parámetro del variograma | Decisión que define |
|---|---|
| Alcance mayor | Radio de búsqueda de muestras |
| Elipsoide de continuidad | Orientación y forma de la búsqueda |
| Pepita relativa | Cuánto suavizará el kriging y qué precisión esperar |
| Meseta | Escala de la varianza de estimación |
| Forma cerca del origen | Cuánto peso reciben las muestras más cercanas |

Mismos datos con distinto modelo dan resultados distintos: **elegir el modelo es una decisión que
cambia la estimación**.

## Errores frecuentes

- Forzar el modelo a pasar por todos los puntos, incluso los ruidosos.
- Ajustar mirando las distancias grandes y descuidar el origen.
- Usar un gaussiano sin efecto pepita.
- Modelar una meseta muy distinta de la varianza sin explicar por qué.
- Definir una anisotropía que contradice la geología.
- Usar el mismo modelo para todos los dominios por comodidad.

## Preguntas de repaso

??? question "Esférico y exponencial con el mismo alcance de 100 m: ¿en qué se diferencian?"
    El esférico llega a la meseta exactamente a 100 m. El exponencial sube más rápido al principio y
    a 100 m está en el 95 % de la meseta, pero no la alcanza nunca. Cerca del origen el
    exponencial indica menos continuidad.

??? question "¿Por qué no se usa un modelo gaussiano para leyes de cobre?"
    Porque su arranque plano representa una continuidad muy alta a corta distancia, que es raro en
    leyes. Además, sin efecto pepita genera inestabilidad numérica en el kriging.

??? question "Un variograma tiene C0 = 0,2 y C = 0,3. ¿Cómo lo lees?"
    La meseta total es 0,5 y la pepita relativa es 0,2 / 0,5 = 0,40: continuidad **moderada**, con
    suavizamiento notorio en la estimación.

??? question "¿Qué significa un variograma de efecto pepita puro para la estimación?"
    Que no hay correlación espacial a la escala del muestreo. El kriging le daría el mismo peso a
    todas las muestras: la estimación equivale a la media del dominio.
