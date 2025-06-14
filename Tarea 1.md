# Tarea 1 - Base de Datos

## 1. Repositorio de GitHub
Repositorio creado: [https://github.com/usuario/bd-pedidos-tienda](https://github.com/usuario/bd-pedidos-tienda)  
*(Reemplaza con tu enlace real)*

---

## 2. Compartición del Repositorio
El enlace fue compartido en la plataforma correspondiente (Teams o Drive).

---

## 3. Descripción de la base de datos (no estructurada)

Mi base de datos representa un sistema de gestión de pedidos de una tienda en línea. Este sistema almacena información sobre los clientes, los productos que ofrece la tienda, los pedidos realizados y el detalle de los productos en cada pedido. A continuación, se describen las entidades involucradas:

- **Cliente**: Información personal de cada usuario que realiza compras.
  - Atributos:
    - `id_cliente` (INT)
    - `nombre` (VARCHAR)
    - `correo` (VARCHAR)
    - `teléfono` (VARCHAR)

- **Producto**: Información de los artículos disponibles para la venta.
  - Atributos:
    - `id_producto` (INT)
    - `nombre` (VARCHAR)
    - `precio` (DECIMAL)
    - `stock` (INT)

- **Pedido**: Registro de cada compra realizada por un cliente.
  - Atributos:
    - `id_pedido` (INT)
    - `fecha` (DATE)
    - `id_cliente` (INT)
    - `total` (DECIMAL)

- **DetallePedido**: Relación entre productos y pedidos (pedido puede tener varios productos y un producto puede estar en varios pedidos).
  - Atributos:
    - `id_detalle` (INT)
    - `id_pedido` (INT)
    - `id_producto` (INT)
    - `cantidad` (INT)
    - `subtotal` (DECIMAL)

### Relaciones:
- Un **cliente** puede realizar varios **pedidos**. (1:N)
- Un **pedido** puede incluir varios **productos**, y un **producto** puede pertenecer a varios **pedidos**. (N:N, resuelta con la tabla `DetallePedido`)

---

## 4. SGBD elegido: PostgreSQL

PostgreSQL es un sistema de gestión de bases de datos relacional de código abierto que destaca por su robustez, confiabilidad y cumplimiento del estándar SQL. Soporta transacciones ACID, integridad referencial, funciones avanzadas como tipos personalizados y extensiones como PostGIS para datos espaciales. Es una opción ideal para aplicaciones empresariales y científicas.

**Fuente**:  
> PostgreSQL Global Development Group. (2024). *PostgreSQL Documentation*. Recuperado de: https://www.postgresql.org/docs/

---

## 5. Archivo entregado
Este archivo ha sido entregado en formato `.md` como especifica la tarea.
