# Instrucciones para Ejecutar la Plataforma de E-commerce

A continuación, se presentan las instrucciones para ejecutar la plataforma de e-commerce, incluyendo la opción de descargar submódulos desde el repositorio principal.

## Requisitos Previos

Asegúrate de tener instalado Node.js y npm en tu máquina. También necesitarás Docker si planeas usar LocalStack para simular el entorno en la nube.

## Diagrama de Alto Nivel

Aquí deberías incluir el diagrama de alto nivel de la aplicación que ilustra la arquitectura y los componentes del sistema.

```plaintext
+---------------------+
|      Frontend       |
|    (S3 + CloudFront)|
+----------+----------+
           |
           v
+---------------------+
|   API Gateway       |
|   (EC2 + Node.js)   |
+----------+----------+
           |
           v
+---------------------+
|  Microservicio de   |
|  Autenticación      |
|   (EC2 + Node.js)   |
+----------+----------+
           |
           v
+---------------------+        +---------------------+
|  E-commerce API     |        |    RDS (Base de    |
|  (EC2 + Node.js)    |        |    Datos SQL)       |
+----------+----------+        +---------------------+
           |
           v
+---------------------+
|     Funciones       |
|     Lambda          |
| (Actualización de   |
|  inventario, insights)|
+---------------------+
```

## Descripción de Componentes

- **Frontend (S3 + CloudFront)**: La aplicación frontend está alojada en un bucket S3 y se distribuye a través de CloudFront para mejorar el rendimiento y la disponibilidad.
- **API Gateway (EC2 + Node.js)**: Este servicio actúa como el punto de entrada para todas las solicitudes, redirigiendo a los microservicios correspondientes.
- **Microservicio de Autenticación (EC2 + Node.js)**: Este microservicio maneja la autenticación y autorización para acceder a los recursos.
- **E-commerce API (EC2 + Node.js)**: Este microservicio gestiona las operaciones relacionadas con productos, categorías, pedidos e inventario.
- **RDS (Base de Datos SQL)**: Utilizada para almacenar datos persistentes como información de productos y usuarios.
- **Funciones Lambda**: Se utilizan para tareas específicas que pueden ser invocadas en respuesta a eventos, como actualizaciones en la base de datos o generación de insights.

## Opciones de Escalado y Balanceo

- **Autoescalado Horizontal**: Se puede configurar el autoescalado en las instancias EC2 que ejecutan la API Gateway y los microservicios para manejar aumentos en la carga de trabajo automáticamente.
- **Balanceo de Carga**: Se puede implementar un balanceador de carga (Elastic Load Balancer) frente a las instancias EC2 para distribuir el tráfico entrante entre múltiples instancias, mejorando así la disponibilidad y la tolerancia a fallos.

## Pasos para Ejecutar los Microservicios

### Repositorio Principal

El repositorio principal que contiene todos los microservicios y el frontend es:

**Enlace al repositorio**: [linktic-app](https://github.com/yotmanreyes/linktic-app)

### Clonación del Repositorio con Submódulos

Para clonar el repositorio principal junto con sus submódulos, utiliza el siguiente comando:

```bash
git clone --recurse-submodules https://github.com/yotmanreyes/linktic-app.git
```

Esto descargará todos los submódulos necesarios automáticamente.

## Navega al Directorio Clonado:

```bash
cd linktic-app
```

## Enlaces a Microservicios Específicos

- **API Gateway**  
  Enlace al repositorio: [API Gateway en Node.js](https://github.com/yotmanreyes/linktic-ms-gateway)

- **Servicio de Autenticación**  
  Enlace al repositorio: [Servicio de Autenticación](https://github.com/yotmanreyes/linktic-ms-auth)

- **API de E-commerce**  
  Enlace al repositorio: [Ecommerce API](https://github.com/yotmanreyes/linktic-ecommerce-api)

## Frontend

Documentación: [Enlace al repositorio](https://github.com/yotmanreyes/linktic-frontend)
