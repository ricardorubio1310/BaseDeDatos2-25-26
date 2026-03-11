# Respuestas y justificación

### Ejercicio 1 – Base de datos relacional (SQL)



* Existen relaciones bien definidas entre entidades
* Se requiere consistencia fuerte en todo momento
* Las transacciones deben cumplir ACID
* El modelo de datos es estable y estructurado
* No hay necesidad de escalar horizontalmente de forma masiva

### Ejercicio 2 – Base de datos Clave–Valor (NoSQL)

* Acceso directo por identificador
* No existen relaciones entre los datos
* Se prioriza velocidad sobre complejidad
* Los datos son temporales y pueden expirar
* No se requieren consultas complejas

### Ejercicio 3 – Base de datos Columnar (NoSQL)

* Volumen muy alto de datos
* Consultas orientadas a resúmenes y estadísticas
* Predominio de lecturas analíticas
* Interés en patrones globales, no en registros individuales
* Escalabilidad horizontal necesaria

### Ejercicio 4 – Base de datos Documental (NoSQL)

* Estructura variable entre entidades
* Cambios frecuentes en el modelo
* Cada entidad es naturalmente autocontenida
* Necesidad de consultas flexibles por campos
* Evita migraciones constantes de esquema

### Ejercicio 5 – Base de datos relacional (SQL)

* Dominio altamente transaccional
* Riesgo crítico ante inconsistencias
* Necesidad de atomicidad y durabilidad
* Modelo relacional claro entre cuentas y movimientos
* No es aceptable consistencia eventual

### Ejercicio 6 – Base de datos de Grafos (NoSQL)

* El valor está en las relaciones entre entidades
* Se analizan conexiones indirectas
* Consultas basadas en recorridos y caminos
* Las relaciones tienen significado propio
* SQL requeriría múltiples joins complejos

### Ejercicio 7 – Base de datos Vectorial (NoSQL)

* Búsqueda basada en similitud semántica
* Comparación aproximada, no exacta
* Uso de representaciones vectoriales
* Integración con modelos de lenguaje o embeddings
* No resoluble eficientemente con SQL tradicional

### Ejercicio 8 – Base de datos relacional (SQL)

* Modelo de datos simple y bien definido
* Volumen controlado
* Relaciones claras y estables
* Consultas estructuradas previsibles
* No se justifica la complejidad de NoSQL

