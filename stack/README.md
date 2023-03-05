# MAINTAINER
- Name: David Aybar
- Email: daybar4@gmail.com
- Web: https://www.davidaybar.com/

## Proceso de instalación
Se expondrán los siguientes puertos:
- 443: Web TCP HTTPS
- 5000: Nexus Registry

### Clonemos el proyecto git al directorio actual
```
git clone <url-to-git-project>
```

### Cambiamos directorio a la ruta del proyecto
```
cd <to-project-directory>
```

### Generamos archivos docker-compose.yml, .env
```
cp docker-compose.yml.dist docker-compose.yml
cp .env.dist .env
```

### Customizar credenciales y volumen paths si es necesario
```
vim .env
```

### Creamos por primera vez directorios persistidos para docker
- Ver docker-compose.yml.dist para lista completa de volúmenes persistidos
```
mkdir -p ./volumes/nginx/logs
mkdir -p ./volumes/nexus/data
```

### Cambiar permisos en directorios persistidos
```
sudo chown -R 200 ./volumes/nexus/data
```

## Accedemos localmente a la web y añadimos "not trusted certificate exception" si es necesario
- https://localhost (or any domain name aliased inside /etc/hosts)

Docker está pensado para ser un sistema cerrado de seguridad, solo exponemos los puertos externos 443/5000 para acceder a través del proxy, nuestra puerta de entrada y hace proxypass al puerto 8081.
Los certificados ssl autoadministrados se generan automáticamente.