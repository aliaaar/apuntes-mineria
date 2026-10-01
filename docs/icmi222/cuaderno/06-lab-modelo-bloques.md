---
tags:
  - ICMI222
  - Cuaderno
---

# Laboratorio: modelo de bloques, dominios y estimación (08/09)

!!! quote "Cuaderno de clases"
    Mis apuntes de esa clase, ordenados y corregidos. Las capturas son de Vulcan y de los laboratorios.
    Las 1 diapositivas del curso que acompañaban estas notas no se publican: su contenido está resumido en [el apunte de clase](../clases/04-variable-regionalizada.md).
    Paso a paso completo, con todos los parámetros: [tutorial del lab](../lab-modelo-bloques-id2.md).

## 6.1 Cargar los compósitos

1. **Geology → Sampling → Load...**
1. En *Load Sample Groups*, dejar el patrón `*` para cargar todos los compósitos.
1. En *Setup Display*: **Samples field = RTTEXT** y **Colour legend = RT**, para ver cada dominio de un color.

<figure markdown="span">
  ![Geology → Sampling → Load.](img/image89.png){ width="760" loading=lazy }
  <figcaption>Geology → Sampling → Load.</figcaption>
</figure>

<figure markdown="span">
  ![Load Sample Groups con patrón * (izquierda) y Setup Display coloreando por RTTEXT (derecha).](img/image35.png){ width="360" loading=lazy }
  ![Load Sample Groups con patrón * (izquierda) y Setup Display coloreando por RTTEXT (derecha).](img/image106.png){ width="360" loading=lazy }
  <figcaption>Load Sample Groups con patrón * (izquierda) y Setup Display coloreando por RTTEXT (derecha).</figcaption>
</figure>

<figure markdown="span">
  ![Setup Display sobre la pantalla de Vulcan.](img/image58.png){ width="539" loading=lazy }
  <figcaption>Setup Display sobre la pantalla de Vulcan.</figcaption>
</figure>

## 6.2 Definir y crear el modelo de bloques

1. **Block → Construction → New Definition...**
1. Usar **Autofit primero**: Vulcan ajusta el origen y la extensión a los datos cargados.
1. Revisar en *Interactive* el tamaño de bloque (20 × 20 × 20 m) y el número de bloques (34 × 30 × 55 = 56.100).
1. En **Variables**, crear la variable de dominio con valor por defecto **none** (en vez de −99) y las leyes con −99.
1. Guardar el .bdf y pinchar **Create Model**.

<figure markdown="span">
  ![Block → Construction → New Definition.](img/image49.png){ width="760" loading=lazy }
  <figcaption>Block → Construction → New Definition.</figcaption>
</figure>

<figure markdown="span">
  ![Block Construction vacío, antes del Autofit.](img/image99.png){ width="588" loading=lazy }
  <figcaption>Block Construction vacío, antes del Autofit.</figcaption>
</figure>

<figure markdown="span">
  ![Edit Interactive Block Model: origen, bearing 36°, bloques de 20 m y 56.100 bloques.](img/image42.png){ width="637" loading=lazy }
  <figcaption>Edit Interactive Block Model: origen, bearing 36°, bloques de 20 m y 56.100 bloques.</figcaption>
</figure>

<figure markdown="span">
  ![Definición final: esquema PARENT de 680 × 600 × 1100 m.](img/image39.png){ width="637" loading=lazy }
  <figcaption>Definición final: esquema PARENT de 680 × 600 × 1100 m.</figcaption>
</figure>

**Así se debe ver:** la caja del modelo envolviendo todos los compósitos.

<figure markdown="span">
  ![Caja del modelo de bloques con los compósitos coloreados por dominio.](img/image15.png){ width="377" loading=lazy }
  <figcaption>Caja del modelo de bloques con los compósitos coloreados por dominio.</figcaption>
</figure>

!!! note "Complemento · −99 no es ley cero"
    - El valor por defecto −99 (o *none* en variables de texto) significa **sin información**. Si se usara 0, los bloques no estimados se promediarían como estéril y se subestimaría el recurso.

## 6.3 Dominios con modelamiento implícito

1. Cargar las triangulaciones de los dominios desde el panel Data (*Triangulations*).
1. **Geology → Implicit Modelling → Implicit Modelling Editor.**
1. *Open Specifications*: RBF, **Categorical**, base `ld.cmp.isis`, campo **RTTEXT**, coordenadas MIDX / MIDY / MIDZ.
1. *Parameters*: limitar los sólidos con la topografía `topo.00t`.
1. *Block Model*: elegir el modelo de bloques creado.
1. *Domains*: una fila por dominio (R101, R102, R111, R112) con su elipsoide de tendencia → **Apply and Run**.

<figure markdown="span">
  ![Triangulaciones en el panel Data (izquierda) y menú Implicit Modelling Editor (derecha).](img/image30.png){ width="360" loading=lazy }
  ![Triangulaciones en el panel Data (izquierda) y menú Implicit Modelling Editor (derecha).](img/image25.png){ width="360" loading=lazy }
  <figcaption>Triangulaciones en el panel Data (izquierda) y menú Implicit Modelling Editor (derecha).</figcaption>
</figure>

<figure markdown="span">
  ![Open Specifications: RBF categórico sobre RTTEXT.](img/image88.png){ width="637" loading=lazy }
  <figcaption>Open Specifications: RBF categórico sobre RTTEXT.</figcaption>
</figure>

<figure markdown="span">
  ![Parameters: límite por topografía y suavizado.](img/image53.png){ width="637" loading=lazy }
  <figcaption>Parameters: límite por topografía y suavizado.</figcaption>
</figure>

