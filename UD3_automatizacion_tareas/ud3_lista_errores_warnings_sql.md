# UD3 - Automatización de tareas: Construcción de guiones de administración

## Lista de errores y warnings comunes en MySQL

MySQL proporciona códigos de error y warning para ayudar a los desarrolladores a identificar y solucionar problemas en sus consultas y procedimientos almacenados. En esta guía, veremos algunos de los errores y warnings más comunes que puedes encontrar al trabajar con MySQL.

### Códigos de error comunes (SQLEXCEPTION)

1. **`1062` - Duplicate entry (Entrada duplicada)**
   - **Descripción:** Ocurre cuando se intenta insertar o actualizar un valor que viola una restricción `UNIQUE`.
   - **Ejemplo:** Insertar un valor duplicado en una columna con clave única.
   - **Mensaje típico:** `Duplicate entry 'valor' for key 'nombre_indice'`.

2. **`1048` - Column cannot be null (Columna no puede ser nula)**
   - **Descripción:** Ocurre cuando se intenta insertar o actualizar un valor `NULL` en una columna que tiene la restricción `NOT NULL`.
   - **Mensaje típico:** `Column 'nombre_columna' cannot be null`.

3. **`1452` - Foreign key constraint fails (Falla la restricción de clave foránea)**
   - **Descripción:** Ocurre cuando se intenta insertar o actualizar un valor que viola una restricción de clave foránea.
   - **Mensaje típico:** `Cannot add or update a child row: a foreign key constraint fails`.

4. **`1366` - Incorrect integer value (Valor entero incorrecto)**
   - **Descripción:** Ocurre cuando se intenta insertar o actualizar un valor que no coincide con el tipo de dato de la columna.
   - **Mensaje típico:** `Incorrect integer value: 'valor' for column 'nombre_columna'`.

5. **`1264` - Out of range value (Valor fuera de rango)**
   - **Descripción:** Ocurre cuando se intenta insertar o actualizar un valor que excede el rango permitido para el tipo de dato de la columna.
   - **Mensaje típico:** `Out of range value for column 'nombre_columna'`.

6. **`1216` - Cannot add or update a child row (No se puede agregar o actualizar una fila hija)**
   - **Descripción:** Ocurre cuando se intenta insertar o actualizar una fila que viola una restricción de clave foránea.
   - **Mensaje típico:** `Cannot add or update a child row: a foreign key constraint fails`.

7. **`1217` - Cannot delete or update a parent row (No se puede eliminar o actualizar una fila padre)**
   - **Descripción:** Ocurre cuando se intenta eliminar o actualizar una fila que está referenciada por una clave foránea en otra tabla.
   - **Mensaje típico:** `Cannot delete or update a parent row: a foreign key constraint fails`.

8. **`1146` - Table doesn't exist (La tabla no existe)**
   - **Descripción:** Ocurre cuando se intenta acceder a una tabla que no existe.
   - **Mensaje típico:** `Table 'nombre_bd.nombre_tabla' doesn't exist`.

9. **`1054` - Unknown column (Columna desconocida)**
   - **Descripción:** Ocurre cuando se hace referencia a una columna que no existe en la tabla.
   - **Mensaje típico:** `Unknown column 'nombre_columna' in 'field list'`.

10. **`1292` - Truncated incorrect value (Valor truncado incorrecto)**
    - **Descripción:** Ocurre cuando se intenta insertar o actualizar un valor que no coincide con el formato esperado (por ejemplo, una fecha incorrecta).
    - **Mensaje típico:** `Incorrect date value: 'valor' for column 'nombre_columna'`.

11. **`1205` - Lock wait timeout exceeded (Tiempo de espera de bloqueo excedido)**
    - **Descripción:** Ocurre cuando una transacción espera demasiado tiempo para adquirir un bloqueo.
    - **Mensaje típico:** `Lock wait timeout exceeded; try restarting transaction`.

