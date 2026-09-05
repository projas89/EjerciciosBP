## Tecnologías

- Postman
- JavaScript
- REST API
- HTML Reporter

## Detalle del proceso
- Crear una nueva colección en postman
- En la nueva colección asignar variable: baseUrl(https://fakestoreapi.com)
- Crear request (de acuerdo a lo indicado y a la solicitud)
- Ingresar la URL (ejm: {{baseUrl}/product/1} - tomado del caso de prueba 1)
- Presionar el botón send
- Agregar validaciones en la pestaña test o Scripts (Automatización de casos de prueba de acuerdo a las validaciones requeridas)
- Una vez configuradas las validaciones, clic en Send (Se despliega la sección Test Result)
- Se visualiza en verde (PASSED) casos de prueba éxitosos
- Se visualiza en rojo (FAILED) casos fallidos.
  
## Casos automatizados

- CP01 - Obtener producto específico
- CP02 - Listar productos por categoría
- CP03 - Crear producto
- CP04 - Actualizar producto
- CP05 - Producto no encontrado
- CP06 - Categoría inválida
- CP07 - Crear producto con datos inválidos
- CP08 - Límite de productos
