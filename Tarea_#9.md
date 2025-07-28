## Tarea #9
### Universidad Autonoma de Nuevo León - FCFM
#### Maestría en Ciencia de Datos - Bases de Datos Relacionales

```sql

-- 1. Función de distancia de Levenshtein en SQL Server
-- SQL Server no la tiene nativa, pero podemos implementarla con una función escalable:

CREATE FUNCTION dbo.Levenshtein (
    @s1 NVARCHAR(100),
    @s2 NVARCHAR(100)
)
RETURNS INT
AS
BEGIN
    DECLARE @s1Len INT = LEN(@s1),
            @s2Len INT = LEN(@s2),
            @i INT,
            @j INT,
            @cost INT,
            @d TABLE (i INT, j INT, dist INT)

    -- Inicializar filas y columnas
    SET @i = 0
    WHILE @i <= @s1Len
    BEGIN
        INSERT INTO @d (i, j, dist) VALUES (@i, 0, @i)
        SET @i = @i + 1
    END

    SET @j = 1
    WHILE @j <= @s2Len
    BEGIN
        INSERT INTO @d (i, j, dist) VALUES (0, @j, @j)
        SET @j = @j + 1
    END

    SET @i = 1
    WHILE @i <= @s1Len
    BEGIN
        SET @j = 1
        WHILE @j <= @s2Len
        BEGIN
            SET @cost = CASE WHEN SUBSTRING(@s1, @i, 1) = SUBSTRING(@s2, @j, 1) THEN 0 ELSE 1 END
            DECLARE @ins INT, @del INT, @sub INT
            SELECT @ins = dist FROM @d WHERE i = @i - 1 AND j = @j
            SELECT @del = dist FROM @d WHERE i = @i AND j = @j - 1
            SELECT @sub = dist FROM @d WHERE i = @i - 1 AND j = @j - 1

            INSERT INTO @d (i, j, dist)
            VALUES (@i, @j, MIN(MIN(@ins + 1, @del + 1), @sub + @cost))

            SET @j = @j + 1
        END
        SET @i = @i + 1
    END

    DECLARE @distance INT
    SELECT @distance = dist FROM @d WHERE i = @s1Len AND j = @s2Len
    RETURN @distance
END;
GO

-- Ejemplo de uso:

SELECT dbo.Levenshtein('casa', 'caza') AS distancia;

-- 2. Procedimiento de regresión lineal simple
-- Vamos a simular una tabla con datos x y y, y crear un procedimiento que calcule pendiente y ordenada al origen:

CREATE PROCEDURE dbo.RegresionLineal
AS
BEGIN
    DECLARE @n INT,
            @sumX FLOAT, @sumY FLOAT,
            @sumXY FLOAT, @sumX2 FLOAT,
            @b FLOAT, @a FLOAT

    -- Supongamos que existe esta tabla
    -- CREATE TABLE datos_xy (x FLOAT, y FLOAT);

    SELECT 
        @n = COUNT(*),
        @sumX = SUM(x),
        @sumY = SUM(y),
        @sumXY = SUM(x * y),
        @sumX2 = SUM(x * x)
    FROM datos_xy;

    SET @b = (@n * @sumXY - @sumX * @sumY) / (@n * @sumX2 - @sumX * @sumX);
    SET @a = (@sumY - @b * @sumX) / @n;

    PRINT 'Pendiente (b): ' + CAST(@b AS VARCHAR(20));
    PRINT 'Intercepto (a): ' + CAST(@a AS VARCHAR(20));
END;
GO

-- Ejemplo de uso:

EXEC dbo.RegresionLineal;

```

## 🔁 1. Función: Levenshtein

**Nombre:** `dbo.Levenshtein`  
**Uso:** Calcular la distancia de edición entre dos cadenas  
**Beneficio:** Muy útil para comparaciones imprecisas como nombres similares

**Ejemplo:**
```sql
SELECT dbo.Levenshtein('casa', 'caza');
-- Resultado: 1
```


## 📈 2. Procedimiento: Regresión lineal

**Nombre:** dbo.RegresionLineal
**Uso:** Calcular pendiente y ordenada al origen sobre pares de datos x, y
**Beneficio:** Ideal para modelos predictivos simples

**Ejemplo:**
```sql
EXEC dbo.RegresionLineal;
-- Resultado: imprime pendiente b e intercepto a
```

## 🧠 Reflexión

Ambas funciones muestran cómo extender SQL Server para lógica más compleja. Aunque el lenguaje SQL no está diseñado para estadística avanzada, con técnicas como estas se pueden calcular medidas clave directamente desde el servidor.