# Bases de datos Vectoriales

### Enunciado de ejemplo

Se requiere implementar un sistema de búsqueda semántica que permita encontrar documentos similares a una consulta de texto, incluso cuando no coinciden las palabras exactas.

El sistema se usará como base para un chatbot y un motor de recomendaciones.

### Análisis semántico

El enunciado enfatiza:

* Similitud semántica
* Comparación aproximada
* Representación matemática del significado
* Integración con modelos de IA

Aquí el significado no está en el valor exacto, sino en la ​distancia entre representaciones vectoriales​.

### Decisión

Una base de datos vectorial es necesaria porque:

* Almacena embeddings numéricos
* Permite búsquedas por similitud (coseno, euclidiana)
* Está optimizada para alta dimensionalidad
* No puede ser reemplazada eficientemente por SQL o NoSQL clásicos

Ejemplos: Pinecone, FAISS, Weaviate.

