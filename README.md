# Pruebas de Rendimiento y Análisis de Resultados
## Tecnología y versiones
- Versión: Apache JMeter 5.6.3: Diseño y ejecución de pruebas
- Java JDK 17
- JSON: Formato del request
CSV: Manejo de usuarios y contraseñas
HTTP Request(JMeter)
HTTP Header Manager (JMeter0)
Response Assertion (JMeter)
Agreate Reporte (JMeter)
## Paso a paso
* Se crea el archivo que contiene el registro de usuarios y contraseñas (usuario.csv) 
* Crear un Test Plan en JMeter
* Añadir y configurar Thread Group (Parámetros: number of Theads(usuarios virtuales): 10, Ram-up period(Incorporar durante 10 segundos):10, Loop Count (Login ejecutado por 5 veces):5)
* Agregar CSV Data SetConfig: Permite la lectura de cada fila y guarda. filename: (ruta de usurios.csv), file encodin: UTF-8, Variable Names: username,pasword, Delimiter: ; , Sharing mode: All Threads.
* Agregar Constant Throughput, configurar Throughput=1200 (20 solicitudes por segundo - 1200/60)
* Agregar HTTP Request: Configurar los parámetros: Server Name: ,Method: POST, Path: auth/login)
* Configurar Body- JSON: Se debe agregar las variables username y password.
* Confiurar Content-Type
* Agregar un Response Assertion (Validar Http 200)
* Agregar un Duration Assertion para Validar el SLA de 1.15 segundos

* Ejecutar 
