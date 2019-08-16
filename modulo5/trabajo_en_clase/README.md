# Actividad en clase

## Requierimientos

- Una terminal para conectarse por ssh

## 1. Crear una llave de ssh

## 2. Conectarse a una maquina remota

```
ssh -i <path a la llave privada> root@<ip de la maquina>
```

## 3. Actualizar los paquetes del sistema operativo

```
apt-get update
```

## 4. Instalar NodeJS

### 4.1 Instalar curl

```
apt-get install curl

```

### 4.2 Configurar el repositorio

```
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
```

### 4.3 Instalar node

```
apt-get install nodejs
```

## 5. Crear el usuario "desarrollo"

```
adduser desarrollo
```

## 6. Ir al home del usuario desarrollo

```
cd ~
```

## 7. Crear el archivo script.sh con el siguiente contenido

```
#!/bin/bash

echo "Buuueeeenasssss"
```

## 8. Verificar los permisos del archivo

```
ll script.sh
``` 

## 9. Dar permisos de ejecución al archivo solo para el usuario dueño del mismo

```
chmod u+x script.sh
```

## 10. Ejecutar el archivo script.sh

```
./script.sh
```

## 11. Crear un archivo server.js con el siguiente contenido

```
var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(3000);
console.log('Server running at 3000');
``` 

