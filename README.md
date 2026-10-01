# Apuntes de Ingeniería en Minas

Tutoriales paso a paso con teoría de los ramos de Ingeniería en Minas (UNAB), publicados con
[MkDocs Material](https://squidfunk.github.io/mkdocs-material/) en GitHub Pages.

**Sitio:** https://aliaaar.github.io/apuntes-mineria/

## Estructura

```
docs/                  contenido del sitio (Markdown)
  index.md             página de inicio
  glosario.md          conceptos que se repiten entre ramos
  etiquetas.md         índice por etiquetas
  icmi222/             un directorio por ramo
    index.md           avance del ramo
    img/               capturas, una carpeta por tutorial
plantillas/tutorial.md plantilla para tutoriales nuevos
mkdocs.yml             configuración y menú del sitio
.github/workflows/     publicación automática en GitHub Pages
```

## Trabajar en local

```bash
pip install -r requirements.txt
python -m mkdocs serve
```

Después abre http://127.0.0.1:8000.

## Publicar

Cada `git push` a `main` construye y publica el sitio con GitHub Actions.
En el repositorio: **Settings → Pages → Source: GitHub Actions** (se configura una sola vez).
