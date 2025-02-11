# UD4 - Optimización y Monitorización en SGBD

## 1. Introducción a la Optimización y Monitorización en SGBD

El rendimiento de un **Sistema Gestor de Bases de Datos (SGBD)** es un factor crítico en entornos donde se manejan grandes volúmenes de datos y múltiples usuarios concurrentes. Una base de datos mal optimizada puede generar tiempos de respuesta elevados, consumo excesivo de recursos y problemas de concurrencia, afectando la experiencia del usuario y la eficiencia del sistema.

Este apartado introduce la importancia de la optimización y la monitorización del rendimiento, así como los principales factores que influyen en el desempeño de un SGBD.

### 1.1. 1.1 Importancia de la Monitorización del Rendimiento

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

### 1.2. 1.2 Factores que afectan el rendimiento en bases de datos

El rendimiento de un SGBD depende de varios factores, que pueden agruparse en **hardware, configuración del servidor, diseño de la base de datos y optimización de consultas**.

#### 1.2.1. 1.2.1 Factores de Hardware

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

#### 1.2.2. 1.2.2 Factores de configuración del servidor

Los parámetros del servidor de bases de datos pueden ajustarse para mejorar el rendimiento. Algunos de los más importantes en MySQL son:

🔸 **`max_connections`**: Número máximo de conexiones simultáneas permitidas.  
🔸 **`query_cache_size`**: Caché de consultas, útil para acelerar consultas repetitivas.  
🔸 **`innodb_log_file_size`**: Tamaño de los archivos de log de transacciones, afecta la velocidad de escritura.  

Ejemplo de cómo consultar estas configuraciones:

```sql
SHOW VARIABLES LIKE 'max_connections';
```

#### 1.2.3. **1.2.3 Factores de Diseño de la Base de Datos**

Un mal diseño de la base de datos puede generar redundancia de datos, consultas ineficientes y bloqueos. Buenas prácticas incluyen:

✔ **Normalización adecuada** para evitar duplicidad de datos.  
✔ **Uso eficiente de índices** para acelerar las búsquedas.  
✔ **Elección de tipos de datos correctos** para reducir el espacio en disco.  

Ejemplo: Si una tabla tiene consultas lentas, podríamos verificar si tiene índices adecuados con:

```sql
SHOW INDEX FROM nombre_tabla;
```

#### 1.2.4. 1.2.4 Factores relacionados con consultas SQL

Las consultas mal diseñadas pueden ser la causa principal de problemas de rendimiento. Factores clave incluyen:

⚠ **Uso excesivo de `SELECT *`**, en lugar de seleccionar solo las columnas necesarias.  
⚠ **Falta de índices en columnas utilizadas en `WHERE`, `JOIN` y `ORDER BY`**.  
⚠ **Consultas que generan tablas temporales innecesarias**.  

Ejemplo: Para analizar una consulta y ver su plan de ejecución, podemos usar:

```sql
EXPLAIN SELECT * FROM pedidos WHERE cliente_id = 10;
```

### 1.3. 1.3 Herramientas y enfoques de optimización

Existen diferentes herramientas y estrategias para optimizar una base de datos:

#### 1.3.1. 1.3.1 Herramientas de Monitorización

🔹 **`SHOW STATUS` y `SHOW VARIABLES`** en MySQL para obtener estadísticas del servidor.  
🔹 **`INFORMATION_SCHEMA`** para analizar estructuras de tablas y consultas.  
🔹 **Logs de consultas lentas (`slow_query_log`)** para identificar consultas ineficientes.  

Ejemplo para activar el registro de consultas lentas:

```sql
SET GLOBAL slow_query_log = 'ON';
SET GLOBAL long_query_time = 1; -- Consultas que tardan más de 1s
```

#### 1.3.2. 1.3.2 Estrategias de Optimización

✅ **Optimización del diseño de la base de datos** (normalización, índices, particiones).  
✅ **Mejora de consultas SQL** (`EXPLAIN`, `OPTIMIZER TRACE`).  
✅ **Configuración adecuada del servidor** (ajuste de buffers, conexiones, caché).  
✅ **Automatización del mantenimiento** (reindexación, limpieza de registros antiguos).  

### 1.4. Resumen

1. La **monitorización del rendimiento** permite detectar problemas antes de que impacten la producción.
2. El **rendimiento de un SGBD depende de múltiples factores**, desde hardware hasta optimización de consultas.
3. **Existen herramientas y estrategias** para analizar y mejorar la eficiencia de las bases de datos.

Este primer apartado sienta las bases para los siguientes, donde se abordarán herramientas específicas de monitorización y técnicas avanzadas de optimización.

## 2. Herramientas de monitorización en SGBD

El rendimiento de un sistema gestor de bases de datos puede degradarse con el tiempo debido al crecimiento de los datos, aumento de la carga de usuarios y consultas ineficientes. Para identificar y solucionar estos problemas, es fundamental el uso de herramientas de monitorización que permitan analizar el comportamiento del servidor y la eficiencia de las consultas.

