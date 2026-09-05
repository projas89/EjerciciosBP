# Pruebas de Rendimiento y Análisis de Resultados
## Tecnología y versiones
Para el diseño, configuración y ejecución de las pruebas de rendimiento se utilizaron las siguientes tecnologías y herramientas:
- Apache JMeter 5.6.3: diseño y ejecución de las pruebas de rendimiento.
- Java JDK 17: entorno de ejecución requerido por JMeter.
- JSON: formato utilizado para estructurar el cuerpo de las solicitudes HTTP.
- CSV: archivo utilizado para gestionar los usuarios y contraseñas empleados durante las pruebas.
- HTTP Request (JMeter): configuración y envío de las solicitudes HTTP.
- HTTP Header Manager (JMeter): configuración de los encabezados HTTP requeridos.
- Response Assertion (JMeter): validación de las respuestas obtenidas del servicio.
- Duration Assertion (JMeter): validación del tiempo máximo de respuesta establecido en el SLA.
- Aggregate Report (JMeter): recopilación y análisis de los resultados obtenidos durante la ejecución.
## Paso a paso
 1. Crear el archivo de usuarios y contraseñas (username, password) : Se crea un archivo usuarios.csv que contiene el registro de los usuarios y sus respectivas contraseñas que serán utilizados durante las pruebas de autenticación:

2. Crear el Test Plan en JMeter: En Apache JMeter se crea un nuevo Test Plan, que será utilizado como estructura principal para organizar y ejecutar los elementos de la prueba de rendimiento.

3. Configurar el Thread Group: Se agrega y configura un Thread Group, que permite definir el comportamiento de los usuarios virtuales durante la prueba.

- Los parámetros configurados son: Number of Threads (usuarios virtuales): 10, Ramp-Up Period: 10 segundos, Loop Count: 5 (Con esta configuración, JMeter simula 10 usuarios virtuales, incorporándolos progresivamente durante un período de 10 segundos, y cada usuario ejecuta el proceso de login 5 veces)

4. Configurar CSV Data Set Config: Se agrega un componente CSV Data Set Config para leer los usuarios y contraseñas almacenados en el archivo usuarios.csv.

- Los parámetros configurados son: Filename: ruta del archivo usuarios.csv, File Encoding: UTF-8, Variable Names: username,password, Delimiter: ;, Sharing Mode: All Threads (De esta manera, los valores de cada fila del archivo CSV pueden utilizarse dinámicamente en las solicitudes realizadas durante la prueba).

5. Configurar el control de rendimiento: Se agrega un elemento Constant Throughput Timer para controlar el número de solicitudes que se generan durante la prueba.

- Se configura un Throughput de 1200 solicitudes por minuto, equivalente a: 1200 / 60 = 20 solicitudes por segundo (Por lo tanto, el objetivo de la prueba es alcanzar aproximadamente 20 solicitudes por segundo).

6. Configurar la solicitud HTTP: Se agrega un elemento HTTP Request para realizar la solicitud al servicio de autenticación.

- Los principales parámetros configurados son: Server Name or IP: servidor donde se encuentra desplegado el servicio, Method: POST, Path: /auth/login
  
7. Configurar el cuerpo de la solicitud: En la sección Body Data del HTTP Request se configura el cuerpo de la solicitud en formato JSON.

- Se utilizan las variables definidas en el archivo CSV para enviar dinámicamente las credenciales de cada usuario:
{
  "username": "${username}",
  "password": "${password}"
}

8. Configurar el Content-Type: Se agrega y configura un HTTP Header Manager para indicar que el contenido enviado en la solicitud corresponde a formato JSON.

- Se establece el encabezado: Content-Type: application/json

9. Configurar Response Assertion:Se agrega un Response Assertion para validar que el servicio responda correctamente.

- Como criterio de validación se establece que la respuesta HTTP debe tener un código de estado:HTTP 200 (OK)

- Esto permite determinar si la solicitud de autenticación fue procesada correctamente desde el punto de vista HTTP.

10. Configurar Duration Assertion:Se agrega un Duration Assertion para validar el cumplimiento del SLA (Service Level Agreement) definido para el servicio.

- El tiempo máximo de respuesta establecido es de:1,15 segundos (1150 ms)
-  Por lo tanto, cada solicitud deberá responder dentro de este tiempo para considerarse dentro del SLA establecido.

11. Ejecutar la prueba: Una vez configurados todos los componentes del Test Plan, se ejecuta la prueba de rendimiento.

- Durante la ejecución se recopilan métricas como:Número de solicitudes realizadas, Porcentaje de errores, Tiempo promedio de respuesta, Tiempo mínimo y máximo de respuesta, Throughput alcanzado, Porcentaje de solicitudes que cumplen el SLA, Resultados de las validaciones realizadas mediante las assertions.

