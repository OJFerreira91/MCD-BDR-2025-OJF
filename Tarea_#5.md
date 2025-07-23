## Tarea #5
### Universidad Autonoma de Nuevo León - FCFM
#### Maestría en Ciencia de Datos - Bases de Datos Relacionales


## Agregar datos ficticios o de otras fuentes de manera automática

## Utilizando Mockaroo.com

Durante esta tarea utilicé la plataforma [Mockaroo](https://mockaroo.com/) para generar datos ficticios automáticamente. Fue una herramienta muy útil porque me permitió crear registros realistas de clientes, productos y pedidos en segundos, lo cual facilitó las pruebas de consultas SQL.

### Hallazgos:
- Mockaroo permite definir tipos de datos personalizados fácilmente.
- Es posible generar archivos directamente en formato SQL Server listos para ejecutar.
- Es muy practica de usar debido a los diferentes formatos que maneja.
- Tiene buena cantidad de datos que puede generar de diferentes indoles.

### Dificultades:
- Algunas claves foráneas requieren cuidado para no generar valores inválidos.
- Los nombres de columnas deben coincidir exactamente con las tablas en la base de datos.
- Al crear las tablas no existe un control para poder tener columnas que se puedan relacionar entre ellas por que los datos son al asar.
- Solo puedes trabajar con bases de 1000 registros por ser la versión gratuita.

### Recomendaciones:
- Verifica que los datos ficticios no rompan integridad referencial.
- Usar el formato directo de SQL para procesar y cargar la data directamente.
- Generar por separado los datos de tablas hijas para evitar FK inválidas.
- El preview de la pagina ayuda a ver los datos que generara, esto te da una idea si lo bajas con formato SQL que puedes cambiar antes de correr en SQL.
- En general es una buena herramienta para crear datos de manera rápida y aleatoria, pero siempre deberá considerarse las relaciones a otras tablas que se quieran hacer. Lo recomendable es crear llaves primarias fáciles de duplicar en las otras tablas, esto para poder hacer joins de tablas.


