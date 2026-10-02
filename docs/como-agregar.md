# Cómo agregar un tutorial

## 1. Crear el archivo

1. Copia `plantillas/tutorial.md` dentro de la carpeta del ramo, por ejemplo
   `docs/icmi222/aed-univariado.md`. Si el ramo es nuevo, crea su carpeta (`docs/icmi333/`) con un
   `index.md`.
2. Llena las etiquetas del inicio (ramo, software, temas). Son las que alimentan la página
   [Etiquetas](etiquetas.md).
3. Guarda las capturas en `docs/<ramo>/img/<nombre-del-tutorial>/` y enlázalas con
   `![descripción](img/<nombre-del-tutorial>/archivo.png)`.

## 2. Agregarlo al menú

En `mkdocs.yml`, dentro de `nav:`, agrega una línea bajo el ramo:

```yaml
nav:
  - ICMI222 · Evaluación de yacimientos:
      - icmi222/index.md
      - Lab · Modelo de bloques, dominios y estimación ID2: icmi222/lab-modelo-bloques-id2.md
      - AED univariado en Vulcan: icmi222/aed-univariado.md
```

Y actualiza la tabla de avance en el `index.md` del ramo.

## 3. Verlo antes de publicar

En una terminal, dentro de la carpeta del proyecto:

```bash
python -m mkdocs serve
```

Abre `http://127.0.0.1:8000` en el navegador. La página se recarga sola cada vez que guardas.

## 4. Publicar

```bash
git add .
git commit -m "Agrega tutorial de AED univariado"
git push
```

GitHub Actions construye y publica el sitio en uno o dos minutos.

## Elementos útiles de Markdown

```markdown
!!! question "¿Por qué se hace cada cosa?"
    Cada paso de un tutorial lleva este recuadro: la razón de cada acción o
    parámetro, y qué pasaría si se hiciera distinto.

!!! note "Teoría: título"
    Texto indentado con 4 espacios.

!!! warning "Cuidado"
    Algo que suele salir mal.

??? question "Pregunta de repaso"
    Respuesta escondida hasta hacer clic.

Fórmula en línea: \( \gamma(h) \)

Fórmula centrada:

\[ z^*(B) = \sum \lambda_i z_i \]
```

Para diagramas de flujo se usan bloques `mermaid` (hay un ejemplo en el tutorial del lab).
