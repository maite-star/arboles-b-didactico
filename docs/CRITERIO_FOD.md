# Criterio FOD modelado por la herramienta

Este documento deja explícitas las reglas operativas que la herramienta intenta seguir para resultar útil en **Fundamentos de Organización de Datos**.

## 1. Qué se busca modelar

La herramienta no intenta ser un índice genérico de producción. Su objetivo es didáctico:

- visualizar el árbol
- mostrar el efecto de cada operación
- justificar decisiones
- respetar el criterio que aparece en práctica y teoría

## 2. Orden del árbol

Se toma `M` como el **orden del árbol**, es decir:

- máximo `M` hijos por nodo
- máximo `M - 1` claves por nodo
- mínimo `ceil(M / 2) - 1` claves en nodos no raíz

## 3. Regla de overflow

Ante overflow:

- siempre se genera un nuevo nodo
- las claves se distribuyen lo más equitativamente posible
- en órdenes impares se promociona la clave central
- en órdenes pares se promociona la menor de las claves mayores

## 4. Diferencia entre B y B+ en overflow

### En árbol B

La clave promovida sube al padre como parte del proceso normal de división.

### En árbol B+

- si el overflow es en hoja, se promociona una **copia** de la clave separadora
- si el overflow es en nodo interno, se usa el mismo criterio que en árbol B

## 5. Regla de baja en árbol B

Si la clave a eliminar aparece en un nodo interno:

1. se reemplaza por la menor clave del subárbol derecho
2. la eliminación efectiva continúa en hoja
3. si aparece underflow, se lo resuelve según la política elegida

## 6. Regla de baja en árbol B+

La eliminación siempre se realiza en hojas. Las claves internas se interpretan como guías.

Por eso:

- una clave puede verse en un nodo interno y no existir como dato eliminable en ese nivel
- al eliminar una clave en hoja, una copia interna puede permanecer si sigue sirviendo de separador

## 7. Casos trampa en B+

La herramienta intenta marcar explícitamente los casos donde se quiere eliminar una clave que:

- aparece en un nodo interno
- pero no existe en hojas como dato real

Desde el punto de vista didáctico, esto ayuda a evitar uno de los errores más comunes de práctica.

## 8. Regla de underflow

Ante underflow:

1. primero se intenta redistribuir
2. si no es posible, se fusiona
3. la corrección puede propagarse hacia arriba

La redistribución solo se considera válida si el hermano puede ceder sin quedar él mismo en underflow.

## 9. Políticas soportadas

La herramienta modela las cuatro políticas trabajadas en la práctica:

- `izq`
- `der`
- `izq-der`
- `der-izq`

Además contempla el caso especial de hojas en extremos, donde solo existe un hermano adyacente posible.

## 10. Lecturas y escrituras

Se intenta que cada operación deje visible:

- qué nodos se leen
- qué nodos se escriben
- en qué orden ocurre cada acceso

Esto es importante porque en FOD no solo interesa el árbol final, sino también el costo de la operación.

## 11. Numeración y reutilización de nodos

La práctica pide mantener numeración coherente con el crecimiento del archivo y reutilizar nodos libres con política **LIFO**. La herramienta sigue ese criterio para que el seguimiento de ejercicios sea más fiel.

## 12. Alcance de esta alineación

La herramienta está alineada con:

- las diapositivas de árboles B
- las diapositivas de árboles B+
- la práctica 4
- la bibliografía base de Bertone-Thomas

Si la cátedra ajusta una convención puntual, conviene reflejarlo primero en este documento y luego revisar la interfaz o los mensajes pedagógicos.
