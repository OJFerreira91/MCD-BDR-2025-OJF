## Tarea #8
### Universidad Autonoma de Nuevo León - FCFM
#### Maestría en Ciencia de Datos - Bases de Datos Relacionales


```sql

-- a) Vista con JOIN

CREATE VIEW vista_pedidos_con_clientes AS
SELECT p.id_pedido, p.fecha, c.nombre, p.total
FROM A1_pedido p
JOIN A1_cliente c ON p.id_cliente = c.id_cliente;

-- b) Vista con LEFT JOIN

CREATE VIEW vista_productos_vendidos AS
SELECT pr.nombre AS producto, dp.cantidad, dp.subtotal
FROM A1_producto pr
LEFT JOIN A1_detalle_pedido dp ON pr.id_producto = dp.id_producto;

-- c) Vista con RIGHT JOIN  SQL Server recomienda evitar RIGHT JOIN en favor de LEFT JOIN

CREATE VIEW vista_detalle_derecha AS
SELECT dp.id_detalle, p.fecha, dp.cantidad
FROM A1_detalle_pedido dp
RIGHT JOIN A1_pedido p ON dp.id_pedido = p.id_pedido;

-- d) Vista con subconsulta

CREATE VIEW vista_clientes_con_total AS
SELECT nombre, (
    SELECT COUNT(*) 
    FROM A1_pedido p 
    WHERE p.id_cliente = c.id_cliente
) AS total_pedidos
FROM A1_cliente c;

-- 2. Crear un TRIGGER (ejemplo para auditoría de inserciones en pedidos)

CREATE TABLE auditoria_pedidos (
    id_auditoria INT IDENTITY(1,1) PRIMARY KEY,
    id_pedido INT,
    fecha_insercion DATETIME DEFAULT GETDATE()
);
GO

CREATE TRIGGER trg_auditoria_insercion
ON A1_pedido
AFTER INSERT
AS
BEGIN
    INSERT INTO auditoria_pedidos (id_pedido)
    SELECT id_pedido FROM inserted;
END;
GO

```

## 🔍 Vistas creadas

1. **vista_pedidos_con_clientes**: Muestra pedidos junto con nombre de cliente (JOIN)
2. **vista_productos_vendidos**: Lista todos los productos, vendidos o no (LEFT JOIN)
3. **vista_detalle_derecha**: Muestra todos los pedidos aunque no tengan detalle (RIGHT JOIN)
4. **vista_clientes_con_total**: Muestra cada cliente con la cantidad total de pedidos (subconsulta)

## 🛑 Trigger creado

**trg_auditoria_insercion**: Disparador que registra cada inserción en `A1_pedido` en la tabla `auditoria_pedidos`.

## ✅ Beneficios

- Las vistas permiten simplificar consultas frecuentes y reutilizar lógica compleja.
- El trigger ayuda a llevar control automático de auditoría sin modificar el código de inserción.