---
tags:
  - Interpretación
---

# Cómo interpretar gráficos

Guía para **leer** los gráficos de un estudio de recursos y **sacar conclusiones** de ellos. No
explica cómo generarlos (eso está en los tutoriales), sino qué mirar, qué significa cada patrón y qué
decisión sale de ahí.

Cada página tiene la misma estructura:

1. **Qué muestra** el gráfico.
2. **Cómo leerlo**, paso a paso.
3. **Patrones típicos**: lo que ves → qué significa → qué hacer.
4. **Ejemplo con datos reales** del dataset ICMI222 (dominio R101 y los demás).
5. **Qué escribir en un informe**.

## Qué gráfico responde cada pregunta

| Pregunta | Gráfico | Decisión que sale de ahí |
|---|---|---|
| ¿Cómo se distribuyen las leyes? ¿Hay una o varias poblaciones? | [Histograma](histograma.md) | Dominios, transformación logarítmica |
| ¿Cómo se comparan los dominios? ¿Dónde están los extremos? | [Box plot](box-plot.md) | Separar o juntar dominios, revisar atípicos |
| ¿Siguen una distribución lognormal? ¿Desde qué valor empiezan los atípicos? | [Gráfico de probabilidad](probabilidad.md) | Umbral de capping o de filtro |
| ¿Dos variables están relacionadas? | [Dispersión y correlación](dispersion.md) | Estimar juntas o por separado, regresión |
| ¿Dos dominios o campañas tienen la misma distribución? | [Gráfico Q-Q](qq.md) | Juntar o separar, detectar sesgo |
| ¿El contacto entre dominios es duro o blando? | [Perfil de contacto](perfil-contacto.md) | Compartir o no muestras al estimar |
| ¿Hasta qué distancia se parecen las leyes? ¿En qué dirección? | [Variograma](variograma.md) | Elipsoide de búsqueda, parámetros de kriging |

## Orden recomendado en un análisis

```mermaid
flowchart LR
    A[Histograma] --> B[Box plot<br>por dominio]
    B --> C[Gráfico de<br>probabilidad]
    C --> D[Dispersión<br>y Q-Q]
    D --> E[Perfil de<br>contacto]
    E --> F[Variograma]
```

Primero se entiende **cada dominio por separado** (forma, extremos), después se comparan **entre sí**
(dispersión, Q-Q, contactos) y al final se mide la **continuidad espacial** (variograma). Cada paso
depende de las decisiones del anterior: un variograma calculado con dominios mezclados o con atípicos
sin revisar no sirve.
