# Teoría resumida: árboles B y B+

Este documento resume los conceptos que aparecen en la herramienta y los organiza con el enfoque de **Fundamentos de Organización de Datos (FOD)**. No busca reemplazar la teoría de clase ni la bibliografía, sino servir como puente entre la práctica y la visualización interactiva.

## 1. Contexto de uso en FOD

En la materia, los árboles B y B+ se estudian como estructuras de acceso para archivos e índices. El objetivo no es solo mantener los datos ordenados, sino también minimizar accesos a disco.

Dos escenarios típicos son:

- Organizar directamente un archivo de datos como árbol B
- Mantener un archivo de datos separado y un archivo índice organizado como árbol B o B+

En ese segundo caso, el índice permite encontrar rápidamente la clave buscada sin recorrer secuencialmente todo el archivo.

## 2. Árbol B de orden M

Según la cátedra, un árbol B de orden `M` cumple estas propiedades:

- Cada nodo puede tener como máximo `M` hijos
- Un nodo interno con `X` hijos contiene `X - 1` claves
- La raíz no tiene hijos o tiene al menos dos
- Todo nodo no raíz tiene como mínimo `ceil(M / 2) - 1` claves
- Todo nodo no raíz tiene como máximo `M - 1` claves
- Todas las hojas están al mismo nivel
- Las claves dentro de cada nodo están ordenadas

### Idea estructural

Los árboles B son multicamino, balanceados, bajos y anchos. Eso reduce la altura del árbol y, por lo tanto, la cantidad de lecturas necesarias durante búsqueda, alta y baja.

## 3. Árbol B+

El árbol B+ conserva las propiedades generales de balance de la familia B, pero agrega una diferencia central:

- Las claves reales se encuentran en las hojas
- Los nodos internos funcionan como separadores o guías
- Las hojas están enlazadas para permitir recorrido secuencial rápido

### Consecuencia didáctica importante

En B+, una clave puede aparecer en un nodo interno sin estar almacenada allí como dato eliminable. Por eso, en bajas, puede aparecer el caso donde una clave "existe" en una guía pero no en hojas. Ese es el origen de muchas trampas conceptuales.

## 4. Búsqueda

### En árbol B

La búsqueda compara la clave con las del nodo actual y decide por qué hijo bajar. Si la clave está en un nodo interno, la operación puede finalizar allí.

### En árbol B+

La búsqueda es similar, pero debe continuar hasta hoja porque allí están las claves efectivas.

## 5. Altas e inserción

El proceso general es:

1. Buscar la hoja o nodo donde debe insertarse la clave.
2. Insertarla en orden.
3. Si no hay overflow, termina la operación.
4. Si hay overflow, se divide el nodo.
5. La promoción puede propagarse hacia arriba.

## 6. Overflow según FOD

La práctica deja explícitas estas reglas:

- Ante overflow, **siempre** se crea un nuevo nodo
- Las claves se distribuyen lo más equitativamente posible entre el nodo original y el nuevo
- En órdenes impares, se promociona la clave ubicada en la posición del medio
- En órdenes pares, se promociona la menor de las claves mayores

### Diferencia entre B y B+ en overflow

En un árbol B+:

- Si el overflow ocurre en una hoja, se promociona una **copia** de la clave separadora
- Si el overflow ocurre en un nodo interno, el tratamiento pasa a ser análogo al de un árbol B

Esta distinción es clave para entender por qué una clave puede quedar repetida como guía en niveles superiores.

## 7. Bajas y eliminación

## En árbol B

Si la clave a eliminar está en una hoja y el nodo sigue cumpliendo el mínimo, no hay trabajo extra.

Si la clave a eliminar está en un nodo interno, la cátedra indica reemplazarla por la **menor clave del subárbol derecho** y luego continuar la eliminación en hoja.

Si después de borrar el nodo queda por debajo del mínimo, aparece underflow.

## En árbol B+