12. **`1064` - Syntax error (Error de sintaxis)**
    - **Descripción:** Ocurre cuando hay un error en la sintaxis de una consulta SQL.
    - **Mensaje típico:** `You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version`.

13. **`1406` - Data too long for column (Datos demasiado largos para la columna)**
    - **Descripción:** Ocurre cuando se intenta insertar o actualizar un valor que excede el tamaño máximo permitido para la columna.
    - **Mensaje típico:** `Data too long for column 'nombre_columna'`.

14. **`3819` - Check constraint violation (Violación de restricción CHECK)**
    - **Descripción:** Ocurre cuando se viola una restricción `CHECK` definida en una columna.
    - **Mensaje típico:** `Check constraint 'nombre_restriccion' is violated`.

### Códigos de warning comunes (SQLWARNING)

1. **`1265` - Data truncated for column (Datos truncados para la columna)**
   - **Descripción:** Ocurre cuando se inserta o actualiza un valor que se trunca para ajustarse al tamaño de la columna.
   - **Mensaje típico:** `Data truncated for column 'nombre_columna'`.

2. **`1263` - Column set to default value (Columna establecida a valor por defecto)**
   - **Descripción:** Ocurre cuando se inserta un valor `NULL` en una columna que no permite `NULL`, y se usa el valor por defecto.
   - **Mensaje típico:** `Column set to default value; NULL supplied to NOT NULL column 'nombre_columna'`.

3. **`1364` - Field doesn't have a default value (Campo no tiene un valor por defecto)**
   - **Descripción:** Ocurre cuando se intenta insertar un valor `NULL` en una columna que no permite `NULL` y no tiene un valor por defecto.
   - **Mensaje típico:** `Field 'nombre_columna' doesn't have a default value`.

4. **`1048` - Column cannot be null (Columna no puede ser nula)**
   - **Descripción:** Similar al error `1048`, pero en algunos casos se maneja como un warning.
   - **Mensaje típico:** `Column 'nombre_columna' cannot be null`.

5. **`1262` - Row truncated (Fila truncada)**
   - **Descripción:** Ocurre cuando se inserta una fila y algunos valores se truncan para ajustarse a las restricciones de la tabla.
   - **Mensaje típico:** `Row X was truncated; it contained more data than there were input columns`.

### Códigos de estado SQL (SQLSTATE)

Además de los códigos de error numéricos, MySQL utiliza códigos de estado SQL (`SQLSTATE`) para categorizar errores. Algunos comunes son:

1. **`23000` - Integrity constraint violation (Violación de restricción de integridad)**
   - Incluye errores como `1062` (duplicados) y `1452` (clave foránea).

2. **`22001` - String data, right truncated (Datos de cadena truncados)**
   - Relacionado con el warning `1265`.

3. **`22003` - Numeric value out of range (Valor numérico fuera de rango)**
   - Relacionado con el error `1264`.

4. **`42000` - Syntax error or access violation (Error de sintaxis o violación de acceso)**
   - Incluye errores como `1064` (sintaxis) y `1142` (permisos).

5. **`HY000` - General error (Error general)**
   - Un código genérico para errores no categorizados.

### **Cómo declarar HANDLERs para estos errores**

Puedes declarar `HANDLER`s para capturar estos errores o warnings en procedimientos almacenados. Por ejemplo:

```sql
DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
BEGIN
    -- Manejar errores (SQLEXCEPTION)
    GET DIAGNOSTICS CONDITION 1
    @errno = MYSQL_ERRNO, @errmsg = MESSAGE_TEXT;
    SELECT CONCAT('Error: ', @errno, ' - ', @errmsg) AS error_message;
END;

DECLARE CONTINUE HANDLER FOR SQLWARNING
BEGIN
    -- Manejar warnings (SQLWARNING)
    GET DIAGNOSTICS CONDITION 1
    @warnno = MYSQL_ERRNO, @warnmsg = MESSAGE_TEXT;
    SELECT CONCAT('Warning: ', @warnno, ' - ', @warnmsg) AS warning_message;
END;
```
