# Tienda de Alimentos para Perritos 🐾 - Backend

Este repositorio contiene la API REST para la aplicación de la **Tienda de Alimentos para Perritos**. Está desarrollada en Node.js utilizando Express y se conecta a una base de datos MySQL para gestionar el inventario de productos.

## 🚀 Tecnologías Utilizadas

- **Node.js**: Entorno de ejecución para JavaScript.
- **Express**: Framework web rápido y minimalista para Node.js.
- **MySQL2**: Driver de base de datos para conectar con MySQL.
- **CORS**: Middleware para habilitar el intercambio de recursos de origen cruzado.
- **Docker**: Contenedorización de la aplicación.

## 📁 Estructura del Proyecto

- `backend/`: Código fuente de la API (servidor Express, endpoints CRUD, etc.).
- `.github/workflows/backend-deploy.yml`: Workflow de GitHub Actions para despliegue continuo en AWS ECS Fargate.
- `.aws/`: Configuración y Task Definitions para el despliegue en AWS.

## 🛠️ Cómo Ejecutar Localmente

### Requisitos Previos

- Node.js (v18 o superior)
- MySQL en ejecución (o contenedor de base de datos de la tienda)

### Pasos para iniciar la API

1. Ingresa a la carpeta del backend:
   ```bash
   cd backend
   ```
2. Instala las dependencias:
   ```bash
   npm install
   ```
3. Configura las variables de entorno en el código o mediante variables de sistema (por ejemplo, host de base de datos, usuario, contraseña).
4. Inicia el servidor:
   ```bash
   npm start
   ```

El servidor estará escuchando por defecto en el puerto `3000`.

## 🐳 Ejecución con Docker

Puedes construir la imagen Docker del backend:

```bash
docker build -t tienda-backend ./backend
```

Y ejecutar el contenedor:

```bash
docker run -d -p 3000:3000 --name tienda-backend-container tienda-backend
```

## ⚙️ Integración Continua (GitHub Actions)

El repositorio cuenta con un flujo CI/CD definido en `.github/workflows/backend-deploy.yml` que:
1. Se activa al realizar un `push` en la rama `main`.
2. Compila la imagen Docker.
3. Sube la imagen a **Amazon ECR**.
4. Despliega la nueva versión en el servicio **Amazon ECS Fargate** (`tienda-perritos-cluster`).
