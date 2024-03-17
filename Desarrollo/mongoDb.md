# Guía Básica de Comandos MongoDB

## USE
El comando `use` se utiliza para seleccionar una base de datos en la que trabajar.

Ejemplo:
```javascript
use nombre_de_la_base_de_datos;
```

## INSERT
El comando `insert` se utiliza para insertar documentos en una colección.

Ejemplo:
```javascript
db.nombre_de_la_coleccion.insert({ campo1: valor1, campo2: valor2 });
```

## FIND
El comando `find` se utiliza para recuperar documentos de una colección.

Ejemplo:
```javascript
db.nombre_de_la_coleccion.find();
```

## UPDATE
El comando `update` se utiliza para actualizar documentos en una colección.

Ejemplo:
```javascript
db.nombre_de_la_coleccion.update({ campo: valor }, { $set: { nuevo_campo: nuevo_valor } });
```

## REMOVE
El comando `remove` se utiliza para eliminar documentos de una colección.

Ejemplo:
```javascript
db.nombre_de_la_coleccion.remove({ campo: valor });
```

## AGGREGATE
El comando `aggregate` se utiliza para realizar operaciones de agregación en documentos de una colección.

Ejemplo:
```javascript
db.nombre_de_la_coleccion.aggregate([ { $group: { _id: "$campo", total: { $sum: 1 } } } ]);
```

## SORT
El comando `sort` se utiliza para ordenar los resultados de una consulta.

Ejemplo:
```javascript
db.nombre_de_la_coleccion.find().sort({ campo: 1 });
```

## LIMIT
El comando `limit` se utiliza para limitar el número de resultados devueltos por una consulta.

Ejemplo:
```javascript
db.nombre_de_la_coleccion.find().limit(10);
```

## DISTINCT
El comando `distinct` se utiliza para encontrar valores distintos para un campo específico en una colección.

Ejemplo:
```javascript
db.nombre_de_la_coleccion.distinct("campo");
```