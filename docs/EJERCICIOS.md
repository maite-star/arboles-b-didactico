# Ejercicios resueltos

Este archivo sirve como base para documentar soluciones de la práctica 4 usando la herramienta. La idea es que cualquier estudiante pueda seguir el razonamiento con el mismo criterio que se trabaja en **FOD**.

## Qué conviene mostrar en cada solución

Para que un ejercicio sea realmente útil al estudiar, conviene incluir:

- Tipo de estructura: árbol B o B+
- Orden del árbol
- Política de underflow
- Árbol inicial
- Secuencia de operaciones
- Justificación de cada decisión
- Lecturas y escrituras en orden
- Árbol final
- Errores conceptuales que conviene evitar

## Criterio de resolución esperado por la materia

Al escribir una solución, intentá mantener este orden:

1. Indicar dónde se busca o dónde se encuentra la clave.
2. Explicar si la operación genera overflow o underflow.
3. Justificar por qué se redistribuye o por qué se fusiona.
4. Aclarar qué política se está aplicando.
5. Anotar las L/E en el orden en que ocurren.
6. Mostrar el árbol resultante.

## Plantilla sugerida

Copiá y pegá este bloque para cada nuevo ejercicio:

```md
## Ejercicio X

**Fuente:** Práctica 4 - FOD UNLP  
**Estructura:** Árbol B / Árbol B+  
**Orden:** Completar  
**Política de underflow:** Completar  
**Objetivo:** Inserción / Eliminación / Mixto

### Enunciado

Completar con el texto resumido del ejercicio.

### Árbol inicial

- Estado inicial:
- Observaciones:

### Secuencia de operaciones

1. ...
2. ...
3. ...

### Resolución paso a paso

#### Paso 1

- Acción:
- Nodo o camino afectado:
- ¿Hay overflow o underflow?:
- Decisión tomada:
- Lecturas/escrituras:
- Resultado parcial:

#### Paso 2

- Acción:
- Nodo o camino afectado:
- ¿Hay overflow o underflow?:
- Decisión tomada:
- Lecturas/escrituras:
- Resultado parcial:

### Resultado final

- Árbol resultante:
- Justificación final:

### Errores frecuentes

- ...
- ...

### Capturas recomendadas

- `assets/screenshots/ejercicio-x-inicial.png`
- `assets/screenshots/ejercicio-x-final.png`
```

## Presets cargados actualmente en la herramienta

| Ejercicio | Estructura | Orden | Política | Foco didáctico |
| --- | --- | --- | --- | --- |
| 7 | B | 5 | Izquierda | Bajas con underflow y criterio fijo hacia la izquierda |
| 8 | B | 4 | Derecha | Inserciones y bajas cortas con política derecha |
| 9 | B | 6 | Der-izq | Secuencia mixta sobre raíz hoja |
| 10 | B | 5 | Derecha | Bajas sucesivas en árbol B |
| 13 | B | 6 | Izq-der | Combinación de altas y bajas con varios rebalanceos |
| 14 | B+ | 4 | Derecha | Caso trampa: clave guía `400` |
| 15 | B+ | 4 | Derecha | Secuencia larga para practicar propagaciones |
| 17 | B+ | 4 | Izq-der | Caso trampa: clave guía `94` |
| 18 | B+ | 6 | Derecha | Seguimiento de L/E con hojas enlazadas |
| 19 | B | 5 | Izq-der | Explicación detallada de decisiones |
| 20 | B+ | 5 | Izq-der | Caso trampa: clave guía `300` |

## Casos especialmente útiles para enseñar

- `Ej. 14`, `Ej. 17` y `Ej. 20` son muy buenos para explicar por qué en B+ una clave puede existir solo como guía.
- `Ej. 7`, `Ej. 8`, `Ej. 10` y `Ej. 13` sirven para practicar la diferencia entre redistribución y fusión.
- `Ej. 18` es especialmente útil para justificar lecturas y escrituras.

## Consejos para armar material de estudio

- Sacá una captura antes de cada operación importante.
- Si una baja genera underflow, anotá primero qué hermanos existen y recién después decidí.
- Cuando trabajes con B+, verificá siempre si la clave está en hoja o solo en un nodo interno.
- Si querés compartir la resolución con otros estudiantes, incluí la secuencia exacta de operaciones.
