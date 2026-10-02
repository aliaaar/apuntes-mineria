---
tags:
  - Interpretación
  - Dominios
---

# Perfil de contacto (análisis de contactos)

## Qué muestra

La **ley media a distintas distancias de un contacto** entre dos dominios: hacia un lado, las muestras
de un dominio; hacia el otro, las del vecino. Responde si para estimar un dominio se pueden usar
muestras del otro, es decir, si el contacto es **duro** o **blando**.

| Elemento (en Vulcan) | Qué representa |
|---|---|
| Eje X | Distancia al contacto (negativa hacia un dominio, positiva hacia el otro) |
| Línea vertical en 0 | El contacto |
| Eje Y | Ley media de las muestras a esa distancia |
| Número sobre cada punto | **Cuántas muestras** hay en esa distancia |
| Líneas horizontales | Ley media global de cada dominio |
| Tablas | Estadísticas de cada lado (*Left / Right statistics*) |

## Cómo leerlo

1. **Mira justo a los dos lados del 0.** ¿La ley salta o es parecida?
2. **Mira la tendencia al acercarse al contacto.** ¿Cada lado se mantiene en su media o cambia
   gradualmente hacia el valor del otro?
3. **Revisa el número de muestras** de cada punto: con menos de ~20–30 muestras, el punto no es
   confiable.
4. **Estima hasta qué distancia llega la transición:** es la distancia hasta la que conviene compartir
   muestras.

## Patrones típicos

| Lo que ves | Tipo de contacto | Qué hacer al estimar |
|---|---|---|
| Salto brusco de ley justo en el 0 | **Duro** | Cada dominio se estima solo con sus muestras |
| Ley parecida a ambos lados del 0, con cambio gradual | **Blando** | Se pueden usar muestras del otro dominio hasta la distancia de la transición |
| Un lado cambia y el otro no | Transición solo en un dominio | Compartir muestras en un solo sentido |
| Puntos lejanos que saltan mucho | Pocas muestras | No interpretar |

!!! question "¿Por qué importa?"
    Si el contacto es duro y se comparten muestras, los bloques junto al contacto se contaminan con
    leyes del otro dominio (un halo pobre sube; un núcleo rico baja). Si el contacto es blando y **no**
    se comparten, la estimación genera un salto artificial que no existe en la roca.

## Ejemplo con datos reales: Cu entre R102 y R112

![Perfil de contacto de Cu entre R102 y R112](img/vulcan-contacto-cu.png)

- **Junto al contacto** la ley es casi igual a ambos lados: ~0,28 % en R102 y ~0,30 % en R112. **No
  hay salto**: es un contacto **blando**.
- **R102 baja gradualmente** al acercarse al contacto (de ~0,34 % a 75 m hasta ~0,28 %), por debajo
  de su media global (0,41 %). La transición se nota en las últimas decenas de metros.
- En **R112**, el pico de 0,43–0,46 % entre 35 y 45 m tiene unas 45 muestras por punto, pero desde
  ~55 m quedan menos de 10 y la curva cae a cero: **no se interpreta**.
- Conclusión de clase: para estimar R102 se pueden usar unos **25 m** de muestras de R112, y para R112
  hasta **75–100 m** de R102.

![Perfil de contacto de Au entre R102 y R112](img/vulcan-contacto-au.png)

## Qué escribir en un informe

- "El perfil de contacto de Cu entre R102 y R112 no muestra un salto de ley en el contacto (0,28 % y
  0,30 % a ambos lados), por lo que se trata como un contacto blando. Se permite usar muestras de
  R112 hasta 25 m del contacto para estimar R102."
- Para cada par de dominios vecinos, qué tipo de contacto se definió y con qué evidencia.