### 2.1. Trazas, logs y alertas

Los sistemas gestores de bases de datos ofrecen mecanismos para registrar actividad en forma de trazas y logs. Estos registros permiten detectar consultas problemáticas, errores en la ejecución y posibles cuellos de botella.

#### 2.1.1. Trazas

Las trazas son registros detallados de la actividad del sistema. En MySQL, pueden configurarse mediante la opción de **general log**, que almacena cada consulta ejecutada.

Activar el log general en MySQL:

```sql
SET GLOBAL general_log = 'ON';
SET GLOBAL general_log_file = '/var/log/mysql/general.log';
```

Verificar si el log general está activado:

```sql
SHOW VARIABLES LIKE 'general_log';
```

#### 2.1.2. Logs

Existen diferentes tipos de logs en MySQL:

- **Error log**: Registra fallos del servidor y problemas en la ejecución de consultas.
- **Slow query log**: Registra las consultas que superan un tiempo de ejecución determinado.
- **Binary log**: Guarda cambios realizados en la base de datos, útil para replicación y recuperación de datos.

Habilitar el log de consultas lentas:

```sql
SET GLOBAL slow_query_log = 'ON';
SET GLOBAL long_query_time = 1; -- Registra consultas que tarden más de 1 segundo
```

Consultar el número de consultas lentas:

```sql
SHOW GLOBAL STATUS LIKE 'Slow_queries';
```

#### 2.1.3. Alertas y notificaciones

Algunas herramientas permiten configurar alertas basadas en umbrales críticos de rendimiento, como el número de conexiones activas, el uso de CPU o el tiempo de respuesta de consultas. Esto permite reaccionar antes de que un problema afecte a los usuarios.

### 2.2. Elementos y parámetros a monitorizar

El análisis del rendimiento en un SGBD implica la monitorización de distintos aspectos clave:

#### 2.2.1. Rendimiento de consultas

- **Tiempo de ejecución de consultas**: Se pueden identificar las más costosas mediante `EXPLAIN` o el log de consultas lentas.
- **Número de filas escaneadas vs. filas retornadas**: Si una consulta revisa muchas filas antes de devolver resultados, podría requerir optimización.
- **Uso de índices**: Consultas que no aprovechan índices pueden ser lentas.

Ejemplo de análisis de una consulta:

```sql
EXPLAIN SELECT * FROM ventas WHERE cliente_id = 10;
```

#### 2.2.2. Concurrencia y escalabilidad

- **Número de conexiones activas**: Controlar el uso de `max_connections` para evitar sobrecarga.
- **Bloqueos y deadlocks**: Identificar conflictos de acceso a los datos con `SHOW ENGINE INNODB STATUS`.
- **Tiempo de espera en transacciones**: Determinar si hay consultas que bloquean la ejecución de otras.

Ejemplo de consulta de conexiones activas:

```sql
SHOW PROCESSLIST;
```

#### 2.2.3. Uso de Recursos

- **Memoria y caché**: Parámetros como `innodb_buffer_pool_size` afectan la velocidad de lectura/escritura.
- **Uso de CPU**: Monitorizar la carga del servidor con herramientas como `top` en Linux o `SHOW STATUS` en MySQL.
- **Espacio en disco**: Bases de datos en crecimiento pueden requerir estrategias de particionamiento.

Consultar uso de la caché en MySQL:

```sql
SHOW STATUS LIKE 'Qcache%';
```

### 2.3. MySQL Enterprise Monitor y otras herramientas de monitorización

Existen diversas herramientas para monitorizar el rendimiento de una base de datos, desde soluciones integradas en MySQL hasta herramientas externas avanzadas.

#### 2.3.1. MySQL Enterprise Monitor

Es una solución oficial de MySQL que ofrece:

- Supervisión en tiempo real del servidor.
- Detección de consultas lentas y posibles bloqueos.
- Alertas personalizadas para distintos parámetros de rendimiento.
- Recomendaciones automáticas para optimización.

