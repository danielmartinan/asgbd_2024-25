# UD3 - Automatización de tareas: Construcción de guiones de administración

- [1. Introducción: La Importancia de las Rutinas en la Automatización de Tareas](#1-introducción-la-importancia-de-las-rutinas-en-la-automatización-de-tareas)
  - [1.1. ¿Por qué utilizar rutinas?](#11-por-qué-utilizar-rutinas)
  - [1.2. Aplicación práctica para un DBA en la Automatización de Tareas](#12-aplicación-práctica-para-un-dba-en-la-automatización-de-tareas)
- [2. Rutinas: procedimientos y funciones](#2-rutinas-procedimientos-y-funciones)
  - [2.1. Creación de Procedimientos y Funciones](#21-creación-de-procedimientos-y-funciones)
  - [2.2. Parámetros de procedimientos y funciones](#22-parámetros-de-procedimientos-y-funciones)
  - [2.3. Sección de características](#23-sección-de-características)
  - [2.4. Cuerpo de las rutinas](#24-cuerpo-de-las-rutinas)
    - [2.4.1. Concepto de Variable y su Uso](#241-concepto-de-variable-y-su-uso)
    - [2.4.2. Alcance de las Variables](#242-alcance-de-las-variables)
    - [2.4.3. Estructuras de Control](#243-estructuras-de-control)
    - [2.4.4. ¿Cómo puedo definir las condiciones?](#244-cómo-puedo-definir-las-condiciones)
    - [2.4.5. Estructuras Repetitivas](#245-estructuras-repetitivas)
  - [2.5. Privilegios y Seguridad en Rutinas](#25-privilegios-y-seguridad-en-rutinas)
  - [2.6. Eliminación y Modificación de Rutinas](#26-eliminación-y-modificación-de-rutinas)
- [3. Eventos en mysql](#3-eventos-en-mysql)
  - [3.1. ¿Qué es un evento en MySQL?](#31-qué-es-un-evento-en-mysql)
  - [3.2. Planificador de eventos](#32-planificador-de-eventos)
    - [3.2.1. ¿Qué es el planificador de eventos?](#321-qué-es-el-planificador-de-eventos)
    - [3.2.2. Verificar el estado del planificador de eventos](#322-verificar-el-estado-del-planificador-de-eventos)
    - [3.2.3. Habilitar o deshabilitar el planificador de eventos](#323-habilitar-o-deshabilitar-el-planificador-de-eventos)
    - [3.2.4. Consideraciones sobre el planificador de eventos](#324-consideraciones-sobre-el-planificador-de-eventos)
  - [3.3. Creación de Eventos](#33-creación-de-eventos)
    - [3.3.1. Sintaxis básica para crear eventos](#331-sintaxis-básica-para-crear-eventos)
    - [3.3.2. Tipos de programación](#332-tipos-de-programación)
    - [3.3.3. Opciones adicionales en la creación de eventos](#333-opciones-adicionales-en-la-creación-de-eventos)
    - [3.3.4. Verificar eventos creados](#334-verificar-eventos-creados)
    - [3.3.5. Ejemplo práctico](#335-ejemplo-práctico)
  - [3.4. Modificación de Eventos](#34-modificación-de-eventos)
    - [3.4.1. Sintaxis básica de ALTER EVENT](#341-sintaxis-básica-de-alter-event)
    - [3.4.2. Opciones disponibles para modificar un evento](#342-opciones-disponibles-para-modificar-un-evento)
    - [3.4.3. Ejemplo completo: Modificar un evento](#343-ejemplo-completo-modificar-un-evento)
  - [3.5. Eliminación de Eventos](#35-eliminación-de-eventos)
    - [3.5.1. Sintaxis básica de `DROP EVENT`](#351-sintaxis-básica-de-drop-event)
    - [3.5.2. Ejemplo básico](#352-ejemplo-básico)
    - [3.5.3. Consideraciones importantes al eliminar eventos](#353-consideraciones-importantes-al-eliminar-eventos)
  - [3.6. Privilegios Relacionados con Eventos](#36-privilegios-relacionados-con-eventos)
    - [3.6.1. Privilegios necesarios](#361-privilegios-necesarios)
    - [3.6.2. Verificar privilegios de un usuario](#362-verificar-privilegios-de-un-usuario)
    - [3.6.3. Restricciones de seguridad](#363-restricciones-de-seguridad)
  - [3.7. Consideraciones de Seguridad y Rendimiento en Eventos](#37-consideraciones-de-seguridad-y-rendimiento-en-eventos)
    - [3.7.1. Consideraciones de Seguridad](#371-consideraciones-de-seguridad)
    - [3.7.2. Consideraciones de Rendimiento](#372-consideraciones-de-rendimiento)
  - [3.8. Ejemplos Prácticos de Uso de Eventos](#38-ejemplos-prácticos-de-uso-de-eventos)
    - [3.8.1. Limpieza Automática de Registros Antiguos](#381-limpieza-automática-de-registros-antiguos)
    - [3.8.2. Generación de Informes Periódicos](#382-generación-de-informes-periódicos)
    - [3.8.3. Reseteo Automático de una Tabla Temporal](#383-reseteo-automático-de-una-tabla-temporal)
    - [3.8.4. Deshabilitación Temporal de Eventos](#384-deshabilitación-temporal-de-eventos)
- [4. Introducción a los Disparadores](#4-introducción-a-los-disparadores)
  - [4.1. ¿Qué son los disparadores?](#41-qué-son-los-disparadores)
  - [4.2. Creación de Disparadores](#42-creación-de-disparadores)
    - [4.2.1. Consideraciones al crear disparadores](#421-consideraciones-al-crear-disparadores)
    - [4.2.2. Errores comunes al crear disparadores](#422-errores-comunes-al-crear-disparadores)
  - [4.3. Modificación, eliminación y muestra de disparadores](#43-modificación-eliminación-y-muestra-de-disparadores)
- [5. Gestión de Errores y Condiciones (Handlers)](#5-gestión-de-errores-y-condiciones-handlers)
  - [5.1. Introducción a la Gestión de Errores](#51-introducción-a-la-gestión-de-errores)
    - [5.1.1. Qué son las condiciones y los handlers](#511-qué-son-las-condiciones-y-los-handlers)
    - [5.1.2. Importancia del manejo de errores en bases de datos](#512-importancia-del-manejo-de-errores-en-bases-de-datos)
    - [5.1.3. Diferencia entre errores y advertencias en MySQL](#513-diferencia-entre-errores-y-advertencias-en-mysql)
  - [5.2. Declaración y Sintaxis](#52-declaración-y-sintaxis)
    - [5.2.1. Estructura básica `DECLARE ... HANDLER`](#521-estructura-básica-declare--handler)
    - [5.2.2. Ámbito de los handlers y reglas de declaración](#522-ámbito-de-los-handlers-y-reglas-de-declaración)
  - [5.3. Tipos de Condiciones](#53-tipos-de-condiciones)
    - [5.3.1. `SQLEXCEPTION`](#531-sqlexception)
    - [5.3.2. `SQLWARNING`](#532-sqlwarning)
    - [5.3.3. `NOT FOUND`](#533-not-found)
    - [5.3.4. Códigos de error específicos de MySQL](#534-códigos-de-error-específicos-de-mysql)
    - [5.3.5. Condiciones personalizadas (`CONDITION`)](#535-condiciones-personalizadas-condition)
    - [5.3.6. `Get Condition` Statement](#536-get-condition-statement)
  - [5.4. Manejo de Errores en la Práctica](#54-manejo-de-errores-en-la-práctica)
    - [5.4.1. Handlers en Procedimientos Almacenados](#541-handlers-en-procedimientos-almacenados)
    - [5.4.2. Handlers en Triggers](#542-handlers-en-triggers)
    - [5.4.3. Handlers en Bloques BEGIN-END](#543-handlers-en-bloques-begin-end)
    - [5.4.4. Handlers con Cursores](#544-handlers-con-cursores)
  - [5.5. Arrojando nuestras propias condiciones](#55-arrojando-nuestras-propias-condiciones)
    - [5.5.1. Sintaxis completa de `SIGNAL`](#551-sintaxis-completa-de-signal)
    - [5.5.2. ¿Por qué usar `SIGNAL` en lugar de estructuras de control como `IF`?](#552-por-qué-usar-signal-en-lugar-de-estructuras-de-control-como-if)
    - [5.5.3. Uso de `SIGNAL` para lanzar errores personalizados](#553-uso-de-signal-para-lanzar-errores-personalizados)
    - [5.5.4. Otras aplicaciones de `SIGNAL` en MySQL](#554-otras-aplicaciones-de-signal-en-mysql)
  - [5.6. Buenas Prácticas](#56-buenas-prácticas)
    - [5.6.1. Estrategias de Gestión de Errores](#561-estrategias-de-gestión-de-errores)
    - [5.6.2. Logging de Errores](#562-logging-de-errores)
    - [5.6.3. Depuración y Troubleshooting](#563-depuración-y-troubleshooting)
    - [5.6.4. Casos Comunes y Soluciones Recomendadas](#564-casos-comunes-y-soluciones-recomendadas)
  - [5.7. Ejemplos Prácticos](#57-ejemplos-prácticos)
    - [5.7.1. Manejo Básico de Errores](#571-manejo-básico-de-errores)
    - [5.7.2. Gestión de Errores en Transacciones](#572-gestión-de-errores-en-transacciones)
    - [5.7.3. Logging de Errores en Tabla](#573-logging-de-errores-en-tabla)
    - [5.7.4. Handlers Múltiples](#574-handlers-múltiples)
- [6. Introducción a los Cursores](#6-introducción-a-los-cursores)
  - [6.1. ¿Qué son los cursores?](#61-qué-son-los-cursores)
  - [6.2. ¿Cuándo y por qué usarlos?](#62-cuándo-y-por-qué-usarlos)
  - [6.3. Tipos de Cursores](#63-tipos-de-cursores)
    - [6.3.1. Cursores implícitos](#631-cursores-implícitos)
    - [6.3.2. Cursores Explícitos](#632-cursores-explícitos)
  - [6.4. Creación y Uso de Cursores](#64-creación-y-uso-de-cursores)
    - [6.4.1. Puntos Importantes a Recordar](#641-puntos-importantes-a-recordar)
  - [6.5. Características principales de los cursores explícitos en MySQL](#65-características-principales-de-los-cursores-explícitos-en-mysql)
    - [6.5.1. Son unidireccionales (forward-only)](#651-son-unidireccionales-forward-only)
    - [6.5.2. Son de solo lectura (read-only)](#652-son-de-solo-lectura-read-only)
    - [6.5.3. No son actualizables](#653-no-son-actualizables)
    - [6.5.4. No son scrollables (no permiten movimientos hacia atrás o saltos)](#654-no-son-scrollables-no-permiten-movimientos-hacia-atrás-o-saltos)
  - [6.6. Ejemplos Prácticos](#66-ejemplos-prácticos)
  - [6.7. Limitaciones de los Cursores](#67-limitaciones-de-los-cursores)
  - [6.8. Buenas Prácticas con Cursores](#68-buenas-prácticas-con-cursores)
- [7. Documentación en MySQL: Procedimientos, Eventos, Handlers y Cursores](#7-documentación-en-mysql-procedimientos-eventos-handlers-y-cursores)
- [8. Recursos adicionales](#8-recursos-adicionales)
- [9. Anexo: tablas temporales en MySQL](#9-anexo-tablas-temporales-en-mysql)
  - [9.1. Creación de tablas temporales](#91-creación-de-tablas-temporales)
  - [9.2. Manipulación de datos en tablas temporales](#92-manipulación-de-datos-en-tablas-temporales)
  - [9.3. Eliminación de tablas temporales](#93-eliminación-de-tablas-temporales)
  - [9.4. Diferencias entre tablas temporales y tablas normales](#94-diferencias-entre-tablas-temporales-y-tablas-normales)
  - [9.5. Casos de uso de tablas temporales](#95-casos-de-uso-de-tablas-temporales)

## 1. Introducción: La Importancia de las Rutinas en la Automatización de Tareas

En la administración de bases de datos, las rutinas (**procedimientos almacenados y funciones**) son herramientas fundamentales para garantizar la eficiencia, la repetibilidad y la seguridad en la ejecución de tareas repetitivas o complejas. Su uso permite **encapsular la lógica del negocio** directamente en el servidor de bases de datos, reduciendo la necesidad de depender de aplicaciones externas para manejar operaciones críticas.

Las **rutinas**, junto a los **disparadores** o **triggers** y a los **eventos**, son particularmente útiles en entornos donde la consistencia y el rendimiento son esenciales, ya que se ejecutan directamente en el servidor, evitando la sobrecarga de la red al minimizar el intercambio de datos entre el cliente y el servidor. Además, proporcionan una manera de **centralizar las operaciones frecuentes**, asegurando que todos los usuarios y aplicaciones sigan el mismo flujo lógico al interactuar con los datos.

### 1.1. ¿Por qué utilizar rutinas?

1. **Eficiencia**:

   1. Las rutinas permiten procesar operaciones complejas en el lado del servidor, reduciendo los tiempos de espera y optimizando los recursos del sistema.

   2. Al agrupar múltiples comandos SQL en una rutina, se evita enviar comandos individuales desde la aplicación al servidor, mejorando el rendimiento.

2. **Consistencia**:

   1. La lógica encapsulada en procedimientos o funciones garantiza que las reglas del negocio se implementen de manera uniforme en todas las operaciones.

   2. Las rutinas también facilitan la validación de datos y la implementación de controles para evitar errores.

3. **Automatización**:

   1. Permiten automatizar tareas recurrentes, como actualizaciones masivas, generación de reportes, limpieza de datos antiguos o cálculo de métricas.

   2. Cuando se combinan con eventos programados, las rutinas son una herramienta poderosa para la planificación de tareas sin intervención manual.

4. **Mantenimiento centralizado**:

   1. Los cambios en la lógica se pueden realizar directamente en el servidor, sin necesidad de modificar múltiples aplicaciones o scripts que interactúen con la base de datos.

### 1.2. Aplicación práctica para un DBA en la Automatización de Tareas

Un **Administrador de Bases de Datos (DBA)** utiliza las rutinas principalmente para automatizar y simplificar la administración diaria del sistema. Algunas aplicaciones comunes incluyen:

1. **Limpieza y Mantenimiento de Datos**

    **Ejemplo**: Creación de un procedimiento para eliminar registros obsoletos:

    ```sql
    CREATE PROCEDURE limpiar_registros()
    BEGIN
        DELETE FROM logs WHERE fecha < DATE_SUB(CURDATE(), INTERVAL 90 DAY);
    END;
    ```

    Un DBA podría combinar este procedimiento con un evento para ejecutarlo automáticamente cada semana:

    ```sql
    CREATE EVENT limpiar_logs
    ON SCHEDULE EVERY 7 DAY
    DO CALL limpiar_registros();
    ```

2. **Gestión de Reportes Periódicos**

    Los procedimientos pueden generar informes directamente desde la base de datos. Por ejemplo:

    ```sql
    CREATE PROCEDURE generar_reporte_ventas(fecha_inicio DATE, fecha_fin DATE)
    BEGIN
        SELECT producto, SUM(cantidad) AS total_vendido
        FROM ventas
        WHERE fecha BETWEEN fecha_inicio AND fecha_fin
        GROUP BY producto;
    END;
    ```

3. **Validación y Transformación de Datos**

    Las funciones permiten aplicar reglas de validación en tiempo real. Por ejemplo:

    ```sql
    CREATE FUNCTION validar_email(email VARCHAR(255)) RETURNS BOOLEAN
    BEGIN
        RETURN email LIKE '%_@_%._%';
    END;
    ```

4. **Automatización de Copias de Seguridad**

    Aunque las copias de seguridad suelen gestionarse fuera de MySQL, un DBA podría programar un procedimiento para volcar datos importantes en una tabla temporal antes de una operación crítica.

## 2. Rutinas: procedimientos y funciones

Las rutinas son un conjunto **de comandos SQL almacenados en el servidor**. De esta forma, un usuario puede ejecutar ese conjunto de comandos de una sola vez en lugar de tener que ejecutarlos de manera independiente.

¿Qué diferencia a los **procedimientos** y a las **funciones**?

- Las funciones devuelven un solo valor, mientras que los procedimientos pueden devolver varios o ninguno.

- Las sentencias `SELECT` que se emplean dentro de una función no son mostradas al terminar la ejecución de la misma; mientras que en los procedimientos sí se muestran, salvo las del tipo `SELECT...INTO` qué almacenan la salida en variables.

- La forma de invocarlos: mientras que la función se llama mediante: `SELECT nombre_func`, el procedimiento se llama utilizando `CALL nombre_proc`. Hay que recordar que phpMyAdmin no admite el uso de la sentencia `CALL`, lo que impide ejecutar procedimientos.

- A diferencia de los procedimientos almacenados, las funciones almacenadas se pueden utilizar en expresiones y pueden incluirse en otras funciones o procedimientos, así como en el interior de sentencias SQL como `SELECT`, `UPDATE`, `DELETE` e `INSERT`.

### 2.1. Creación de Procedimientos y Funciones

La sintaxis completa para la creación de un procedimiento o una función es la siguiente:

```sql
CREATE
    [DEFINER = user]
    PROCEDURE [IF NOT EXISTS] sp_name ([proc_parameter[,...]])
    [characteristic ...] routine_body

CREATE
    [DEFINER = user]
    FUNCTION [IF NOT EXISTS] sp_name ([func_parameter[,...]])
    RETURNS type
    [characteristic ...] routine_body

proc_parameter:
    [ IN | OUT | INOUT ] param_name type

func_parameter:
    param_name type

type:
    Any valid MySQL data type

characteristic: {
    COMMENT 'string'
  | LANGUAGE SQL
  | [NOT] DETERMINISTIC
  | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
  | SQL SECURITY { DEFINER | INVOKER }
}

routine_body:
    SQL routine
```

En su sintaxis más básica, este sería un **ejemplo de procedimiento**:

```sql
DELIMITER //
CREATE PROCEDURE nombre_procedimiento(param1 Tipo, param2 Tipo)
BEGIN
    -- Bloque de instrucciones
END //
DELIMITER ;
```

Como vemos, el procedimiento comienza a definirse mediante `CREATE PROCEDURE`. A continuación, vemos que el procedimiento recibe un **nombre** (descriptivo, que indica qué realiza) y, posteriormente, encerrado entre paréntesis, una lista de **parámetros**, que son datos proporcionados al procedimiento para realizar su cometido.

Luego nos encontramos con la palabra reservada `BEGIN`, que indicaría el inicio del bloque de instrucciones que incluye nuestro procedimiento, y, tras estas, la palabra `END`, seguida del delimitador que hayamos configurado antes de crear el procedimiento.

*Nota: **Por qué usar `DELIMITER` en procedimientos almacenados***

*Por defecto, MySQL utiliza ‘`;`’ como delimitador para identificar el final de una instrucción SQL. Sin embargo, cuando estás creando un procedimiento o función, el cuerpo del procedimiento puede contener múltiples instrucciones SQL, y MySQL necesita saber que todas esas instrucciones forman parte de la definición del procedimiento, no comandos independientes.*

*Para resolver esto, se utiliza el comando `DELIMITER` para **cambiar temporalmente el delimitador** a algo distinto, como `//` o cualquier otra secuencia que no sea conflictiva, mientras se define el procedimiento. Al final de todo, se reestablece el delimitador al ‘`;`’.*

Ejemplo básico: Procedimiento para insertar un estudiante en la tabla `estudiantes`:

```sql
CREATE PROCEDURE insertar_estudiante(
    IN nombreEstudiante VARCHAR(100),
    IN correoEstudiante VARCHAR(100),
    IN fecha DATE
)
BEGIN
    INSERT INTO estudiantes (nombre, correo, fecha_matricula)
    VALUES (nombreEstudiante, correoEstudiante, fecha);
END;
```

El ejemplo anterior es simplemente demostrativo, ya que no tiene sentido crear un procedimiento para realizar una inserción, al menos que hagamos otras operaciones (por ejemplo, validación de datos o transformaciones previas). El procedimiento lleva por nombre insertar\_estudiante y tiene 3 parámetros (todos de tipo IN, es decir, de entrada, de los cuales podremos leer información, pero no escribir en ella). El primero tiene como nombre nombreEstudiante y es de tipo VARCHAR(100); el segundo tiene como nombre correoEstudiante  y es de tipo VARCHAR(100); y el tercero lleva por nombre fecha y es de tipo DATE. A ellos haremos referencia dentro del bloque **BEGIN ... EN**, como vemos, en una sentencia **INSERT**.

Por su parte, en su sintaxis más básica, este sería un **ejemplo de función:**

```sql
DELIMITER //
CREATE FUNCTION nombre_funcion(param Tipo) RETURNS Tipo
BEGIN
    -- Bloque de instrucciones
    RETURN valor;
END //

DELIMITER ;
```

### 2.2. Parámetros de procedimientos y funciones

Los **parámetros** permiten al procedimiento recibir y/o devolver información. Y pueden ser:

- De entrada: **`IN`**  
- De salida: **`OUT`**  
- De entrada/salida: **`INOUT`**

Para definir cada **parámetro** se sigue el siguiente formato:

```sql
[IN | OUT | INOUT] NombreParámetro Tipo
```

- **`IN`**: el procedimiento recibe el parámetro y no lo modifica. Lo usa para consultar y utilizar su valor.  
- **`OUT`**: el procedimiento únicamente puede escribir en el parámetro, no puede consultarlo.  
- **`INOUT`**: el procedimiento recibe el parámetro y puede consultarlo y modificarlo.

Los parámetros **`OUT`** o **`INOUT`** se usan cuando se desea que un procedimiento nos devuelva valores en determinadas variables, esto es, los parámetros de salida permiten simular que el procedimiento devuelve valores.

- Es obligatorio escribir una lista de parámetros, aunque sea una lista vacía, reflejada con **`( )`**.  
- Por defecto cada parámetro es de tipo **`IN`**. Si queremos especificar otro tipo se escribe delante del nombre del parámetro.

**`NombreParámetro:`** es el nombre que tendrá el parámetro y con el que nos referiremos a él en el cuerpo de la rutina.

**`Tipo`**: es el Tipo de datos devuelto, puede ser cualquier tipo de datos válido de MySQL(**`INT, DATE, CHAR, VARCHAR`**, etc).

**Ejemplo de procedimiento con validación de Usuario:**

Este procedimiento valida si un usuario existe y actualiza su último acceso. Usa:

- **`IN`**: Recibe el nombre del usuario.  
- **`OUT`**: Devuelve un mensaje indicando si el usuario existe o no.  
- **`INOUT`**: Actualiza la última fecha de acceso.

```sql
DELIMITER //
CREATE PROCEDURE validar_usuario(
    IN nombre_usuario VARCHAR(100),
    OUT mensaje VARCHAR(255),
    INOUT ultima_visita DATETIME
)
BEGIN
    -- Verificar si el usuario existe
    IF EXISTS (SELECT 1 FROM usuarios WHERE nombre = nombre_usuario) THEN
        -- Usuario encontrado, actualizar última visita
        UPDATE usuarios
        SET ultima_acceso = ultima_visita
        WHERE nombre = nombre_usuario;

        SET mensaje = 'Usuario encontrado y actualizado.';
    ELSE
        -- Usuario no encontrado
        SET mensaje = 'Usuario no encontrado.';
        SET ultima_visita = NULL;
    END IF;
END //

DELIMITER ;
```

**Uso del procedimiento:**

```sql
-- Definir una variable para la última visita y el mensaje
SET @ultima_visita = NOW();
SET @mensaje = '';

-- Llamar al procedimiento
CALL validar_usuario('Juan Pérez', @mensaje, @ultima_visita);

-- Ver los resultados
SELECT @mensaje AS Mensaje, @ultima_visita AS UltimaVisita;
```

**Salida esperada (usuario encontrado):**

```plaintext
Mensaje                     | UltimaVisita
----------------------------|------------------------
Usuario encontrado y actualizado. | 2024-12-20 12:34:56
```

**Salida esperada (usuario no encontrado)**:

```plaintext
Mensaje                     | UltimaVisita
----------------------------|------------------------
Usuario no encontrado.       | NULL
```

### 2.3. Sección de características

En la **sección de características** se puede especificar la siguiente información:

```sql
characteristic: {
    COMMENT 'string'
  | LANGUAGE SQL
  | [NOT] DETERMINISTIC
  | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
  | SQL SECURITY { DEFINER | INVOKER }
}
```

- **`LANGUAGE SQL`** significa que el cuerpo del procedimiento está escrito en SQL. Por defecto se tiene esa característica para prever la posible construcción de procedimientos almacenados con otros lenguajes, como Java.  
- **`DETERMINISTIC / NOT DETERMINISTIC.`** El procedimiento se considera “determinista” si siempre produce el mismo resultado para los mismos parámetros de entrada, y “no determinista” si no es así. Por defecto es **`NOT DETERMINISTIC`**.  
- **`SQL SECURITY`** sirve especificar si el procedimiento es llamado, usando los permisos del usuario que lo creó (**`DEFINER`**, que es el valor por defecto), o usando los permisos del usuario que está haciendo la llamada (**`INVOKER`**).  
- **`COMMENT`** se usa para escribir el comentario que aparecerá cuando se ejecute una sentencia para ver el contenido de un procedimiento o de una función con:

**`SHOW CREATE PROCEDURE` o `SHOW CREATE FUNCTION`**

Las cláusulas de la sección de características tienen como **valores predeterminados** los siguientes:

- **`LANGUAGE SQL`**  
- **`NOT DETERMINISTIC`**
- **`SQL SECURITY DEFINER`**
- **`COMMENT ''`**

### 2.4. Cuerpo de las rutinas

Entendemos por el cuerpo de la rutina al conjunto de sentencias y operaciones realizadas entre las palabras `BEGIN` y `END` de un procedimiento o función.

Además de sentencias SQL, podremos utilizar otras estructuras como **bucles** y **condiciones**. Además, podemos utilizar **variables** y otras estructuras de SQL, como los **cursores**. Con todas estas herramientas, podremos programar el comportamiento de dicha rutina para que realice la tarea de nuestro interés.

#### 2.4.1. Concepto de Variable y su Uso

Una variable es un espacio en memoria que se utiliza para almacenar temporalmente valores que se usarán dentro del procedimiento o función.

En MySQL, las variables locales deben declararse dentro de un bloque `BEGIN...END` usando el comando `DECLARE`.

```sql
DECLARE nombre_variable TIPO [DEFAULT valor];
```

**Ejemplo:**

```sql
DECLARE contador INT DEFAULT 0;
DECLARE mensaje VARCHAR(100) DEFAULT 'Inicio del proceso';
```

Los tipos de variables pueden ser `INT`, `DECIMAL`, `CHAR`, `VARCHAR`, `DATE`, etc. Las variables pueden tomar valores calculados mediante `SET` o directamente en una consulta SQL con `SELECT INTO`.

**Ejemplo con `SET`:**

```sql
SET contador = contador + 1;
SET mensaje = 'Proceso completado';
```

Las expresiones anteriores debemos interpretarlas de derecha a izquierda, y teniendo en cuenta que `=` es el operador de asignacion, que permite asignar (dar un valor) a una variable. No debemos verlo como un operador que comprueba si dos cosas son iguales. Concretamente, las lineas anteriores debemos leerlas como: "*calculo 'contador + 1' y el resultado se lo asigno a la variable contador*", o "*asigno a la variable mensaje el valor 'Proceso completado'* ".

**Ejemplo con `SELECT INTO`:**

```sql
SELECT COUNT(*) INTO contador FROM estudiantes WHERE fecha_matricula > '2023-01-01';
```

#### 2.4.2. Alcance de las Variables

El **alcance de una variable** se refiere al contexto dentro del cual una variable es accesible y válida. En MySQL, el alcance de una variable local está limitado al bloque en el que fue declarada (dentro de un procedimiento, función o evento). Una vez que se sale de ese bloque, la variable deja de existir.

**Características del Alcance:**

- Las variables declaradas con `DECLARE` solo existen dentro del cuerpo del procedimiento o función donde se definen.  
- Al salir del bloque `BEGIN...END`, las variables locales se eliminan automáticamente.

**Ejemplo de Variable con Alcance Local:**

```sql
DELIMITER //
CREATE PROCEDURE ejemplo_alcance()
BEGIN
    DECLARE contador INT DEFAULT 0; -- Variable local
    SET contador = contador + 1;    -- Operación permitida dentro del bloque
    SELECT contador;                -- Visible dentro del procedimiento
END //
DELIMITER ;

CALL ejemplo_alcance(); -- Salida: 1
```

#### 2.4.3. Estructuras de Control

Las estructuras de control permiten tomar decisiones dentro de un procedimiento o función. MySQL admite estructuras condicionales como `IF`, `CASE`, y bloques de control de flujo.

**IF-THEN-ELSE:** Se usa para ejecutar diferentes bloques de código dependiendo de una **condición**.

**Sintaxis:**

```sql
IF condición THEN
    -- Bloque de código
ELSEIF otra_condición THEN
    -- Otro bloque de código
ELSE
    -- Código alternativo
END IF;
```

**Ejemplo:**

```sql
IF contador > 10 THEN
    SET mensaje = 'Contador alto';
ELSE
    SET mensaje = 'Contador bajo';
END IF;
```

**CASE:** Alternativa compacta a `IF-THEN-ELSE`.

**Sintaxis:**

```sql
CASE
    WHEN condición1 THEN resultado1
    WHEN condición2 THEN resultado2
    ELSE resultado_defecto
END;
```

**Ejemplo:**

```sql
SET mensaje = CASE
    WHEN contador > 10 THEN 'Contador alto'
    WHEN contador = 10 THEN 'Contador exacto'
    ELSE 'Contador bajo'
END;
```

#### 2.4.4. ¿Cómo puedo definir las condiciones?

Las condiciones en MySQL se construyen utilizando expresiones lógicas que se evalúan como verdaderas o falsas. Estas expresiones pueden incluir:

- Comparaciones entre valores.
- Llamadas a funciones.
- Operadores lógicos.

Ejemplos de condiciones válidas:

```sql
IF cantidad > 10 THEN -- Comparación directa
    ...
END IF;

WHILE EXISTS (SELECT 1 FROM tabla WHERE estado = 'pendiente') DO -- Función EXISTS
    ...
END WHILE;

CASE
    WHEN stock < 0 THEN 'Sin stock' -- Evaluación condicional
    ELSE 'Stock disponible'
END;

```

Estas condiciones se podrán aplicar tanto en las estructuras de control como en las estructuras de repetición, condicionando la ejecución de los bucles.

**Operadores para Condiciones:**

- Operadores de Comparación: se utilizan para comparar valores numéricos, cadenas o fechas.

  | Operador | Descripción | Ejemplo |
  | ----- | ----- | ----- |
  | `=` | Igual a | `precio = 100` |
  | `!=` | Diferente | `cantidad != 5` |
  | `<` | Menor que | `edad < 18` |
  | `>` | Mayor que | `ventas > 1000` |
  | `<=` | Menor o igual que | `fecha <= '2024-01-01'` |
  | `>=` | Mayor o igual que | `calificacion >= 6` |
  | `<=>` | Igual, considerando `NULL` | `valor <=> NULL` |

- Operadores Lógicos. permiten combinar varias condiciones en una expresión.

  | `AND` | Verdadero si ambas lo son | `cantidad > 0 AND stock > 0` |
  | :---- | :---- | :---- |
  | `OR` | Verdadero si una lo es | `precio < 50 OR descuento > 0` |
  | `NOT` | Niega la condición | `NOT (cantidad > 10)` |
  | `XOR` | Verdadero si una, pero no ambas | `ventas > 100 XOR devoluciones > 5` |

- Operadores de Comparación Avanzada:
  - BETWEEN ... AND: Verifica si un valor está en un rango.

    ```sql
    IF fecha BETWEEN '2024-01-01' AND '2024-12-31' THEN ...
    ```

  - IN: Comprueba si un valor pertenece a un conjunto.

    ```sql
    IF estado IN ('pendiente', 'completado') THEN ...
    ```

  - LIKE y NOT LIKE: Comparación con patrones.

    ```sql
    IF nombre LIKE 'A%' THEN ... -- Empieza con 'A'
    ```

  - IS NULL y IS NOT NULL: Verifica valores nulos.

    ```sql
    IF direccion IS NULL THEN
    ```

#### 2.4.5. Estructuras Repetitivas

Las estructuras repetitivas se usan para ejecutar un bloque de código varias veces. MySQL admite tres tipos principales: `WHILE`, `LOOP` y `REPEAT`.

**WHILE:** Ejecuta un bloque de código mientras la condición sea verdadera.

**Sintaxis:**

```sql
WHILE condición DO
    -- Código a ejecutar
END WHILE;
```

**Ejemplo:**

```sql
DECLARE contador INT DEFAULT 1;
WHILE contador <= 5 DO
    INSERT INTO log_proceso (mensaje) VALUES (CONCAT('Iteración ', contador));
    SET contador = contador + 1;
END WHILE;
```

**LOOP:** Ejecuta un bloque de código indefinidamente hasta que se use una condición de salida (`LEAVE`).

**Sintaxis:**

```sql
[nombrebucle:] LOOP
    -- Código a ejecutar
    IF condición_salida THEN
        LEAVE nombrebucle;
    END IF;
END LOOP nombrebucle;
```

**Ejemplo:**

```sql
DECLARE contador INT DEFAULT 1;
nombre_bucle: LOOP
    INSERT INTO log_proceso (mensaje) VALUES (CONCAT('Iteración ', contador));
    SET contador = contador + 1;
    IF contador > 5 THEN
        LEAVE nombre_bucle;
    END IF;
END LOOP nombre_bucle;
```

**REPEAT:** Ejecuta el bloque de código **al menos una vez** y luego verifica la condición al final.

**Sintaxis:**

```sql
REPEAT
    -- Código a ejecutar
UNTIL condición
END REPEAT;
```

**Ejemplo:**

```sql
DECLARE contador INT DEFAULT 1;

REPEAT
    INSERT INTO log_proceso (mensaje) VALUES (CONCAT('Iteración ', contador));
    SET contador = contador + 1;
UNTIL contador > 5
END REPEAT;
```

A continuación se presenta un procedimiento que utiliza variables, estructuras de control y repetitivas para procesar datos en la tabla `ventas` y calcular totales:

```sql
DELIMITER //

CREATE PROCEDURE procesar_ventas()
BEGIN
    DECLARE total INT DEFAULT 0;
    DECLARE contador INT DEFAULT 0;

    -- Contar el total de registros
    SELECT COUNT(*) INTO total FROM ventas;

    -- Procesar cada registro
    nombre_bucle: WHILE contador < total DO
        SET contador = contador + 1;
        INSERT INTO log_proceso (mensaje) VALUES (CONCAT('Procesando registro ', contador));
    END WHILE;

    -- Mensaje final
    INSERT INTO log_proceso (mensaje) VALUES ('Proceso completado');
END //

DELIMITER ;
```

### 2.5. Privilegios y Seguridad en Rutinas

Para crear, modificar o ejecutar rutinas, los usuarios necesitan ciertos privilegios específicos:

- Privilegios para procedimientos y funciones:  
  - `CREATE ROUTINE`: Permite crear rutinas.  
  - `ALTER ROUTINE`: Permite modificar rutinas existentes.  
  - `EXECUTE`: Permite ejecutar rutinas creadas por otros.  
  - `DROP`: Permite eliminar rutinas.

Ejemplo de asignación de privilegios:

```sql
GRANT CREATE ROUTINE, EXECUTE ON universidad.* TO 'usuario'@'localhost';
```

### 2.6. Eliminación y Modificación de Rutinas

Para eliminar un procedimiento debemos utilizar la sentencia DROP:

```sql
DROP PROCEDURE IF EXISTS nombre_procedimiento;
DROP FUNCTION IF EXISTS nombre_funcion;
```

MySQL no permite modificar una rutina directamente, por lo que, si queremos hacer cambios en ella. debe eliminarse y volverse a crear.

## 3. Eventos en mysql

### 3.1. ¿Qué es un evento en MySQL?

Un evento en MySQL es una tarea programada que se ejecuta automáticamente en el servidor según una programación definida. Puede ser:

- **De ejecución única**: Se ejecuta solo una vez en un momento específico.  
- **Recurrente**: Se ejecuta de manera periódica en intervalos definidos.

### 3.2. Planificador de eventos

#### 3.2.1. ¿Qué es el planificador de eventos?

El planificador de eventos (`event_scheduler`) es un componente de MySQL que permite ejecutar estas tareas automatizadas. Es responsable de gestionar todos los eventos definidos en el servidor.

#### 3.2.2. Verificar el estado del planificador de eventos

Antes de trabajar con eventos, es necesario asegurarse de que el planificador esté habilitado. Puedes verificar su estado con el siguiente comando:

```sql
SHOW VARIABLES LIKE 'event_scheduler';
```

**Salida esperada**:

- `ON`: El planificador está habilitado y ejecutando eventos.  
- `OFF`: El planificador está deshabilitado.  
- `DISABLED`: El planificador está deshabilitado por completo (requiere reiniciar el servidor para cambiar este estado).

#### 3.2.3. Habilitar o deshabilitar el planificador de eventos

Puedes habilitar o deshabilitar el planificador dinámicamente o en la configuración del servidor.

1. **Habilitar/Deshabilitar dinámicamente**:

    Para habilitar el planificador:

    ```sql
    SET GLOBAL event_scheduler = ON;
    ```

    Para deshabilitarlo:

    ```sql
    SET GLOBAL event_scheduler = OFF;
    ```

    Hay que tener en cuenta que esta configuración se pierde si el servidor MySQL se reinicia.

2. **Habilitar/Deshabilitar de forma permanente**:

    Edita el archivo de configuración (`my.cnf` o `my.ini`) y añade:

    ```sql
    event_scheduler = ON
    ```

    Se debe reiniciar el servidor MySQL para aplicar los cambios.

#### 3.2.4. Consideraciones sobre el planificador de eventos

- El planificador consume recursos del servidor para ejecutar tareas, por lo que no es recomendable habilitarlo si no hay eventos definidos.  
- Es importante supervisar el uso de eventos recurrentes para evitar sobrecargar el servidor.

### 3.3. Creación de Eventos

#### 3.3.1. Sintaxis básica para crear eventos

La sintaxis completa para la creación de un evento en mysql es la siguiente:

```sql
CREATE
    [DEFINER = user]
    EVENT
    [IF NOT EXISTS]
    event_name
    ON SCHEDULE schedule
    [ON COMPLETION [NOT] PRESERVE]
    [ENABLE | DISABLE | DISABLE ON SLAVE]
    [COMMENT 'string']
    DO event_body;

schedule: {
    AT timestamp [+ INTERVAL interval] ...
  | EVERY interval
    [STARTS timestamp [+ INTERVAL interval] ...]
    [ENDS timestamp [+ INTERVAL interval] ...]
}

interval:
    quantity {YEAR | QUARTER | MONTH | DAY | HOUR | MINUTE |
              WEEK | SECOND | YEAR_MONTH | DAY_HOUR | DAY_MINUTE |
              DAY_SECOND | HOUR_MINUTE | HOUR_SECOND | MINUTE_SECOND}
```

En su sintaxis más básica:

```sql
CREATE EVENT nombre_evento
ON SCHEDULE tipo_programacion
DO
    instruccion_sql;
```

**Partes clave**:

- **`nombre_evento`**: Nombre único del evento en la base de datos.  
- **`ON SCHEDULE`**: Define el momento y la frecuencia de ejecución.  
- **`DO`**: Contiene la instrucción SQL que se ejecutará.

#### 3.3.2. Tipos de programación

1. **Ejecución única**: se usa `AT` para definir una fecha y hora específica.

    ```sql
    CREATE EVENT evento_unico
    ON SCHEDULE AT '2024-01-15 10:00:00'
    DO
        DELETE FROM logs WHERE fecha < '2023-12-31';
    ```

2. **Ejecución recurrente**: se usa `EVERY` para definir un intervalo y opcionalmente un tiempo de inicio.

    ```sql
    CREATE EVENT evento_recurrente
    ON SCHEDULE EVERY 1 DAY
    STARTS '2024-01-01 00:00:00'
    ENDS '2024-12-31 23:59:59'
    DO
        DELETE FROM logs WHERE fecha < DATE_SUB(CURDATE(), INTERVAL 30 DAY);
    ```

**Nota**: Si no se especifica `STARTS`, el evento comienza inmediatamente.

#### 3.3.3. Opciones adicionales en la creación de eventos

1. **Habilitación/Deshabilitación del evento**: por defecto, un evento se crea habilitado (`ENABLE`), pero puedes deshabilitarlo con:

    ```sql
    CREATE EVENT nombre_evento
    ON SCHEDULE EVERY 1 HOUR
    DISABLE
    DO
        DELETE FROM logs WHERE fecha < CURDATE();
    ```

2. **Preservar el evento después de la ejecución**: por defecto, los eventos de ejecución única se eliminan tras ejecutarse (`ON COMPLETION NOT PRESERVE`).

    ```sql
    CREATE EVENT nombre_evento
    ON SCHEDULE AT '2024-01-15 10:00:00'
    ON COMPLETION PRESERVE
    DO
        DELETE FROM logs WHERE fecha < '2023-12-31';
    ```

#### 3.3.4. Verificar eventos creados

Los eventos en MySQL **se almacenan en el esquema del sistema** y puedes verlos utilizando comandos específicos o consultando las tablas adecuadas en el esquema **`information_schema`**. Los eventos definidos en una base de datos se guardan en la tabla **`EVENTS`** dentro del esquema del sistema **`information_schema`**. Esta tabla almacena toda la información sobre los eventos, como su nombre, estado, programación, y la última vez que se ejecutaron.

**Cómo listar y ver eventos creados:**

1. Usar `SHOW EVENTS`:  el comando `SHOW EVENTS` te permite listar todos los eventos creados en una base de datos específica.

    ```sql
    SHOW EVENTS FROM nombre_base_datos;
    ```

    **Salida esperada:**

    ```plaintext
    +-------------------+-----------------+---------+------------+-------------+-----------+
    | Db                | Name            | Definer | Time zone  | Type        | Status    |
    +-------------------+-----------------+---------+------------+-------------+-----------+
    | nombre_base_datos | limpiar_logs    | root@%  | SYSTEM     | RECURRING   | ENABLED   |
    | nombre_base_datos | reporte_semanal | root@%  | SYSTEM     | ONE TIME    | COMPLETED |
    +-------------------+-----------------+---------+------------+-------------+-----------+
    ```

    - **`Db`**: Base de datos donde está definido el evento.  
    - **`Name`**: Nombre del evento.  
    - **`Type`**: Si es de ejecución única (`ONE TIME`) o recurrente (`RECURRING`).  
    - **`Status`**: Estado actual del evento (`ENABLED`, `DISABLED`, `COMPLETED`).

2. Consultar la tabla `information_schema.EVENTS`: si necesitas más detalles sobre los eventos, puedes consultar directamente la tabla **`information_schema.EVENTS`**.

    ```sql
    SELECT EVENT_NAME, EVENT_DEFINITION, STATUS, STARTS, ENDS, LAST_EXECUTED
    FROM information_schema.EVENTS
    WHERE EVENT_SCHEMA = 'nombre_base_datos';
    ```

    **Salida esperada:**

    ```plaintext
    +-----------------+-------------------------+-----------+---------------------+---------+---------------------+
    | EVENT_NAME      | EVENT_DEFINITION        | STATUS    | STARTS              | ENDS    | LAST_EXECUTED       |
    +-----------------+-------------------------+-----------+---------------------+---------+---------------------+
    | limpiar_logs    | DELETE FROM logs ...    | ENABLED   | 2024-01-01 00:00:00 | NULL    | 2024-01-08 00:00:00 |
    | reporte_semanal | CALL generar_reporte(); | COMPLETED | NULL                | NULL    | 2024-01-07 23:59:59 |
    +-----------------+-------------------------+-----------+---------------------+---------+---------------------+
    ```

**Columnas importantes**:

- **`EVENT_NAME`**: Nombre del evento.  
- **`EVENT_DEFINITION`**: La instrucción SQL que ejecuta el evento.  
- **`STATUS`**: Estado del evento (`ENABLED`, `DISABLED`, o `COMPLETED`).  
- **`STARTS`** y **`ENDS`**: Momentos de inicio y fin de la programación.  
- **`LAST_EXECUTED`**: Última vez que se ejecutó el evento.

Puedes filtrar eventos según su estado o programación. Por ejemplo, listar sólo los eventos activos:

```sql
SELECT EVENT_NAME, STATUS, LAST_EXECUTED
FROM information_schema.EVENTS
WHERE EVENT_SCHEMA = 'nombre_base_datos' AND STATUS = 'ENABLED';
```

Hay que tener en cuenta que:

- Cada base de datos puede tener sus propios eventos definidos.  
- Los eventos no son compartidos entre bases de datos; están asociados exclusivamente a la base de datos donde se crean.

#### 3.3.5. Ejemplo práctico

Un evento recurrente que limpia registros antiguos cada semana:

```sql
CREATE EVENT limpiar_logs_semanal
ON SCHEDULE EVERY 1 WEEK
STARTS '2024-01-01 00:00:00'
DO
    DELETE FROM logs WHERE fecha < DATE_SUB(CURDATE(), INTERVAL 90 DAY);
```

Para verificar su creación:

```sql
SHOW EVENTS FROM nombre_base_datos;
```

### 3.4. Modificación de Eventos

Los eventos en MySQL pueden modificarse usando el comando **`ALTER EVENT`**. Este comando permite cambiar cualquier aspecto del evento, como su programación, estado, o incluso la instrucción que ejecuta.

#### 3.4.1. Sintaxis básica de ALTER EVENT

```sql
ALTER EVENT nombre_evento
[ON SCHEDULE nuevo_horario]
[RENAME TO nuevo_nombre]
[ENABLE | DISABLE]
[DO nueva_instruccion];
```

#### 3.4.2. Opciones disponibles para modificar un evento

**Cambiar la programación (`ON SCHEDULE`)**: Puedes modificar la hora o frecuencia de ejecución del evento.

```sql
ALTER EVENT limpiar_logs
ON SCHEDULE EVERY 1 MONTH
STARTS '2024-02-01 00:00:00';
```

**Cambiar el nombre del evento (`RENAME TO`)**: Si necesitas renombrar un evento:

```sql
ALTER EVENT limpiar_logs
RENAME TO limpiar_logs_mensual;
```

**Habilitar o deshabilitar un evento (`ENABLE` o `DISABLE`)**:

1. **`ENABLE`**: Activa el evento para que se ejecute según su programación.  
2. **`DISABLE`**: Desactiva el evento, deteniendo su ejecución.

```sql
ALTER EVENT limpiar_logs DISABLE;
```

**Cambiar la instrucción que ejecuta el evento (`DO`)**: Modifica la lógica que se ejecuta dentro del evento.

```sql
ALTER EVENT limpiar_logs
DO
    DELETE FROM logs WHERE fecha < DATE_SUB(CURDATE(), INTERVAL 60 DAY);
```

#### 3.4.3. Ejemplo completo: Modificar un evento

Supongamos que tienes un evento que borra registros antiguos cada semana. Ahora quieres:

- Cambiar su frecuencia a una vez al mes.  
- Actualizar la instrucción para conservar registros más antiguos.

**Antes (definición original del evento):**

```sql
CREATE EVENT limpiar_logs
ON SCHEDULE EVERY 1 WEEK
DO
    DELETE FROM logs WHERE fecha < DATE_SUB(CURDATE(), INTERVAL 30 DAY);
```

**Modificación:**

```sql
ALTER EVENT limpiar_logs
ON SCHEDULE EVERY 1 MONTH
DO
    DELETE FROM logs WHERE fecha < DATE_SUB(CURDATE(), INTERVAL 90 DAY);
```

**Resultado esperado:** El evento ahora se ejecutará mensualmente y conservará registros de hasta 90 días de antigüedad.

### 3.5. Eliminación de Eventos

Cuando un evento ya no es necesario, puedes eliminarlo del sistema utilizando el comando **`DROP EVENT`**.

#### 3.5.1. Sintaxis básica de `DROP EVENT`

```sql
DROP EVENT [IF EXISTS] nombre_evento;
```

**`IF EXISTS`**: Evita errores si el evento no existe.

#### 3.5.2. Ejemplo básico

Eliminar un evento llamado `limpiar_logs`:

```sql
DROP EVENT limpiar_logs;
```

Si el evento no existe, el comando generará un error. Para evitar esto:

```sql
DROP EVENT IF EXISTS limpiar_logs;
```

#### 3.5.3. Consideraciones importantes al eliminar eventos

1. **Impacto en procesos automatizados**:  
   - Antes de eliminar un evento, asegúrate de que ninguna operación dependiente quede afectada.  
   - Revisa la tabla **`information_schema.EVENTS`** para confirmar el propósito del evento.  
2. **Eliminación permanente**:  
   - Una vez eliminado, no se puede recuperar el evento ni su programación. Si crees que puede ser necesario en el futuro, considera deshabilitarlo en lugar de eliminarlo:

    ```sql
    ALTER EVENT nombre_evento DISABLE;
    ```

### 3.6. Privilegios Relacionados con Eventos

Para trabajar con eventos en MySQL, los usuarios deben tener ciertos privilegios específicos, además de permisos generales para las bases de datos afectadas.

#### 3.6.1. Privilegios necesarios

1. **`EVENT`**:  
   - Permite al usuario crear, modificar y eliminar eventos en una base de datos.  
   - Este privilegio debe asignarse explícitamente.

    ```sql
    GRANT EVENT ON nombre_base_datos.* TO 'usuario'@'localhost';
    ```

2. **`CREATE` y `ALTER` en las tablas afectadas**:  
   - Si el evento modifica datos en una tabla, el usuario también necesita permisos para operar en esas tablas (por ejemplo, `INSERT`, `UPDATE`, `DELETE`).  

3. **`SUPER` (en casos avanzados)**:  
   - Es necesario si un evento utiliza privilegios elevados o modifica variables globales.

#### 3.6.2. Verificar privilegios de un usuario

Como recordatorio, para verificar los privilegios actuales de un usuario:

```sql
SHOW GRANTS FOR 'usuario'@'localhost';
```

#### 3.6.3. Restricciones de seguridad

1. **Eventos creados por usuarios específicos**:
   - Los eventos están asociados al "definer" (creador del evento). Si el usuario que creó el evento pierde sus privilegios, el evento puede dejar de funcionar. Revisa el campo **`DEFINER`** en `information_schema.EVENTS` para identificar al creador:

    ```sql
    SELECT EVENT_NAME, DEFINER FROM information_schema.EVENTS WHERE EVENT_SCHEMA = 'nombre_base_datos';
    ```

2. **Revocar privilegios**: Si necesitas evitar que un usuario administre eventos, puedes revocar el privilegio `EVENT`:

    ```sql
    REVOKE EVENT ON nombre_base_datos.* FROM 'usuario'@'localhost';
    ```

### 3.7. Consideraciones de Seguridad y Rendimiento en Eventos

El uso de eventos en MySQL puede tener un impacto significativo en la seguridad y el rendimiento del servidor. Una gestión adecuada ayuda a garantizar que los eventos no comprometan la integridad de los datos ni sobrecarguen el sistema.

#### 3.7.1. Consideraciones de Seguridad

**Evita privilegios excesivos**:

- Los eventos heredan los privilegios del usuario que los define (**`DEFINER`**).  
- Asegúrate de que el usuario **definer** tenga solo los permisos necesarios para la tarea del evento. Revisa el campo **`DEFINER`** en `information_schema.EVENTS`:

    ```sql
    SELECT EVENT_NAME, DEFINER FROM information_schema.EVENTS WHERE EVENT_SCHEMA = 'nombre_base_datos';
    ```

**Restricción de acceso a eventos**: Solo asigna el privilegio `EVENT` a usuarios que realmente necesiten crear o administrar eventos.

**Validación de instrucciones SQL en eventos**:

- Asegúrate de que las instrucciones dentro de los eventos sean seguras y no permitan inyecciones SQL.  
- Usa variables o valores controlados en las consultas.

#### 3.7.2. Consideraciones de Rendimiento

1. **Impacto de eventos recurrentes**:  
   - Eventos que se ejecutan con demasiada frecuencia (por ejemplo, cada segundo) pueden sobrecargar el servidor.  
   - Usa intervalos razonables (`EVERY 1 HOUR`, `EVERY 1 DAY`) para minimizar el impacto.  
2. **Uso eficiente de recursos**:  
   - Evita que los eventos realicen operaciones complejas o que bloqueen tablas por largos períodos.  
   - Opta por operaciones por lotes si el evento afecta grandes cantidades de datos.  
3. **Planificador de eventos (`event_scheduler`)**:  
   - El planificador debe estar habilitado solo si hay eventos configurados.  
   - Monitoriza su uso y ajusta la configuración si observas un impacto negativo en el rendimiento.  
4. **Supervisión de eventos en ejecución**:  
   - Usa la columna **`LAST_EXECUTED`** en `information_schema.EVENTS` para verificar si los eventos se están ejecutando correctamente.  
   - Identifica retrasos en la ejecución o problemas con eventos deshabilitados.

### 3.8. Ejemplos Prácticos de Uso de Eventos

Los eventos en MySQL tienen aplicaciones prácticas en una variedad de escenarios. A continuación se presentan algunos ejemplos para diferentes casos de uso:

#### 3.8.1. Limpieza Automática de Registros Antiguos

Este evento elimina registros de la tabla `logs` que sean más antiguos de 90 días. Se ejecuta automáticamente cada semana.

**Definición del evento:**

```sql
CREATE EVENT limpiar_logs_semanal
ON SCHEDULE EVERY 1 WEEK
STARTS '2024-01-01 00:00:00'
DO
    DELETE FROM logs WHERE fecha < DATE_SUB(CURDATE(), INTERVAL 90 DAY);
```

**Verificación del evento:**

```sql
SHOW EVENTS FROM nombre_base_datos;
```

#### 3.8.2. Generación de Informes Periódicos

Un evento que ejecuta un procedimiento para generar un informe semanal y guarda los resultados en la tabla `reportes`.

**Definición del procedimiento:**

```sql
CREATE PROCEDURE generar_reporte()
BEGIN
    INSERT INTO reportes (fecha_generacion, total_ventas)
    SELECT CURDATE(), SUM(importe) FROM ventas WHERE fecha = CURDATE();
END;
```

**Definición del evento:**

```sql
CREATE EVENT reporte_semanal
ON SCHEDULE EVERY 1 WEEK
STARTS '2024-01-01 00:00:00'
DO
    CALL generar_reporte();
```

#### 3.8.3. Reseteo Automático de una Tabla Temporal

Un evento que vacía la tabla `temp_sesiones` cada noche para liberar espacio y mantenerla limpia.

**Definición del evento:**

```sql
CREATE EVENT limpiar_sesiones
ON SCHEDULE EVERY 1 DAY
STARTS '2024-01-01 02:00:00'
DO
    TRUNCATE TABLE temp_sesiones;
```

Como recordatorio, la sentencia `TRUNCATE` vacía por completo una tabla (requiere de permisos de eliminación 'DROP'), y seróia equivalente a la secuencia `DROP TABLE` y `CREATE TABLE`.

#### 3.8.4. Deshabilitación Temporal de Eventos

Un DBA deshabilita temporalmente un evento mientras realiza tareas de mantenimiento.

**Comando para deshabilitar:**

```sql
ALTER EVENT limpiar_logs_semanal DISABLE;
```

**Comando para habilitar nuevamente:**

```sql
ALTER EVENT limpiar_logs_semanal ENABLE;
```

## 4. Introducción a los Disparadores

### 4.1. ¿Qué son los disparadores?

Un **disparador (trigger)** es una rutina almacenada en el servidor MySQL que se ejecuta automáticamente en respuesta a un evento específico en una tabla. Estos eventos pueden ser:

- **`INSERT`**: Cuando se inserta una nueva fila.  
- **`UPDATE`**: Cuando se modifica una fila existente.  
- **`DELETE`**: Cuando se elimina una fila.

Los disparadores están diseñados para operar **por cada fila** afectada por el evento. Esto significa que, en una operación que afecta múltiples filas, el disparador se ejecutará tantas veces como filas estén involucradas.

**¿Cuándo se usan los disparadores?**

Los disparadores son útiles para automatizar tareas y garantizar la integridad de los datos. Algunos casos comunes incluyen:

1. **Auditoría de datos**:  
   - Registrar automáticamente cambios realizados en una tabla (por ejemplo, quién y cuándo modificó una fila).  
2. **Sincronización de tablas**:  
   - Actualizar automáticamente una tabla secundaria cuando se realizan cambios en la tabla principal.  
3. **Validación de datos**:  
   - Evitar que se inserten datos inválidos o inconsistentes.  
4. **Lógica de negocio**:  
   - Implementar reglas específicas del negocio que deban ejecutarse automáticamente.

**Ventajas y desventajas de los disparadores:**

| Ventajas | Desventajas |
| ----- | ----- |
| Automatizan tareas repetitivas. | Dificultan la depuración de errores si son complejos. |
| Garantizan consistencia y reglas del negocio. | Pueden impactar el rendimiento en tablas grandes. |
| Son invisibles para las aplicaciones externas. | Aumentan la complejidad si no se documentan bien. |

### 4.2. Creación de Disparadores

En su sintaxis más simple, esta sería la forma de crear un disparador en mysql:

```sql
CREATE TRIGGER nombre_disparador
{BEFORE | AFTER} {INSERT | UPDATE | DELETE}
ON nombre_tabla
FOR EACH ROW
BEGIN
    -- Instrucciones SQL que ejecuta el disparador
END;
```

**Descripción de los componentes:**

1. **`nombre_disparador`**:  
   - Nombre único para el disparador dentro de la base de datos y tabla.  
2. **`BEFORE` o `AFTER`**:  
   - **`BEFORE`**: Se ejecuta **antes** de que se aplique el cambio en la tabla.  
     - Ideal para validaciones o cálculos previos.  
   - **`AFTER`**: Se ejecuta **después** de que el cambio ha sido aplicado.  
     - Útil para registrar cambios o sincronizar tablas.  
3. **`INSERT`, `UPDATE`, `DELETE`**:  
   - Evento que activa el disparador.  
   - Cada disparador puede estar asociado a **un solo evento**.  
4. **`ON nombre_tabla`**:  
   - Tabla en la que se define el disparador.  
5. **`FOR EACH ROW`**:  
   - Indica que el disparador se ejecutará una vez por cada fila afectada.  
6. **Pseudotablas (`NEW` y `OLD`)**:  
   - **`NEW`**: Contiene los valores nuevos (solo disponible en `INSERT` y `UPDATE`).  
   - **`OLD`**: Contiene los valores antiguos (solo disponible en `DELETE` y `UPDATE`).

A continuación, se presentan algunos ejemplos de disparadores:

**Ejemplo 1: Auditoría de cambios en una tabla.**

Registrar automáticamente los cambios realizados en la tabla `clientes`.

```sql
CREATE TRIGGER auditoria_actualizacion_cliente
AFTER UPDATE
ON clientes
FOR EACH ROW
BEGIN
    INSERT INTO auditoria_clientes (id_cliente, accion, fecha_cambio, detalle_cambio)
    VALUES (OLD.id_cliente, 'UPDATE', NOW(),
            CONCAT('Nombre cambiado de ', OLD.nombre, ' a ', NEW.nombre));
END;
```

- **Propósito**: registra quién actualizó un cliente y detalla los cambios realizados.

**Ejemplo 2: Validación previa a una operación.**

Evitar que se inserten productos con precios negativos en la tabla `productos`.

```sql
CREATE TRIGGER validar_precio_producto
BEFORE INSERT
ON productos
FOR EACH ROW
BEGIN
    IF NEW.precio < 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'El precio del producto no puede ser negativo';
    END IF;
END;
```

- **Propósito**: garantiza que no se ingresen datos inválidos en la tabla.

**Ejemplo 3: Sincronización entre tablas.**

Actualizar automáticamente el inventario cuando se realiza una venta.

```sql
CREATE TRIGGER actualizar_inventario
AFTER INSERT
ON ventas
FOR EACH ROW
BEGIN
    UPDATE inventario
    SET cantidad = cantidad - NEW.cantidad
    WHERE id_producto = NEW.id_producto;
END;
```

- **Propósito**: sincroniza la tabla `inventario` tras cada inserción en la tabla `ventas`.

#### 4.2.1. Consideraciones al crear disparadores

1. **Cantidad de disparadores por tabla**:  
   - Una tabla puede tener **un solo disparador por tipo de evento y momento**. Ejemplo:  
     - `BEFORE INSERT`  
     - `AFTER INSERT`  
     - `BEFORE UPDATE`, etc.  
2. **Órdenes dentro del disparador**:  
   - Los disparadores no pueden ejecutar **`COMMIT`**, **`ROLLBACK`** o instrucciones que modifiquen el estado de la transacción.  
3. **Evitar ciclos de disparadores**:  
   - Un disparador no debe causar la ejecución de otro disparador que produzca un ciclo infinito.

#### 4.2.2. Errores comunes al crear disparadores

**Falta de delimitadores**: los disparadores contienen bloques `BEGIN...END`, lo que requiere cambiar el delimitador antes de crearlos, como hemos visto con la creación de funciones y procedimientos.

**Confundir `NEW` y `OLD`**: Usar pseudotablas incorrectamente, como intentar acceder a `OLD` en un `INSERT`. Estas son las combinaciones posibles

| Acción | Pseudotabla | Descripción |
| ----- | ----- | ----- |
| `INSERT` | `NEW` | Contiene los valores de las nuevas filas que se están insertando. |
| `UPDATE` | `NEW` | Contiene los valores de las nuevas filas después de la actualización. |
| `UPDATE` | `OLD` | Contiene los valores de las filas antes de la actualización. |
| `DELETE` | `OLD` | Contiene los valores de las filas que se están eliminando. |

**Ausencia de permisos**: Asegúrate de que el usuario tiene el privilegio **`TRIGGER`**:

```sql
GRANT TRIGGER ON nombre_base_datos.* TO 'usuario'@'localhost';
```

### 4.3. Modificación, eliminación y muestra de disparadores

Podemos comprobar qué disparadores tiene una base de datos mediante la sentencia

```sql
SHOW TRIGGERS
    [{FROM | IN} db_name]
    [LIKE 'pattern' | WHERE expr]
```

Podemos filtrar los triggers haciendo uso de la expresion **LIKE** 'pattern', donde 'pattern' servirá para indicar el nombre de las tablas afectadas (no del propio trigger), o **WHERE** para filtrar por filas.

También lo podemos hacer mediante una consulta a la tabla TRIGGERS de information\_schema:

```sql
SELECT TRIGGER_NAME, EVENT_MANIPULATION, ACTION_STATEMENT
FROM information_schema.TRIGGERS
WHERE TRIGGER_SCHEMA = 'nombre_base_datos' AND EVENT_OBJECT_TABLE = 'nombre_tabla';
```

MySQL no proporciona una sentencia para modificar un disparador, por lo que tendremos que eliminarlo y volverlo a crear. Localizaremos el trigger que deseamos modificar mediante alguno de los métodos anteriores, y lo eliminaremos mediante la sentencia

```sql
DROP TRIGGER [IF EXISTS] nombre_disparador;
```

Luego podremos crearlo de nuevo haciendo los cambios que consideremos necesarios.

## 5. Gestión de Errores y Condiciones (Handlers)

### 5.1. Introducción a la Gestión de Errores

#### 5.1.1. Qué son las condiciones y los handlers

En MySQL, una **condición** es cualquier situación específica que puede ocurrir durante la ejecución de código SQL, como:

- **Errores** (división por cero, violación de clave única...)  
- **Advertencias** (truncamiento de datos, conversión de tipos...)  
- **Situaciones especiales** (no se encontraron más registros...)

Un **handler** (literalmente, manejador) es un bloque de código que especifica qué hacer cuando ocurre una condición determinada. Es similar al bloque try-catch en otros lenguajes de programación.

#### 5.1.2. Importancia del manejo de errores en bases de datos

El manejo adecuado de errores es crucial en bases de datos por varios motivos:

- **Integridad de datos**: Asegura que los datos permanezcan consistentes incluso cuando ocurren errores.

    ```sql
    -- Ejemplo: Transferencia bancaria
    BEGIN
        DECLARE error_found BOOLEAN DEFAULT FALSE;
        DECLARE CONTINUE HANDLER FOR SQLEXCEPTION SET error_found = TRUE;
        
        UPDATE cuentas SET saldo = saldo - 1000 WHERE id = 1;
        UPDATE cuentas SET saldo = saldo + 1000 WHERE id = 2;
        
        IF error_found THEN
            ROLLBACK;
            SELECT 'Error en la transferencia';
        ELSE
            COMMIT;
            SELECT 'Transferencia exitosa';
        END IF;
    END;
    ```

- **Experiencia de usuario**: Proporciona mensajes de error significativos en lugar de fallos catastróficos.  
- **Mantenibilidad**: Facilita la depuración y el diagnóstico de problemas.  
- **Robustez**: Hace que las aplicaciones sean más resistentes a condiciones inesperadas.

#### 5.1.3. Diferencia entre errores y advertencias en MySQL

**Errores**: Son condiciones graves que impiden que una operación se complete.

- Código de error positivo  
- Detienen la ejecución (si no se manejan)  
- Ejemplo: Error 1062 (Violación de clave duplicada)

**Advertencias**: Son condiciones menos graves que permiten que la operación continúe.

- No detienen la ejecución  
- Se pueden consultar con `SHOW WARNINGS`  
- Ejemplo: Truncamiento de datos en una inserción

### 5.2. Declaración y Sintaxis

#### 5.2.1. Estructura básica `DECLARE ... HANDLER`

La sintaxis básica para declarar un handler es:

```sql
DECLARE [tipo_acción] HANDLER 
FOR [condición(es)]
[bloque_de_código]
```

- **`tipo_acción`**: especifica qué debe hacer MySQL cuando encuentra la condición:
  - **CONTINUE**: Ejecuta el bloque `bloque_de_código` del handler y continúa con la ejecución normal:

    ```sql
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
        SET @error = 'Ha ocurrido un error';
    ```

  - **EXIT**: Ejecuta el bloque `bloque_de_código` del handler y termina la ejecución del bloque actual:

    ```sql
    DECLARE EXIT HANDLER FOR SQLEXCEPTION
    BEGIN
        ROLLBACK;
        SET @error = 'Error - operación cancelada';
    END;
    ```

- **`condición(es)`**: indicamos la condicion (excepción, advertencia o situación excepcional) que queremos gestionar. Puede especificarse de varias formas:
  - **Valor único**:

    ```sql
    -- Usando código de error específico
    DECLARE CONTINUE HANDLER FOR 1062 
        SET @mensaje = 'Registro duplicado';
    ```

  - **Lista de valores**:

    ```sql
    -- Múltiples códigos de error
    DECLARE CONTINUE HANDLER FOR 1051, 1146, 1052
        SET @mensaje = 'Error en la estructura de tabla';
    ```

  - **Condición predefinida**:

    ```sql
    DECLARE CONTINUE HANDLER FOR NOT FOUND
        SET @fin = TRUE;
    ```

- **Bloque de Código**: son la sentencia o conjunto de sentencias SQL que queremos que se ejecuten cuando sucede la condición indicada. Puede ser:
  - Una única instrucción  
  - Un bloque **`BEGIN .. END`** con múltiples instrucciones

    ```sql
    -- Instrucción única
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
        SET @error = TRUE;

    -- Bloque múltiple
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET @error = TRUE;
        SET @mensaje = 'Error en la operación';
        ROLLBACK;
    END;
    ```

#### 5.2.2. Ámbito de los handlers y reglas de declaración

**Ubicación**: Los handlers deben declararse:

- Después de las declaraciones de variables y condiciones  
- Antes de cualquier otra sentencia ejecutable  
- Dentro del bloque donde se utilizarán

**Orden de Precedencia**:

- Se ejecuta el handler más específico que coincida con la condición  
- Si hay varios handlers para la misma condición, se usa el último declarado

```sql
DELIMITER //
CREATE PROCEDURE ejemplo_ambito()
BEGIN
    -- 1. Primero: Variables
    DECLARE v_error BOOLEAN DEFAULT FALSE;
    DECLARE v_mensaje VARCHAR(100);
    
    -- 2. Segundo: Condiciones personalizadas (si las hay)
    DECLARE error_custom CONDITION FOR 1062;
    
    -- 3. Tercero: Handlers
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET v_error = TRUE;
        SET v_mensaje = 'Error SQL general';
    END;
    
    -- 4. Finalmente: Código ejecutable
    START TRANSACTION;
    -- ... resto del código
END //
DELIMITER ;
```

A continuación se presenta un ejemplo completo con diferentes niveles de ámbito:

```sql
DELIMITER //
CREATE PROCEDURE gestionar_empleado(p_id INT)
BEGIN
    -- Bloque principal
    DECLARE v_error BOOLEAN DEFAULT FALSE;
    
    -- Handler para el bloque principal
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET v_error = TRUE;
        ROLLBACK;
    END;
    
    START TRANSACTION;
    
    BEGIN  -- Sub-bloque
        -- Variables locales al sub-bloque
        DECLARE v_salario DECIMAL(10,2);
        
        -- Handler específico para este sub-bloque
        DECLARE CONTINUE HANDLER FOR NOT FOUND
        BEGIN
            SET v_salario = 0;
        END;
        
        -- Código del sub-bloque
        SELECT salario INTO v_salario 
        FROM empleados 
        WHERE id = p_id;
        
    END;  -- Fin sub-bloque
    
    IF v_error THEN
        SELECT 'Operación fallida' AS resultado;
    ELSE
        COMMIT;
        SELECT 'Operación exitosa' AS resultado;
    END IF;
    
END //
DELIMITER ;
```

### 5.3. Tipos de Condiciones

A continuación se detallan algunas de las condiciones más comunes a gestionar en SQL.

#### 5.3.1. `SQLEXCEPTION`

Engloba todos los errores (condiciones con códigos de error positivos). Se usa para capturar cualquier error SQL:

```sql
DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
BEGIN
    -- Código para manejar el error
    SET @error_msg = 'Ha ocurrido un error SQL';
    ROLLBACK;
END;
```

#### 5.3.2. `SQLWARNING`

Captura todas las advertencias MySQL:

```sql
DECLARE CONTINUE HANDLER FOR SQLWARNING
BEGIN
    -- Código para manejar la advertencia
    SET @warning_msg = 'Se ha producido una advertencia';
END;
```

#### 5.3.3. `NOT FOUND`

Se dispara cuando:

- Una `SELECT ... INTO` no encuentra registros  
- Un cursor llega al final del conjunto de resultados  
- Una `UPDATE` o `DELETE` no afecta a ninguna fila

```sql
DECLARE CONTINUE HANDLER FOR NOT FOUND
BEGIN
    SET done = TRUE;
END;
```

#### 5.3.4. Códigos de error específicos de MySQL

Podemos manejar errores específicos por su número:

```sql
-- Manejar error de clave duplicada
DECLARE CONTINUE HANDLER FOR 1062
BEGIN
    SET @error_msg = 'El registro ya existe';
END;

-- Manejar múltiples errores específicos
DECLARE CONTINUE HANDLER FOR 1051, 1146
BEGIN
    SET @error_msg = 'Problema con la estructura de la tabla';
END;
```

Puedes encontrar la referencia de todos los posibles errores de mysql [aquí](https://dev.mysql.com/doc/mysql-errors/8.4/en/server-error-reference.html). Los errores propios de SQL (SQLTATE) más comunes son:

- `45000`: Excepción genérica en el código SQL  
- `23000`: Violación de una restricción de clave única  
- `22001`: Truncamiento de datos en una columna  
- `42000`: Error de sintaxis en la consulta SQL  

Puedes obtener el código de error de la última operación ejecutada con la función `MYSQL_ERRNO`:

```sql
DECLARE v_error_code INT;
DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    SET v_error_code = MYSQL_ERRNO;
```

Entre los errores específicos de MySQL podemos destacar:

- **`1062`**: Violación de clave única (duplicado)  
- **`1051`**: Tabla desconocida  
- **`1146`**: Tabla no existe  
- **`1365`**: División por cero  
- **`1406`**: Truncamiento de datos  
- **`1452`**: Violación de clave foránea  

```sql
DECLARE CONTINUE HANDLER FOR 1062
BEGIN
    SET @error_msg = 'Clave duplicada';
END;
```

#### 5.3.5. Condiciones personalizadas (`CONDITION`)

Podemos crear nombres significativos para condiciones específicas:

```sql
-- Declarar una condición personalizada
DECLARE dup_entry CONDITION FOR 1062;

-- Usar la condición personalizada en un handler
DECLARE CONTINUE HANDLER FOR dup_entry
BEGIN
    SET @error_msg = 'Entrada duplicada detectada';
END;
```

#### 5.3.6. `Get Condition` Statement

Para obtener información sobre la condición que ha activado un handler, podemos usar la instrucción `GET DIAGNOSTICS`:

```sql
DECLARE v_error_code INT;
DECLARE v_error_msg VARCHAR(500);

DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
BEGIN
    GET DIAGNOSTICS CONDITION 1
        v_error_code = MYSQL_ERRNO,
        v_error_msg = MESSAGE_TEXT;
END;

-- Código que puede generar un error, por ejemplo, un insert a una tabla con clave duplicada
INSERT INTO tabla_ejemplo (id, nombre) VALUES (1, 'Ejemplo');

-- Mostrar información del error: si se ha producido un error, v_error_code y v_error_msg contendrán información sobre el error, rellenada por el handler a partir de la información de la condición mediante GET DIAGNOSTICS
SELECT v_error_code, v_error_msg;

```

`GET DIAGNOSTICS` permite acceder a información específica sobre la última condición (error, warning, etc.) que ocurrió en la ejecución de una sentencia SQL. Esta información incluye:

- **Código de error (`MYSQL_ERRNO`):** El número de error específico.
- **Mensaje de error (`MESSAGE_TEXT`):** Una descripción textual del error.
- **Estado SQL (`RETURNED_SQLSTATE`):** El código de estado SQL asociado al error.
- Entre otros detalles, como el nombre de la tabla o columna afectada.

##### **Sintaxis básica**

La sintaxis de `GET DIAGNOSTICS` es la siguiente:

```sql
GET DIAGNOSTICS CONDITION <condition_number>
    <variable1> = <item1>,
    <variable2> = <item2>,
    ...;
```

- **`CONDITION <condition_number>`:** Especifica el número de la condición que deseas consultar. Normalmente se usa `CONDITION 1` para obtener la primera condición (el último error o warning).
- **`<variable1> = <item1>`:** Asigna el valor de un elemento de diagnóstico (como `MYSQL_ERRNO` o `MESSAGE_TEXT`) a una variable.

##### Elementos de diagnóstico comunes

Los elementos de diagnóstico más utilizados son:

1. **`MYSQL_ERRNO`:** El número de error específico de MySQL (por ejemplo, `1062` para entradas duplicadas).
2. **`MESSAGE_TEXT`:** El mensaje de error o warning asociado.
3. **`RETURNED_SQLSTATE`:** El código de estado SQL (por ejemplo, `23000` para violaciones de restricciones de integridad).
4. **`TABLE_NAME`:** El nombre de la tabla afectada.
5. **`COLUMN_NAME`:** El nombre de la columna afectada.

##### Ejemplo de uso

Supongamos que estás manejando una excepción en un procedimiento almacenado y quieres obtener detalles sobre el error que ocurrió. Puedes usar `GET DIAGNOSTICS` de la siguiente manera:

```sql
DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
BEGIN
    -- Declarar variables para almacenar la información del error
    DECLARE errno INT;
    DECLARE errmsg VARCHAR(255);
    DECLARE sqlstate CHAR(5);

    -- Obtener detalles del error
    GET DIAGNOSTICS CONDITION 1
        errno = MYSQL_ERRNO,
        errmsg = MESSAGE_TEXT,
        sqlstate = RETURNED_SQLSTATE;

    -- Mostrar o registrar el error
    SELECT CONCAT('Error: ', errno, ' - ', errmsg, ' (SQLSTATE: ', sqlstate, ')') AS error_message;
END;
```

**Explicación paso a paso**:

1. **Declarar variables:**
   - Se declaran variables para almacenar el número de error (`errno`), el mensaje de error (`errmsg`) y el estado SQL (`sqlstate`).

2. **Manejar la excepción:**
   - Cuando ocurre un error, el manejador (`HANDLER`) captura la excepción y ejecuta el bloque de código dentro del `BEGIN ... END`.

3. **Obtener detalles del error:**
   - `GET DIAGNOSTICS CONDITION 1` obtiene la información de la primera condición (el último error).
   - Se asignan los valores de `MYSQL_ERRNO`, `MESSAGE_TEXT` y `RETURNED_SQLSTATE` a las variables declaradas.

4. **Mostrar o registrar el error:**
   - En este ejemplo, se muestra un mensaje concatenado con los detalles del error. En un entorno real, podrías registrar el error en una tabla de logs o lanzar una excepción personalizada.

##### Ejemplo práctico

Imagina que estás realizando una inserción en una tabla y quieres manejar un posible error de clave duplicada (`1062`):

```sql
CREATE PROCEDURE insertar_usuario(IN nombre VARCHAR(255))
BEGIN
    DECLARE EXIT HANDLER FOR SQLEXCEPTION
    BEGIN
        DECLARE errno INT;
        DECLARE errmsg VARCHAR(255);
        DECLARE sqlstate CHAR(5);

        -- Obtener detalles del error
        GET DIAGNOSTICS CONDITION 1
            errno = MYSQL_ERRNO,
            errmsg = MESSAGE_TEXT,
            sqlstate = RETURNED_SQLSTATE;

        -- Mostrar el error
        SELECT CONCAT('Error: ', errno, ' - ', errmsg, ' (SQLSTATE: ', sqlstate, ')') AS error_message;
    END;

    -- Intentar la inserción
    INSERT INTO usuarios (nombre) VALUES (nombre);
END;
```

Si intentas insertar un nombre que ya existe y viola una restricción `UNIQUE`, el manejador capturará el error y mostrará algo como:

```sql
Error: 1062 - Duplicate entry 'Juan' for key 'nombre_unico' (SQLSTATE: 23000)
```

##### Consideraciones adicionales

1. **Múltiples condiciones:**
   - Si una consulta genera múltiples errores o warnings, puedes usar `CONDITION 2`, `CONDITION 3`, etc., para acceder a cada uno de ellos.

2. **Uso en combinación con `HANDLER`s:**
   - `GET DIAGNOSTICS` es más útil cuando se combina con manejadores de excepciones (`DECLARE HANDLER`), ya que te permite capturar y manejar errores de manera controlada.

3. **Registro de errores:**
   - En lugar de mostrar el error, podrías insertarlo en una tabla de logs para su posterior análisis.

La descripción completa de `GET DIAGNOSTICS` se puede encontrar en la documentación oficial de MySQL, [aquí](https://dev.mysql.com/doc/refman/8.0/en/get-diagnostics.html) y [aquí](https://dev.mysql.com/doc/refman/8.4/en/diagnostics-area.html)

### 5.4. Manejo de Errores en la Práctica

#### 5.4.1. Handlers en Procedimientos Almacenados

Los procedimientos almacenados son el lugar más común para usar handlers. Ejemplo típico:

```sql
DELIMITER //
CREATE PROCEDURE insertar_empleado(
    IN p_nombre VARCHAR(100),
    IN p_salario DECIMAL(10,2)
)
BEGIN
    -- Declaraciones
    DECLARE v_error_ocurrido BOOLEAN DEFAULT FALSE;
    DECLARE v_error_mensaje VARCHAR(100);

    -- Handlers
    DECLARE CONTINUE HANDLER FOR 1062
        SET v_error_mensaje = 'El empleado ya existe';
    
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET v_error_ocurrido = TRUE;
        SET v_error_mensaje = 'Error general en la operación';
    END;

    -- Operación principal
    INSERT INTO empleados(nombre, salario) 
    VALUES (p_nombre, p_salario);

    -- Control de resultados
    IF v_error_ocurrido THEN
        SELECT v_error_mensaje AS 'Error';
    ELSE
        SELECT 'Empleado insertado correctamente' AS 'Resultado';
    END IF;
END //
DELIMITER ;
```

#### 5.4.2. Handlers en Triggers

En triggers, los handlers son especialmente útiles para validar datos y mantener la integridad:

```sql
DELIMITER //
CREATE TRIGGER validar_salario
BEFORE INSERT ON empleados
FOR EACH ROW
BEGIN
    DECLARE v_salario_minimo DECIMAL(10,2);
    DECLARE v_error_mensaje VARCHAR(100);
    
    DECLARE EXIT HANDLER FOR SQLEXCEPTION
    BEGIN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Error en validación de salario';
    END;

    SELECT MIN(salario) INTO v_salario_minimo 
    FROM rangos_salario 
    WHERE departamento = NEW.departamento;
    
    IF NEW.salario < v_salario_minimo THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Salario por debajo del mínimo permitido';
    END IF;
END //
DELIMITER ;
```

#### 5.4.3. Handlers en Bloques BEGIN-END

Los bloques BEGIN-END permiten agrupar lógica y manejar errores de forma localizada:

```sql
BEGIN
    DECLARE v_error BOOLEAN DEFAULT FALSE;
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION SET v_error = TRUE;

    BEGIN  -- Bloque interno
        DECLARE v_count INT;
        DECLARE error_en_conteo CONDITION FOR SQLSTATE '01000';
        DECLARE CONTINUE HANDLER FOR error_en_conteo 
            SET v_count = 0;

        -- Operaciones del bloque interno
        SELECT COUNT(*) INTO v_count FROM tabla_ejemplo;
    END;

    IF v_error THEN
        -- Manejar error del bloque externo
    END IF;
END;
```

#### 5.4.4. Handlers con Cursores

Los handlers son esenciales cuando trabajamos con cursores. Éstos los veremos en el siguiente apartado.

### 5.5. Arrojando nuestras propias condiciones

En MySQL, es posible definir **condiciones personalizadas** para manejar errores y situaciones excepcionales dentro de procedimientos almacenados, funciones y disparadores. Para ello, se usa la sentencia **`SIGNAL`**, que permite generar errores de manera explícita y con mensajes personalizados.  

```sql
DELIMITER //

CREATE PROCEDURE insertar_empleado(p_nombre VARCHAR(100), p_salario DECIMAL(10,2))
BEGIN
    DECLARE v_error BOOLEAN DEFAULT FALSE;
    DECLARE v_error_msg VARCHAR(100);
    
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET v_error = TRUE;
        SET v_error_msg = 'Error en la operación';
    END;
    
    IF p_salario < 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'El salario no puede ser negativo';
    END IF;
    
    IF v_error THEN
        SELECT v_error_msg AS 'Error';
    ELSE
        INSERT INTO empleados(nombre, salario) VALUES (p_nombre, p_salario);
        SELECT 'Empleado insertado correctamente' AS 'Resultado';
    END IF;
END //

DELIMITER ;
```

#### 5.5.1. Sintaxis completa de `SIGNAL`

La sentencia `SIGNAL` se usa para lanzar errores personalizados en MySQL. Su sintaxis completa es:

```sql
SIGNAL condition_value
    [SET signal_information_item
    [, signal_information_item] ...]

condition_value: {
    SQLSTATE [VALUE] sqlstate_value
  | condition_name
}

signal_information_item:
    condition_information_item_name = simple_value_specification

condition_information_item_name: {
    CLASS_ORIGIN
  | SUBCLASS_ORIGIN
  | MESSAGE_TEXT
  | MYSQL_ERRNO
  | CONSTRAINT_CATALOG
  | CONSTRAINT_SCHEMA
  | CONSTRAINT_NAME
  | CATALOG_NAME
  | SCHEMA_NAME
  | TABLE_NAME
  | COLUMN_NAME
  | CURSOR_NAME
}
```

Puedes encontrar toda la información oficial sobre la sentencia `SIGNAL`en la [documentación oficial de MySQL](https://dev.mysql.com/doc/refman/8.4/en/signal.html)

#### 5.5.2. ¿Por qué usar `SIGNAL` en lugar de estructuras de control como `IF`?

Tradicionalmente, los errores en MySQL se gestionaban mediante estructuras como `IF`, combinadas con `LEAVE` o el uso de valores de retorno. Sin embargo, estas estrategias tienen **limitaciones importantes**:  

| Método | Ventajas | Desventajas |
|--------|---------|-------------|
| **`IF` con `LEAVE` o `RETURN`** | Permite manejar errores sin interrumpir la ejecución del procedimiento. | No detiene inmediatamente la ejecución y no genera errores SQL explícitos. |
| **`SIGNAL`** | Detiene la ejecución y devuelve un error personalizado al usuario. | Puede ser más restrictivo si se usa sin planificación. |

**Ejemplo de gestión de errores con `IF` (limitado):**  

```sql
CREATE PROCEDURE verificar_stock(p_producto_id INT)
BEGIN
    DECLARE stock_actual INT;
    
    -- Obtener el stock del producto
    SELECT stock INTO stock_actual FROM productos WHERE id = p_producto_id;
    
    -- Si no hay stock suficiente, simplemente mostramos un mensaje, pero la ejecución sigue
    IF stock_actual <= 0 THEN
        SELECT 'No hay stock disponible' AS mensaje;
    END IF;
    
    -- Continúa con la lógica del procedimiento...
END;
```

⚠ **Problema:** La ejecución **no se detiene** si hay un error. Solo muestra un mensaje, pero podría seguir ejecutando otras operaciones erróneas.  

#### 5.5.3. Uso de `SIGNAL` para lanzar errores personalizados

El uso de `SIGNAL` permite detener la ejecución inmediatamente y devolver un código de error y un mensaje descriptivo.  

**Ejemplo de `SIGNAL` en un procedimiento:**  

```sql
CREATE PROCEDURE verificar_stock(p_producto_id INT)
BEGIN
    DECLARE stock_actual INT;
    
    -- Obtener el stock del producto
    SELECT stock INTO stock_actual FROM productos WHERE id = p_producto_id;
    
    -- Si no hay stock suficiente, lanzamos un error
    IF stock_actual <= 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Error: No hay stock disponible para este producto.';
    END IF;
    
    -- Continúa solo si hay stock...
END;
```

🔹 **Ventajas de este enfoque:**  
✅ Detiene la ejecución inmediatamente si ocurre un error.  
✅ Devuelve un error SQL que puede ser capturado por el cliente o la aplicación.  
✅ Permite definir **mensajes personalizados** para depuración.  

 **Ejemplo de ejecución y error:**  

```sql
CALL verificar_stock(5);
```

🔴 **Salida esperada si no hay stock:**

```
ERROR 1644 (45000): Error: No hay stock disponible para este producto.
```

⚠ **IMPORTANTE:** `45000` es un código de error genérico definido por el usuario. Se recomienda **evitar códigos SQLSTATE reservados por MySQL**, como `23000` (violación de clave única) o `42000` (error de sintaxis).  

#### 5.5.4. Otras aplicaciones de `SIGNAL` en MySQL

🔹 **1️⃣ Validación de parámetros en procedimientos almacenados**  
Si un usuario intenta registrar una compra con un total negativo:

```sql
CREATE PROCEDURE registrar_compra(p_total DECIMAL(10,2))
BEGIN
    IF p_total < 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'El total de la compra no puede ser negativo.';
    END IF;
END;
```

```sql
CALL registrar_compra(-50);
```

🔴 **Salida:**  

```sql
ERROR 1644 (45000): El total de la compra no puede ser negativo.
```

🔹 **2️⃣ Uso en `TRIGGERS` para evitar modificaciones no permitidas**  
Ejemplo: Evitar que un usuario elimine productos con stock.  

```sql
CREATE TRIGGER evitar_borrar_productos_con_stock
BEFORE DELETE ON productos
FOR EACH ROW
BEGIN
    IF OLD.stock > 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'No puedes eliminar productos con stock disponible.';
    END IF;
END;
```

**✅ Conclusión: ¿Cuándo usar `SIGNAL`?**  

| **Situación** | **¿Usar `IF` o `SIGNAL`?** | **Motivo** |
|--------------|----------------|-----------|
| Validaciones de negocio en procedimientos | `SIGNAL` | Garantiza que las reglas se cumplan y detiene la ejecución. |
| Mostrar mensajes sin interrumpir la ejecución | `IF` | Útil si solo se necesita advertir sin generar errores. |
| Evitar operaciones indebidas en `TRIGGERS` | `SIGNAL` | Previene acciones no permitidas antes de que ocurran. |
| Manejo de errores en transacciones | `SIGNAL` + `ROLLBACK` | Permite revertir cambios y lanzar un mensaje de error. |

### 5.6. Buenas Prácticas

#### 5.6.1. Estrategias de Gestión de Errores

La gestión efectiva de errores en MySQL requiere un enfoque estructurado:

1. **Jerarquía de Handlers**:
   - Handlers específicos para errores conocidos
   - Handler general para SQLEXCEPTION como respaldo

2. **Transacciones**:
   - Usar siempre que se modifiquen múltiples tablas
   - Implementar rollback en caso de error

3. **Variables de Control**:
   - Mantener flags de estado
   - Almacenar mensajes de error descriptivos

```sql
BEGIN
    DECLARE v_error BOOLEAN DEFAULT FALSE;
    DECLARE v_error_msg VARCHAR(100);
    
    DECLARE CONTINUE HANDLER FOR 1062 
    BEGIN
        SET v_error = TRUE;
        SET v_error_msg = 'Registro duplicado';
    END;
    
    -- ... código ...
    
    IF v_error THEN
        -- Manejar error
    END IF;
END;
```

#### 5.6.2. Logging de Errores

Es buena práctica mantener un registro de errores para diagnóstico y seguimiento:

```sql
CREATE TABLE error_log (
    id INT AUTO_INCREMENT PRIMARY KEY,
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    procedimiento VARCHAR(100),
    codigo_error INT,
    mensaje VARCHAR(500),
    datos_entrada JSON
);

-- Ejemplo de uso
DELIMITER //
CREATE PROCEDURE insertar_con_log(IN p_datos JSON)
BEGIN
    DECLARE v_error_code INT;
    DECLARE v_error_msg VARCHAR(500);
    
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        GET DIAGNOSTICS CONDITION 1
            v_error_code = MYSQL_ERRNO,
            v_error_msg = MESSAGE_TEXT;
            
        INSERT INTO error_log(procedimiento, codigo_error, mensaje, datos_entrada)
        VALUES (
            'insertar_con_log',
            v_error_code,
            v_error_msg,
            p_datos
        );
    END;
    
    -- Código principal...
END //
DELIMITER ;
```

#### 5.6.3. Depuración y Troubleshooting

Técnicas efectivas para identificar y resolver problemas:

1. **Usar Variables de Diagnóstico**:
```sql
GET DIAGNOSTICS CONDITION 1
    @errno = MYSQL_ERRNO,
    @msg = MESSAGE_TEXT;
```

2. **Crear Puntos de Control**:
```sql
SET @debug_point = 'Inicio proceso';
-- ... código ...
SET @debug_point = 'Después de primera operación';
```

3. **Logging Detallado**:
```sql
CREATE PROCEDURE debug_proceso()
BEGIN
    DECLARE v_step VARCHAR(100);
    
    SET v_step = 'Iniciando proceso';
    INSERT INTO debug_log(paso, timestamp) VALUES (v_step, NOW());
    
    -- ... código ...
    
    SET v_step = 'Proceso completado';
    INSERT INTO debug_log(paso, timestamp) VALUES (v_step, NOW());
END;
```

#### 5.6.4. Casos Comunes y Soluciones Recomendadas

1. **Violación de Clave Única**:
```sql
DECLARE CONTINUE HANDLER FOR 1062
BEGIN
    -- Intentar actualizar en lugar de insertar
    UPDATE tabla SET campo = nuevo_valor WHERE clave = valor_clave;
END;
```

2. **Registros No Encontrados**:
```sql
DECLARE CONTINUE HANDLER FOR NOT FOUND
BEGIN
    -- Crear registro por defecto
    INSERT INTO tabla (campos) VALUES (valores_default);
END;
```

3. **Error de División por Cero**:
```sql
DECLARE CONTINUE HANDLER FOR 1365
BEGIN
    -- Asignar valor por defecto
    SET resultado = 0;
END;
```

### 5.7. Ejemplos Prácticos

#### 5.7.1. Manejo Básico de Errores

```sql
DELIMITER //
CREATE PROCEDURE ejemplo_basico(IN p_id INT)
BEGIN
    DECLARE v_error BOOLEAN DEFAULT FALSE;
    DECLARE v_mensaje VARCHAR(100);
    
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET v_error = TRUE;
        SET v_mensaje = 'Error en la operación';
    END;
    
    -- Operación principal
    UPDATE clientes SET activo = 1 WHERE id = p_id;
    
    IF v_error THEN
        SELECT v_mensaje AS 'Error';
    ELSE
        SELECT 'Operación exitosa' AS 'Resultado';
    END IF;
END //
DELIMITER ;
```

#### 5.7.2. Gestión de Errores en Transacciones

```sql
DELIMITER //
CREATE PROCEDURE transferencia(
    IN p_origen INT,
    IN p_destino INT,
    IN p_cantidad DECIMAL(10,2)
)
BEGIN
    DECLARE v_error BOOLEAN DEFAULT FALSE;
    
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET v_error = TRUE;
        ROLLBACK;
    END;
    
    START TRANSACTION;
    
    UPDATE cuentas 
    SET saldo = saldo - p_cantidad 
    WHERE id = p_origen;
    
    UPDATE cuentas 
    SET saldo = saldo + p_cantidad 
    WHERE id = p_destino;
    
    IF v_error THEN
        SELECT 'Error en la transferencia' AS 'Error';
    ELSE
        COMMIT;
        SELECT 'Transferencia exitosa' AS 'Resultado';
    END IF;
END //
DELIMITER ;
```

#### 5.7.3. Logging de Errores en Tabla

```sql
DELIMITER //
CREATE PROCEDURE operacion_con_log(IN p_data JSON)
BEGIN
    DECLARE v_inicio TIMESTAMP;
    DECLARE v_fin TIMESTAMP;
    DECLARE v_resultado VARCHAR(10) DEFAULT 'OK';
    
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET v_resultado = 'ERROR';
        INSERT INTO error_log (
            operacion,
            fecha_inicio,
            fecha_fin,
            resultado,
            datos
        ) VALUES (
            'operacion_con_log',
            v_inicio,
            CURRENT_TIMESTAMP,
            v_resultado,
            p_data
        );
    END;
    
    SET v_inicio = CURRENT_TIMESTAMP;
    
    -- Código principal...
    
    SET v_fin = CURRENT_TIMESTAMP;
    
    -- Log de éxito
    IF v_resultado = 'OK' THEN
        INSERT INTO operaciones_log (
            operacion,
            fecha_inicio,
            fecha_fin,
            resultado,
            datos
        ) VALUES (
            'operacion_con_log',
            v_inicio,
            v_fin,
            v_resultado,
            p_data
        );
    END IF;
END //
DELIMITER ;
```

#### 5.7.4. Handlers Múltiples

```sql
DELIMITER //
CREATE PROCEDURE ejemplo_handlers_multiples()
BEGIN
    DECLARE v_error_tipo VARCHAR(50);
    DECLARE v_mensaje VARCHAR(100);
    
    -- Handler para duplicados
    DECLARE CONTINUE HANDLER FOR 1062
    BEGIN
        SET v_error_tipo = 'DUPLICADO';
        SET v_mensaje = 'Registro duplicado';
    END;
    
    -- Handler para tabla no existe
    DECLARE CONTINUE HANDLER FOR 1146
    BEGIN
        SET v_error_tipo = 'TABLA';
        SET v_mensaje = 'La tabla no existe';
    END;
    
    -- Handler para división por cero
    DECLARE CONTINUE HANDLER FOR 1365
    BEGIN
        SET v_error_tipo = 'CALCULO';
        SET v_mensaje = 'Error en cálculo';
    END;
    
    -- Handler general para otros errores
    DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
    BEGIN
        SET v_error_tipo = 'GENERAL';
        SET v_mensaje = 'Error no especificado';
    END;
    
    -- Código principal...
    
    IF v_error_tipo IS NOT NULL THEN
        INSERT INTO log_errores (tipo, mensaje)
        VALUES (v_error_tipo, v_mensaje);
    END IF;
END //
DELIMITER ;
```

## 6. Introducción a los Cursores

### 6.1. ¿Qué son los cursores?

Un **cursor** es una estructura de control que permite procesar fila por fila el resultado de una consulta SQL. Actúa como un **puntero** o **indicador** que se mueve a través del conjunto de resultados, permitiendo acceder y manipular cada registro de manera individual.

En el contexto de MySQL y la administración de bases de datos, los cursores son especialmente útiles cuando necesitamos realizar operaciones que no pueden resolverse con una única consulta SQL y requieren un procesamiento registro a registro.

### 6.2. ¿Cuándo y por qué usarlos?

Los cursores son útiles en situaciones específicas como:

1. Cuando necesitamos realizar **operaciones complejas** que dependen de los valores de cada fila.  
2. En procesos de migración de datos donde se requiere transformar información registro a registro.  
3. Para **generar informes** que requieren cálculos o lógica específica para cada registro.  
4. En situaciones donde necesitamos **tomar decisiones** basadas en el contenido de cada fila.

Sin embargo, es importante destacar que los cursores no siempre son la mejor solución, ya que pueden tener un impacto significativo en el rendimiento cuando se trabaja con grandes volúmenes de datos.

### 6.3. Tipos de Cursores

#### 6.3.1. Cursores implícitos

Los cursores implícitos son gestionados automáticamente por MySQL sin necesidad de declararlos explícitamente. Se utilizan en operaciones como:

- Sentencias UPDATE  
- Sentencias DELETE  
- Sentencias INSERT  
- Sentencias SELECT que devuelven un único registro

MySQL maneja internamente estos cursores y proporciona información sobre su estado a través de variables como:

```sql
ROW_COUNT() -- Número de filas afectadas
FOUND_ROWS() -- Número de filas encontradas
```

#### 6.3.2. Cursores Explícitos

Los cursores explícitos son aquellos que el programador define y controla directamente. En MySQL, estos cursores:

1. Deben declararse dentro de procedimientos almacenados o funciones  
2. Son de solo lectura (no se pueden actualizar los datos a través del cursor)  
3. No son scrollables (solo pueden avanzar hacia adelante)

A continuación, vamos a definir con detalle como crear y utlizar un cursor.

### 6.4. Creación y Uso de Cursores

Esta es la sintaxis general para declarar un cursor en mysql:

```sql
DECLARE cursor_name CURSOR FOR select_statement
```

Esta sentencia debe añadirse al cuerpo de una rutina, y sirve para obtener un mecanismo de control sobre los resultados obtenidos a través de la sentencia `select_statement`. Tal y como se indica en la documentación oficial:

- la sentencia **`SELECT`** definida no debe incluir la cláusula **`INTO`**
- La declaración del cursor debe aparecer antes de la declaración del handler y después de la declaración de variables y condiciones. Sobre los handler hablaremos en apartados posteriores.

Ejemplo básico de **declaración** de un cursor explícito dentro de un procedimiento:

```sql
DELIMITER //
CREATE PROCEDURE ejemplo_cursor()
BEGIN
    -- 1. Declaración de variables
    DECLARE v_nombre VARCHAR(100);
    DECLARE v_salario DECIMAL(10,2);
    DECLARE v_done BOOLEAN DEFAULT FALSE;

    -- 2. Declaración del cursor
    DECLARE cur_empleados CURSOR FOR
        SELECT nombre, salario 
        FROM empleados 
        WHERE departamento = 'IT';

    -- 3. Declaración del manejador de eventos
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET v_done = TRUE;
```

Una vez declarado el cursor, necesitamos abrirlo para empezar a usarlo. La estructura típica es la siguiente:

```sql
-- 1. Abrir el cursor
    OPEN cur_empleados;

    -- 2. Bucle de lectura
    read_loop: LOOP
        -- Obtener siguiente fila
        FETCH cur_empleados INTO v_nombre, v_salario;
        
        -- Comprobar si hemos terminado
        IF v_done THEN
            LEAVE read_loop;
        END IF;

        -- Aquí procesamos los datos...
        -- Por ejemplo:
        IF v_salario < 30000 THEN
            INSERT INTO aumentos_pendientes(nombre, salario_actual)
            VALUES (v_nombre, v_salario);
        END IF;
    END LOOP;
```

Es muy importante cerrar el cursor cuando hayamos terminado de usarlo para liberar recursos:

```sql
-- Cerrar el cursor
    CLOSE cur_empleados;
END //
DELIMITER ;
```

Veamos ahora un ejemplo completo:

```sql
DELIMITER //
CREATE PROCEDURE actualizar_salarios_departamento(IN p_departamento VARCHAR(50))
BEGIN
    -- Declaración de variables
    DECLARE v_id INT;
    DECLARE v_salario DECIMAL(10,2);
    DECLARE v_anos_servicio INT;
    DECLARE v_done BOOLEAN DEFAULT FALSE;

    -- Declaración del cursor
    DECLARE cur_empleados CURSOR FOR
        SELECT id, salario, YEAR(CURDATE()) - YEAR(fecha_contratacion)
        FROM empleados
        WHERE departamento = p_departamento;

    -- Declaración del manejador de errores
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET v_done = TRUE;

    -- Crear tabla temporal para log
    CREATE TEMPORARY TABLE IF NOT EXISTS log_actualizaciones (
        empleado_id INT,
        salario_anterior DECIMAL(10,2),
        salario_nuevo DECIMAL(10,2),
        fecha_modificacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    );

    -- Abrir cursor
    OPEN cur_empleados;

    -- Bucle de procesamiento
    read_loop: LOOP
        -- Obtener siguiente empleado
        FETCH cur_empleados INTO v_id, v_salario, v_anos_servicio;

        -- Salir si no hay más registros
        IF v_done THEN
            LEAVE read_loop;
        END IF;

        -- Calcular nuevo salario basado en años de servicio
        IF v_anos_servicio >= 5 THEN
            -- Guardar log del cambio
            INSERT INTO log_actualizaciones (empleado_id, salario_anterior, salario_nuevo)
            VALUES (v_id, v_salario, v_salario * 1.1);

            -- Actualizar salario
            UPDATE empleados
            SET salario = v_salario * 1.1
            WHERE id = v_id;
        END IF;

    END LOOP;

    -- Cerrar cursor
    CLOSE cur_empleados;

    -- Mostrar resultados
    SELECT * FROM log_actualizaciones;
    
    -- Limpiar
    DROP TEMPORARY TABLE IF EXISTS log_actualizaciones;

END //
```

Recordamos que para utilizar el procedimiento definido en el ejemplo anterior, ejecutaríamos:

```sql
-- Llamar al procedimiento para un departamento específico
CALL actualizar_salarios_departamento('IT');
```

Nota :bulb: : Puedes encontrar más información sobre las tablas temporales en el [anexo](#anexo) al final de este documento.

#### 6.4.1. Puntos Importantes a Recordar

1. **Orden de Declaración**: Las variables deben declararse antes que el cursor, y el manejador de eventos después del cursor.  
2. **Variables de FETCH**: El número y tipo de variables en el FETCH debe coincidir exactamente con las columnas seleccionadas en el cursor.  
3. **Manejo de Errores**: Siempre es importante incluir un manejador para NOT FOUND para evitar bucles infinitos.  
4. **Recursos**: No olvides cerrar el cursor cuando termines de usarlo.  
5. **Tablas Temporales**: Son útiles para almacenar resultados intermedios cuando procesas datos con cursores.

### 6.5. Características principales de los cursores explícitos en MySQL

#### 6.5.1. Son unidireccionales (forward-only)

Imagina que tienes un libro y sólo puedes leer las páginas avanzando hacia adelante, sin poder retroceder. Así funcionan los cursores en MySQL:

- Solo pueden moverse hacia adelante en el conjunto de resultados  
- Una vez que avanzas a la siguiente fila, no puedes volver a la anterior  
- El recorrido es secuencial: fila 1 → fila 2 → fila 3 → ...

```sql
-- Ejemplo de recorrido unidireccional
FETCH cursor_ejemplo INTO variable;  -- Lee fila 1
FETCH cursor_ejemplo INTO variable;  -- Lee fila 2
-- No hay manera de volver a leer la fila 1
```

#### 6.5.2. Son de solo lectura (read-only)

Es como tener un libro en PDF: puedes leer su contenido pero no puedes modificarlo. En los cursores:

- Puedes leer los datos de cada fila  
- No puedes modificar los datos mientras los lees con el cursor  
- Si necesitas actualizar datos, deberás hacerlo con una sentencia UPDATE separada

```sql
-- Correcto: Leer datos
FETCH mi_cursor INTO nombre, edad, salario;

-- Incorrecto: No se puede hacer esto
UPDATE CURRENT OF mi_cursor;  -- No permitido en MySQL
```

#### 6.5.3. No son actualizables

No puedes usar sentencias UPDATE o DELETE directamente sobre la fila actual del cursor. Si necesitas actualizar datos, debes:

- Leer los datos con el cursor  
- Guardar los valores en variables  
- Realizar un UPDATE normal usando esos valores

```sql
-- Ejemplo de cómo actualizar datos cuando usamos cursores
DELIMITER //
CREATE PROCEDURE actualizar_salarios()
BEGIN
    DECLARE done INT DEFAULT FALSE;
    DECLARE emp_id INT;
    DECLARE emp_salario DECIMAL(10,2);
    
    -- Declarar cursor
    DECLARE cur_empleados CURSOR FOR 
        SELECT id, salario FROM empleados;
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
    
    OPEN cur_empleados;
    
    read_loop: LOOP
        FETCH cur_empleados INTO emp_id, emp_salario;
        IF done THEN
            LEAVE read_loop;
        END IF;
        
        -- Actualizar usando una sentencia UPDATE normal
        UPDATE empleados 
        SET salario = emp_salario * 1.1
        WHERE id = emp_id;
    END LOOP;
    
    CLOSE cur_empleados;
END //
DELIMITER ;
```

#### 6.5.4. No son scrollables (no permiten movimientos hacia atrás o saltos)

### 6.6. Ejemplos Prácticos

Cursor para actualizar salarios:

```sql 
DELIMITER //
CREATE PROCEDURE actualizar_salarios()
BEGIN
    DECLARE done INT DEFAULT FALSE;
    DECLARE emp_id INT;
    DECLARE emp_salario DECIMAL(10,2);
    
    -- Declarar cursor
    DECLARE cur_empleados CURSOR FOR 
        SELECT id, salario FROM empleados;
    
    -- Declarar handler
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
    
    OPEN cur_empleados;
    
    read_loop: LOOP
        FETCH cur_empleados INTO emp_id, emp_salario;
        IF done THEN
            LEAVE read_loop;
        END IF;
        
        -- Aumentar salario en 5% si es menor a 3000
        IF emp_salario < 3000 THEN
            UPDATE empleados 
            SET salario = salario * 1.05 
            WHERE id = emp_id;
        END IF;
    END LOOP;
    
    CLOSE cur_empleados;
END //
DELIMITER ;
```

Cursor con múltiples tablas:

```sql
DELIMITER //
CREATE PROCEDURE generar_reporte_ventas()
BEGIN
    DECLARE done INT DEFAULT FALSE;
    DECLARE v_cliente_id INT;
    DECLARE v_total DECIMAL(10,2);
    
    DECLARE cur_ventas CURSOR FOR 
        SELECT cliente_id, SUM(monto) 
        FROM ventas 
        GROUP BY cliente_id;
    
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
    
    -- Crear tabla temporal para el reporte
    CREATE TEMPORARY TABLE reporte_temp (
        cliente_id INT,
        total_ventas DECIMAL(10,2),
        categoria VARCHAR(20)
    );
    
    OPEN cur_ventas;
    
    read_loop: LOOP
        FETCH cur_ventas INTO v_cliente_id, v_total;
        IF done THEN
            LEAVE read_loop;
        END IF;
        
        INSERT INTO reporte_temp
        VALUES (v_cliente_id, v_total,
            CASE 
                WHEN v_total > 10000 THEN 'Premium'
                WHEN v_total > 5000 THEN 'Regular'
                ELSE 'Básico'
            END);
    END LOOP;
    
    CLOSE cur_ventas;
END //
DELIMITER ;
```

### 6.7. Limitaciones de los Cursores

Algunas limitaciones en el uso de cursores:

- **Rendimiento**:
	- los cursores procesan registros uno a uno, lo que es menos eficiente que operaciones set-based
	- Consumen más recursos de memoria y CPU que las consultas directas
	- Pueden causar bloqueos más prolongados en las tablas
- **Escalabilidad**:
	- No son adecuados para procesar grandes volúmenes de datos
	- El rendimiento se degrada significativamente con conjuntos de datos grandes
	- Pueden causar problemas de timeout en conexiones
- **Restricciones técnicas**:
	- Solo pueden avanzar en una dirección (no son scrollables en MySQL)
	- No se pueden actualizar directamente (no son actualizables)
	- Limitados a una única consulta SELECT por cursor
- **Manejo de memoria**:
	- Requieren gestión explícita de apertura y cierre
	- Pueden causar fugas de memoria si no se cierran correctamente
	- El número máximo de cursores abiertos está limitado por la variable de sistema

### 6.8. Buenas Prácticas con Cursores

**Cuándo usar cursores**:

- Usar solo cuando sea **estrictamente necesario** procesar fila por fila
- Preferir operaciones SET cuando sea posible
- Ideal para operaciones que requieren **lógica compleja por registro**

Optimización:

- **Minimizar** la cantidad de datos recuperados en el cursor
- Usar **índices** apropiados en las columnas de la consulta del cursor
- **Cerrar cursores** tan pronto como sea posible

Manejo de errores:

- Implementar siempre **handlers** para manejar excepciones
- Asegurar que los cursores se cierren en caso de error
- Usar transacciones cuando sea necesario para mantener la consistencia

Estructura y mantenimiento:

- Documentar claramente el propósito del cursor
- Mantener la lógica dentro del cursor lo más simple posible
- Considerar el **impacto en el rendimiento general** de la aplicación

Alternativas a considerar:

- Evaluar el uso de JOIN y subconsultas
- Considerar operaciones en lote (BATCH)
- Usar variables de usuario cuando sea apropiado

Pruebas:

- Probar con diferentes volúmenes de datos
- Verificar el comportamiento con conjuntos de datos extremos
- Monitorear el consumo de recursos durante la ejecución

## 7. Documentación en MySQL: Procedimientos, Eventos, Handlers y Cursores

La documentación adecuada de los objetos de base de datos es un aspecto fundamental pero frecuentemente descuidado en el desarrollo de sistemas. En el contexto de MySQL, donde los procedimientos almacenados, eventos, handlers y cursores pueden formar parte de lógicas de negocio complejas, una documentación clara y completa se vuelve esencial no solo para el mantenimiento del código, sino también para garantizar su correcta utilización y evolución.

Una buena documentación debe servir como guía tanto para el desarrollador original como para futuros mantenedores del código, proporcionando información clara sobre el propósito, funcionamiento y requisitos de cada objeto. Esto incluye detallar los parámetros de entrada y salida, las condiciones de error manejadas, las dependencias con otros objetos de la base de datos, y cualquier consideración especial de rendimiento o seguridad. Además, mantener un registro de cambios actualizado permite entender la evolución del código y facilita la resolución de problemas cuando surgen.

Para documentar las rutinas almacenadas, eventos, triggers o cursores, haremos uso de los bloques de comentarios, utilizando los símbolos `/* comentario */` para comentarios multilínea y `--` para comentarios de una sola línea. A continuación, se muestran ejemplos prácticos de documentación para cada tipo de objeto.

Estándares de Documentación:

```sql
--Ejemplo de documentación de un procedimiento almacenado
DELIMITER //

/*
* =============================================
* Procedimiento: calcular_ventas_mensuales
* =============================================
* Descripción: Calcula el total de ventas por mes y actualiza la tabla de estadísticas
* 
* Parámetros:
*   @p_anio INT - Año a procesar
*   @p_mes INT - Mes a procesar
*
* Retorna:
*   @out_total DECIMAL - Total calculado
*
* Excepciones manejadas:
*   - 1329: No data found
*   - 1264: Out of range value
*
* Cursores utilizados:
*   - cur_ventas: Cursor para procesar ventas del período
*
* Autor: Juan Pérez
* Fecha creación: 2024-01-20
* Última modificación: 2024-01-20
* =============================================
*/
CREATE PROCEDURE calcular_ventas_mensuales(
    IN p_anio INT,
    IN p_mes INT,
    OUT out_total DECIMAL(10,2)
)
BEGIN
    -- Resto del código...
END //

DELIMITER ;
```

Documentación de Eventos:

```sql
/*
* =============================================
* Evento: limpiar_logs_diarios
* =============================================
* Descripción: Limpia registros de log antiguos
* 
* Programación: Diaria a las 00:00
* Preserva: Últimos 30 días de registros
* 
* Tablas afectadas:
*   - logs_sistema (DELETE)
*   - log_estadisticas (UPDATE)
*
* Autor: Ana García
* Fecha creación: 2024-01-20
* =============================================
*/
CREATE EVENT limpiar_logs_diarios
    ON SCHEDULE EVERY 1 DAY
    STARTS '2024-01-20 00:00:00'
    DO
    BEGIN
        -- Código del evento...
    END;
```

Documentación de **Handlers**:

```sql
/*
* Handler para manejo de errores específicos
* Registra en tabla de auditoría y notifica
*/
DECLARE CONTINUE HANDLER FOR 
    SQLSTATE '23000',     -- Duplicate key
    SQLSTATE '22003'      -- Out of range
BEGIN
    -- Documentar cada acción del handler
    INSERT INTO log_errores (
        fecha,
        codigo_error,
        mensaje,
        procedimiento
    ) VALUES (
        NOW(),
        SQLSTATE,
        MESSAGE_TEXT,
        'nombre_procedimiento'
    );
END;
```

Documentación de **cursores**:

```sql
/*
* Cursor: cur_procesar_clientes
* Propósito: Procesa clientes para actualización de estado
* 
* Columnas recuperadas:
*   - cliente_id: ID único del cliente
*   - total_compras: Suma total de compras
*   - ultima_compra: Fecha de última compra
*
* Variables de cursor:
*   - v_cliente_id: Almacena ID actual
*   - v_total: Almacena total actual
*
* Notas de rendimiento:
*   - Utiliza índice idx_clientes_fecha
*   - Procesa aprox. 1000 registros por ejecución
*/
DECLARE cur_procesar_clientes CURSOR FOR
    SELECT cliente_id, total_compras, ultima_compra
    FROM clientes
    WHERE estado = 'PENDIENTE'
    ORDER BY ultima_compra DESC;
```

Metadatos y Comentarios en Sistema:

```sql
-- Agregar comentarios a nivel de sistema

-- Añadimos comentario a una columna en la creación de tabla
CREATE TABLE empleados (
    id INT COMMENT 'Identificador único del empleado',
    nombre VARCHAR(100) COMMENT 'Nombre completo del empleado'
) COMMENT 'Tabla principal de empleados';

-- O alterando una tabla existente
ALTER TABLE empleados MODIFY COLUMN 
    nombre VARCHAR(100) COMMENT 'Nombre completo del empleado';

-- Indices
CREATE INDEX idx_nombre ON empleados(nombre) COMMENT 'Índice para búsquedas por nombre';

-- Eventos
CREATE EVENT mi_evento
ON SCHEDULE EVERY 1 DAY
COMMENT 'Evento de limpieza diaria'
DO
BEGIN
    -- código del evento
END;

ALTER EVENT limpiar_logs_diarios
    COMMENT 'Evento de limpieza diaria. Requiere monitoreo en tabla log_eventos.';
```

Documentación de Mantenimiento:

```sql
/*
* =============================================
* Registro de Cambios
* =============================================
* Fecha       | Autor        | Descripción
* ---------------------------------------------
* 2024-01-20  | Juan Pérez   | Creación inicial
* 2024-01-21  | Ana García   | Agregado manejo de errores
* 2024-01-22  | Pedro López  | Optimización de cursor
* 
* Próximas mejoras planificadas:
* - Agregar soporte para múltiples monedas
* - Implementar caché de resultados
* =============================================
*/
```

Buenas Prácticas de Documentación:

- Mantener un estándar consistente en todo el código
- Documentar parámetros de entrada/salida
- Especificar pre-condiciones y post-condiciones
- Incluir ejemplos de uso cuando sea relevante
- Documentar los handlers y su propósito
- Mantener un registro de cambios actualizado
- Incluir información de rendimiento y optimización
- Documentar las dependencias entre objetos
- Mencionar las tablas afectadas y el tipo de operación
- Incluir información de contacto del responsable

## 8. Recursos adicionales

A continuación se incluyen algunos recursos adicionales de interes:

- [Documentacion oficial de Mysql sobre rutinas almacenadas](https://dev.mysql.com/doc/refman/8.0/en/stored-programs-defining.html)
- [Documentación oficial de Mysql sobre cursores](https://dev.mysql.com/doc/refman/8.0/en/cursors.html)
- [Documentación oficial de Mysql sobre eventos](https://dev.mysql.com/doc/refman/8.0/en/event-scheduler.html)
- [Documentación oficial de Mysql sobre handlers](https://dev.mysql.com/doc/refman/8.0/en/condition-handling.html)
- [Ejercicios resueltos de gonzaleztroyano - github](https://github.com/gonzaleztroyano/ASIR2-ASGBD-Examples)

## 9. Anexo: tablas temporales en MySQL

Las **tablas temporales** (`TEMPORARY TABLES`) en MySQL permiten almacenar datos de manera transitoria dentro de una sesión. Son útiles para manipular datos intermedios sin afectar las tablas reales de la base de datos.  

Cuando se crea una tabla temporal, **solo es accesible en la sesión actual** y se elimina automáticamente cuando la sesión se cierra o cuando se ejecuta `DROP TEMPORARY TABLE`.  

### 9.1. Creación de tablas temporales

**Sintaxis básica:**

```sql
CREATE TEMPORARY TABLE nombre_tabla (
    columna1 INT,
    columna2 VARCHAR(100)
);
```

**Ejemplo de uso:**

```sql
CREATE TEMPORARY TABLE temp_clientes AS 
SELECT id, nombre, ciudad FROM clientes WHERE ciudad = 'Madrid';
```

🔹 **Explicación:** Se crea una tabla temporal `temp_clientes` con los clientes de Madrid.  

### 9.2. Manipulación de datos en tablas temporales

Las tablas temporales se utilizan de la misma manera que las tablas normales. Puedes insertar, actualizar, eliminar y consultar datos en ellas.

**Insertar datos manualmente:**  
```sql
INSERT INTO temp_clientes (id, nombre, ciudad) VALUES (1001, 'Carlos Pérez', 'Madrid');
```

**Actualizar registros:**  
```sql
UPDATE temp_clientes SET ciudad = 'Barcelona' WHERE id = 1001;
```

**Eliminar registros:**  
```sql
DELETE FROM temp_clientes WHERE ciudad = 'Madrid';
```

**Consultar datos en la tabla temporal:**  
```sql
SELECT * FROM temp_clientes;
```

### 9.3. Eliminación de tablas temporales

Las tablas temporales **se eliminan automáticamente** al cerrar la sesión.  
Si necesitas eliminarlas manualmente antes de cerrar la sesión, usa:  

```sql
DROP TEMPORARY TABLE temp_clientes;
```

⚠ **Importante:**  
Si intentas eliminar una tabla temporal con `DROP TABLE` sin `TEMPORARY`, MySQL eliminará una tabla permanente con el mismo nombre si existe.  


### 9.4. Diferencias entre tablas temporales y tablas normales

| Característica        | Tablas temporales | Tablas normales |
|----------------------|-----------------|----------------|
| **Alcance**         | Solo dentro de la sesión actual | Persiste hasta ser eliminada |
| **Disponibilidad**   | Solo para el usuario que la creó | Accesible por todos los usuarios con permisos |
| **Persistencia**     | Se elimina automáticamente al cerrar la sesión | Debe eliminarse manualmente con `DROP TABLE` |
| **Uso recomendado**  | Datos intermedios, cálculos temporales | Datos permanentes en la aplicación |

### 9.5. Casos de uso de tablas temporales

✔ **Optimización de consultas complejas:** Guardar resultados parciales para reducir cálculos repetitivos.  
✔ **Evitar bloqueos en consultas de gran volumen:** Se pueden procesar datos sin afectar las tablas principales.  
✔ **Uso en procedimientos almacenados:** Para almacenar datos temporales durante la ejecución de un procedimiento.  
✔ **Filtrado de datos intermedios:** Agrupar y transformar datos antes de generar reportes finales.  
