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

### 4. Instalar dependencias de docker

```
apt install apt-transport-https ca-certificates curl software-properties-common
```

### 5. Instalar las llaves de GPG de docker

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

### 6. Agregar el repositorio de Docker en los repositorios de APT

```
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
```

### 7. Actualizar los repositorios

```
apt update
```

### 8. Limpiar la cache de repositorios

```
apt-cache policy docker-ce
```

### 9. Instalar docker

```
apt install docker-ce
```

### 10. Validar que docker este corriendo

```
systemctl status docker
```

## 11. Crear el usuario "desarrollo" e impersonarme con el usuario desarrollo

```
adduser desarrollo
```

Agregar el usuario desarrollo al grupo docker

```
usermod -aG docker desarrollo
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
su desarrollo
```

## 13. Ir al directorio "home" del usuario desarrollo

```
cd
```

## 14. Hacer un clone del siguiente repositorio

```
git clone https://github.com/alejandrobernalcollazos/abernal-attitudes
```

## 15. Hacer un clone del siguiente repositorio

```
git clone https://github.com/alejandrobernalcollazos/abernal
```

## 16. Ingresar al folder abernal

```
cd abernal
```

## 17. Crear una imagen de docker del frontend

```
docker build -t frontend:v1 .
```

## 18. Crear un contenedor de frontend en base a la imagen frontend:v1

```
docker run -p 80:80 frontend:v1
```

## 19. Probar que el contenedor este funcionando accediendo por la ip desde el browser

## 20. Salir de la carpeta frontend

```
cd ..
```

## 21. Entrar a la carpeta abernal-attitudes

```
cd abernal-attitudes
```

## 22. Crear la imagen de docker "attitudes" de la api

```
docker build -t attitudes:v1 .
```

## 23. Crear un contenedor basado en la imagen "attitudes"

```
docker run -p 80:80 attitudes:v1
```

## 24. Hacer Trouble Shooting en clase, por la conexión a la DB