En cualquier caso, se encuentra descatalogada y sin soporte desde el 1 de enero de 2025 (ver [*End of Life Notice*](https://dev.mysql.com/doc/mysql-monitor/8.0/en/mem-eol.html)) y se recomienda el uso de otras herramientas más modernas.

#### 2.3.2. Otras Herramientas de Monitorización

- **Percona Monitoring and Management (PMM)**: Plataforma gratuita que permite visualizar métricas de rendimiento y detectar problemas en bases de datos MySQL.
- **Zabbix**: Herramienta de monitorización de sistemas y bases de datos que permite configurar alertas y visualizar datos en dashboards.
- **Nagios**: Monitorea la disponibilidad y rendimiento del servidor MySQL, generando notificaciones ante incidencias.
- **Grafana + Prometheus**: Solución moderna para la recolección y visualización de métricas en bases de datos.

Ejemplo de consulta de métricas básicas en MySQL:

```sql
SHOW GLOBAL STATUS LIKE 'Threads%';
```

Las herramientas de monitorización permiten mantener un control proactivo sobre el rendimiento del servidor, evitando problemas antes de que impacten en la operativa del sistema.

## 3. Optimización del rendimiento en bases de datos

El rendimiento de una base de datos depende de múltiples factores, desde la arquitectura del hardware hasta la estructura de las consultas SQL. Una optimización adecuada permite mejorar la velocidad de acceso a los datos, reducir la carga del servidor y garantizar una mejor experiencia para los usuarios. En este apartado se abordan diversas estrategias para optimizar el almacenamiento, los índices, las consultas y la configuración del servidor.

### 3.1 Optimización del almacenamiento en memoria y espacio en disco

El almacenamiento eficiente de los datos impacta directamente en el rendimiento del sistema. Optimizar el uso de memoria y disco permite reducir el tiempo de acceso a los datos y mejorar la eficiencia en la ejecución de consultas.

#### Factores que afectan el almacenamiento

Algunos aspectos clave que influyen en el rendimiento del almacenamiento son:

- **Uso de la memoria RAM**: Un almacenamiento en memoria optimizado reduce la necesidad de acceder al disco, lo que acelera las consultas.  
- **Tamaño y estructura de las tablas**: Un mal diseño de tablas genera redundancia y desperdicio de espacio.  
- **Tipo de motor de almacenamiento**: En MySQL, elegir entre **InnoDB** y **MyISAM** afecta el rendimiento en diferentes escenarios.  
- **Caché de consultas y buffers**: Parámetros como `innodb_buffer_pool_size` permiten mejorar el acceso a datos en memoria.

Para verificar el tamaño actual del buffer de InnoDB, se puede ejecutar:

```sql
SHOW VARIABLES LIKE 'innodb_buffer_pool_size';
```

#### Reducción del espacio ocupado por las tablas

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

### 3.2 Optimización de índices

Los índices permiten acelerar la búsqueda de datos dentro de una tabla. Sin embargo, un mal uso de los índices puede aumentar el tiempo de escritura y generar sobrecarga en la base de datos.

#### Tipos de índices en MySQL

En MySQL, los tipos de índices más comunes son:

- **Índice primario (PRIMARY KEY)**: Identifica de manera única cada fila en una tabla.  
- **Índice único (UNIQUE)**: Garantiza que los valores de una columna sean únicos.  
- **Índice compuesto**: Se aplica a múltiples columnas para mejorar el rendimiento en consultas con varias condiciones.  
- **Índice de texto completo (FULLTEXT)**: Permite búsquedas eficientes en grandes volúmenes de texto.

Para listar los índices de una tabla:

```sql
SHOW INDEX FROM nombre_tabla;
```

### **Identificación de índices ineficientes**

Si una consulta no está utilizando índices de manera óptima, es posible analizar su plan de ejecución con `EXPLAIN`:

```sql
EXPLAIN SELECT * FROM pedidos WHERE cliente_id = 10;
```

Si la consulta escanea demasiadas filas (`rows` elevado) sin usar un índice (`possible_keys` vacío), es recomendable crear uno:

```sql
CREATE INDEX idx_cliente ON pedidos(cliente_id);
```

### 3.3 Optimización de consultas

Las consultas SQL mal diseñadas pueden generar tiempos de respuesta elevados y afectar el rendimiento general del sistema. Algunas estrategias para optimizar consultas incluyen:

#### Uso de `EXPLAIN` para analizar consultas

La instrucción `EXPLAIN` permite ver cómo se ejecutará una consulta y detectar posibles problemas.

```sql
EXPLAIN SELECT * FROM ventas WHERE fecha > '2024-01-01';
```

Elementos clave en el resultado de `EXPLAIN`:

- **type**: Debe ser `index` o `range` para consultas eficientes. Si aparece `ALL`, indica que se está realizando un escaneo completo de la tabla.  
- **possible\_keys**: Muestra los índices que podrían utilizarse. Si está vacío, es recomendable crear un índice.  
- **rows**: Indica el número de filas que se espera leer; un número alto puede significar una consulta ineficiente.

#### Evitar `SELECT *` innecesarios

Siempre que sea posible, se deben seleccionar solo las columnas necesarias en lugar de usar `SELECT *`.

```sql
SELECT nombre, precio FROM productos WHERE categoria = 'electrónica';
```

#### Reescritura de consultas con `JOIN` optimizados

El uso de `JOIN` puede ser más eficiente que ejecutar múltiples consultas separadas.

```sql
SELECT c.nombre, p.total
FROM clientes c
JOIN pedidos p ON c.id = p.cliente_id
WHERE p.fecha > '2024-01-01';
```

### 3.4 Optimización del servidor de bases de datos

El ajuste de los parámetros del servidor permite mejorar la eficiencia en la ejecución de consultas y la gestión de conexiones.

#### Parámetros clave de configuración

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
