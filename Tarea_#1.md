## Tarea #1
### Universidad Autonoma de Nuevo León - FCFM
#### Maestría en Ciencia de Datos - Bases de Datos Relacionales

## Definición de Base de Datos

Una base de datos es una recopilación organizada de información o datos estructurados, que normalmente se almacena de forma electrónica en un sistema informático. Normalmente, una base de datos está controlada por un sistema de gestión de bases de datos (DBMS). En conjunto, los datos y el DBMS, junto con las aplicaciones asociadas a ellos, reciben el nombre de sistema de bases de datos, abreviado normalmente a simplemente base de datos.

Los datos de los tipos más comunes de bases de datos en funcionamiento actualmente se suelen utilizar como estructuras de filas y columnas en una serie de tablas para aumentar la eficacia del procesamiento y la consulta de datos. Así, se puede acceder, gestionar, modificar, actualizar, controlar y organizar fácilmente los datos. La mayoría de las bases de datos utilizan un lenguaje de consulta estructurada (SQL) para escribir y consultar datos [^1].

## Definición de SGBD

Un Sistema de Gestión de Bases de Datos (SGBD) almacena, organiza y gestiona eficazmente los datos. Sin un SGBD, los datos estarían dispersos en varios archivos, lo que dificultaría su localización o actualización. Un SGBD simplifica estas tareas proporcionando un sistema centralizado, que permite a los usuarios añadir, modificar o eliminar datos fácilmente, garantizando al mismo tiempo su exactitud y coherencia[^2].


## Descripción de la base de datos (no estructurada)

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

#### ¿Qué es PostgreSQL? y opción elegida:

PostgreSQL, comúnmente pronunciado "Post-GRES", es una base de datos de código abierto que tiene una sólida reputación por su fiabilidad, flexibilidad y soporte de estándares técnicos abiertos. A diferencia de otros RDMBS (sistemas de gestión de bases de datos relacionales), PostgreSQL (enlace externo a ibm.com) soporta tipos de datos relacionales y no relacionales. Esto la convierte en una de las bases de datos relacionales más compatibles, estables y maduras disponibles actualmente[^3].

Las razones por las que elegí PostgreSQL:

"Su diseño versátil y accesible convierte a PostgreSQL en una solución de "talla única" para muchas empresas que buscan formas rentables y eficientes de mejorar sus sistemas de gestión de bases de datos."

#### Referencias:

[^1]: Oracle. (s.f.). *¿Qué es una base de datos?* Recuperado de: [https://www.oracle.com/mx/database/what-is-database](https://www.oracle.com/mx/database/what-is-database)

[^2]:DataCamp. (2023). What is a DBMS? Recuperado de:, de https://www.datacamp.com/es/blog/what-is-a-dbms

[^3]:IBM. (s. f.). PostgreSQL. Recuperado de:, de https://www.ibm.com/mx-es/topics/postgresql




