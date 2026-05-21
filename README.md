# Árboles B y B+ Didáctico

![MIT License](https://img.shields.io/badge/license-MIT-green?style=flat-square)
![HTML5](https://img.shields.io/badge/HTML5-Static-orange?style=flat-square)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow?style=flat-square)
![SVG](https://img.shields.io/badge/visualization-SVG-blue?style=flat-square)
![Offline](https://img.shields.io/badge/works-offline-success?style=flat-square)

Herramienta interactiva para aprender, visualizar y practicar operaciones sobre **árboles B y B+** de forma didáctica. Fue pensada para estudiantes de **Fundamentos de Organización de Datos (FOD)** de la **UNLP**, con foco en entender tanto el resultado final como el proceso interno de cada operación y en respetar el criterio de resolución usado en la materia.

El proyecto funciona como un sitio estático: se puede abrir en el navegador sin instalar nada y también sirve como material de estudio offline.

## Autora

**Maite Diaz Cortinez**  
Estudiante de la **Licenciatura en Sistemas**

## Demo online

Disponible en GitHub Pages:

`https://maite-star.github.io/arboles-b-didactico/`

## Screenshots

Capturas recomendadas para agregar en `assets/screenshots/`:

- `overview.png` para la vista general de la herramienta
- `step-by-step.png` para una operación con explicación paso a paso
- `exercises.png` para mostrar los ejercicios precargados

Cuando subas esas imágenes, esta sección se puede volver a cambiar para mostrarlas embebidas en el README.

## Qué es este proyecto

Este repositorio reúne una herramienta educativa para estudiar:

- Inserciones y eliminaciones en árboles B y B+
- Overflow y underflow
- Redistribución y fusión
- Políticas de resolución de underflow
- Diferencias conceptuales entre árboles B y B+
- Casos trampa típicos en borrado sobre B+
- Cálculo y seguimiento de lecturas/escrituras

Está orientado a:

- Estudiantes que preparan práctica o parciales de FOD
- Docentes o ayudantes que quieran mostrar el paso a paso en clase
- Personas que necesiten una referencia visual para entender estas estructuras

## Características principales

- Visualización del árbol mediante SVG
- Soporte para árboles **B** y **B+**
- Operaciones de **alta (+)** y **baja (-)** con explicación paso a paso
- Presets con ejercicios de la **práctica 4**
- Indicadores de **lecturas/escrituras (L/E)**
- Explicación visual de **overflow**, **underflow**, **redistribución** y **fusión**
- Políticas de underflow: **izquierda**, **derecha**, **izq-der** y **der-izq**
- Detección de "trampas" en árboles **B+**, por ejemplo cuando se intenta eliminar una clave que solo actúa como guía
- Documentación de apoyo alineada con teoría, práctica y bibliografía de FOD
- Uso completamente **offline**
- Implementación en un único HTML, simple de compartir y estudiar

## Cómo usar

### Opción rápida

1. Descargá o cloná este repositorio.
2. Abrí `index.html` con cualquier navegador moderno.
3. Explorá los ejercicios precargados o probá tus propias operaciones.

### Clonar con Git

```bash
git clone https://github.com/maite-star/arboles-b-didactico.git
cd arboles-b-didactico
```

Después abrí `index.html` haciendo doble clic o desde el navegador.

## Estructura recomendada

```text
.
|-- index.html
|-- arbol_b_didactico_v2.html
|-- README.md
|-- LICENSE
|-- .gitignore
|-- assets/
|   `-- screenshots/
|       `-- README.md
`-- docs/
    |-- CRITERIO_FOD.md
    |-- EJERCICIOS.md
    |-- GITHUB_PAGES.md
    `-- TEORIA.md
```

### Ubicación del HTML principal

La opción más simple es usar tu archivo actual como:

`index.html`

Esto evita configuraciones extra y permite que GitHub Pages lo publique automaticamente. En este scaffold se conserva tambien `arbol_b_didactico_v2.html` como nombre original, pero la version que conviene publicar es `index.html`.

## Ejercicios incluidos

La herramienta trae ejercicios precargados de la practica 4. Esta tabla refleja los presets detectados en el HTML actual.

| Preset | Orden | Politica | Estructura | Secuencia cargada |
| --- | --- | --- | --- | --- |
| Ej. 7 | 5 | Izquierda | Arbol B | `+320,-390,-400,-533` |
| Ej. 8 | 4 | Derecha | Arbol B | `+5,+9,+80,+15,-92,-77` |
| Ej. 9 | 6 | Der-izq | Arbol B | `+15,+71,+3,+48,+24,+38,-56,-100` |
| Ej. 10 | 5 | Derecha | Arbol B | `+450,-485,-511,-614` |
| Ej. 13 | 6 | Izq-der | Arbol B | `+300,+577,-586,-570,-380,-460` |
| Ej. 14 | 4 | Derecha | Arbol B+ | `+80,-400,-50,-11,-77` |
| Ej. 15 | 4 | Derecha | Arbol B+ | `+120,+110,+52,+70,+15,-45,-52,+22,+19,-66,-22,-19,-23,-89` |
| Ej. 17 | 4 | Izq-der | Arbol B+ | `+4,+44,-94,-104` |
| Ej. 18 | 6 | Derecha | Arbol B+ | `+159,-5,-190` |
| Ej. 19 | 5 | Izq-der | Arbol B | `+165,+260,+800,-110` |
| Ej. 20 | 5 | Izq-der | Arbol B+ | `+250,-300,-40` |

## Documentación incluida

- `docs/TEORIA.md`: resumen teórico con foco en árboles B, B+, overflow, underflow y diferencias conceptuales
- `docs/CRITERIO_FOD.md`: reglas operativas que la herramienta intenta modelar según práctica y teoría
- `docs/EJERCICIOS.md`: plantilla y guía para documentar resoluciones con el lenguaje de la materia
- `docs/FUENTES.md`: referencias académicas usadas para alinear la herramienta con FOD
- `docs/GITHUB_PAGES.md`: pasos para publicar la demo online

## Tecnologías

- HTML5
- CSS3
- JavaScript ES6
- SVG

Sin frameworks, sin backend y sin necesidad de servidor para usar la herramienta.

## Créditos

- Proyecto desarrollado por **Maite Diaz Cortinez**
- Basado en contenidos de la materia **Fundamentos de Organización de Datos (FOD)** de la **Universidad Nacional de La Plata**
- Inspirado en los ejercicios de la **práctica 4**
- Referencia teórica: **Bertone - Thomas, _Introducción a las Bases de Datos_**
- Alineado con reglas de resolución sobre overflow, underflow y políticas de rebalanceo trabajadas en clase

Si usás este material en clase, apuntes o tutorías, se agradece mencionar el repositorio.

## Roadmap

Ideas para futuras versiones:

- Importar y exportar árboles en JSON
- Modo "resolver ejercicio" con validación automática
- Historial de pasos con retroceso manual
- Generador aleatorio de ejercicios
- Vista comparativa B vs B+ lado a lado
- Mejora de accesibilidad visual y atajos de teclado
- Versión separada en archivos `HTML + CSS + JS` para facilitar mantenimiento
- Publicación de guía teórica ampliada con ejemplos resueltos

## Contribuir

Las contribuciones son bienvenidas, especialmente si ayudan a:

- Corregir explicaciones teóricas
- Agregar ejercicios resueltos
- Mejorar la claridad visual de la interfaz
- Detectar errores en presets o casos borde
- Sumar documentación para estudiantes

Si querés colaborar:

1. Hacé un fork del repositorio.
2. Creá una rama con tu mejora.
3. Abrí un Pull Request explicando el cambio.

Para cambios grandes, conviene abrir antes un issue para discutir la idea.

## Licencia

Este proyecto se distribuye bajo la licencia [MIT](LICENSE).
