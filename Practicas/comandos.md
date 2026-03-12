# Cheat Sheet MongoDB - Sintaxis y Comandos Clave

## 1. Operadores de Comparación (Filtros)
Los operadores se utilizan dentro de las consultas de búsqueda para establecer condiciones lógicas. Se derivan de sus siglas en inglés.

* `$gt` (Greater Than): Mayor que `>`. Ejemplo: `{ precio: { $gt: 50 } }`
* `$gte` (Greater Than or Equal): Mayor o igual que `>=`. Ejemplo: `{ precio: { $gte: 50 } }`
* `$lt` (Less Than): Menor que `<`. Ejemplo: `{ precio: { $lt: 50 } }`
* `$lte` (Less Than or Equal): Menor o igual que `<=`. Ejemplo: `{ precio: { $lte: 50 } }`
* `$ne` (Not Equal): Distinto de `!=`. Ejemplo: `{ categoria: { $ne: "ropa" } }`

## 2. Operaciones CRUD Básicas y Avanzadas

### Consultas (Find)
* Búsqueda exacta: `db.coleccion.find({ estado: "activo" })`
* Búsqueda en campos anidados: `db.coleccion.find({ "cliente.ciudad": "Madrid" })` (Requiere comillas).
* Proyección (Mostrar/Ocultar campos): `db.coleccion.find({}, { nombre: 1, precio: 1, _id: 0 })` (1 muestra, 0 oculta).

### Actualizaciones (Update)
* `$set`: Crea o modifica un campo específico sin borrar el resto del documento.
* `$unset`: Elimina un campo del documento. `{$unset: {telefono: ""}}`
* `$inc`: Incrementa o decrementa un valor numérico. `{$inc: {stock: -5}}`
* `$push`: Añade un elemento al final de un arreglo. `{$push: {etiquetas: "nuevo"}}`
* `$pull`: Elimina un elemento específico de un arreglo. `{$pull: {etiquetas: "obsoleto"}}`
* `upsert: true`: Parámetro que se añade al final. Si no encuentra el documento a actualizar, lo crea.

## 3. Índices y Análisis de Rendimiento

* Crear Índice Simple: `db.coleccion.createIndex({ categoria: 1 })` (1 ascendente, -1 descendente).
* Crear Índice Compuesto: `db.coleccion.createIndex({ categoria: 1, precio: -1 })` (Ideal para filtrar por categoría y ordenar por precio).
* Crear Índice Único: `db.coleccion.createIndex({ email: 1 }, { unique: true })` (Evita duplicados).
* Crear Índice Sparse: `db.coleccion.createIndex({ telefono_secundario: 1 }, { sparse: true })` (Ahorra espacio omitiendo documentos que no tienen ese campo).
* Mostrar índices existentes: `db.coleccion.getIndexes()`
* Analizar consulta: `db.coleccion.find({ categoria: "computacion" }).explain("executionStats")`
  * Objetivo: Lograr `stage: "IXSCAN"` (Uso de índice). Evitar `stage: "COLLSCAN"` (Escaneo secuencial completo).

## 4. Aggregation Framework (Procesamiento de Datos)

El pipeline de agregación ejecuta etapas en estricto orden secuencial. 

### Etapas principales (Stages)
1. `$match`: Actúa como un `find()`. Filtra los documentos. **Debe ir siempre al principio del pipeline** para poder aprovechar los índices de la base de datos (IXSCAN).
2. `$unwind`: Si un documento tiene un arreglo, crea un duplicado del documento por cada elemento del arreglo.
3. `$group`: Agrupa documentos en base a un identificador único y permite realizar cálculos matemáticos.
   * Sintaxis obligatoria: Requiere el campo `_id` para agrupar.
   * Acumuladores: `$sum` (sumar), `$avg` (promedio), `$max` (máximo), `$min` (mínimo).
4. `$project`: Redefine la estructura del documento de salida (crea campos nuevos, oculta otros).
5. `$sort`: Ordena los resultados. `{ $sort: { total: -1 } }` (-1 para mayor a menor).
6. `$limit`: Recorta la cantidad de resultados devueltos al número especificado.

### Ejemplo Completo Estructurado
Objetivo: Obtener el stock total por categoría, únicamente de los productos con precio mayor a 100, ordenados de mayor a menor stock.

```javascript
db.productos.aggregate([
  // 1. Filtrar primero (Puede usar índices, reduce el volumen de datos)
  { $match: { precio: { $gt: 100 } } },
  
  // 2. Agrupar la información restante
  { $group: { 
      _id: "$categoria", 
      stockTotal: { $sum: "$stock" } 
    } 
  },
  
  // 3. Ordenar el resultado final
  { $sort: { stockTotal: -1 } }
])