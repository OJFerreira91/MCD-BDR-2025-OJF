## Tarea #6
### Universidad Autonoma de Nuevo León - FCFM
#### Maestría en Ciencia de Datos - Bases de Datos Relacionales


```sql

-- Consulta 1
-- Objetivo: Obtener el promedio del total de los pedidos:

SELECT AVG(total) AS promedio_total_pedidos
FROM A1_pedido;

-- Consulta 2
-- Objetivo:  Precio mínimo y máximo de los productos:

SELECT 
    MIN(precio) AS precio_minimo,
    MAX(precio) AS precio_maximo
FROM A1_producto;

-- Consulta 3
-- En SQL Server, no hay función directa para cuantiles como en R o Python, pero puedes simularlo con percentiles usando PERCENTILE_CONT.

--Ejemplo: calcular el percentil 0.25 del total de los pedidos:

SELECT 
    PERCENTILE_CONT(0.25) WITHIN GROUP (ORDER BY total) 
    OVER () AS percentil_25
FROM A1_pedido;

--Esto solo funciona en SQL Server 2012+ y devuelve el valor que representa el percentil 25 (Q1), distinto a la mediana (Q2).

-- Consulta 4
-- SQL Server no tiene función MODE(), pero puedes simularla con TOP 1 y GROUP BY.

--Ejemplo: encontrar la cantidad más frecuente en la tabla detalle:

SELECT TOP 1 cantidad, COUNT(*) AS frecuencia
FROM A1_detalle_pedido
GROUP BY cantidad
ORDER BY COUNT(*) DESC;

```

### Reporte de funciones estadísticas

Durante esta tarea se aplicaron funciones de agregación en SQL Server para analizar la base de datos `biAla`. Aquí los principales hallazgos:

### Hallazgos:
- El total promedio de pedidos es útil para estimar ticket promedio por cliente.
- Usar `PERCENTILE_CONT()` fue la mejor forma de obtener un cuantil distinto a la mediana en SQL Server.

### Dificultades:
- SQL Server no tiene función directa para moda ni cuantiles → se requiere usar `GROUP BY`, `TOP`, y `PERCENTILE_CONT()` con `OVER ()`.


