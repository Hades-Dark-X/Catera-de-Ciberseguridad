Descripción del proyecto

La empresa requiere recuperar información específica de la base de datos, con el objetivo de investigar posibles problemas de seguridad y actualizar las pc que necesiten actualización para mantener a la organización segura y en optimo funcionamiento

Mi objetivo:

Recuperar información especifica mediante consultas SQL a la base de datos

Análisis:

La base de datos organization contiene las siguientes tablas:

- log_in_attempts

- employees

## log_in_attempts

La tabla log_in_attempts (intentos de inicio de sesión) incluye las siguientes columnas:

- event_id: El número de identificación asignado a cada evento de inicio de sesión.

- username: El nombre de usuario del/de la empleado/a.

-  login_date: La fecha en que se registró el intento de inicio de sesión.

- login_time: La hora en que se registró el intento de inicio de sesión.

- country: El país donde tuvo lugar el intento de inicio de sesión.

- ip_address: La dirección IP del equipo de ese/a empleado/a.

- success: El éxito del intento de inicio de sesión; FALSE indica un intento fallido.

En el shell MariaDB, estas columnas se devuelven como:

![](file:///C:\Users\Marcos\AppData\Local\Temp\ksohtml28460\wps1.jpg) 

## employees (empleados/as)

La tabla employees (empleados/as) incluye las siguientes columnas:

- employee_id: El número de identificación asignado a cada empleado/a.

- device_id: El número de identificación asignado a cada dispositivo que usa el/la empleado/a.

- username: El nombre de usuario del/de la empleado/a.

- department: El departamento al que pertenece el/la empleado/a.

- office: La oficina donde se encuentra el/la empleado/a.

En el shell MariaDB, estas columnas se devuelven como:

![](file:///C:\Users\Marcos\AppData\Local\Temp\ksohtml28460\wps2.jpg) 

## Recupera intentos de acceso fallidos después del horario de atención

EL equipo está investigando intentos de acceso fallidos realizados después del horario de atención. Si deseo recuperar esta información de la actividad de acceso e identificar todos los intentos fallidos después de las 6:00 p.m.

Realizo la siguiente consulta SQL:

SELECT *

->FROM log_in_attempts

-> WHERE login_time > “18:00” AND success = “false”;

El operador “>” le indica a SQL que la hora debe ser mayor de las 6pm

El operador AND le indica a SQL que se debe cumplir las dos condiciones y devolver los resultados

> NOTA: La columna success de la tabla log_in_attempts contiene valores de TRUE o FALSE para indicar si el acceso se concretó.

![](file:///C:\Users\Marcos\AppData\Local\Temp\ksohtml28460\wps3.jpg) 

## Recupera intentos de acceso en fechas específicas

Mi equipo está investigando eventos sospechosos que ocurrieron el 2022-05-09. Debo recuperar todos los intentos de acceso que ocurrieron ese día y el anterior 2022-05-08.

Para lo cual hago la siguiente consulta SQL

SELECT *

->FROM log_in_attempts

-> WHERE login_date = “2022-05-09” OR login_date = “2022-05-08”;

El operador OR le indica a SQL que se debe cumplir por lo menos una de las dos condiciones

![](file:///C:\Users\Marcos\AppData\Local\Temp\ksohtml28460\wps4.jpg) 

## Recupera intentos de acceso realizados fuera de México

Ahora, el equipo está investigando accesos que no se originaron en México y necesito encontrar esa información.

Entonces realizo la siguiente consulta SQL

SELECT *

->FROM log_in_attempts

-> WHERE NOT country LIKE “MEX%”;

El operador NOT le indica a SQL que se debe negar la condición que se esta pasando

> NOTA: en consultas anteriores se puede ver que Mexico puede aparecer como: MEXICO o MEX,por  eso hago la consulta con LIKE “MEX%”, para indicar que busque palabras que contengan la palabra “MEX”

![](file:///C:\Users\Marcos\AppData\Local\Temp\ksohtml28460\wps5.jpg) 

## Recupera información de los empleados de Marketing

El equipo está actualizando las máquinas de los empleados y necesitamos obtener información sobre los empleados del departamento de Marketing de todas las oficinas del edificio East,

Para obtener esa información hago lo siguiente

SELECT *

->FROM employees

-> WHERE department = “Marketing” AND office = “East%”;

El operador AND le indica a SQL que se debe cumplir las dos condiciones para devolver un resultado

![](file:///C:\Users\Marcos\AppData\Local\Temp\ksohtml28460\wps6.jpg) 

## Recupera información de los empleados de Finanzas o Ventas

Ahora, el equipo necesita realizar una actualización diferente en las computadoras de todos los empleados del departamento de Finanzas o de Ventas, y necesito encontrar la información correspondiente.

Lo hago con la siguiente consulta

SELECT *

->FROM employees

-> WHERE department = “Finance” OR department = “Sales”;

El operador OR le indica a SQL que se debe cumplir por lo menos una de las dos condiciones

![](file:///C:\Users\Marcos\AppData\Local\Temp\ksohtml28460\wps7.jpg) 

## Recupera información de los empleados que no pertenecen al departamento de TI

El equipo necesita hacer una actualización más. Esta actualización ya se realizó en las computadoras de los empleados del departamento de Tecnología de la información. El equipo necesita información sobre los empleados que no pertenecen a ese departamento.

Uso la siguiente consulta

SELECT *

->FROM employees

-> WHERE NOT department = “Information Technology”;

El operador OR le indica a SQL que debe negarse la condición que le estamos dando

![](file:///C:\Users\Marcos\AppData\Local\Temp\ksohtml28460\wps8.jpg) 

## Resumen

Aplicamos filtros sobre diversas consultas

Se trabajo con distintas tablas de una base de datos para obtener la información necesaria

Se hizo uso de operadores como: AND, OR, NOT ademas se uso LIKE como comodín y se trabajo con patrones mediante “%”

Se logro el objetivo propuesto al inicio del análisis.