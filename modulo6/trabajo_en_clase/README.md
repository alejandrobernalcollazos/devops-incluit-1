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

## 5. Instalar Docker

### 5.1 Instalar dependencias

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

### 5.2 Instalar las llaves de GPG

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

### 5.3 Agregar el repositorio de Docker en los repositorios de APT

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
```

### 5.4 Actualizar los repositorios

```
sudo apt update
```

### 5.5 Limpiar la cache de repositorios

```
apt-cache policy docker-ce
```

### 5.6 Instalar docker

```
sudo apt install docker-ce
```

### 5.7 Validar que docker este corriendo

```
sudo systemctl status docker
```

## 6. Crear el usuario "desarrollo" e impersonarme con el usuario desarrollo

```
adduser desarrollo
```

Agregar el usuario desarrollo al grupo docker

```
usermod -aG docker desarrollo
```

Impersonarme como el usuario desarrollo
```
sudo su desarrollo
```

## 7. Ir al home del usuario desarrollo

```
cd ~
```

## 8. hacer un clone del repositorio de frontEnd

```
git clone https://github.com/alejandrobernalcollazos/abernal
```

## 9. Entrar a la carpeta principal del repositorio

```
cd abernal
```

## 10. Ejecutar el comando docker build

```
docker build -t frontend:v1 .
```

## 11. Crear un contenedor a partir de la imagen frontend:v1

```
docker run -d -p 80:80 frontend:v1
```

## 12. Pide a tu coordinador crear un registro A en el servidor de DNS para apuntar a tu maquina

## 13. Valida que la pagina web este respondiendo en el subdominio asignado por el coordinador

## 14. Verifica los contenedores que tienes corriendo

```
docker ps
```

## 15. Verificar las imagenes existentes en la maquina local

```
docker images
```
## 16. Parar el contenedor corriendo actualmente

```
docker stop <container name>
```

## 17. Valida que la pagina web ya no responde en el subdominio asignado por el coordinador

## 18. Para el servicio de docker engine

este comando debes ejecutarlo como root

```
systemctl stop docker
```

## 19. Valida que docker engine no este corriendo

```
docker version
```

# Parte 2

## 20. Ser root

## 21. Instalar un servidor de MySQL 

```
apt install mysql-server
```

## 22. Ingresar en la consola de la base de datos

```
mysql
```

## 23. Crear la base de datos curriculum

```
mysql> CREATE DATABASE curriculum;
```

## 24. Seleccionar la base de datos para comenzar a trabajar en ella

```
mysql> USE curriculum;
```

## 25. Crear la tabla "attitudes"

```
mysql> CREATE TABLE IF NOT EXISTS attitudes (
    id int(11) NOT NULL,
    name varchar(200) NOT NULL,
    description varchar(200) NOT NULL
  ) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

## 26. Configurar el campo id como clave primaria en la tabla "attitudes"

```
mysql> ALTER TABLE attitudes ADD PRIMARY KEY (id);
mysql> ALTER TABLE attitudes MODIFY id int(11) NOT NULL AUTO_INCREMENT;
```

Agregamos también datos para pruebas

```
mysql> INSERT INTO attitudes (name, description) VALUES
  ('Pasión', 'Soy una persona muy apasionada '),
  ('Honestidad', 'Soy una persona que trata de ser lo más honesta posible'),
  ('Tolerancia', 'Soy una persona tolerante'),
  ('Respeto', 'Soy una persona muy respetuosa');
```

## 27. Crear el usuario "attitudes"

```
mysql> CREATE USER 'attitudes'@'localhost' IDENTIFIED BY 'password';
```

## 28. Dar permisos al usuario "attitudes" sobre la base de datos curriculum y todas sus tablas

```
mysql> GRANT ALL PRIVILEGES ON curriculum.attitudes TO 'attitudes'@'localhost';
```

## 29. Actualizar privilegios

```
mysql> FLUSH PRIVILEGES;
```

## 30. Salir de la consola de mysql

```
mysql> exit;
```

## 31. Convertirse en el usuario desarrollo

```
sudo su desarrollo
```

## 32. Ir al directorio "home" del usuario desarrollo

```
cd
```

## 33. Crear una carpeta con el nombre "values-api" e ingresar a la misma

```
mkdir values-api
cd values-api
```

## 34. Ejecutar el comando npm init y npm install

```
npm init --yes
npm install 
```

## 35. Instalar express, mysql y body-parser

```
npm install express --save
npm install mysql --save
npm install body-parser --save
```

## 36. Crear el archivo  server.js con el siguiente contenido

```
var express = require('express');
var app = express();
var bodyParser = require('body-parser');
var mysql = require('mysql');
  
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({
    extended: true
}));
  
  
// default route
app.get('/', function (req, res) {
    return res.send({ error: true, message: 'hello' })
});
// connection configurations
var dbConn = mysql.createConnection({
    host: 'localhost',
    user: 'attitudes',
    password: 'password',
    database: 'curriculum'
});
  
// connect to database
dbConn.connect(); 
 
 
// Retrieve all attitudes 
app.get('/attitudes', function (req, res) {
    dbConn.query('SELECT * FROM attitudes', function (error, results, fields) {
        if (error) throw error;
        return res.send({ error: false, data: results, message: 'attitudes list.' });
    });
});
 
 
// Retrieve attitude with id 
app.get('/attitude/:id', function (req, res) {
  
    let attitude_id = req.params.id;
  
    if (!attitude_id) {
        return res.status(400).send({ error: true, message: 'Please provide attitude_id' });
    }
  
    dbConn.query('SELECT * FROM attitudes where id=?', attitude_id, function (error, results, fields) {
        if (error) throw error;
        return res.send({ error: false, data: results[0], message: 'attitudes list.' });
    });
  
});
 
 
// Add a new attitude  
app.post('/attitude', function (req, res) {
  
    let name = req.body.name;
    let description = req.body.description;
  
    if (!name || !description) {
        return res.status(400).send({ error:true, message: 'Please provide name and description' });
    }
  
    dbConn.query("INSERT INTO attitudes SET ? ", { name: name, description: description }, function (error, results, fields) {
        if (error) throw error;
        return res.send({ error: false, data: results, message: 'New attitude has been created successfully.' });
    });
});
 
 
//  Update attitude with id
app.put('/attitude', function (req, res) {
  
    let attitude_id = req.body.attitude_id;
    let attitude = req.body.attitude;
  
    if (!attitude_id || !attitude) {
        return res.status(400).send({ error: attitude, message: 'Please provide attitude and attitude_id' });
    }
  
    dbConn.query("UPDATE attitudes SET attitude = ? WHERE id = ?", [attitude, attitude_id], function (error, results, fields) {
        if (error) throw error;
        return res.send({ error: false, data: results, message: 'attitude has been deleted successfully.' });
    });
});
 
 
//  Delete attitude
app.delete('/attitude', function (req, res) {
  
    let attitude_id = req.body.attitude_id;
  
    if (!attitude_id) {
        return res.status(400).send({ error: true, message: 'Please provide attitude_id' });
    }
    dbConn.query('DELETE FROM attitudes WHERE id = ?', [attitude_id], function (error, results, fields) {
        if (error) throw error;
        return res.send({ error: false, data: results, message: 'attitude has been updated successfully.' });
    });
}); 
 
// set port
app.listen(3000, function () {
    console.log('Node app is running on port 3000');
});
 
module.exports = app;
```
