# Documentación de la fase 1 para el proyecto de laboratorio


##  Requerimientos Técnicos

### Frontend
Para la parte del Frontend se desarrollará con los lenguajes de javascript y python, utilizando 
los frameworks de Angular y Django. Las funciones se separan segun los diferentes microservicios
descritos más adelante.

### Backend
Para el Backend se utilzará los lenguajes de programación NodeJs con el framework de Express,
para el segundo legunaje se utilizará python con el framework de Flask.

### Base de Datos
En la base de datos se utilizará una de tipo relacional, por sus propiedades de ACID, 
ya que esta aplicación por su naturaleza necesita seguridad, y las base de datos relacionales 
suelen ser más seguras, además tiene opciones accesibles como mysql o postgresql, 
estas bases de datos son candidatas, y suelen comunicarse de manera fácil con 
los frameworks mencionados anteriormente.


### Aplicación Responsiva
 Para la parte de la aplicación responsiva, se hará utilziando la herramienta 
 de Boostrap, y al mismo tiempo utilizar sus propiedades para un mejor diseño 
 de la aplicación.


## Comunicación entre los servidores

Para la comunicación entre los servidores se piensa utilizar datos en formato Json
ya que es un estándard de comunicación entre lenguajes de comunicación. 
Dependiendo de la tecnología, se puede utilizar API REST, sin embargo,
dado que existe en python la librería requests, se puedencomunicar via http. 
(esto se describirá más a detalle en los siguientes puntos).


## Diagrama de Autenticación
![image](./src/diagramaAutenticacion.jpg)

## Diagrama de Votación
![image](./src/diagramaVotacion.jpg)

## Diagrama de Registro de ciudadanos
![image](./src/diagramaRegistro.jpg)



## MicroServicios Identificados
### Renap (consulta de información)
    Este microservicio ayudará a recolectar la información de los ciudadanos,
    solo estará para la lectura de la información y saber si el ciudadano puede votar o no
    es basicamente para el lado del backend, la lectura podrá realziarse por medio de su front
    el cual será otro micro servicio.

### Renap (consulta de información) Front
    En este microservicio se mostrará los datos consultados en el backend de Renap
    esto con el fin de ser mayor atractivo. También por su manejo sencillo se hará desde acá
    la carga de datos por parte de los entes encargados o los administradores.


### Creacion de Elecciones (Back)
    Este microservicio se implementará para hacer la creación de las elecciones y los candidatos asignados a dicha
    elección esto es muy importante, tratar de separar este servicio que tenga que ver exclusivamente con las elecciones, todo lo previo antes de votar.

### Creacion de Elecciones (Back)
    Este microservicio se implementará para hacer la creación de las elecciones y los candidatos asignados a dicha
    elección esto es muy importante, tratar de separar este servicio que tenga que ver exclusivamente con las elecciones, todo lo previo antes de votar.

### Creacion de Elecciones (Front)
    Este microservicio se implementará para la parte gráfica de ingreso y creación de las elecciones, ingreso de los candidatos, y asignación de los candidatos a las elecciones correspondientes.


### Registro de Usuarios y Votos (Backend)
    Este microservicio se implementará, para realizar el registro d eusuario con sus campos corresopndientes, (nombre, cui, telefono, foto pin, tipo, país, etc.) al mismo tiempo por la cantidad de integrantes en el equipo se pensará realizar el registro de usuarios
    y las funciones de votación en el mismo servicio. Aqui irá la elección  de candidato durante el voto, la seguridad correspondiente al voto
    el método de seguridad 2FA y la tecnología blockchain.

### Registro de Usuarios y Votos (Frontend)
    Este microservicio se implementará, para realizar el registro d eusuario con sus campos corresopndientes, (nombre, cui, telefono, foto pin, tipo, país, etc.) al mismo tiempo por la cantidad de integrantes en el equipo se pensará realizar el registro de usuarios
    y las funciones de votación en el mismo servicio. Aqui irá la elección  de candidato durante el voto, la seguridad correspondiente al voto
    el método de seguridad 2FA y la tecnología blockchain.



### Creacion de microservicio Base de Datos
    Este microservicio de la base de datos también se realizará, esta base de datos se construirá con una base de datos mysql
    se eligió mysql por su adaptabilidad a los frameworks de para python y nodejs, también está la opción de utilizar
    postgresSql, sin embargo por el tipo de aplicación en la que se requiere seguridad se analiza implementar una base de datos
    relacional por sus propiedades de ACID.



## Descripción de la seguridad de la aplicación.

La seguridad de la aplicación primero que nada inicia con la implementación de una base de datos relacional, de manera que 
sean durables entre otras. En la parte de la autenticación se le sumará un 2FA, para agregarle seguridad en el momento de la votación.
En este caso se piensa agregar un código QR temporal, osea utilizar un 2FA TOTP. En la parte del registro se buscará si es apto para votar
o si su expediente no deja que vote. Luego de eso en la parte del envío de la data se utilizará JWT para encriptar la cadena con llaves y
poder modificar que el token sea temporal. Y por último agregar la tecnología BlockChain al final del voto para serciorase que
el voto sea aceptado por las entidades más importantes, quienes su trabajo es auditar la transparencia.

## Descripción del uso de la tecnología blockchain.
Como se mencionaba anteriormente la tecnología blockchain nos ayudará a poder utilizar a las entidades que se encargan de la transparencia
a funcionar como nodos y que en el momento de cada voto se pueda sercioarar que el voto sea válido y no se haya cometido algún fraude
y quede registrado sin que esos datos puedan editarse.

## Documentación de las Pipelines para los servicios.
Para el caso de los pipelines se utilizarán los que comunmente se trabajan, para garantizar que el softwre cumpla con lo requerido para 
poder ser desplegado, cada una de los microservicios serán testeados para saber si cada una de sus funcionalidades están correctas
luego se procede a construir las imágenes y por último de desplegarlas, teniendo en consideración que por cada microservicio que falle
podrá funcionar la demás aplicación sin que los demás microservicios sean afectados y funcionar correctamente.
