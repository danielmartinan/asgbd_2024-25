# UD4 - Optimización y Monitorización en SGBD

- [1. Introducción a la Optimización y Monitorización en SGBD](#1-introducción-a-la-optimización-y-monitorización-en-sgbd)
  - [1.1. Importancia de la Monitorización del Rendimiento](#11-importancia-de-la-monitorización-del-rendimiento)
  - [1.2. Factores que afectan el rendimiento en bases de datos](#12-factores-que-afectan-el-rendimiento-en-bases-de-datos)
    - [1.2.1. Factores de Hardware](#121-factores-de-hardware)
    - [1.2.2. Factores de configuración del servidor](#122-factores-de-configuración-del-servidor)
    - [1.2.3. Factores de Diseño de la Base de Datos](#123-factores-de-diseño-de-la-base-de-datos)
    - [1.2.4. Factores relacionados con consultas SQL](#124-factores-relacionados-con-consultas-sql)
  - [1.3. Herramientas y enfoques de optimización](#13-herramientas-y-enfoques-de-optimización)
    - [1.3.1. Herramientas de Monitorización](#131-herramientas-de-monitorización)
    - [1.3.2. Estrategias de Optimización](#132-estrategias-de-optimización)
  - [1.4. Resumen](#14-resumen)
- [2. Optimización del rendimiento en bases de datos](#2-optimización-del-rendimiento-en-bases-de-datos)
  - [2.1. Optimización del almacenamiento en memoria y espacio en disco](#21-optimización-del-almacenamiento-en-memoria-y-espacio-en-disco)
    - [2.1.1. Factores que afectan el almacenamiento](#211-factores-que-afectan-el-almacenamiento)
    - [2.1.2. Reducción del espacio ocupado por las tablas](#212-reducción-del-espacio-ocupado-por-las-tablas)
  - [2.2. Índices y su impacto en el rendimiento](#22-índices-y-su-impacto-en-el-rendimiento)
    - [2.2.1. Introducción a los índices](#221-introducción-a-los-índices)
    - [2.2.2. Tipos de índices en MySQL](#222-tipos-de-índices-en-mysql)
    - [2.2.3. Creación y gestión de índices](#223-creación-y-gestión-de-índices)
    - [2.2.4. Evaluación del uso de índices](#224-evaluación-del-uso-de-índices)
  - [2.3. Optimización del diseño de bases de datos](#23-optimización-del-diseño-de-bases-de-datos)
  - [2.4. Optimización de consultas](#24-optimización-de-consultas)
    - [2.4.1. Uso de `EXPLAIN` para analizar consultas](#241-uso-de-explain-para-analizar-consultas)
    - [2.4.2. Reescritura de consultas para la mejora de rendimiento](#242-reescritura-de-consultas-para-la-mejora-de-rendimiento)
    - [2.4.3. Uso de particiones y vistas materializadas](#243-uso-de-particiones-y-vistas-materializadas)
  - [2.5. Optimización del servidor de bases de datos](#25-optimización-del-servidor-de-bases-de-datos)
    - [2.5.1. Parámetros clave de configuración](#251-parámetros-clave-de-configuración)
  - [2.6. Mantenimiento y verificación de integridad](#26-mantenimiento-y-verificación-de-integridad)
    - [2.6.1. Verificación de tablas con `CHECK TABLE`](#261-verificación-de-tablas-con-check-table)
    - [2.6.2. Reparación de tablas con `REPAIR TABLE`](#262-reparación-de-tablas-con-repair-table)
    - [2.6.3. Detección de cambios con `CHECKSUM TABLE`](#263-detección-de-cambios-con-checksum-table)
    - [2.6.4. Resumen y mejores prácticas](#264-resumen-y-mejores-prácticas)
  - [2.7. Otros aspectos de optimización](#27-otros-aspectos-de-optimización)
    - [2.7.1. Sistemas de permisos](#271-sistemas-de-permisos)
    - [2.7.2. Modificadores de MySQL](#272-modificadores-de-mysql)

## 1. Introducción a la Optimización y Monitorización en SGBD

Una vez terminada las tareas de implantación de un Sistema Gestor de Bases de Datos, y este se encuentra en fase de explotación, es necesario llevar a cabo una serie de tareas de monitorización y optimización para garantizar su correcto funcionamiento y rendimiento. La monitorización y optimización de un SGBD es un proceso continuo que permite identificar y corregir problemas de rendimiento, mejorar la eficiencia de las consultas y garantizar la disponibilidad de los datos.

El rendimiento de un **Sistema Gestor de Bases de Datos (SGBD)** es un factor crítico en entornos donde se manejan grandes volúmenes de datos y múltiples usuarios concurrentes. Una base de datos mal optimizada puede generar tiempos de respuesta elevados, consumo excesivo de recursos y problemas de concurrencia, afectando la experiencia del usuario y la eficiencia del sistema.

Este apartado introduce la importancia de la optimización y la monitorización del rendimiento, así como los principales factores que influyen en el desempeño de un SGBD.

### 1.1. Importancia de la Monitorización del Rendimiento

La **monitorización del rendimiento** permite identificar problemas en la base de datos antes de que impacten en la producción. Algunas razones clave para monitorear una base de datos incluyen:

✅ **Prevención de cuellos de botella**: Detectar consultas lentas, bloqueos y alta carga del servidor.  
✅ **Optimización de recursos**: Mejorar el uso de CPU, memoria, disco y red.  
✅ **Gestión de la concurrencia**: Minimizar conflictos entre múltiples transacciones simultáneas.  
✅ **Mantenimiento proactivo**: Automatizar tareas como la reindexación y el archivado de registros históricos.  

Ejemplo de consulta para monitorear consultas lentas en MySQL:

```sql
SHOW GLOBAL STATUS LIKE 'Slow_queries';
```

Esto permite conocer cuántas consultas han tardado más de lo definido en `long_query_time`.

### 1.2. Factores que afectan el rendimiento en bases de datos

El rendimiento de un SGBD depende de varios factores, que pueden agruparse en **hardware, configuración del servidor, diseño de la base de datos y optimización de consultas**.

#### 1.2.1. Factores de Hardware

El rendimiento de una base de datos está directamente relacionado con los **recursos físicos** del servidor. Algunos aspectos clave son:

🔹 **Procesador (CPU)**: Determina la velocidad de ejecución de consultas complejas y transacciones concurrentes.
🔹 **Memoria RAM**: Un mayor tamaño de memoria permite almacenar más datos en caché y reducir accesos al disco.
🔹 **Disco duro (HDD vs SSD)**: Los discos SSD mejoran significativamente el acceso a datos en comparación con los HDD.
🔹 **Red**: En bases de datos distribuidas, la latencia de la red afecta el tiempo de respuesta de consultas.

Ejemplo: Para verificar el uso de memoria en MySQL, podemos consultar:

```sql
SHOW VARIABLES LIKE 'innodb_buffer_pool_size';
```

Esto muestra la cantidad de memoria asignada a la caché de InnoDB.

#### 1.2.2. Factores de configuración del servidor

Los parámetros del servidor de bases de datos pueden ajustarse para mejorar el rendimiento. Algunos de los más importantes en MySQL son:

🔸 **`max_connections`**: Número máximo de conexiones simultáneas permitidas.  
🔸 **`query_cache_size`**: Caché de consultas, útil para acelerar consultas repetitivas.  
🔸 **`innodb_log_file_size`**: Tamaño de los archivos de log de transacciones, afecta la velocidad de escritura.  

Ejemplo de cómo consultar estas configuraciones:

```sql
SHOW VARIABLES LIKE 'max_connections';
```

#### 1.2.3. Factores de Diseño de la Base de Datos

Un mal diseño de la base de datos puede generar redundancia de datos, consultas ineficientes y bloqueos. Buenas prácticas incluyen:

✔ **Normalización adecuada** para evitar duplicidad de datos.  
✔ **Uso eficiente de índices** para acelerar las búsquedas.  
✔ **Elección de tipos de datos correctos** para reducir el espacio en disco.  

Ejemplo: Si una tabla tiene consultas lentas, podríamos verificar si tiene índices adecuados con:

```sql
SHOW INDEX FROM nombre_tabla;
```

#### 1.2.4. Factores relacionados con consultas SQL

Las consultas mal diseñadas pueden ser la causa principal de problemas de rendimiento. Factores clave incluyen:

⚠ **Uso excesivo de `SELECT *`**, en lugar de seleccionar solo las columnas necesarias.  
⚠ **Falta de índices en columnas utilizadas en `WHERE`, `JOIN` y `ORDER BY`**.  
⚠ **Consultas que generan tablas temporales innecesarias**.  

Ejemplo: Para analizar una consulta y ver su plan de ejecución, podemos usar:

```sql
EXPLAIN SELECT * FROM pedidos WHERE cliente_id = 10;
```

### 1.3. Herramientas y enfoques de optimización

Existen diferentes herramientas y estrategias para optimizar una base de datos:

#### 1.3.1. Herramientas de Monitorización

🔹 **`SHOW STATUS` y `SHOW VARIABLES`** en MySQL para obtener estadísticas del servidor.  
🔹 **`INFORMATION_SCHEMA`** para analizar estructuras de tablas y consultas.  
🔹 **Logs de consultas lentas (`slow_query_log`)** para identificar consultas ineficientes.  

Ejemplo para activar el registro de consultas lentas:

```sql
SET GLOBAL slow_query_log = 'ON';
SET GLOBAL long_query_time = 1; -- Consultas que tardan más de 1s
```

#### 1.3.2. Estrategias de Optimización

✅ **Optimización del diseño de la base de datos** (normalización, índices, particiones).  
✅ **Mejora de consultas SQL** (`EXPLAIN`, `OPTIMIZER TRACE`).  
✅ **Configuración adecuada del servidor** (ajuste de buffers, conexiones, caché).  
✅ **Automatización del mantenimiento** (reindexación, limpieza de registros antiguos).  

### 1.4. Resumen

1. La **monitorización del rendimiento** permite detectar problemas antes de que impacten la producción.
2. El **rendimiento de un SGBD depende de múltiples factores**, desde hardware hasta optimización de consultas.
3. **Existen herramientas y estrategias** para analizar y mejorar la eficiencia de las bases de datos.

Este primer apartado sienta las bases para los siguientes, donde se abordarán herramientas específicas de monitorización y técnicas avanzadas de optimización.

## 2. Optimización del rendimiento en bases de datos

El rendimiento de una base de datos depende de múltiples factores, desde la arquitectura del hardware hasta la estructura de las consultas SQL. Una optimización adecuada permite mejorar la velocidad de acceso a los datos, reducir la carga del servidor y garantizar una mejor experiencia para los usuarios. En este apartado se abordan diversas estrategias para optimizar el almacenamiento, los índices, las consultas y la configuración del servidor.

### 2.1. Optimización del almacenamiento en memoria y espacio en disco

El almacenamiento eficiente de los datos impacta directamente en el rendimiento del sistema. Optimizar el uso de memoria y disco permite reducir el tiempo de acceso a los datos y mejorar la eficiencia en la ejecución de consultas.

#### 2.1.1. Factores que afectan el almacenamiento

Algunos aspectos clave que influyen en el rendimiento del almacenamiento son:

- **Uso de la memoria RAM**: Un almacenamiento en memoria optimizado reduce la necesidad de acceder al disco, lo que acelera las consultas.  
- **Tamaño y estructura de las tablas**: Un mal diseño de tablas genera redundancia y desperdicio de espacio.  
- **Tipo de motor de almacenamiento**: En MySQL, elegir entre **InnoDB** y **MyISAM** afecta el rendimiento en diferentes escenarios.  
- **Caché de consultas y buffers**: Parámetros como `innodb_buffer_pool_size` permiten mejorar el acceso a datos en memoria.

Para verificar el tamaño actual del buffer de InnoDB, se puede ejecutar:

```sql
SHOW VARIABLES LIKE 'innodb_buffer_pool_size';
```

#### 2.1.2. Reducción del espacio ocupado por las tablas

Un diseño eficiente de tablas permite reducir el consumo de disco sin afectar la integridad de los datos. Algunas estrategias incluyen:

- **Elección de tipos de datos adecuados**: Usar `TINYINT` en lugar de `INT` cuando sea posible.  
- **Evitar el uso innecesario de `TEXT` y `BLOB`**: Estos tipos de datos ocupan más espacio y ralentizan el acceso.  
- **Eliminación de registros obsoletos**: Implementar procesos de limpieza automática.

Para comprobar el tamaño de una tabla en MySQL:

```sql
SELECT table_name, ROUND((data_length + index_length) / 1024 / 1024, 2) AS tamaño_MB
FROM information_schema.tables
WHERE table_schema = 'nombre_base_datos';
```

### 2.2. Índices y su impacto en el rendimiento

Los índices en bases de datos son estructuras que permiten acelerar las búsquedas y optimizar la ejecución de consultas. Sin embargo, su uso inadecuado puede generar problemas de rendimiento debido al coste asociado a su mantenimiento. En este apartado se analiza cómo funcionan los índices, los tipos disponibles en MySQL y cómo evaluarlos para garantizar su correcta utilización.  
  
#### 2.2.1. Introducción a los índices

Un índice es una estructura de datos que permite **acelerar la recuperación de información** en una base de datos. Funciona de manera similar a un índice en un libro, permitiendo localizar registros específicos sin necesidad de recorrer toda la tabla.  

Para comprender mejor lo que son y cómo funcionan, vamos a utilizar un ejemplo con una consulta a una tabla de una base de datos. Imaginemos que tenemos una base de datos `tienda_online` que cuenta con una tabla de pedidos, y queremos obtener todos los pedidos de un cliente en concreto:

```sql
SELECT * FROM pedidos WHERE cliente_id = 50;
```

Para hacer la consulta, MySQL debe ir leyendo uno a uno todos los registros de la tabla `pedidos` e ir seleccionando los que coincidan con el id de cliente solicitado. Teniendo encuentra que puede haber millones de registros en la tabla, este trabajo resultaría muy ineficiente. Sin embargo, si tuviéramos ordenados los registros por el código de cliente, todo sería mas fácil: bastaría con localizar el cliente indicado, y capturar todos los datos. Para lograr esto, se emplean los índices, o campos indizados. Estos funcionan como el índice de un libro, permitiendo localizar rápidamente los registros que cumplen con una condición específica.

Los índices se crean sobre campos que suelen ser muy utilizados en consultas. Por ejemplo, para añadir un índice a la columna `cliente_id`de `pedidos`, haríamos

```sql
ALTER TABLE pedidos ADD INDEX idx_cliente_id (cliente_id);
```

De este modo, le decimos al servidor que cree una lista ordenada con todos los identificadores de cliente de la tabla `pedidos`, es decir, se crea una nueva tabla donde se reflejan los id de cliente y su posición dentro de la tabla original, tal y como se haría en un índice de un libro.

**Ventajas del uso de índices**:

✅ **Aceleran la búsqueda de registros**, reduciendo el número de lecturas necesarias en disco.  
✅ **Mejoran el rendimiento de `JOIN` y `ORDER BY`**, al permitir accesos más rápidos a los datos.  
✅ **Optimizan la búsqueda en grandes volúmenes de datos**, especialmente en tablas con millones de registros.  

**Costes y desventajas de los índices:**  

⚠ **Ocupan espacio adicional en disco y memoria**, ya que requieren almacenamiento aparte.  
⚠ **Reducen el rendimiento en operaciones de escritura** (`INSERT`, `UPDATE`, `DELETE`), ya que cada cambio en los datos requiere actualizar los índices.  
⚠ **Un índice mal diseñado puede no ser utilizado por el motor de la base de datos**, generando sobrecarga sin beneficios reales.  

#### 2.2.2. Tipos de índices en MySQL

Los índices en MySQL pueden clasificarse según su **funcionalidad** (cómo afectan la integridad y el acceso a los datos) y su **estructura** (cómo están organizados dentro del motor de almacenamiento). Cada tipo de índice tiene características específicas que lo hacen más adecuado para ciertos tipos de consultas y operaciones.  

Los índices se pueden clasificar en dos grandes grupos:  

1. **Índices según su funcionalidad**  
   - **`PRIMARY KEY`**: Garantiza unicidad y orden en la tabla.  
   - **`UNIQUE`**: Asegura que no haya valores duplicados en una columna.  
   - **`MULTIPLE KEY`**: Permite múltiples índices en una misma tabla.  
   - **`FULLTEXT`**: Optimiza búsquedas de texto en grandes volúmenes de datos.  
   - **`SPATIAL`**: Se usa para almacenar y consultar datos geoespaciales (`GEOMETRY`).  

2. **Índices según su estructura y aplicación**  
   - **Índices parciales**: Indexan solo parte de los valores de una columna.  
   - **Índices multicolumna (compuestos)**: Contienen más de una columna y su orden es clave.  
   - **Índices secundarios**: No son claves primarias, pero mejoran la velocidad de búsqueda.  
   - **Índices agrupados (`Clustered`)**: Ordenan físicamente los datos en disco según el índice.  

Cada tipo de índice tiene ventajas y desventajas dependiendo del tipo de consultas y del motor de almacenamiento utilizado. En las siguientes secciones se detallan sus características y cuándo utilizarlos.

##### Índices según su funcionalidad

###### Índices primarios y únicos

- Un **índice primario** (`PRIMARY KEY`) se crea sobre los campos que forman parte de la clave primaria de una tabla. En este caso, es mejor que sean numéricos y en caso de no saber cual elegir como clave, conviene crear un identificador autonumérico.  
- Un **índice único** (`UNIQUE`) se crea sobre campos cuyo valor no se repite en la tabla.  

**Ejemplo de índice primario y único:**  

```sql
CREATE TABLE clientes (
    id INT AUTO_INCREMENT PRIMARY KEY,  
    email VARCHAR(100) UNIQUE
);
```  

Por tanto, no es necesario crear explicitamente un índice sobre campos que ya son `PRIMARY KEY` o `UNIQUE`. Lo mismo ocurre si definimos como UNIQUE un conjunto de campos:

```sql
CREATE TABLE pedidos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    codigo_pedido VARCHAR(20),
    codigo_cliente INT,
    UNIQUE (codigo_pedido, codigo_cliente)
);
```

Mysql, de manera automática, creará un índice sobre `codigo_pedido` y `codigo_cliente`.

***Nota***: En MySQL, el índice primario es un índice único, pero no al revés. Es decir, un índice único puede tener valores nulos, mientras que el índice primario no.
***Nota 2***: La restricción UNIQUE no considera los valores nulos como repetidos, por lo que se permite tener varios registros con valores nulos en un campo único.* Si se desea que un campo no admita valores nulos y sea único, se puede combinar con la restricción NOT NULL.

```sql
CREATE TABLE ejemplo (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    apellido VARCHAR(255) NOT NULL,
    UNIQUE (nombre, apellido)
);
```

###### Índices múltiples (`multiple key`)

Los **índices múltiples** en MySQL permiten definir **varios índices independientes en diferentes columnas de una misma tabla**. Esto permite que MySQL elija el índice más adecuado según la consulta ejecutada.  

A diferencia de los **índices multicolumna (compuestos)**, donde un solo índice abarca varias columnas en un orden específico, los **índices múltiples** son **índices separados** que pueden ser utilizados de manera independiente.  

**Características de los índices múltiples**:

✅ **Permiten definir más de un índice en una tabla**, lo que puede ser útil para diferentes tipos de consultas.  
✅ **Cada índice actúa de manera independiente**, por lo que una consulta puede beneficiarse de uno u otro índice según su condición de búsqueda.  
✅ **Útiles cuando las consultas no siempre incluyen las mismas combinaciones de columnas.**  
⚠ **No combinan columnas dentro del mismo índice**, por lo que no optimizan consultas que buscan varias columnas a la vez.  
⚠ **En una consulta con condiciones en varias columnas, MySQL solo usará un índice, no ambos a la vez (salvo en ciertos casos con "index merge").**  

**Ejemplo de índice múltiple**:

La siguiente tabla almacena información de clientes y tiene dos índices separados en `apellido` y `nombre`:  

```sql
CREATE TABLE clientes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50),
    apellido VARCHAR(50),
    ciudad VARCHAR(50),
    INDEX idx_apellido (apellido),
    INDEX idx_nombre (nombre)
);
```

Aquí, `idx_apellido` e `idx_nombre` son **índices múltiples**, lo que significa que MySQL puede elegir uno u otro según la consulta.  

✔ **Ejemplo de consulta que usará el índice en `apellido`**

```sql
SELECT * FROM clientes WHERE apellido = 'García';
```

✔ **Ejemplo de consulta que usará el índice en `nombre`**

```sql
SELECT * FROM clientes WHERE nombre = 'Ana';
```

❌ **Consulta que MySQL no optimizará con ambos índices** (usará solo uno):

```sql
SELECT * FROM clientes WHERE apellido = 'García' AND nombre = 'Ana';
```

En este caso, MySQL generalmente elegirá solo **uno de los índices**, a menos que use la estrategia de [**index merge**](#25-optimización-con-index-merge), que desarrollaremos en apartados posteriores.

###### Índices de texto completo (`FULLTEXT`)

Utilizados para búsquedas en grandes volúmenes de texto, permiten realizar búsquedas más avanzadas que `LIKE`.  
  
```sql
CREATE FULLTEXT INDEX idx_descripcion ON productos (descripcion);
```  

```sql
SELECT * FROM productos WHERE MATCH(descripcion) AGAINST ('teclado mecánico');
```  

###### Índices espaciales (`SPATIAL`)

Permiten almacenar y consultar datos geoespaciales, como coordenadas y áreas.  

```sql
CREATE TABLE ubicaciones (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100),
    coordenadas POINT,
    SPATIAL INDEX idx_coordenadas (coordenadas)
);
```  

```sql
SELECT * FROM ubicaciones WHERE ST_DISTANCE(coordenadas, POINT(40.416775, -3.703790)) < 1000;
```

###### Índices en columnas JSON

MySQL permite crear índices en datos almacenados en formato JSON, optimizando consultas en estructuras complejas.  

```sql
ALTER TABLE pedidos ADD INDEX idx_json ((datos->'$.cliente_id'));
```  

##### Índices según su aplicación y estructura

###### Índices parciales

Un **índice parcial** es un índice que **incluye solo una parte de los valores de una columna** en lugar de indexar todas las filas de la tabla.  

**Características**:

✅ Reduce el espacio en disco al indexar solo un subconjunto de datos.  
✅ Mejora el rendimiento en consultas específicas donde solo se necesitan ciertas filas.  

:exclamation: MySQL no soporta de manera nativa los índices parciales, pero se pueden simular mediante **columnas generadas** y **índices filtrados**.

**Columnas generadas**: Permiten crear una columna calculada que almacena un valor derivado de otras columnas.  

```sql
ALTER TABLE pedidos ADD COLUMN es_urgente TINYINT(1) AS (estado = 'URGENTE') STORED;
```

Con la sentencia anterior, se crea una nueva columna `es_urgente` que vale `1` si el estado del pedido es `'URGENTE'` y `0` en caso contrario. La palabra clave `STORED` indica que el valor se almacena físicamente en la tabla, frente a `VIRTUAL` que solo lo calcula en tiempo de ejecución. Más información sobre [columnas generadas en MySQL](https://dev.mysql.com/doc/refman/8.0/en/create-table-generated-columns.html).

**Índices filtrados**: Permiten indexar solo un subconjunto de filas que cumplan una condición específica.  

```sql
CREATE INDEX idx_pedidos_urgentes ON pedidos (es_urgente) WHERE es_urgente = 1;
```

A la sentencia `CREATE INDEX` se le añade una cláusula `WHERE` que filtra las filas a indexar. En este caso, solo se indexan los pedidos urgentes (`es_urgente = 1`).

**Ejemplo completo de simulación de un índice parcial en MySQL**:
 
```sql
CREATE TABLE alumnos(
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100),
    edad INT,
    es_mayor_de_edad TINYINT(1) AS (edad >= 18) STORED
)

-- Crear índice filtrado en la columna generada
CREATE INDEX idx_mayores_edad ON alumnos (es_mayor_de_edad) WHERE es_mayor_de_edad = 1;
```  

🔹 **Explicación**:

- Se crea una tabla `alumnos` con una columna generada `es_mayor_de_edad` que indica si el alumno es mayor de edad.
- Se crea un índice filtrado `idx_mayores_edad` que indexa solo los alumnos mayores de edad.
- Este índice mejora el rendimiento en consultas que buscan solo alumnos mayores de edad.

###### Índices compuestos

Un **índice compuesto** indexa **varias columnas en conjunto**, permitiendo optimizar consultas que filtran por más de un campo.  

**Características**:

✅ Optimiza búsquedas que incluyen múltiples condiciones (`WHERE col1 = X AND col2 = Y`).  
✅ Respeta el **orden de las columnas**, por lo que el primer campo del índice es crucial.  
✅ Se puede usar incluso si la consulta no incluye todas las columnas del índice, pero siempre comenzando desde la primera columna.  

**Ejemplo de creación de un índice multicolumna**:

```sql
CREATE INDEX idx_cliente_fecha ON pedidos (id_cliente, fecha_pedido);
```  

**Reglas importantes**:

- **Consulta que usa el índice correctamente:**

  ```sql
  SELECT * FROM pedidos WHERE id_cliente = 5 AND fecha_pedido = '2024-01-01';
  ```

  Se usa el índice porque respeta el orden de las columnas.  

- **Consulta parcialmente optimizada:**

  ```sql
  SELECT * FROM pedidos WHERE id_cliente = 5;
  ```

  Funciona porque `id_cliente` es la primera columna del índice.  

- **Consulta que no usa el índice:**

  ```sql
  SELECT * FROM pedidos WHERE fecha_pedido = '2024-01-01';
  ```

  No usa el índice porque **`fecha_pedido` no es la primera columna** del índice compuesto.  

#### 2.2.3. Creación y gestión de índices

La gestión de índices en MySQL se realiza mediante los comandos **`CREATE INDEX`**, **`SHOW INDEX`** y **`DROP INDEX`**. En esta sección se explicará la sintaxis de cada uno, junto con ejemplos prácticos y configuraciones avanzadas.  
  
##### `CREATE INDEX`: creación de índices

El comando **`CREATE INDEX`** permite definir un nuevo índice en una tabla para mejorar el rendimiento de las consultas. 

###### Sintaxis completa

```sql
CREATE [UNIQUE | FULLTEXT | SPATIAL] INDEX index_name
    [index_type]
    ON tbl_name (key_part,...)
    [index_option]
    [algorithm_option | lock_option] ...

key_part: {col_name [(length)] | (expr)} [ASC | DESC]

index_option: {
    KEY_BLOCK_SIZE [=] value
  | index_type
  | WITH PARSER parser_name
  | COMMENT 'string'
  | {VISIBLE | INVISIBLE}
  | ENGINE_ATTRIBUTE [=] 'string'
  | SECONDARY_ENGINE_ATTRIBUTE [=] 'string'
}

index_type:
    USING {BTREE | HASH}

algorithm_option:
    ALGORITHM [=] {DEFAULT | INPLACE | COPY}

lock_option:
    LOCK [=] {DEFAULT | NONE | SHARED | EXCLUSIVE}
```

###### Sintaxis básica
  
```sql
CREATE [UNIQUE | FULLTEXT | SPATIAL] INDEX nombre_indice
ON nombre_tabla (columna1 [(longitud)] [ASC | DESC], columna2 [(longitud)] [ASC | DESC])
[USING {BTREE | HASH}];
```  

###### Explicación de cada parámetro

- **`UNIQUE`** → Crea un índice único que impide valores duplicados. Funcionalmente, equivale a definir una restricción `UNIQUE` sobre una columna de una tabla.
- **`FULLTEXT`** → Crea un índice para búsquedas de texto completo en columnas tipo `TEXT` o `VARCHAR`, mejorando el comportamiento frente a consultas con `LIKE`. Solo son compatibles con los motores de almacenamiento `MyISAM` e `InnoDB` (a partir de MySQL 5.6)
- **`SPATIAL`** → Índice especial para columnas de tipo `GEOMETRY`.  
- **`nombre_indice`** → Nombre del índice.  
- **`nombre_tabla`** → Tabla donde se creará el índice.  
- **`columna1, columna2`** → Columnas que formarán parte del índice.  
- **`longitud`** → (Opcional) Longitud del índice en columnas tipo `VARCHAR` o `TEXT`. Esta longitud permite indexar solo una parte de la columna.
- **`ASC | DESC`** → (Opcional) Especifica si los valores del índice se almacenan en orden ascendente o descendente (solo en MySQL 8.0+).  
- **`USING {BTREE | HASH}`** → (Opcional) Define el tipo de estructura a utilizar en el índice. No profundizaremos sobre este concepto de la estructura interna del índice, pare se puede consultar información adicional [aquí](https://dev.mysql.com/doc/refman/8.4/en/index-btree-hash.html).

###### Ejemplos de creación de índices

**Crear un índice simple (secundario) en una columna**:

```sql
CREATE INDEX idx_nombre ON empleados (nombre);
```  
  
**Crear un índice único para evitar duplicados**:

```sql
CREATE UNIQUE INDEX idx_email ON clientes (email);
```  
  
**Crear un índice compuesto en varias columnas**:

```sql
CREATE INDEX idx_pedido ON pedidos (cliente_id, fecha);
```  

**Crear un índice en una tabla MEMORY con HASH**:

```sql
CREATE INDEX idx_sesiones ON sesiones (token) USING HASH;
```  

**Crear un índice parcial sobre una columna de texto**:

```sql
CREATE INDEX idx_descripcion ON productos (descripcion(255));
```

Este índice parcial solo indexa los primeros 255 caracteres de la columna `descripcion`.

**Crear un índice FULLTEXT para búsquedas en texto**:

```sql
CREATE FULLTEXT INDEX idx_descripcion ON productos (descripcion);
```

A partir de este índice, se pueden realizar búsquedas avanzadas en la columna `descripcion`:

```sql
SELECT * FROM productos WHERE MATCH(descripcion) AGAINST ('teclado mecánico');
```

Esta consulta busca productos que contengan la frase `'teclado mecánico'` en la descripción. En MySQL también podemos hacer búsquedas en modo booleano, para refinar los resultados.

```sql
SELECT * FROM productos WHERE MATCH(descripcion) AGAINST ('+teclado -mecánico' IN BOOLEAN MODE);
```

En este caso, se buscan productos que contengan la palabra `'teclado'` pero no `'mecánico'`.

Para más información sobre búsquedas en texto completo, consultar la [documentación oficial](https://dev.mysql.com/doc/refman/8.4/en/fulltext-search.html)

**Crear un índice SPATIAL en una columna GEOMETRY**:

```sql
CREATE SPATIAL INDEX idx_geo ON ubicaciones (coordenadas);
```  

**Crear un índice en una columna JSON**:

```sql
CREATE INDEX idx_cliente_id ON pedidos ((datos->'$.cliente_id'));
```

En este caso, se crea un índice en el campo `cliente_id` de la columna `datos` de tipo JSON.

**Crear un índice ordenado de manera descendente**:

```sql
CREATE INDEX idx_fecha_desc ON ventas (fecha DESC);
```

En este caso, el índice se ordena de manera descendente según la columna `fecha`. Esto significa que las búsquedas por fecha serán más eficientes en orden inverso.

Para más información sobre la sintaxis completa de `CREATE INDEX`, se puede consultar la [documentación oficial de MySQL](https://dev.mysql.com/doc/refman/8.0/en/create-index.html).

##### Creación de `INDEX`en `CREATE TABLE`

En MySQL, es posible crear índices directamente al definir una tabla con la sentencia `CREATE TABLE`. Esto permite definir índices primarios, únicos y secundarios al mismo tiempo que se crea la tabla.

###### Sintaxis

```sql
CREATE TABLE nombre_tabla (
    columna1 tipo_dato PRIMARY KEY,
    columna2 tipo_dato UNIQUE,
    columna3 tipo_dato,
    INDEX idx_columna3 (columna3),
    ...
);
```

En la definición de la tabla, se pueden incluir índices primarios, únicos y secundarios. La sintaxis es similar a la de `CREATE INDEX`, pero se incluye directamente en la definición de la tabla.

###### Ejemplo de creación de tabla con índices

```sql
CREATE TABLE productos (
    id INT PRIMARY KEY,
    nombre VARCHAR(100) UNIQUE,
    descripcion TEXT,
    INDEX idx_descripcion (descripcion(255))
);
```

En este ejemplo, se crea una tabla `productos` con un índice primario en `id`, un índice único en `nombre` y un índice parcial en los primeros 255 caracteres de `descripcion`.

##### `SHOW INDEX`: visualización de índices

El comando **`SHOW INDEX`** permite listar todos los índices existentes en una tabla.  

###### Sintaxis

```sql
SHOW [EXTENDED] {INDEX | INDEXES | KEYS}
    {FROM | IN} tbl_name
    [{FROM | IN} db_name]
    [WHERE expr]
```  

1. **`SHOW`**:
   - Es el comando principal para mostrar información sobre los índices.

2. **`[EXTENDED]`** (opcional):
   - Si se especifica, MySQL muestra información adicional sobre los índices, como estadísticas internas. Sin embargo, esta opción rara vez se usa en la práctica.

3. **`{INDEX | INDEXES | KEYS}`**:
   - Puedes usar cualquiera de estas palabras clave para referirte a los índices. Todas son equivalentes:

4. **`{FROM | IN} tbl_name`**:
   - Especifica la tabla de la cual deseas obtener información sobre los índices. Puedes usar `FROM` o `IN`, ambas son equivalentes.
   - Ejemplo: `FROM mi_tabla` o `IN mi_tabla`.

5. **`[{FROM | IN} db_name]`** (opcional):
   - Si la tabla no está en la base de datos actual, puedes especificar la base de datos usando `FROM` o `IN`.
   - Ejemplo: `FROM mi_base_de_datos.mi_tabla` o `IN mi_base_de_datos.mi_tabla`.

6. **`[WHERE expr]`** (opcional):
   - Permite filtrar los resultados utilizando una condición. La expresión `expr` puede hacer referencia a cualquiera de las columnas devueltas por `SHOW INDEX`.
   - Ejemplo: `WHERE Column_name = 'mi_columna'`.

###### Columnas devueltas por `SHOW INDEX`

Cuando ejecutas `SHOW INDEX`, obtienes un conjunto de columnas con información detallada sobre los índices. Aquí están las columnas más comunes:

| Columna           | Descripción                                                                     |
|-------------------|---------------------------------------------------------------------------------|
| `Table`           | Nombre de la tabla.                                                             |
| `Non_unique`      | Indica si el índice permite valores duplicados: `0` (único) o `1` (no único).   |
| `Key_name`        | Nombre del índice. Para la clave primaria, siempre es `PRIMARY`.                |
| `Seq_in_index`    | Posición de la columna en el índice (comienza en 1).                            |
| `Column_name`     | Nombre de la columna que forma parte del índice.                                |
| `Collation`       | Cómo se ordena la columna en el índice: `A` (ascendente) o `NULL` (no ordenado).|
| `Cardinality`     | Estimación del número de valores únicos en el índice.                           |
| `Sub_part`        | Número de caracteres indexados si solo se indexa una parte de la columna.       |
| `Packed`          | Indica si el índice está empaquetado (rara vez se usa).                         |
| `Null`            | Indica si la columna puede contener valores `NULL`: `YES` o `''`.               |
| `Index_type`      | Tipo de índice (por ejemplo, `BTREE`, `HASH`, `FULLTEXT`, etc.).                |
| `Comment`         | Comentarios adicionales sobre el índice.                                        |
| `Index_comment`   | Comentario especificado al crear el índice.                                     |

###### Ejemplos prácticos

```sql
SHOW INDEX FROM clientes;
```  

Ejemplo de salida esperada:  

```plaintext
+------------+------------+-------------+-------------+-------------+-----------+
| Table      | Non_unique | Key_name    | Seq_in_index| Column_name | Index_type|
+------------+------------+-------------+-------------+-------------+-----------+
| clientes   | 0          | PRIMARY     | 1           | id          | BTREE     |
| clientes   | 0          | idx_email   | 1           | email       | BTREE     |
+------------+------------+-------------+-------------+-------------+-----------+
```  

En este ejemplo, la tabla `clientes` tiene dos índices: uno es la clave primaria (`PRIMARY`) y el otro es un índice único en la columna `email` (`idx_email`).  

```sql
SHOW INDEX FROM empleados WHERE Key_name = 'PRIMARY';
```

Este comando muestra solo los detalles del índice primario de la tabla `empleados`.  

```sql
SHOW INDEX FROM empleados WHERE Column_name = 'nombre';
```

Muestra los índices que contienen la columna `nombre` en la tabla `empleados`.  

###### Notas adicionales

- Los índices `FULLTEXT`, `PRIMARY KEY`, `UNIQUE`, e índices regulares se muestran en los resultados de `SHOW INDEX`.
- La columna `Cardinality` es una estimación y puede no ser precisa. Se actualiza cuando se ejecuta `ANALYZE TABLE`.
- Si no especificas una base de datos, MySQL asume que la tabla está en la base de datos actual.

##### `DROP INDEX`: eliminación de índices

El comando **`DROP INDEX`** se usa para eliminar un índice de una tabla.  

###### Sintaxis

```sql
DROP INDEX nombre_indice ON nombre_tabla;
```  
  
###### Ejemplo práctico
  
**Eliminar un índice existente**:

```sql
DROP INDEX idx_email ON clientes;
```  

##### Gestión de índices mediante `ALTER TABLE`

La sentencia **`ALTER TABLE`** permite modificar la estructura de una tabla, incluyendo la **creación**, **modificación** y **eliminación** de índices.

```sql
ALTER TABLE nombre_tabla ADD INDEX nombre_indice (columna);
```  

```sql
ALTER TABLE nombre_tabla DROP INDEX nombre_indice;
```

⚠ **Importante**: No se puede eliminar un índice `PRIMARY KEY` directamente con `DROP INDEX`. En su lugar, se debe modificar la estructura de la tabla:

```sql
ALTER TABLE empleados DROP PRIMARY KEY;
```  

#### 2.2.4. Evaluación del uso de índices

Es importante analizar si los índices están siendo utilizados correctamente.  

##### Uso de `EXPLAIN` para analizar consultas

El comando `EXPLAIN` muestra cómo MySQL ejecutará una consulta y si aprovechará los índices.  

```sql
EXPLAIN SELECT * FROM ventas WHERE fecha = '2024-01-01';
```  

Ejemplo de salida de `EXPLAIN`:  

```sql
+----+-------------+--------+------+---------------+-----------+---------+-------+------+-------------+
| id | select_type | table  | type | possible_keys | key       | key_len | ref   | rows | Extra       |
+----+-------------+--------+------+---------------+-----------+---------+-------+------+-------------+
|  1 | SIMPLE      | ventas | ref  | idx_fecha     | idx_fecha | 4       | const |  10  | Using index |
+----+-------------+--------+------+---------------+-----------+---------+-------+------+-------------+
```  
  
**Interpretación de la salida:**

- **`possible_keys`**: Índices que podrían ser utilizados.  
- **`key`**: Índice realmente utilizado.  
- **`rows`**: Número de filas analizadas (cuanto menor sea, mejor).  
- **`Extra`**: Si aparece `Using index`, significa que el índice está optimizando la consulta.  

##### Optimización de índices con `ANALYZE TABLE` y `OPTIMIZE TABLE`

Cuando operamos sobre tablas que cuentan con indices (realizamos actualizaciones, inserciones o eliminaciones), es recomendable ejecutar `ANALYZE TABLE` y `OPTIMIZE TABLE` para mantener la integridad y eficiencia de los índices.

- `OPTIMIZE TABLE` reorganiza los datos en la tabla para mejorar la eficiencia de acceso. Se reduce el espacio y se mejora la eficiencia en operaciones de entrada/salida. Los cambios que se efectuarán sobre una tabla depende del motor de almacenamiento usado por la misma. En todo caso, debe usarse este comando en los siguientes casos:
  - Después de realizar cambios sustanciales de inserción, actualización o eliminación sobre una tabla InnoDB que tiene su propio fichero .ibd, es decir, su propio fichero de almacenamiento. Se produce cuando la tabla se crea con la opción `innodb_file_per_table` activada. La tabla y los índices son reorganizados, y el espacio devuelto al sistema operativo.
  - Después de realizar cambios sustanciales de inserción, actualización y eliminación sobre columnas que sean parte de un índice `FULLTEXT` en una tabla InnoDB.
  - Después de eliminar una parte importante de una tabla MyISAM o ARCHIVE, o de realizar muchos cambios a tablas MyISAM o ARCHIVE con filas de longitud variable (aquellas que tienen campos `VARCHAR`, `VARBINARY`, `BLOB` o `TEXT`).
  
  Ejemplo de uso:

  ```sql
  OPTIMIZE TABLE ventas;
  ```  

- `ANALYZE TABLE` actualiza estadísticas de los índices, permitiendo que el optimizador de MySQL haga mejores elecciones. Durante el análisis, la tabla se bloquea con un bloqueo de lectura. Funciona en tablas MyISAM, BDB, y InnoDB

    ```sql
    ANALYZE TABLE ventas;
    ```  



##### Optimización con `index merge`  

En algunos casos, MySQL puede combinar índices múltiples a través de una estrategia llamada **`index merge`**, permitiendo que se usen más de un índice en una consulta.  

Ejemplo de consulta que podría beneficiarse de `index merge`:

```sql
EXPLAIN SELECT * FROM clientes WHERE apellido = 'García' OR nombre = 'Ana';
```

Si MySQL decide utilizar `index merge`, el resultado de `EXPLAIN` mostrará algo como:  

```sql
| id | select_type | table    | type        | possible_keys            | key                      | key_len | ref  | rows | Extra                    |
|----|-------------|----------|-------------|--------------------------|--------------------------|---------|------|------|--------------------------|
|  1 | SIMPLE      | clientes | index_merge | idx_apellido, idx_nombre | idx_apellido, idx_nombre | 52      | NULL | 2    | Using index merge        |
```

Esto significa que MySQL combinará los resultados de ambos índices para devolver la consulta más rápido. Sin embargo, **`index merge` no siempre es eficiente**, por lo que un **índice multicolumna podría ser mejor en algunos casos**.

Por tanto, podríamos investigar más si:

1. Notamos que la consulta es lenta
2. El número de rows examinadas es mucho mayor del esperado
3. Vemos "Using filesort" o "Using temporary" junto con index_merge

En estos casos, podrías:

1. Comparar el rendimiento creando un índice compuesto
2. Medir el tiempo de la consulta actual vs alternativas
3. Analizar si la consulta se puede reescribir de forma más eficiente

### 2.3. Optimización del diseño de bases de datos

Para optimizar el funcionamiento del SGBD, podemos realizar **optimizaciones en el propio diseño** de la base de datos, es decir, en la estructura de las tablas y relaciones entre ellas.

En general, debemos realizar un diseño inicial pensando en minimizar el espacio que ocupan en disco, de modo que se reduzca el flujo de E/S en disco. Podemos tener en cuenta lo siguiente:

- **Usar los tipos de datos más pequeños posibles**, siempre que se ajusten a los requisitos. Por ejemplo, un `MEDIUMINT` (3 bytes) ocupa un 25% menos de espacio que un `INT` (4 bytes).
- Siempre que sea posible, **usaremos NOT NULL en las columnas**, ya que facilita la indexación y evita verificaciones innecesarias de valores nulos en las consultas. Si fuera necesario, definiremos un valor `DEFAULT` para evitar valores nulos.
- Atributos calculados: en lugar de almacenar datos calculados, podemos usar **columnas calculadas o vistas** para obtener los **resultados en tiempo de ejecución**. Por ejemplo, en lugar de almacenar la edad de una persona, podemos calcularla a partir de la fecha de nacimiento.
- Evitar el abuso de `VARCHAR`: si un campo tiene longitud definida, es mejor usar `CHAR(n)` en lugar de `VARCHAR`, ya que `CHAR` es más rápido para búsquedas y comparaciones.
- La **clave primaria debe ser lo más pequeña posible**, preferiblemente un número entero (`INT UNSIGNED` o `BIGINT UNSIGNED` si es necesario), ya que en InnoDB se usa como clave del índice agrupado (Clustered Index), lo que impacta directamente en la velocidad de búsqueda.
- Es conveniente que los **campos iguales se declaren exactamente igual**, sobre todo si intervienen en operaciones de JOIN.
- Particionado de tablas: dividir una tabla en varias partes más pequeñas, lo que puede mejorar el rendimiento de las consultas. Podemos realizar el particionado tanto vertical como horizontalmente.
  - En el **particionado horizontal**, se dividen las filas de una tabla en particiones, generalmente por un rango de valores en una columna. Por ejemplo, podemos particionar una tabla de empleados por años de contratación:

  ```sql
  CREATE TABLE empleados (
      id INT AUTO_INCREMENT,
      nombre VARCHAR(100),
      departamento VARCHAR(50),
      fecha_contrato DATE NOT NULL
      PRIMARY KEY (id, fecha_contrato)
  ) ENGINE=InnoDB
  PARTITION BY RANGE (fecha_contrato) (
      PARTITION p2019 VALUES LESS THAN (2020),
      PARTITION p2020 VALUES LESS THAN (2021),
      PARTITION p2021 VALUES LESS THAN (2022)
  );
  ```

  - En el **particionado vertical**, se dividen las columnas de una tabla en dos o más tablas separadas. Se usa cuando algunas columnas son accedidas con más frecuencia que otras, mejorando la velocidad de consultas y reduciendo el consumo de memoria en caché

  Nota :bulb: : Para hacer particionado horizontal `BY RANGE` es necesario que la columna por la que se particiona sea parte de la clave primaria. Si no es así, MySQL lanzará un error. Se pueden usar otras estrategias de particionado horizontal, como `BY HASH`. Para más información, consultar la [documentación oficial](https://dev.mysql.com/doc/refman/8.0/en/partitioning.html).

- **Normalización de tablas**: La normalización consiste en dividir una tabla en varias tablas relacionadas para reducir la redundancia y mejorar la integridad de los datos. Se realiza siguiendo las formas normales (1FN, 2FN, 3FN, BCNF, etc.), dependiendo del grado de optimización necesario.
- **Desnormalización de tablas**: la desnormalización combina varias tablas en una sola para reducir la necesidad de JOINs en consultas frecuentes. Es útil en sistemas donde la **lectura es prioritaria sobre la escritura**, como en sistemas OLAP o almacenes de datos (Data Warehouses).

### 2.4. Optimización de consultas

Las consultas SQL mal diseñadas pueden generar tiempos de respuesta elevados y afectar el rendimiento general del sistema. Algunas estrategias para optimizar consultas incluyen:

#### 2.4.1. Uso de `EXPLAIN` para analizar consultas

La instrucción `EXPLAIN` permite ver cómo se ejecutará una consulta y detectar posibles problemas.

```sql
EXPLAIN SELECT * FROM ventas WHERE fecha > '2024-01-01';
```

El resultado de `EXPLAIN` muestra información sobre cómo MySQL ejecutará la consulta:

```sql
+----+-------------+--------+------+---------------+-----------+---------+-------+------+-------------+
| id | select_type | table  | type | possible_keys | key       | key_len | ref   | rows | Extra       |
+----+-------------+--------+------+---------------+-----------+---------+-------+------+-------------+
|  1 | SIMPLE      | ventas | range| idx_fecha     | idx_fecha | 3       | NULL  |  10  | Using index |
+----+-------------+--------+------+---------------+-----------+---------+-------+------+-------------+
```

- `id`: Número de tabla en la consulta.
- `select_type`: rol de la tabla en la consulta. Puede tener, entre otros, los siguientes valores:
  - `SIMPLE`: la tabla es la primera en la consulta.
  - `PRIMARY`: la tabla es la primera en un JOIN.
  - `DERIVED`: la tabla es una subconsulta.
  - `UNION`: la tabla es parte de una unión.
  - `SUBQUERY`: la tabla es una subconsulta.
  - `DEPENDENT SUBQUERY`: la tabla es una subconsulta dependiente.
- `table`: nombre de la tabla de la que se extraen los registros.
- `type`: tipo de acceso a la tabla. Puede ser, entre otros:
  - `ALL`: escaneo completo de la tabla.
  - `index`: escaneo completo de un índice.
  - `range`: búsqueda de un rango de valores.
  - `ref`: búsqueda por referencia a una columna.
  - `eq_ref`: búsqueda por igualdad en un índice único.
  - `const`: búsqueda por clave primaria.
- `possible_keys`: índices que MySQL podría usar.
- `key`: índice que MySQL ha decidido usar.
- `key_len`: longitud del índice utilizado.
- `ref`: columna o constante comparada con el índice.
- `rows`: número de filas que MySQL espera examinar antes de devolver los resultados. Es solo una estimación, no necesariamente coincidirá con el número real de filas.
- `Extra`: información adicional sobre la consulta. Algunos valores posibles:
  - `Using index`: MySQL usa solo el índice para recuperar los resultados.
  - `Using where`: MySQL filtra las filas después de recuperarlas.
  - `Using temporary`: MySQL usa una tabla temporal para procesar los resultados.
  - `Using filesort`: MySQL necesita ordenar los resultados antes de devolverlos.

##### Uso de `Optimizer Trace` para análisis avanzado

Si una consulta no usa índices correctamente o sufre problemas de rendimiento, `OPTIMIZER TRACE` ayuda a entender por qué.

Activar el rastreo del optimizador:

```sql
SET optimizer_trace="enabled=on";  
```

Ejecutar la consulta a analizar:

```sql
SELECT * FROM ventas WHERE fecha = '2024-01-01';
```

Obtener el rastreo:

```sql
SELECT * FROM INFORMATION_SCHEMA.OPTIMIZER_TRACE;
```

Esto permite ver qué caminos ha considerado el optimizador de MySQL y por qué eligió una estrategia de ejecución en particular. El resultado de la consulta anterior arroja los siguientes campos:

| QUERY | TRACE | MISSING_BYTES_BEYOND_MAX_MEM_SIZE | INSUFFICIENT_PRIVILEGES |
|-------|-------|-----------------------------------|-------------------------|

Concretamente, en el campo `TRACE` se muestra un JSON con información detallada sobre la ejecución de la consulta:

```JSON
{
    "steps": [
      {
        "join_preparation": {
          "select#": 1,
          "steps": [
            {
              "expanded_query": "/* select#1 */ select `pedidos`.`id` AS `id`,`pedidos`.`cliente_id` AS `cliente_id`,`pedidos`.`fecha` AS `fecha`,`pedidos`.`total` AS `total`,`pedidos`.`estado` AS `estado` from `pedidos` where (`pedidos`.`fecha` = ''2022-01-01'') limit 1000000000"
            }
          ]
        }
      },
      {
        "join_optimization": {
          "select#": 1,
          "steps": [
            {
              "condition_processing": {
                "condition": "WHERE",
                "original_condition": "(`pedidos`.`fecha` = ''2022-01-01'')",
                "steps": [
                  {
                    "transformation": "equality_propagation",
                    "resulting_condition": "multiple equal(''2022-01-01'', `pedidos`.`fecha`)"
                  },
                  {
                    "transformation": "constant_propagation",
                    "resulting_condition": "multiple equal(''2022-01-01'', `pedidos`.`fecha`)"
                  },
                  {
                    "transformation": "trivial_condition_removal",
                    "resulting_condition": "multiple equal(DATE''2022-01-01'', `pedidos`.`fecha`)"
                  }
                ]
              }
            },
            {
              "substitute_generated_columns": {
              }
            },
            {
              "table_dependencies": [
                {
                  "table": "`pedidos`",
                  "row_may_be_null": false,
                  "map_bit": 0,
                  "depends_on_map_bits": [
                  ]
                }
              ]
            },
            {
              "ref_optimizer_key_uses": [
                {
                  "table": "`pedidos`",
                  "field": "fecha",
                  "equals": "DATE''2022-01-01''",
                  "null_rejecting": true
                }
              ]
            },
            {
              "rows_estimation": [
                {
                  "table": "`pedidos`",
                  "range_analysis": {
                    "table_scan": {
                      "rows": 9379238,
                      "cost": 959929
                    },
                    "potential_range_indexes": [
                      {
                        "index": "PRIMARY",
                        "usable": false,
                        "cause": "not_applicable"
                      },
                      {
                        "index": "idx_fecha",
                        "usable": true,
                        "key_parts": [
                          "fecha",
                          "id"
                        ]
                      },
                      {
                        "index": "idx_cliente_id",
                        "usable": false,
                        "cause": "not_applicable"
                      }
                    ],
                    "setup_range_conditions": [
                    ],
                    "group_index_range": {
                      "chosen": false,
                      "cause": "not_group_by_or_distinct"
                    },
                    "skip_scan_range": {
                      "potential_skip_scan_indexes": [
                        {
                          "index": "idx_fecha",
                          "usable": false,
                          "cause": "query_references_nonkey_column"
                        }
                      ]
                    },
                    "analyzing_range_alternatives": {
                      "range_scan_alternatives": [
                        {
                          "index": "idx_fecha",
                          "ranges": [
                            "fecha = ''2022-01-01''"
                          ],
                          "index_dives_for_eq_ranges": true,
                          "rowid_ordered": true,
                          "using_mrr": true,
                          "index_only": false,
                          "in_memory": 0,
                          "rows": 6669,
                          "cost": 6946.13,
                          "chosen": true
                        }
                      ],
                      "analyzing_roworder_intersect": {
                        "usable": false,
                        "cause": "too_few_roworder_scans"
                      }
                    },
                    "chosen_range_access_summary": {
                      "range_access_plan": {
                        "type": "range_scan",
                        "index": "idx_fecha",
                        "rows": 6669,
                        "ranges": [
                          "fecha = ''2022-01-01''"
                        ]
                      },
                      "rows_for_plan": 6669,
                      "cost_for_plan": 6946.13,
                      "chosen": true
                    }
                  }
                }
              ]
            },
            {
              "considered_execution_plans": [
                {
                  "plan_prefix": [
                  ],
                  "table": "`pedidos`",
                  "best_access_path": {
                    "considered_access_paths": [
                      {
                        "access_type": "ref",
                        "index": "idx_fecha",
                        "rows": 6669,
                        "cost": 7335.67,
                        "chosen": true
                      },
                      {
                        "access_type": "range",
                        "range_details": {
                          "used_index": "idx_fecha"
                        },
                        "chosen": false,
                        "cause": "heuristic_index_cheaper"
                      }
                    ]
                  },
                  "condition_filtering_pct": 100,
                  "rows_for_plan": 6669,
                  "cost_for_plan": 7335.67,
                  "chosen": true
                }
              ]
            },
            {
              "attaching_conditions_to_tables": {
                "original_condition": "(`pedidos`.`fecha` = DATE''2022-01-01'')",
                "attached_conditions_computation": [
                ],
                "attached_conditions_summary": [
                  {
                    "table": "`pedidos`",
                    "attached": "(`pedidos`.`fecha` = DATE''2022-01-01'')"
                  }
                ]
              }
            },
            {
              "finalizing_table_conditions": [
                {
                  "table": "`pedidos`",
                  "original_table_condition": "(`pedidos`.`fecha` = DATE''2022-01-01'')",
                  "final_table_condition   ": null
                }
              ]
            },
            {
              "refine_plan": [
                {
                  "table": "`pedidos`"
                }
              ]
            }
          ]
        }
      },
      {
        "join_execution": {
          "select#": 1,
          "steps": [
          ]
        }
      }
    ]
  }'
```

`OPTIMIZER TRACE` es una herramienta avanzada y no profundizaremos en su uso. Para más información, se puede consultar la [documentación oficial](https://dev.mysql.com/doc/refman/8.0/en/optimizer-tracing.html).

#### 2.4.2. Reescritura de consultas para la mejora de rendimiento

Es posible optimizar una consulta sin modificar la estructura de la base de datos, simplemente ajustando su sintaxis o su lógica de ejecución.

##### Evitar `SELECT *` innecesarios

Siempre que sea posible, se deben seleccionar solo las columnas necesarias en lugar de usar `SELECT *`.

❌ Mala práctica:

```sql
SELECT * FROM productos WHERE categoria = 'electrónica';
```

✔ Buena práctica:

```sql
SELECT nombre, precio FROM productos WHERE categoria = 'electrónica';
```

##### Usar `EXISTS` en lugar de `IN` para subconsultas

En consultas con subconsultas, `EXISTS` suele ser más eficiente que `IN`.

❌ Mala práctica:

```sql  
SELECT nombre FROM clientes WHERE id IN (SELECT cliente_id FROM pedidos);
```

✔ Buena práctica:

```sql
SELECT nombre FROM clientes c WHERE EXISTS (SELECT 1 FROM pedidos p WHERE p.cliente_id = c.id);
```

##### Evitar funciones en `WHERE`

El uso de funciones en la cláusula `WHERE` puede impedir el uso de índices.

❌ Mala práctica:

```sql
SELECT * FROM productos WHERE YEAR(fecha) = 2024;
```

✔ Buena práctica:

```sql
SELECT * FROM productos WHERE fecha >= '2024-01-01' AND fecha < '2025-01-01';
```

##### Reescritura de consultas con `JOIN` optimizados

El uso de `JOIN` puede ser más eficiente que ejecutar múltiples consultas separadas.

```sql
SELECT c.nombre, p.total
FROM clientes c
JOIN pedidos p ON c.id = p.cliente_id
WHERE p.fecha > '2024-01-01';
```

##### Consultas con `ORDER BY`

En muchas consultas se incluye la cláusula `ORDER BY` para ordenar los resultados. El proceso de ordenación es costoso, por lo que debemos evitarlo siempre que sea posible. Si ejecutamos EXPLAIN en una consulta y vemos que se está utilizando `Using filesort`, significa que MySQL necesita ordenar los resultados antes de devolverlos.

```sql
EXPLAIN SELECT * FROM productos ORDER BY precio DESC;
```

```sql
+----+-------------+-----------+------+---------------+------+---------+------+-------+-------------+
| id | select_type | table     | type | possible_keys | key  | key_len | ref  | rows  | Extra       |
+----+-------------+-----------+------+---------------+------+---------+------+-------+-------------+
|  1 | SIMPLE      | productos | ALL  | NULL          | NULL | NULL    | NULL | 10000 | Using filesort |
+----+-------------+-----------+------+---------------+------+---------+------+-------+-------------+
```

Si los campos de ordenación están indexados, MySQL puede usar el índice para ordenar los resultados, evitando el uso de `Using filesort`, y realizando la consulta de manera más eficiente.

#### 2.4.3. Uso de particiones y vistas materializadas

##### Particiones

Las particiones permiten dividir grandes tablas en partes más pequeñas y eficientes, reduciendo el número de filas a escanear en cada consulta.

Ejemplo de partición por rango en una tabla de ventas:

```sql
CREATE TABLE ventas (
    id INT NOT NULL,
    fecha DATE NOT NULL,
    total DECIMAL(10,2),
    PRIMARY KEY (id, fecha)
) PARTITION BY RANGE (YEAR(fecha)) (
    PARTITION p2022 VALUES LESS THAN (2023),
    PARTITION p2023 VALUES LESS THAN (2024),
    PARTITION p2024 VALUES LESS THAN (2025)
);
```

De esta forma, las consultas filtradas por año se ejecutarán más rápido, ya que MySQL solo escaneará las particiones necesarias.

```sql
SELECT * FROM ventas WHERE fecha BETWEEN '2023-01-01' AND '2023-12-31';
```

##### Vistas materializadas

Las vistas materializadas son tablas físicas que almacenan el resultado de una consulta compleja, permitiendo acelerar consultas frecuentes. 

:warning: **Nota**: Las vistas materializadas no están soportadas de manera nativa en MySQL, pero pueden ser simuladas con tablas temporales o procedimientos almacenados.

**Ejemplo de vista materializada con tabla temporal**:

```sql
CREATE TABLE reporte_ventas AS 
SELECT cliente_id, SUM(total) AS total_ventas 
FROM ventas GROUP BY cliente_id;

-- Actualización periódica de la vista materializada mediante evento
CREATE EVENT actualizar_reporte_ventas
ON SCHEDULE EVERY 1 DAY
DO 
    REPLACE INTO reporte_ventas 
    SELECT cliente_id, SUM(total) AS total_ventas FROM ventas GROUP BY cliente_id;
```

### 2.5. Optimización del servidor de bases de datos

El ajuste de los parámetros del servidor permite mejorar la eficiencia en la ejecución de consultas y la gestión de conexiones.

#### 2.5.1. Parámetros clave de configuración

Algunos de los parámetros más importantes en MySQL incluyen:

- **`innodb_buffer_pool_size`**: Determina la cantidad de memoria RAM asignada a la caché de InnoDB.  
- **`query_cache_size`**: Define la cantidad de memoria reservada para almacenar consultas repetitivas.  
- **`max_connections`**: Establece el número máximo de conexiones simultáneas permitidas.

Para visualizar la configuración actual de estos parámetros:

```sql
SHOW VARIABLES LIKE 'innodb_buffer_pool_size';
SHOW VARIABLES LIKE 'query_cache_size';
SHOW VARIABLES LIKE 'max_connections';
```

Veremos con detalle estos aspectos en el apartado de monitorización.

### 2.6. Mantenimiento y verificación de integridad

El mantenimiento de la base de datos es fundamental para garantizar su correcto funcionamiento y prevenir problemas de corrupción de datos. MySQL proporciona varias herramientas para verificar la integridad de las tablas y reparar errores en caso de que se detecten.  

A continuación, se explican tres comandos esenciales:  

- `CHECK TABLE`: verifica si una tabla tiene errores.  
- `REPAIR TABLE`: intenta corregir errores en una tabla.  
- `CHECKSUM TABLE`: permite detectar cambios en los datos calculando un valor de verificación.  

#### 2.6.1. Verificación de tablas con `CHECK TABLE`

El comando `CHECK TABLE` permite comprobar la integridad de una o varias tablas y detectar posibles errores.  

**Sintaxis básica:**

```sql
CHECK TABLE nombre_tabla;
```

**Ejemplo:**  

```sql
CHECK TABLE pedidos;
```

**Salida esperada:**

```plaintext
+----------------+-------+----------+----------+
| Table          | Op    | Msg_type | Msg_text |
+----------------+-------+----------+----------+
| tienda.pedidos | check | status   | OK       |
+----------------+-------+----------+----------+
```

✅ **Si el estado es `OK`**, significa que la tabla no tiene errores.  
❌ **Si se detectan errores**, MySQL los notificará en la columna `Msg_text`.  

Para más información sobre el comando `CHECK TABLE`, se puede consultar la [documentación oficial](https://dev.mysql.com/doc/refman/8.4/en/check-table.html).

#### 2.6.2. Reparación de tablas con `REPAIR TABLE`

Si `CHECK TABLE` detecta problemas en una tabla de tipo `MyISAM` o `ARCHIVE`, se puede intentar repararla con `REPAIR TABLE`.  

**Sintaxis básica:**

```sql
REPAIR TABLE nombre_tabla;
```

**Ejemplo:**

```sql
REPAIR TABLE pedidos;
```

**Salida esperada:**

```plaintext
+----------------+--------+----------+-----------------+
| Table          | Op     | Msg_type | Msg_text        |
+----------------+--------+----------+-----------------+
| tienda.pedidos | repair | status   | OK              |
+----------------+--------+----------+-----------------+
```

**Importante:**

- `REPAIR TABLE` **solo funciona en MyISAM y ARCHIVE**, no en InnoDB.  
- En **InnoDB**, la única forma de reparar una tabla corrupta es **reconstruyéndola** (ver `ALTER TABLE Method` [aquí](https://dev.mysql.com/doc/refman/8.4/en/rebuilding-tables.html#rebuilding-tables-alter-table)):  
  
  ```sql
  ALTER TABLE pedidos ENGINE=InnoDB;
  ```

- **Si el error persiste, es recomendable restaurar la tabla desde una copia de seguridad.**  

Más información sobre `REPAIR TABLE` en la [documentación oficial](https://dev.mysql.com/doc/refman/8.4/en/repair-table.html).

#### 2.6.3. Detección de cambios con `CHECKSUM TABLE`

El comando `CHECKSUM TABLE` permite calcular un **valor hash** sobre los datos de una tabla. Esto es útil para detectar si ha habido modificaciones en los registros sin necesidad de comparar manualmente cada fila.  

**Sintaxis básica:**

```sql
CHECKSUM TABLE nombre_tabla;
```

**Ejemplo:**

```sql
CHECKSUM TABLE pedidos;
```

**Salida esperada:**

```plaintext
+--------------+------------+
| Table        | Checksum   |
+--------------+------------+
| tienda.pedidos | 298734265 |
+--------------+------------+
```

**Cómo usarlo para detectar cambios:**

1. Se ejecuta `CHECKSUM TABLE` y se guarda el resultado.
2. Si en otro momento el **valor de `Checksum` cambia**, significa que los datos han sido modificados.  

**Limitaciones**:

- Puede **no ser exacto en tablas grandes**, ya que no siempre detecta cambios en registros individuales.  

Más información sobre `CHECKSUM TABLE` en la [documentación oficial](https://dev.mysql.com/doc/refman/8.4/en/checksum-table.html).

#### 2.6.4. Resumen y mejores prácticas

| **Comando**           | **Función**                                        | **Soporta InnoDB?** |
|----------------------|------------------------------------------------|------------------|
| `CHECK TABLE`        | Verifica si una tabla tiene errores.           | ✔️ Sí |
| `REPAIR TABLE`       | Intenta reparar una tabla dañada.               | ❌ No (solo MyISAM) |
| `CHECKSUM TABLE`     | Detecta cambios en los datos.                   | ✔️ Sí, pero con limitaciones |

**Recomendaciones:**

- Ejecutar `CHECK TABLE` regularmente en bases de datos con alto tráfico.  
- En MyISAM, si hay fallos, usar `REPAIR TABLE`.  
- Usar `CHECKSUM TABLE` para auditar cambios en datos sensibles.  
- Para InnoDB, en caso de corrupción, realizar una **reconstrucción de la tabla (`ALTER TABLE ... ENGINE=InnoDB`) o restaurar desde una copia de seguridad.**  

### 2.7. Otros aspectos de optimización

#### 2.7.1. Sistemas de permisos

Como norma general, debemos evitar un sistema de permisos muy sobrecargado, para evitar accesos a las tablas de permisos en cada consulta.

En MySQL, los permisos se almacenan en la tabla `mysql.user`, y cada vez que se realiza una consulta, MySQL debe comprobar si el usuario tiene permisos para ejecutarla. Si el sistema de permisos es muy complejo, esto puede ralentizar el rendimiento del servidor. En su lugar, podemos usar **roles** para simplificar la gestión de permisos.

#### 2.7.2. Modificadores de MySQL

Si observamos la sintaxis completa de una sentencia `SELECT`, veremos que se permiten ciertas clausulas reservadas para determinar el modo de hacer la consulta en cuanto a su optimización:

```sql
SELECT
[ALL | DISTINCT | DISTINCTROW]
  [HIGH_PRIORITY]
  [STRAIGHT_JOIN]
  [SQL_SMALL_RESULT] [SQL_BIG_RESULT] [SQL_BUFFER_RESULT]
  [SQL_CACHE | SQL_NO_CACHE] [SQL_CALC_FOUND_ROWS]
  ...
```

- `SQL_CACHE`: indica que no se almacenen los resultados de una consulta en la caché salvo que la variable `query_cache_type` esté activada, en cuyo caso no tiene efecto y todas las consultas se almacenan en la caché.
- `STRAIGHT_JOIN`: indica a MySQL que lea las tablas en el orden en que se especifican en la consulta.

    ```sql
    SELECT * FROM tabla1 STRAIGHT_JOIN tabla2 ON tabla1.id = tabla2.id;
    ```

- `SQL_BIG_RESULT`: indica a MySQL que la consulta devolverá un gran número de filas. De esta manera, el servidor utilizará tablas temporales.
- `SQL_BUFFER_RESULT`: obliga al servidor a incluir el resultado en una tabla temporal. Esta opción está diseñada para escenarios en los que un cliente realiza una consulta y, mientras el resultado completo no se haya enviado por completo, la consulta sigue "en ejecución" y por tanto podrían producirse bloqueos. Mediante esta opción evitamos bloquear la tabla en esa fase de envío de resultados al cliente, por si esta se pudiese demorar.

[Siguiente sección: monitorización](../UD4_monitorizacion.md)
