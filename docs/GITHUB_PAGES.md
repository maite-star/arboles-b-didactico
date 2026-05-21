# Publicar con GitHub Pages

Esta guía asume que el archivo principal del proyecto se llama `index.html` y está ubicado en la raíz del repositorio.

## Configuración recomendada

- **Source:** `Deploy from a branch`
- **Branch:** `main`
- **Folder:** `/ (root)`

## Pasos

1. Subí el proyecto a GitHub.
2. Entrá al repositorio.
3. Abrí `Settings`.
4. En el menú lateral, elegí `Pages`.
5. En `Build and deployment`, seleccioná:
   - `Source`: `Deploy from a branch`
   - `Branch`: `main`
   - `Folder`: `/ (root)`
6. Guardá los cambios.
7. Esperá unos minutos hasta que GitHub publique el sitio.

## URL esperada

La URL va a tener este formato:

`https://TU-USUARIO.github.io/TU-REPO/`

## Qué actualizar después

Cuando el sitio quede publicado:

1. Copiá la URL final.
2. Reemplazá el placeholder en `README.md`.
3. Si querés, agregá un badge o link directo arriba del README.

## Problemas comunes

### Se publica un 404

Verificá que exista `index.html` en la raíz del repositorio.

### No se reflejan cambios

- Esperá unos minutos
- Forzá recarga en el navegador
- Confirmá que los cambios estén en la rama `main`

### Las imágenes no aparecen

Revisá que los archivos de screenshots estén realmente dentro de `assets/screenshots/` y que el nombre coincida exactamente con el usado en el README.

