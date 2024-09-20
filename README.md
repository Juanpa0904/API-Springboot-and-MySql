# LABORATORIO 1


INSTRUCTIVO DEL LABORATORIO (Se encuentra el docuemnto con imagenes en el repositorio)

Creación de un proyecto API Rest con el framework Spring Boot, motor de base de datos MySQL, JAVA, JPA y repositorio de dependencia Maven.
A través del IDE Eclipse se realizará la creación de la aplicación Laboratorio1 con las anteriores tecnologías mencionadas, para esto Eclipse deberá tener configurado Spring Boot la cual se puede realizar por la opción Help 🡪 Eclipse Marketplace  para posterior mente buscar Spring Boot.
   
Creación de base de datos “ppooii” y la tabla “persona”,  para el proceso se debe tener la base de datos con algunos datos referentes para la generación y visualización correspondiente. 

La tabla persona se crea con tres campos 
ID: identificador único de los registros de persona de tipo bigint configurado AUTO_INCREMENT y con el constraint PRIMARY KEY
PNOMBRE: representa el primer nombre de una persona y será de tipo varchar y no podrá ser null
EDAD: representa la edad de la persona y será de tipo INT y puede ser null.

CREATE DATABASE `ppooii` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */;
-- ppooii.persona definition
CREATE TABLE `persona` (
  `ID` bigint NOT NULL AUTO_INCREMENT,
  `PNOMBRE` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL,
  `EDAD` int DEFAULT NULL,
  PRIMARY KEY (`ID`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

Creación de proyecto Sprint Boot
Crear un nuevo proyecto Spring con la opción “Spring Starter Project”

Realizar las siguientes configuraciones iniciales del proyecto, como lo es el nombre, el tipo de repositorio de dependencias Mave y la definición del paquete como lo muestra la imagen.

Al dar siguiente habilitar las respectivas dependencias del proyecto como lo muestra la imagen
Spring Data JPA
Spring Web
MySQL Driver
Rest Repositories



Continuar con la configuración y dar finalizar 


Terminada la configuración se creará un proyecto con la siguiente estructura




Se realiza la configuración de la base de datos creada en el punto 1 de la siguiente forma. Importante configurar un puerto que no esté ocupado por alguna aplicación previamente instalada.



Seguida esta configuración corre el proyecto como una aplicación Sprint Boot.



Y en la consola de salida se podrá evidenciar la inicialización del proyecto Laboratorio y donde se verifica el puerto por donde los servicios Rest serán accedidos.

Creación de paquete, entidad persona, repositorio, servicio y controlador
Creación de la entidad “Persona”, la cual a través de la etiqueta @Entity se accederá a la persistencia de la tabla persona de la BD.

Primero se crea el paquete “Entities”


A continuación, se crea la clase “Persona” que representa la entidad, respetando las anotaciones configuradas.

      




Creación de la interfaz de repositorio en la cual se definen los métodos de acceso a la entidad, en este caso a los definidos por JpaRepository y CrudRepository con la anotación @Repository.

Primero se crea el paquete “Repository”

		A continuación, se crea la respectiva interfaz

		

Creación de los servicios que serán accedidos desde el controlador, para esto se define a través, de una interfaz los servicios que se implementarán posteriormente en la clase “PersonaServiceImpl” la cual se definirá con la anotación @Service.

Primero se crea el paquete “Services”
  
Se definen los métodos a implementar a través de la interfaz “IPersonaService” 


Por último, se crea la clase “PersonaServiceImpl” la cual implementa los métodos definidos en la interfaz “IPersonaService”. 
En esta clase se puede identificar la declaración de un atributo de tipo 
“PersonaRepository”, el cual permitirá a los métodos implementados del servicio acceder a la capa de persistencia realizando operaciones de extracción de datos, creación, actualizaciones y eliminación.


   






Creación del controlador, el cual definirá las formas de acceso a los servicios implementados usando la anotación @RestController

Primero se crea el paquete “Controller”
 

Seguido a lo anterior se crea la clase “PersonaController”, en esta clase se crea un atributo de tipo “PersonaServiceImpl” con el cual se accede a los métodos implementados del servicio de persona.
También se definen los diferentes métodos (GET, POST, PUT, DELETE) de acceso a los servicios.

  






Verificación acceso a los servicios con su respectivo método





Configurar y validar los demás servicios de consulta configurados en el controlador





