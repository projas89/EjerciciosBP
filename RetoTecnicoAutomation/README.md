## Tecnologías
Para el diseño, ejecución y automatización de los casos de prueba se utilizaron las siguientes tecnologías y herramientas:

- Postman: diseño, ejecución y automatización de las pruebas de API.
- JavaScript: implementación de scripts para las validaciones y automatización de los casos de prueba.
- REST API: arquitectura utilizada para la comunicación con los servicios mediante solicitudes HTTP.
- HTML Reporter: generación de reportes en formato HTML con los resultados obtenidos durante la ejecución de las pruebas.

## Detalle del proceso
- Crear una nueva colección en postman: Se crea una nueva Collection en Postman, en la cual se organizan los diferentes requests correspondientes a los casos de prueba.
- Configurar las variables de la colección: Dentro de la colección se define la variable baseUrl, correspondiente a la URL base del servicio que será utilizado durante las pruebas: baseUrl(https://fakestoreapi.com)
- Crear y configurar los requests: Para cada caso de prueba se crea un request de acuerdo con el escenario y los requerimientos establecidos(ejm: {{baseUrl}}/products/1 - En este caso, el identificador 1 corresponde al producto utilizado en el CP01 - Obtener producto específico.)
- Ejecutar el request:Una vez configurado el request, se presiona el botón Send para ejecutar la solicitud y obtener la respuesta del servicio.
- Implementar las validaciones: En la pestaña Tests o Scripts de Postman se agregan los scripts necesarios para automatizar las validaciones correspondientes a cada caso de prueba.
-  Ejecutar las pruebas automatizadas: Una vez configurados los scripts de validación, se ejecuta nuevamente el request mediante el botón Send.
- Postman muestra los resultados de las validaciones en la sección Test Results, donde: PASSED (verde): indica que la validación del caso de prueba fue exitosa, FAILED (rojo): indica que una o más validaciones del caso de prueba no fueron satisfactorias.
  
## Casos automatizados

Se implementaron y automatizaron los siguientes casos de prueba:

- CP01 - Obtener producto específico
- CP02 - Listar productos por categoría
- CP03 - Crear producto
- CP04 - Actualizar producto
- CP05 - Producto no encontrado
- CP06 - Categoría inválida
- CP07 - Crear producto con datos inválidos
- CP08 - Límite de productos
