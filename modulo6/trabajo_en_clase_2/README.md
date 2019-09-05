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

## 12. Pide a tu coordinador crear un registro A en el servidor de DNS para apuntar a tu maquina

# Parte 2

## 1. Ser root

## 2. Instalar un servidor de MySQL 

```
apt install mysql-server
```

## 3. Ingresar en la consola de la base de datos

```
mysql
```

## 4. Crear la base de datos curriculum

```
mysql> CREATE DATABASE curriculum;
```

## 5. Seleccionar la base de datos para comenzar a trabajar en ella

```
mysql> USE curriculum;
```

## 6. Crear la tabla "attitudes"

```
mysql> CREATE TABLE IF NOT EXISTS attitudes (
    id int(11) NOT NULL,
    name varchar(200) NOT NULL,
    description varchar(200) NOT NULL
  ) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

## 7. Configurar el campo id como clave primaria en la tabla "attitudes"

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

## 8. Crear el usuario "attitudes"

```
mysql> CREATE USER 'attitudes'@'localhost' IDENTIFIED BY 'password';
```

## 9. Dar permisos al usuario "attitudes" sobre la base de datos curriculum y todas sus tablas

```
mysql> GRANT ALL PRIVILEGES ON curriculum.attitudes TO 'attitudes'@'localhost';
```

## 10. Actualizar privilegios

```
mysql> FLUSH PRIVILEGES;
```

## 11. Salir de la consola de mysql

```
mysql> exit;
```

## 12. Convertirse en el usuario desarrollo

```
sudo su desarrollo
```

## 13. Ir al directorio "home" del usuario desarrollo

```
cd
```

## 14. Crear una carpeta con el nombre "attitudes-api" e ingresar a la misma

```
mkdir attitudes-api
cd attitudes-api
```

## 15. Ejecutar el comando npm init y npm install

```
npm init --yes
npm install 
```

## 16. Instalar express, mysql y body-parser

```
npm install express --save
npm install mysql --save
npm install body-parser --save
```

## 17. Crear el archivo server.js con el siguiente contenido

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

// set port
app.listen(3000, function () {
    console.log('Node app is running on port 3000');
});

module.exports = app;
```

## 18. Correr el archivo server.js como un demonio

```
node server.js &
```

## 19. Probar en postman un request GET

A la siguiente url 

```
http://nombre-de-dominio:puerto/
```

## 20. Verificar que la api devuelva datos

## 21. En la consola matar al demonio

### 21.1 volverse root

```
exit
```

### 21.2 ejecutar el comando kill

```
kill -9 <PID del proceso de la API>
```

## 22. Agregar datos de conección a la base de datos MySQL

### 22.1 Volverse el usuario desarrollo

```
sudo su desarrollo
```

ir a la carpeta home

```
cd
```

### 22.2 Dentro de la carpeta attitudes-api

```
cd attitudes-api
```

### 22.3 Modificar el archivo server.js

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

// set port
app.listen(3000, function () {
    console.log('Node app is running on port 3000');
});

module.exports = app;
```

## 23. Correr el archivo server.js como un demonio

```
node server.js &
```

## 24. Probar en postman un request GET

A la siguiente url

```
http://nombre-de-dominio:puerto/
```

## 25. Verificar que la api devuelva datos

## 26. En la consola matar al demonio

### 26.1 volverse root

```
exit
```

### 26.2 ejecutar el comando kill

```
kill -9 <PID del proceso de la API>
```

## 27. Agregar datos de conección a la base de datos MySQL

### 27.1 Volverse el usuario desarrollo

```
sudo su desarrollo
```

ir a la carpeta home

```
cd
```

### 27.2 Dentro de la carpeta attitudes-api

```
cd attitudes-api
```

### 27.3 Modificar el archivo server.js

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

// set port
app.listen(3000, function () {
    console.log('Node app is running on port 3000');
});

module.exports = app;
```
