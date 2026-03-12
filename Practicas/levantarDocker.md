# Guía de Configuración y Comandos - Entorno MongoDB

Este documento contiene los comandos esenciales para levantar el entorno de base de datos usando Docker y conectarse a la consola de MongoDB (mongosh) dentro de GitHub Codespaces.

## 1. Gestión del Entorno (Docker)

Los siguientes comandos deben ejecutarse en la terminal principal del Codespace, en el mismo directorio donde se encuentra el archivo `docker-compose.yml`.

### Levantar el entorno
Inicia los contenedores en segundo plano. Si el Codespace se reinició, este comando vuelve a levantar la infraestructura respetando los datos guardados en el volumen.
```bash
docker compose up -d
docker ps
docker compose down Apagar el entorno (Conservando datos)
docker compose down -v Reinicio de emergencia (Destrucción total)
docker exec -it mongosh_docencia mongosh mongodb://admin:admin123@mongodb_docencia:27017  Entrar a la consola de MongoDB (mongosh)
show dbs 
use nombre_del_examen
show collections
cls