# Diccionario de Datos

## Sistema Gestor de Inventarios

### Tabla: Categorias
--------------------------------------------------------------------------------
|Campo          |Tipo de Dato  |Tamaño    |Restricciones |Descripción |
|:--------------|:-----------:|:---------:|:------------:|-----------:|
|id_categoria   | INT         |   11       |   PK,AUTO_INCREMENT,NOT NULL |Identificador unico de entrada|
|Nombre_categoria|INT| 100|   NOT NULL| Nombre de la categoria
|Descripcion|VARCHAR| 255|  NULL|Descripcion de la categoria|
--------------------------------------------------------------------------------

### Tabla: Productos

--------------------------------------------------------------------------------
|Campo          |Tipo de Dato  |Tamaño    |Restricciones |Descripción |
|:--------------|:-----------:|:---------:|:------------:|-----------:|
|Id_Producto|INT|11|PK, AUTO_INCREMENT, NOT NULL|Identificador unico del producto|
|Nombre|VARCHAR|100|NOT NULL|NOMBRE DEL PRODUCTO|
|Descripcion| VARCHAR| 255 |NULL| DESCRIPCION DEATALLADA|
|Precio_Unitario|DECIMAL| 10.2| NOT NULL|PRECIO UNITARIO DEL PRODUCTO|
|Stock_Actual|INT| 11 |NOT NULL| PRECIO UNITARIO DEL PRODUCTO|
|stock_actual|INT|11|NOT NULL|Cantidad disponible en inventario|
|stock_minimo|INT|11|NOT NULL|Cantidad mínima permitida|
|stock_minimo|INT |11 |NOT NULL |Cantidad mínima permitida|
-------------------------------------------------------------------------------

### Tabla: Proveedores

--------------------------------------------------------------------------------
|Campo          |Tipo de Dato  |Tamaño    |Restricciones |Descripción |
|:--------------|:-----------:|:---------:|:------------:|-----------:|
|id_proveedor|INT|11|PK, AUTO_INCREMENT, NOT NULL|Identificador único del proveedor|
|nombre_empresa|VARCHAR|150|NOT NULL|Nombre de la empresa proveedora|
|telefono|VARCHAR|20|NULL|Número telefónico|
|correo|VARCHAR|100|NULL|Correo electrónico|
|direccion|VARCHAR|200|NULL|Dirección física|
------------------------------------------------------------------------------

### Tabla: Usuarios

--------------------------------------------------------------------------------
|Campo          |Tipo de Dato  |Tamaño    |Restricciones |Descripción |
|:--------------|:-----------:|:---------:|:------------:|-----------:|
|id_usuario|INT|11|PK, AUTO_INCREMENT, NOT NULL|Identificador único del usuario|
|nombre|VARCHAR|100|NOT NULL|Nombre completo|
|correo|VARCHAR|100|UNIQUE, NOT NULL|Correo electrónico|
|password|VARCHAR|255|NOT NULL|Contraseña cifrada|
|rol|VARCHAR|50|NOT NULL|Rol del usuario|
|estado|BOOLEAN|-|NOT NULL|Estado de la cuenta|

--------------------------------------------------------------------------

### Tabla: Entradas_Inventario

--------------------------------------------------------------------------------
|Campo          |Tipo de Dato  |Tamaño    |Restricciones |Descripción |
|:--------------|:-----------:|:---------:|:------------:|-----------:|
|id_entrada|INT|11|PK, AUTO_INCREMENT, NOT NULL|Identificador de entrada|
|fecha_entrada|DATETIME|-|NOT NULL|Fecha y hora del movimiento|
|cantidad|INT|11|NOT NULL|Cantidad ingresada|
|id_producto|INT|11|FK, NOT NULL|Producto ingresado|
|id_proveedor|INT|11|FK, NOT NULL|Proveedor relacionado|
|id_usuario|INT|11|FK, NOT NULL|Usuario que registró la entrada|

-----------------------------------------------------------------------------

### Tabla: Salidas_Inventario

--------------------------------------------------------------------------------
|Campo          |Tipo de Dato  |Tamaño    |Restricciones |Descripción |
|:--------------|:-----------:|:---------:|:------------:|-----------:|
|id_salida|INT|11|PK, AUTO_INCREMENT, NOT NULL|Identificador de salida|
|fecha_salida|DATETIME|-|NOT NULL|Fecha y hora del movimiento|
|cantidad|INT|11|NOT NULL|Cantidad retirada|
|motivo|VARCHAR|100|NOT NULL|Motivo de la salida|
|id_producto|INT|11|FK, NOT NULL|Producto retirado|
|id_usuario|INT|11|FK, NOT NULL|Usuario que registró la salida|