La eliminación siempre se realiza sobre hojas. Si una copia de la clave eliminada aparece en un nodo interno como separador, esa copia puede permanecer si sigue siendo útil para guiar la búsqueda.

Eso explica por qué no toda clave visible en un nodo interno debe eliminarse físicamente de ese nivel.

## 8. Underflow según FOD

Hay underflow cuando, después de una baja, un nodo queda con menos de `ceil(M / 2) - 1` claves.

La regla práctica es:

1. Intentar **redistribución** con un hermano adyacente
2. Si no es posible, realizar **fusión**
3. Si la corrección afecta al padre, el proceso puede propagarse

### Aclaración importante de la práctica

Ante underflow, lo primero que se intenta **siempre** es redistribuir, siempre que el hermano pueda ceder sin quedar él mismo en underflow.

## 9. Políticas de resolución de underflow

La práctica 4 trabaja con cuatro políticas:

- `izquierda`: se intenta redistribuir con el hermano izquierdo; si no se puede, se fusiona con el izquierdo
- `derecha`: se intenta redistribuir con el hermano derecho; si no se puede, se fusiona con el derecho
- `izq-der`: se intenta con el izquierdo; si no se puede, con el derecho; si tampoco se puede, se fusiona con el izquierdo
- `der-izq`: se intenta con el derecho; si no se puede, con el izquierdo; si tampoco se puede, se fusiona con el derecho

### Caso especial

Si el nodo en underflow es una hoja de un extremo, debe intentarse con el único hermano adyacente que exista, independientemente del nombre de la política.

## 10. Redistribución y fusión

### Redistribución

Consiste en mover claves entre hermanos y actualizar el separador del padre para repartir mejor la carga sin eliminar nodos.

### Fusión

Consiste en unir el nodo en underflow con un hermano adyacente, absorbiendo también el separador correspondiente del padre cuando la estructura lo requiere.

La fusión puede liberar nodos y provocar un nuevo underflow en el nivel superior.

## 11. Lecturas y escrituras de nodos

En FOD no alcanza con dar el árbol final. También se espera justificar:

- Qué nodos se leen
- Qué nodos se escriben
- En qué orden ocurre cada acceso

La práctica además pide:

- Mantener numeración coherente con el crecimiento del archivo
- Reutilizar nodos libres con política **LIFO**
- Justificar cada decisión con el vocabulario de la materia

## 12. Diferencias clave entre B y B+

| Tema | Árbol B | Árbol B+ |
| --- | --- | --- |
| Dónde están las claves efectivas | Internos y hojas | Hojas |
| Rol de nodos internos | Almacenan y separan | Separan y guían |
| Búsqueda exitosa | Puede terminar antes de hoja | Debe llegar a hoja |
| Recorrido secuencial | Menos natural | Muy eficiente por hojas enlazadas |
| Copias como guía | No es la idea principal | Sí, son esperables |

## 13. Errores frecuentes al estudiar

- Confundir el orden `M` con la cantidad máxima de claves
- Promocionar la clave equivocada en órdenes pares
- Eliminar una clave guía en B+ como si fuera un dato hoja
- Aplicar fusión sin intentar redistribución antes
- Resolver el underflow con una política distinta a la pedida
- No actualizar separadores del padre después de redistribuir
- Contar mal lecturas y escrituras

## 14. Cómo usar esta teoría junto con la herramienta

La herramienta resulta más útil si la usás así:

1. Cargá un preset de la práctica.
2. Anticipá en papel qué creés que va a pasar.
3. Ejecutá la operación.
4. Compará el resultado con tu predicción.
5. Revisá las L/E y la justificación paso a paso.

## 15. Fuentes de referencia

- Diapositivas de FOD sobre árboles B
- Diapositivas de FOD sobre árboles B+
- Práctica 4 de árboles B y B+
- Bertone, R. y Thomas, P. _Introducción a las Bases de Datos_
