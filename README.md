# Gas Mapocho - Config Server

Este repositorio contiene el Config Server del proyecto **Gas Mapocho**, desarrollado para el curso de Desarrollo de Aplicaciones Web II de Cibertec.

Su función es centralizar las configuraciones de los microservicios para que todos puedan obtener sus propiedades desde un mismo lugar, sin necesidad de tenerlas repetidas en cada proyecto.

## Tecnologías utilizadas

- Java 25
- Spring Boot
- Spring Cloud Config Server
- Netflix Eureka Client
- Maven
- Docker

## ¿Cómo funciona?

El Config Server se encarga de obtener las configuraciones desde un repositorio y proporcionarlas a los demás microservicios.

Por ejemplo, el servicio de pedidos puede solicitar su configuración dependiendo del entorno en el que se encuentre, ya sea desarrollo o producción.

De esta manera, si necesitamos cambiar alguna propiedad, podemos hacerlo desde el repositorio de configuraciones sin tener que modificar directamente el código de cada microservicio.

## Requisitos

Para ejecutar el proyecto necesitamos:

- JDK 25
- Git
- Maven (o utilizar el Maven Wrapper incluido)
- Docker (opcional)

## Instalación

Primero clonamos el repositorio:

```bash
git clone https://github.com/Sophia-1827/DAW-II_Grupo09_gasmapocho_config-server.git
```

Ingresamos a la carpeta:

```bash
cd DAW-II_Grupo09_gasmapocho_config-server
```

Compilamos el proyecto:

```bash
.\mvnw.cmd clean install
```

Finalmente, ejecutamos el servidor:

```bash
.\mvnw.cmd spring-boot:run
```

## Configuración

El Config Server está pensado para trabajar en el puerto **8888**.

Una vez que esté funcionando y tenga acceso a las configuraciones, podemos realizar peticiones como estas:

**Configuración de pedidos en desarrollo:**

```http
GET http://localhost:8888/pedido-service/dev
```

**Configuración de pedidos en producción:**

```http
GET http://localhost:8888/pedido-service/prod
```

El servidor devolverá las propiedades correspondientes, siempre que estén disponibles en el repositorio de configuraciones.

## Ejecución con Docker

También podemos levantar el proyecto utilizando Docker.

Primero construimos la imagen:

```bash
docker build -t gasmapocho-config-server .
```

Luego ejecutamos el contenedor:

```bash
docker run -p 8888:8888 gasmapocho-config-server
```

## Relación con los demás microservicios

Este proyecto forma parte de la arquitectura de microservicios de Gas Mapocho.

El Config Server proporciona las configuraciones que necesitan los demás servicios, como el API Gateway, pedidos y pagos.

También utiliza Eureka Client para integrarse con el servidor de descubrimiento de servicios.

Es recomendable tener levantados los servicios de infraestructura antes de iniciar los microservicios que dependan de ellos.

## Integrantes

**Grupo 09 - Cibertec**

## Curso

Desarrollo de Aplicaciones Web II
