**FASE 1: Investigación Técnica**

1.  **Métodos HTTP Semánticos:**

-   **GET:** Se utiliza para pedir o recuperar un dato o elemento.
-   **POST:** Se suele utilizar para agregar un dato o elemento al
    sistema.
-   **PUT:** Se usa para hacer cambios en valores de datos ya
    existentes.
-   **DELETE:** Borra un dato.
-   **PATCH:** Se usa para agregar datos de forma parcial.

**2. Estructura JSON**

JSON(**JavaScript Object Notation)** Es un formato de intercambio de
datos basado en el lenguaje JavaScript. Un ejemplo puede ser:

{
\"Id_Producto\": 1,
\"nombre\": \"Laptop\",
\"stock\": 15
}

Al ser mas liger, y fácil de entender este mismo destaco por encima de
XML como un estándar universal además de la utilización de menos
recursos y menor demanda de ancho de banda

**3. Códigos de Error HTTP**

Los códigos HTTP se agrupan en familias según el tipo de respuesta.
1.  **Respuestas informativas (100--199),**
2.  **Respuestas satisfactorias (200--299),**
3.  **Redirecciones (300--399),**
4.  **Errores de los clientes (400--499),**
5.  **Errores de los servidores (500--599).**

**Ejemplos**:

**100-199**

**100 Continue**
La petición fue aceptada correctamente y queda a la espera de la acción
del usuario

**102 Prosessing**
El servidor aun esta procesando la solicitud

**200-299**

**201 Created**
La petición se creo y se ejecuto correctamente

**204 No content**
Se ejecuto la petición sin embargo no existe contenido

**300-399**

**300 Multiple choice**
El servidor espera una respuesta del cliente ante multiples opciones

**308 Permanent Redirect**
El servidor URL del servidor ha cambiado y te redirecciona
automaticamente

**400-499**

> **400 Bad Request**\
> Indica que la solicitud enviada por el cliente contiene datos
> incorrectos o incompletos.

> **404 Not Found**\
> Indica que el recurso solicitado no existe.

> **418 Im a teapot**
> El servidor es una tetera

**500-599**

> **503 Service Unavailable**\
> Indica que el servidor no puede procesar la solicitud temporalmente
> debido a una sobrecarga o a que algún servicio necesario no está
> disponible, como una base de datos fuera de línea.

**504 Gateway timeout**
Cuando el servidor no recibe una respuesta en un tiempo determinado

**Diferencia entre 400, 404, 503**

El código 400 se refiere a que el usuario ingreso datos incorrectos e
incompletos, mientras que el 404 se refiere a que el registro no existe
por lo tanto no puede ejectuarse la acción y el código 503 nos dice que
el servidor no se encuentra disponible

**4. Especificación OpenAPI (Swagger)**

OpenAPI, Es una herramienta que ayuda a que los desarrolladores de APIs,
logren corroborar que su sistema Funciona para mutiples sistemas que
requieran de el.

Swagger es una aplicación que ayuda a la implementación de OpenAPI
funcionando como un sistema de documentación.

**5. Contratos de Interfaz (Código)**

Se puede entender como un contrato inmutable ya que maneja una serie de
reglas claras entre los componentes del sistema.

**6. Manejo de Excepciones y Resiliencia**

Un StacktraceMuestra de manera detallada cada uno de los errores que el
sistema detecte, este mismo es de suma importancia para los
desarrolladores ya que con ello pueden identificar el problema

**¿Porque no mostrarlo al cliente?**

Porque podría comprometer información sensible de la empresa como podrán
ser nombres de las tablas, rutas direcciones ocultas etc.

**FASE 2: Análisis del Caso de Estudio**

El escenario que más se acerca a lo que es la arquitectura de nuestro
proyecto es el Cajero Web ya que utilizamos un modelo de capas, y de
estilo de microservicios, por ende el caso Web es el que mas se ajusta a
nuestro proyecto de inventarios.

**REFERENCIAS**

<https://developer.mozilla.org/es/docs/Web/HTTP/Reference/Methods>

<https://datatracker.ietf.org/doc/html/rfc9110#name-method-definitions>

<https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/JSON>

<https://developer.mozilla.org/es/docs/Web/HTTP/Reference/Status>

<https://learn.microsoft.com/es-es/microsoft-cloud/dev/dev-proxy/concepts/what-is-openapi-spec>