<figure markdown="span">
  ![Block Model: el modelo de bloques donde se escriben los dominios.](img/image107.png){ width="637" loading=lazy }
  <figcaption>Block Model: el modelo de bloques donde se escriben los dominios.</figcaption>
</figure>

<figure markdown="span">
  ![Domains: elipsoide de tendencia y código de salida de cada dominio.](img/image41.png){ width="637" loading=lazy }
  <figcaption>Domains: elipsoide de tendencia y código de salida de cada dominio.</figcaption>
</figure>

- A cada dominio se le da una **influencia** (elipsoide de tendencia). Esta información la entrega el **geólogo**, que indica hasta qué profundidad y en qué dirección se extiende cada cuerpo.
- Con este resultado se hace una **validación visual**: comparar los sólidos y los bloques con los compósitos.

## 6.4 Estimación por inverso de la distancia

1. **Block → Grade Estimation → Univariate Estimation Editor.**
1. Pinchar **New** y dar un nombre al escenario (por ejemplo, ID2_101).
1. *Samples Selection*: base `ld.cmp.isis`, grupo LD, coordenadas MIDX / MIDY / MIDZ y la ley a estimar (CU).
1. *Select Using Filter*: **Character Filter** por RTTEXT con el texto del dominio (R101) y pinchar **Find All** para probar.
1. *Estimation Result Variables*: variable del modelo donde se guarda la ley.
1. *Search Region*: elipsoide de búsqueda (bearing 180, dip −70; 400 / 200 / 100 m).
1. *Inverse Distance*: **Normalize** los radios anisotrópicos y potencia 2.
1. *Sample Count*: mínimo 2 y máximo 16 muestras.
1. *Block Selection*: **Use Bounding Triangulation** con el sólido del dominio → **Save and Run**.

<figure markdown="span">
  ![Block → Grade Estimation → Univariate Estimation Editor.](img/image90.png){ width="760" loading=lazy }
  <figcaption>Block → Grade Estimation → Univariate Estimation Editor.</figcaption>
</figure>

<figure markdown="span">
  ![Editor vacío con el botón New (izquierda) y nombre del escenario ID2_101 (derecha).](img/image10.png){ width="360" loading=lazy }
  ![Editor vacío con el botón New (izquierda) y nombre del escenario ID2_101 (derecha).](img/image64.png){ width="360" loading=lazy }
  <figcaption>Editor vacío con el botón New (izquierda) y nombre del escenario ID2_101 (derecha).</figcaption>
</figure>

<figure markdown="span">
  ![Samples Selection: base de datos, grupo y ley a estimar.](img/image51.png){ width="637" loading=lazy }
  <figcaption>Samples Selection: base de datos, grupo y ley a estimar.</figcaption>
</figure>

<figure markdown="span">
  ![Select Using Filter: filtro de texto RTTEXT = R101 y Find All.](img/image103.png){ width="637" loading=lazy }
  <figcaption>Select Using Filter: filtro de texto RTTEXT = R101 y Find All.</figcaption>
</figure>

<figure markdown="span">
  ![Estimation Result Variables.](img/image17.png){ width="637" loading=lazy }
  <figcaption>Estimation Result Variables.</figcaption>
</figure>

<figure markdown="span">
  ![Search Region: elipsoide de búsqueda.](img/image98.png){ width="637" loading=lazy }
  <figcaption>Search Region: elipsoide de búsqueda.</figcaption>
</figure>

<figure markdown="span">
  ![Inverse Distance: radios anisotrópicos normalizados y potencia 2.](img/image94.png){ width="637" loading=lazy }
  <figcaption>Inverse Distance: radios anisotrópicos normalizados y potencia 2.</figcaption>
</figure>

<figure markdown="span">
  ![Sample Count: mínimo y máximo de muestras por estimación.](img/image91.png){ width="637" loading=lazy }
  <figcaption>Sample Count: mínimo y máximo de muestras por estimación.</figcaption>
</figure>

<figure markdown="span">
  ![Block Selection con el sólido RT_101 como límite y prueba con Find All.](img/image70.png){ width="360" loading=lazy }
  ![Block Selection con el sólido RT_101 como límite y prueba con Find All.](img/image22.png){ width="360" loading=lazy }
  <figcaption>Block Selection con el sólido RT_101 como límite y prueba con Find All.</figcaption>
</figure>

## 6.5 Visualizar el resultado

1. **Block → Viewing → Load Dynamic Model...**
1. Elegir el modelo, la variable estimada (cu) y la leyenda de colores.
1. Opcional: mostrar el valor de cada bloque como texto (*Block Model Variable Annotation*).

<figure markdown="span">
  ![Block → Viewing → Load Dynamic Model.](img/image95.png){ width="539" loading=lazy }
  <figcaption>Block → Viewing → Load Dynamic Model.</figcaption>
</figure>

<figure markdown="span">
  ![Dynamic Block Model Details (izquierda) y anotación del valor de cada bloque (derecha).](img/image80.png){ width="360" loading=lazy }
  ![Dynamic Block Model Details (izquierda) y anotación del valor de cada bloque (derecha).](img/image7.png){ width="360" loading=lazy }
  <figcaption>Dynamic Block Model Details (izquierda) y anotación del valor de cada bloque (derecha).</figcaption>
</figure>

!!! note "Complemento · Resultado de la estimación de R101 (desarrollada el 30/09)"
    - 2.692 compósitos de R101 (Cu medio 0,753 %), 2.266 bloques dentro del sólido RT_101 y **100 % estimados**.
    - El máximo de R101 es **12,51 % Cu** (sondaje 154): no se aplicó capping y ese valor infla los bloques vecinos.
    - El tutorial completo, con todos los parámetros, está en aliaaar.github.io/apuntes-mineria.
