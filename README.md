# Sistema de Gestión de Envíos

Sistema de gestión de envíos basado en arquitectura de microfrontends (MFE) utilizando Docker. 

## 📋 Descripción

Este proyecto implementa un sistema de gestión de envíos distribuido en múltiples microfrontends: 

- **shell-mfe**:  Aplicación principal que orquesta los demás microfrontends
- **auth-mfe**: Módulo de autenticación y autorización
- **order-mfe**:  Módulo de gestión de pedidos
- **quotation-mfe**: Módulo de cotizaciones
- **tracking-mfe**: Módulo de seguimiento de envíos

## 🔧 Prerrequisitos

Antes de comenzar, asegúrate de tener instalado:

- [Docker](https://www.docker.com/get-started) (versión 20.10 o superior)
- [Docker Compose](https://docs.docker.com/compose/install/) (versión 2.0 o superior)
- [Git](https://git-scm.com/downloads)

## 📥 Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/Dan1el71/Sistema-de-gestion-de-envios.git
cd Sistema-de-gestion-de-envios
```

### 2. Inicializar los submódulos

Este proyecto utiliza Git submodules para los microfrontends:

```bash
git submodule init
git submodule update
```

O puedes clonar el repositorio con todos los submódulos de una vez:

```bash
git clone --recurse-submodules https://github.com/Dan1el71/Sistema-de-gestion-de-envios.git
```

## ⚙️ Configuración

### Estructura de Puertos

El sistema utiliza los siguientes puertos:

| Servicio | Puerto Local | Puerto Contenedor |
|----------|-------------|-------------------|
| Shell    | 3000        | 4173             |
| Auth     | 3001        | 4173             |
| Order    | 3002        | 4173             |
| Quotation| 3003        | 4173             |
| Tracking | 3004        | 4173             |

**Nota**:  Asegúrate de que estos puertos estén disponibles en tu máquina local. 

### Variables de Entorno 



## 🚀 Ejecución

### Levantar todos los servicios

Para iniciar todos los servicios del sistema:

```bash
docker-compose up
```

Para ejecutar en segundo plano (modo detached):

```bash
docker-compose up -d
```

### Construcción y ejecución

Si es la primera vez o has realizado cambios en el código:

```bash
docker-compose up --build
```

### Verificar el estado de los servicios

```bash
docker-compose ps
```

## 🌐 Acceso a la Aplicación

Una vez que los servicios estén en ejecución, puedes acceder a: 

- **Aplicación Principal (Shell)**: http://localhost:3000
- **Autenticación**: http://localhost:3001
- **Gestión de Pedidos**: http://localhost:3002
- **Cotizaciones**:  http://localhost:3003
- **Seguimiento**:  http://localhost:3004

## 🛑 Detener los Servicios

Para detener todos los servicios:

```bash
docker-compose down
```

Para detener y eliminar los volúmenes:

```bash
docker-compose down -v
```

## 🔍 Comandos Útiles

### Ver logs de todos los servicios

```bash
docker-compose logs -f
```

### Ver logs de un servicio específico

```bash
docker-compose logs -f shell
docker-compose logs -f auth
```

### Reiniciar un servicio específico

```bash
docker-compose restart shell
```

### Reconstruir un servicio específico

```bash
docker-compose up --build shell
```

## 🐛 Solución de Problemas

### Los contenedores no inician

1.  Verifica que Docker esté ejecutándose:
   ```bash
   docker --version
   ```

2. Verifica que los puertos no estén en uso:
   ```bash
   # En Linux/Mac
   lsof -i :3000
   # En Windows
   netstat -ano | findstr :3000
   ```

### Error al clonar submódulos

Si tienes problemas con los submódulos:

```bash
git submodule update --init --recursive --force
```

### Reconstruir desde cero

Si experimentas problemas, prueba reconstruir todo desde cero:

```bash
docker-compose down -v
docker-compose build --no-cache
docker-compose up
```

## 📝 Desarrollo

Para desarrollar en un microfrontend específico, puedes acceder al contenedor: 

```bash
docker-compose exec shell sh
```

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor: 

1. Haz fork del proyecto
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -m 'Agregar nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la licencia especificada en el archivo LICENSE. 

## 👤 Autor

Dan1el71 - [GitHub](https://github.com/Dan1el71)
```
