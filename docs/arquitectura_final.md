**SECCION 1: Estrategia y Alcance**

**Objetivo General**

Desarrollar un Sistema Gestor de Inventarios que permita controlar existencias, registrar entradas y salidas de productos y generar reportes básicos para apoyar la toma de decisiones.

**Requerimientos Funcionales (RF)**
* 1- Registrar productos.
* 2- Actualizar información de productos.
* 3- Registrar entradas de inventario.
* 4- Registrar salidas de inventario.
* 5- Gestionar proveedores.
* 6- Consultar existencias.
* 7- Generar reportes de inventario.

**Requerimientos No Funcionales (RNF)**
* 1- El sistema deberá responder consultas de una manera rapida.
* 2- Solo usuarios autorizados podrán acceder al sistema.
* 3- La información deberá almacenarse de forma persistente.

**Atributos de Calidad Prioritarios**

* Disponibilidad
  El sistema debe permanecer operativo durante la jornada laboral.

* Seguridad
  La informacion debe protegerse contra accesos no autorizados

* Mantenibilidad
  Los módulos deben poder actualizarse sin afectar el resto del sistema.

-----------------------

**SECCION 2: Vista Estructural (C4)**

```mermaid
flowchart TD
  A[Usuario] --> B[Frontend Interfaz de Usuario]
  B --> C[API Gateway]
  C -->D[Microservicios inventario]
  C -->F[Microservicio proveedor]
  D --> E[capa de negocio
  -Gestion de productos
  -Control de stock
  -Entrada y Salida]
  F --> G[Capa de negocio
    - Gestion de compra
    - Orden de compra
    - Recepcion de producto]
  E -->H[Capa de acceso a datos]
  G -->I[Capa de acceso a datos]
  H -->j[InvantarioDB]
  I-->K[ProveedoresDB]
  j -->L[ ]
  K -->L[Microservicio de reporte]
  L -->M[Capa de Negocio
    - Reportes de existencia
    - Reportes de Movimiento
    - Alertas de stock Bajo]
  M-->N[Capa de Acceso a datos]
  N-->O[ReportesDB]
  ```
--------------------
**SECCION 3: Vista de Fronteras y Contratos**

**Flujo Crítico 1: Registrar Entrada de Inventario**

Este proceso inicia cuando un usuario registra la llegada de mercancía al almacén. El sistema recibe la información del producto, el proveedor asociado y la cantidad ingresada.
Una vez validada la información, el servicio de inventario registra el movimiento de entrada, actualiza el stock disponible y genera un identificador único para la operación.
Como resultado, el usuario recibe una confirmación indicando que la entrada fue registrada correctamente junto con la cantidad actualizada de existencias.

**Flujo Crítico 2: Registrar Salida de Inventario**

Este proceso ocurre cuando un usuario registra la salida de productos del almacén por motivos como ventas, devoluciones o consumo interno.
El sistema recibe la información del producto, la cantidad que será retirada y el motivo de la salida. Posteriormente valida que exista suficiente inventario disponible para completar la operación.
Si la validación es exitosa, se registra el movimiento, se descuenta la cantidad correspondiente del stock y se devuelve una confirmación con el nuevo nivel de existencias.

**Manejo de Caja Rota (Resiliencia)**

Si durante cualquiera de los procesos anteriores la base de datos deja de estar disponible, el sistema no intentará continuar con la operación para evitar inconsistencias en la información.
En este escenario, se mostrará al usuario un mensaje indicando que el servicio se encuentra temporalmente no disponible y que debe intentar nuevamente más tarde.
Adicionalmente, el error será registrado en los archivos de monitoreo internos para facilitar su diagnóstico y corrección por parte del equipo técnico. 
En ningún caso se mostrarán detalles técnicos, excepciones o stacktraces al usuario final, garantizando la seguridad y una mejor experiencia de uso.

----------------------------------------------------------

**SECCION 4: Vista de Persistencia (DER)**

**Entidades**
Categorias
Productos
Proveedores
Usuarios
Entradas_Inventario
Salidas_Inventario

**Relaciones**
Categorias 1:N Productos
Productos 1:N Entradas_Inventario
Productos 1:N Salidas_Inventario
Entradas_Inventario N:1 Proveedores
Salidas_Inventario N:1 Usuarios

**Diccionario de Datos**

## Sistema Gestor de Inventarios

### Tabla: Categorias
--------------------------------------------------------------------------------
|Campo          |Tipo de Dato  |Tamaño    |Restricciones |Descripción |
|:--------------|:-----------:|:---------:|:------------:|-----------:|
|id_categoria   | INT         |   11       |   PK,AUTO_INCREMENT,NOT NULL |Identificador unico de entrada|
|Nombre_categoria|INT| 100|   NOT NULL| Nombre de la categoria
|Descripcion|VARCHAR| 255|  NULL|Descripcion de la categoria|

---------------------------------------------------------------------------------

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


```mermaid
erDiagram
    Categorias ||--o{ Productos : contiene
    Productos ||--o{ Entradas_Inventarios : genera
    Productos ||--o{ Salidas_inventarios : genera
    Entradas_Inventarios||--|{ Proveedores : alta
    Salidas_inventarios ||--o{ Usuarios : baja
    
    Categorias {
        int id_Categoria 
        string Nombre_Categoria
        string Descripcion
    }
    Productos {
        int  Id_Producto
        varchar Nombre 
        varchat Descripcion
        decimal Precio_Unitario 
        int Stock_Actual 
        int Stock_Minimo 
        int Id_Categoria
    }
    Proveedores {
        string Id_Proveedor
        string Nombre_Empresa
        float Telefono
        int Correo
        int Direccion
    }
    Usuarios {
        string Id_Usuarios
        string Nombre
        float Correo
        int Password
        int Rol
        int Estado
    }    
    Entradas_Inventarios {
        string Id_Entradas
        string Fecha_Entrada
        float Cantidad
        int Id_Producto
        int Id_Proveedor
        int Id_Usuarios
    }  
    Salidas_inventarios {
        string Id_Salida
        string Fecha_Salida
        float Cantidad
        int Motivo
        int Id_Producto
        int Id_Usuarios
    }  
```

------------------------------

**SECCION 5: Vista de Despliegue e Infraestructura**

**Tipo de Despliegue Seleccionado**

Despliegue Local.

**Infraestructura**
* Frontend React.
* API Gateway.
* Microservicio Inventario.
* Microservicio Proveedores.
* Microservicio Reportes.
* Base de Datos MySQL.

**Justificación**

Se eligió un despliegue local porque simplifica el desarrollo y las pruebas del MVP. Además, reduce costos de infraestructura y facilita la integración de todos los componentes en un único entorno controlado.

**Escenario de Resiliencia**

Si la base de datos deja de responder durante 10 minutos:
* Los microservicios detectan el fallo.
* Se devuelve un mensaje controlado al usuario.
* No se muestran detalles internos del sistema.
* Se registran los errores para diagnóstico posterior.
* La interfaz continúa funcionando y notificando el problema de manera amigable.

