## Tarea #4
### Universidad Autonoma de Nuevo León - FCFM
#### Maestría en Ciencia de Datos - Bases de Datos Relacionales

## Base de Datos, Tablas SQL Server

El codigo se hizo en  SQL Server de la empresa donde trabajo

## 🗂 Nombre de la base de datos
**biAla**

---

##  Tablas creadas

- A1_cliente
- A1_producto
- A1_pedido
- A1_detalle_pedido

---

##  Relaciones

- `A1_pedido.id_cliente` → FK hacia `A1_cliente.id_cliente`
- `A1_detalle_pedido.id_pedido` → FK hacia `A1_pedido.id_pedido`
- `A1_detalle_pedido.id_producto` → FK hacia `A1_producto.id_producto`

---

## Script de creación e inserción de datos

```sql
-- Usar la base de datos
USE biAla;
GO

-- Tabla CLIENTE
CREATE TABLE A1_cliente (
    id_cliente INT IDENTITY(1,1) PRIMARY KEY,
    nombre NVARCHAR(100),
    correo NVARCHAR(100),
    telefono NVARCHAR(15)
);
GO

-- Tabla PRODUCTO
CREATE TABLE A1_producto (
    id_producto INT IDENTITY(1,1) PRIMARY KEY,
    nombre NVARCHAR(100),
    precio DECIMAL(10,2),
    stock INT
);
GO

-- Tabla PEDIDO
CREATE TABLE A1_pedido (
    id_pedido INT IDENTITY(1,1) PRIMARY KEY,
    fecha DATE,
    id_cliente INT FOREIGN KEY REFERENCES A1_cliente(id_cliente),
    total DECIMAL(10,2)
);
GO

-- Tabla DETALLE_PEDIDO
CREATE TABLE A1_detalle_pedido (
    id_detalle INT IDENTITY(1,1) PRIMARY KEY,
    id_pedido INT FOREIGN KEY REFERENCES A1_pedido(id_pedido),
    id_producto INT FOREIGN KEY REFERENCES A1_producto(id_producto),
    cantidad INT,
    subtotal DECIMAL(10,2)
);
GO

-- Insertar CLIENTES
INSERT INTO A1_cliente (nombre, correo, telefono) VALUES
('Juan Pérez', 'juan@example.com', '5551234567'),
('María López', 'maria@example.com', '5559876543'),
('Carlos Ruiz', 'carlos@example.com', '5551112233'),
('Carlos Ochoa','carlosochoa@example.com','5551112234'),
('Nelson Levy', 'nelson@example.com', '5559876560');
GO

-- Insertar PRODUCTOS
INSERT INTO A1_producto (nombre, precio, stock) VALUES
('Laptop', 15000.00, 10),
('Mouse', 250.00, 100),
('Teclado', 500.00, 80),
('Monitor', 3000.00, 20),
('Celular', 8500.00, 15);
GO

-- Insertar PEDIDOS
INSERT INTO A1_pedido (fecha, id_cliente, total) VALUES
('2025-07-01', 1, 15500.00),
('2025-07-02', 2, 8750.00),
('2025-07-03', 1, 750.00),
('2025-07-04', 2, 950.00),
('2025-07-05', 3, 5000.00);
GO

-- Insertar DETALLES
INSERT INTO A1_detalle_pedido (id_pedido, id_producto, cantidad, subtotal) VALUES
(1, 1, 1, 15000.00),
(1, 2, 2, 500.00),
(2, 5, 1, 8500.00),
(2, 2, 1, 250.00),
(3, 3, 1, 500.00),
(3, 2, 1, 250.00);
GO

--- Revisando los valores de las tablas

SELECT TOP 10 * FROM A1_cliente;
SELECT TOP 10 * FROM A1_producto;
SELECT TOP 10 * FROM A1_pedido;
SELECT TOP 10 * FROM A1_detalle_pedido;

```