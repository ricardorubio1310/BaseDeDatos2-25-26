# Bases de datos de Grafos

### Enunciado de ejemplo

Se necesita analizar relaciones entre usuarios, transacciones y dispositivos para detectar patrones de fraude.

Es importante identificar caminos indirectos y relaciones de segundo o tercer nivel en tiempo casi real.

### Análisis semántico

El enunciado contiene términos clave:

* Relaciones complejas
* Conexiones indirectas
* Caminos entre entidades
* Análisis relacional profundo

Semánticamente, el foco no está en los datos aislados, sino en cómo se conectan y ​qué patrones emergen de esas conexiones.

### Decisión

Una base de datos de grafos es la mejor opción porque:

* Modela relaciones como "ciudadanos de primera clase"
* Optimiza recorridos y búsquedas de caminos
* Simplifica consultas que en SQL serían costosas
* Representa naturalmente redes y dependencias

### En bases de datos de grafos

Las relaciones:

* Existen como **objetos explícitos**
* Tienen **tipo** (AMIGO, COMPRA, SIGUE)
* Tienen **dirección**
* Pueden tener **propiedades propias**
* Están **indexadas y optimizadas**

Ejemplo conceptual:

La relación “USUARIO —COMPRA→ PRODUCTO”:

* Tiene identidad
* Puede tener fecha, importe, canal
* Puede ser consultada directamente
* Puede formar parte de recorridos complejos

La relación es ​un dato​, no una consecuencia o referen.

### Por qué se dice “ciudadanos de primera clase”

La expresión viene de programación y modelado de sistemas.
Un “ciudadano de primera clase” es algo que:

* Se puede crear explícitamente
* Se puede almacenar
* Se puede consultar directamente
* Tiene propiedades propias
* No depende de otros para existir

En grafos:

* Un nodo puede existir sin relaciones
* Una relación **también puede existir con identidad propia**
* Ambas son partes fundamentales del modelo

Ejemplos: Neo4j, JanusGraph.

![1770305868049](images/5-casos-uso-grafos/1770305868049.png)

