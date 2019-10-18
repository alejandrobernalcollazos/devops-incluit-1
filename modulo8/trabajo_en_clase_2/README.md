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

## 4 Instalar curl

```
apt-get install curl

```

## 5 Configurar el repositorio de nodejs

```
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
```

## 6 Instalar nodejs

```
apt-get install nodejs
```

## 7 Instalar un servidor de MySQL 

```
apt install mysql-server
```

## 8 Ingresar en la consola de la base de datos

```
mysql
```

## 9 Crear la base de datos curriculum

```
mysql> CREATE DATABASE curriculum;
```

## 10 Seleccionar la base de datos para comenzar a trabajar en ella

```
mysql> USE curriculum;
```

## 11 Crear la tabla "attitudes"

```
mysql> CREATE TABLE IF NOT EXISTS attitudes (
    id int(11) NOT NULL,
    name varchar(200) NOT NULL,
    description varchar(200) NOT NULL
  ) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

## 12 Configurar el campo id como clave primaria en la tabla "attitudes"

```
mysql> ALTER TABLE attitudes ADD PRIMARY KEY (id);
mysql> ALTER TABLE attitudes MODIFY id int(11) NOT NULL AUTO_INCREMENT;
```

## 13 Agregar datos de prueba en la tabla "attitudes"

```
mysql> INSERT INTO attitudes (name, description) VALUES
  ('Pasión', 'Soy una persona muy apasionada '),
  ('Honestidad', 'Soy una persona que trata de ser lo más honesta posible'),
  ('Tolerancia', 'Soy una persona tolerante'),
  ('Respeto', 'Soy una persona muy respetuosa');
```

## 14 Crear el usuario "attitudes"

```
mysql> CREATE USER 'attitudes'@'%' IDENTIFIED BY 'password';
```

## 15 Dar permisos al usuario "attitudes" sobre la base de datos curriculum y todas sus tablas

```
mysql> GRANT ALL PRIVILEGES ON curriculum.attitudes TO 'attitudes'@'%';
```

## 16 Actualizar privilegios

```
mysql> FLUSH PRIVILEGES;
```

## 17 Salir de la consola de mysql

```
mysql> exit;
```

## 18 Crear el usuario "desarrollo"

```
adduser desarrollo
```

Agrega una password simple


## 19 Impersonarme como el usuario desarrollo

```
sudo su desarrollo
```

## 20 Ir al home del usuario desarrollo

```
cd ~
```


## 21 Crear una carpeta con el nombre "attitudes-api" e ingresar a la misma

```
mkdir attitudes-api
cd attitudes-api
```

## 22 Ejecutar el comando npm init y npm install

```
npm init --yes
npm install 
```

## 23 Instalar express, mysql y body-parser

```
npm install express --save
npm install mysql --save
npm install body-parser --save
```

## 24 Crear el archivo server.js con el siguiente contenido

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
