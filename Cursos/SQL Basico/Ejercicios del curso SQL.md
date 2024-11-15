### SELECCIONAR LOS PEDIDOS CON IMPORTES ENTRE 100 Y 500
```sql
--SELECCIONAR LOS PEDIDOS CON IMPORTES ENTRE 100 Y 500

--1 Visualizar la tabla
SELECT * FROM PEDIDOS

--2 Hacer la consulta
-- BETWEEN
SELECT * 
	FROM PEDIDOS
	WHERE IMPORTE BETWEEN 100 AND 500;

--ALTERNATIVA
SELECT * 
	FROM PEDIDOS
	WHERE IMPORTE >= 100 AND IMPORTE <= 500;
```
**RESULTADO DE LA CONSULTA**
![[Captura desde 2024-09-17 02-17-13.png]]

### SELECCIONAR EL NOMBRE, EL PRIMER APELLIDO Y LA EDAD
De las personas que en el primer apellido tengan la letra **Z**

```sql
--SELECCIONAR LOS PEDIDOS CON IMPORTES ENTRE 100 Y 500

--1 Visualizar la tabla
SELECT * FROM PERSONAS
SELECT APELLIDO1, EDAD FROM PERSONAS WHERE APELLIDO1 LIKE "%Z%"

```

**RESULTADO DE LA CONSULTA**
![[Captura desde 2024-09-17 02-30-29.png]]

### SELECCIONAR EL NOMBRE, EL PRIMER APELLIDO Y LA EDAD Y EL DEPARTAMENTO
De las personas cuyo nombre sea antonio
Ademas el resultado debe estar ordenado por departamento

```sql
--Seleccionamos las columnas de tabla 1 y tabla 2
SELECT NOMBRE, APELLIDO1, EDAD, DEPARTAMENTO 
FROM PERSONAS 
--Y unirla con join de tabla 2
JOIN DEPARTAMENTOS 
WHERE NOMBRE = "ANTONIO" AND PERSONAS.DEP = DEPARTAMENTOS.DEP 
ORDER BY DEPARTAMENTO;
```

**RESULTADO DE LA CONSULTA**
![[Captura desde 2024-09-17 02-46-20 1.png]]
### Selecciona los pedidos de impresoras y los pedidos con un importe mayor de 500 usando UNION 
```sql
SELECT * FROM PRODUCTOS
SELECT * FROM PEDIDOS

SELECT * FROM PEDIDOS
 WHERE PRODUCTO = "IMPRESORA"
UNION ALL
SELECT * FROM PEDIDOS
 WHERE IMPORTE > 500;
```
### Selecciona los pedidos cuyo importe sea mayor que el importe medio de todos los pedidos
 ```sql
 SELECT * FROM PEDIDOS WHERE IMPORTE > (SELECT AVG(IMPORTE) FROM PEDIDOS)
 ```
### Selecciona el numero de personas que tienen menos de 50 años
```sql
SELECT * FROM PERSONAS
SELECT COUNT(*) FROM PERSONAS WHERE EDAD < 50
```
### Selecciona los 2 primeros pedidos que tengan un importe mayor de 80 euros
 ```sql
 SELECT * FROM PEDIDOS WHERE IMPORTE > 80 limit 2
 ```

### Seleccionar aquellos pedidos que tengan un importe de 150,500 o 600
```sql
SELECT * FROM PEDIDOS WHERE IMPORTE = 150 OR IMPORTE = 500 OR IMPORTE = 600 ORDER BY IMPORTE
SELECT * FROM PEDIDOS WHERE IMPORTE IN (150,500,600) ORDER BY IMPORTE
```
 
### Crear una nueva tabla denominada TABLA2
```sql
--Incluir 2 columnas:
-- Primera columna nombre 'ID' y de tipo numero entero
-- Segunda columna con nombre 'DATOS' de tipo texto

CREATE TABLE TABLA2(
	ID INTEGER PRIMARY KEY AUTOINCREMENT, 
	DATOS TEXT
);

SELECT * FROM TABLA2

```

###  Insertar datos en TABLA2
```sql
SELECT * FROM TABLA2

-- INSERTAR 2 nuevas filas en nuestra tabla TABLA2
DROP TABLE TABLA2
INSERT INTO TABLA2 VALUES(null, "Texto promocional 2")
```

### Borrar todos los registros de nuestra TABLA2
```sql
--pero sin borrar la TABLA2
--TRUNCATE es la instruccion comun pero en SQLITE seria con DELETE

DELETE FROM TABLA2 
SELECT * FROM TABLA2

```

### Borrar definitivamente la TABLA2
```sql
DROP TABLE TABLA2
SELECT * FROM TABLA2
```

![[Tipos de Datos SQL]]

