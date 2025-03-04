# API Gateway Kong

## Descripción
API Gateway Kong es una solución de gestión de API basada en Kong Gateway, diseñada para enrutar, proteger y optimizar las solicitudes entre clientes y servicios dentro de un ecosistema de microservicios.

Este servicio proporciona autenticación, control de tráfico, limitación de velocidad y registro de solicitudes, asegurando una gestión eficiente y segura de las APIs. Está preparado para ejecutarse en entornos Dockerizados, facilitando su despliegue y escalabilidad.

## Tecnologías utilizadas
- **Kong Gateway** - API Gateway de alto rendimiento.
- **PostgreSQL** - Base de datos para la configuración de Kong.
- **Docker & Docker Compose** - Para la contenedorización y despliegue del servicio.
- **Konga** - Interfaz gráfica para la administración de Kong.

## Requisitos previos
Antes de ejecutar el servicio, asegúrate de tener instalado:
- Docker y Docker Compose
- PostgreSQL (opcional, si se ejecuta sin Docker)

## Configuración
Crea un archivo `.env` en la raíz del proyecto con las siguientes variables de entorno:

```env
# Configuración de PostgreSQL para Kong
POSTGRES_DB_KONG=kong
POSTGRES_USER_KONG=kong
POSTGRES_PASSWORD_KONG=kong
POSTGRES_PORT_KONG=5432

# Configuración de PostgreSQL para Konga
POSTGRES_DB_KONGA=konga
POSTGRES_USER_KONGA=konga
POSTGRES_PASSWORD_KONGA=konga

# Configuración de Kong
KONG_DATABASE=postgres
KONG_PG_HOST=kong-db
KONG_PG_PORT=5432
KONG_PG_USER=kong
KONG_PG_PASSWORD=kong
KONG_ADMIN_LISTEN=0.0.0.0:8001, 0.0.0.0:8444 ssl
```

## Instalación y ejecución

### 1. Clona el repositorio:
```bash
git clone https://github.com/2A2G/api-gateway-kong.git
cd api-gateway-kong
```

### 2. Configura las variables de entorno
Asegúrate de tener el archivo `.env` con los valores adecuados.

### 3. Ejecuta el servicio con Docker Compose:
```bash
docker-compose up -d
```
Esto iniciará los siguientes contenedores:
- **Kong Database** (`kong-db`)
- **Kong Migration** (`kong-migration`) para inicializar la base de datos.
- **Kong API Gateway** (`kong`)
- **Konga Database** (`konga-db`)
- **Konga UI** (`konga`)

### 4. Acceder a la interfaz de Konga
Una vez que los servicios estén en ejecución, puedes acceder a la interfaz de Konga en:
```
http://localhost:1337
```
Desde allí, podrás administrar Kong de manera gráfica.

## Despliegue con Docker Compose
Para levantar los servicios en segundo plano:
```bash
docker-compose up -d
```
Para detenerlos:
```bash
docker-compose down
```

## Licencia
Este proyecto está bajo la Licencia MIT.

© 2025 [2A2G](https://github.com/2A2G).

Se permite el uso, modificación y distribución de este software de forma gratuita, siempre que se conserve este aviso de licencia.

