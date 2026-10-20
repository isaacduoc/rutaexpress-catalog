# RutaExpress — Microservicio Catalog (EP2)

Microservicio de catálogo y gestión de tickets de bodega del proyecto académico RutaExpress.

## Función principal

Catalog participa en el procesamiento de envíos y la gestión de información de bodega.

Se integra con RabbitMQ para procesar mensajes de forma asíncrona y utiliza Oracle Database para persistir la información correspondiente.

## Tecnologías

- Java 21
- Spring Boot
- Maven
- Oracle Database
- RabbitMQ
- Docker

## Arquitectura

El microservicio forma parte de una arquitectura de microservicios desplegada en AWS.

**Flujo de procesamiento:**

Shipments → RabbitMQ → Catalog → Oracle Database

## Integración con RabbitMQ

Catalog participa en el procesamiento de mensajes relacionados con tickets de bodega.

La routing key utilizada para este proceso es `warehouse.ticket`.

El procesamiento de mensajes se integra con la configuración de colas, confirmaciones y manejo de errores de RabbitMQ.

## Base de datos

Catalog utiliza Oracle Database para almacenar información del dominio de bodega, incluyendo los tickets generados durante el flujo de envíos.

Las credenciales y parámetros de conexión deben configurarse mediante variables de entorno, sin publicar contraseñas en GitHub.

## Compilación

Desde la carpeta del microservicio, en Windows:

```powershell
.\mvnw.cmd -DskipTests clean package
```

La opción `-DskipTests` omite la ejecución de pruebas automatizadas.

## Docker

El repositorio incluye un `Dockerfile` para construir la imagen del microservicio.

Puerto interno utilizado: **8083**.

El despliegue en AWS se administra desde el repositorio principal mediante Docker Compose.

## Evidencias EP2

Durante las pruebas de integración se verificó el procesamiento de mensajes de bodega y la persistencia de tickets en Oracle.

## Repositorio principal

https://github.com/isaacduoc/rutaexpress

Proyecto académico RutaExpress — Entrega Parcial 2.