```sql
CREATE TABLE SALARIOS(
	ID INTEGER PRIMARY KEY AUTOINCREMENT,
	NOMBRE TEXT,
	EDAD INTEGER NOT NULL,
	DIRECCION VARCHAR(50),
	SALARIOS REAL
);
```

### SELECT * FROM SALARIOS

```SQL
--Ejercicio
--Insertar en la tabla "SALARIOS" con los siguientes campos:	
--Creamos con los siguientes datos
-- NOMBRE    EDAD   DIRECCION    SALARIO
-- Antonio   30     "Calle 1"    2000.00
-- Juan		 40     "Calle 2"    3000.00

INSERT INTO SALARIOS VALUES(null,"Antonio",30,"Calle 1",2000.00)
INSERT INTO SALARIOS VALUES(null,"Juan",40,"Calle 2",3000.00)

```

### COPIAR DATOS DE TABLA A TABLA
```sql
--Ejercicio
--Modificar el tipo de dato de una columna
--1. Renombar la tabla SALARIOS a SALARIOS2
--2. Crear una nueva tabla SALARIOS con los campos
-- ID: entero, clave primaria, autoincremental
-- NOMBRE:  text no nulo
-- EDAD: entero
-- DIRECCION:  texto variable de 50 posiciones
-- SALARIO: Entero
--3. Copiar los datos de la tabla SALARIOS2 a SALARIOS

--1. Renombar la tabla SALARIOS a SALARIOS2
ALTER TABLE SALARIOS RENAME TO SALARIOS2;

--2. Crear una nueva tabla SALARIOS con los campos
-- ID: entero, clave primaria, autoincremental
-- NOMBRE:  text no nulo
-- EDAD: entero
-- DIRECCION:  texto variable de 50 posiciones
-- SALARIO: Entero
CREATE TABLE SALARIOS(
	ID INTEGER PRIMARY KEY AUTOINCREMENT,
	NOMBRE TEXT NOT NULL,
	EDAD INTEGER,
	DIRECCION VARCHAR(50),
	SALARIO INTEGER
);

INSERT INTO SALARIOS
SELECT * FROM SALARIOS2


SELECT * FROM SALARIOS
SELECT * FROM SALARIOS2

--ALTERNATIVA
INSERT INTO SALARIOS(NOMBRE,EDAD,DIRECCION,SALARIO)
SELECT NOMBRE,EDAD,DIRECCION,SALARIO FROM SALARIOS2

```

### SELECCIONAR LAS ULTIMAS FILAS DE UNA TABLA
```sql
SELECT * FROM PERSONAS
ORDER BY PER DESC
LIMIT 2;
```

### SUMAR LA FILA IMPORTE DE PEDIDOS Y AGRUPARLO POR PRODUCTOS
```sql
--Obtener el importe total de los pedidos agrupados por PRODUCTO
--Por cada producto de la tabla pedidos calcular los importes
--Renombar la columna que suma los importes como IMPORTE_TOTAL

SELECT * from PEDIDOS

SELECT PRODUCTO, SUM(IMPORTE) AS IMPORTE_TOTAL 
FROM PEDIDOS
GROUP BY PRODUCTO;


```

### Personas cuyo salario mayor a 4000
```sql
--Ejercicio
--Seleccionar aquellas personas cuyo salario es mayor de 4000
--Insertar una nueva persona en la tabla SALARIOS

SELECT * FROM SALARIOS
INSERT INTO SALARIOS VALUES(3,"Marta",40,"Calle 3",5000.00)
INSERT INTO PERSONAS VALUES(null,"Marta","Santos","Perez","30222863P",62,1,null)

SELECT NOMBRE FROM SALARIOS WHERE SALARIO > 4000

SELECT * FROM PERSONAS
WHERE NOMBRE = (SELECT NOMBRE FROM SALARIOS WHERE SALARIO > 4000)
```

### Obtener el nombre que coincida por edad menor a 30
```sql
SELECT NOMBRE FROM PERSONAS
WHERE EDAD < 30
UNION
SELECT NOMBRE FROM SALARIOS
WHERE SALARIO > 2500 AND SALARIO < 4000
```
### Consulta para obtener el nombre completo nombre, apellidos y ordenado
```sql
--Ejercicio 21
--Crear una consulta que devuelva en una sola columna
--el nombre y los 2 apellidos concatenados y separados por espacios
--Ordenar el resultado por esta nueva columna que se llamara "PERSONA"

SELECT * FROM PERSONAS
SELECT NOMBRE || ' ' || APELLIDO1 || ' ' || APELLIDO2 AS PERSONA
FROM PERSONAS
ORDER BY PERSONA DESC
```

Continuar la clase 94