# Documentación para la instalación de Redis en Linux

## Introducción

Este documento proporciona una guía paso a paso para instalar y configurar Redis, un sistema gestor de bases de datos NoSQL, en un entorno Linux. Se detallarán los requisitos previos, el proceso de instalación, la seguridad y la gestión básica del servicio.

## Requisitos

Antes de comenzar con la instalación, asegúrese de tener los siguientes paquetes instalados:

```bash
sudo apt install lsb-release curl gpg
```

Además, agregaremos la clave de autenticación y el repositorio Redis a nuestro sistema:

```bash
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list
```

## Instalación

Una vez configurados los repositorios, actualizamos la lista de paquetes disponibles e instalamos Redis:

```bash
sudo apt-get update
sudo apt-get install redis
```

Con estos pasos, Redis debería estar instalado en su máquina Linux.

## Securización de la Instalación

Por defecto, Redis bloquea el acceso remoto a la base de datos. Para permitirlo, modificamos el archivo de configuración `/etc/redis/redis.conf` cambiando la línea `bind 127.0.0.1` a `bind 0.0.0.0`. Además, desactivamos el modo protegido en `redis-cli` con el siguiente comando:

```bash
CONFIG SET protected-mode no
```

## Gestión del Servicio

Para gestionar el servicio de Redis en el sistema operativo, utilizamos los siguientes comandos:

- **Arrancar el servicio:**
```bash
sudo systemctl start redis
```

- **Verificar el estado del servicio:**
```bash
sudo systemctl status redis
```

- **Apagar el servicio:**
```bash
sudo systemctl stop redis
```

## Configuración y Localización de Archivos

- **Archivo de Configuración:**
El archivo de configuración de Redis se encuentra en `/etc/redis/redis.conf`.

- **Datos Físicos:**
Redis no utiliza almacenamiento en disco; los datos se mantienen en la memoria RAM.

## Cambio de Puerto

El puerto por defecto en el que Redis escucha es `6379`. Para cambiarlo, se modifica el archivo de configuración `/etc/redis/redis.conf`.

## Conexión a la Base de Datos

Para conectarse a la base de datos Redis, puede utilizar herramientas de gestión como Redis Insight o programas que admitan conexiones a Redis.

## Conclusiones

En este documento, se ha proporcionado una guía detallada para la instalación, configuración y gestión básica de Redis en un entorno Linux. Con esta información, los técnicos informáticos pueden implementar y administrar eficazmente esta base de datos NoSQL en sus sistemas.