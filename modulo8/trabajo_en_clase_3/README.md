# Actividad en clase

## Requierimientos

- Una terminal para conectarse por ssh

## 1. Crear una llave de ssh

## 2. Conectarse a una maquina remota

## 3. Instalar dependencias de Docker

```
apt install apt-transport-https ca-certificates curl software-properties-common -y
```

## 4. Configurar las llave de GPG para el repositorio de docker

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

## 5. Agregar el repositorio de Docker en los repositorios de APT

```
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
```

## 6. Limpiar la cache de repositorios

```
apt-cache policy docker-ce
```

## 7. Instalar docker

```
apt install docker-ce -y
```

## 8. Validar que docker este corriendo

```
systemctl status docker
```

## 9. Instalar Java

```
apt install openjdk-8-jdk -y
```

## 10. Importar las llaves de GPG del repositorio de jenkins dentro del manejador de paquetes de ubuntu "apt"

```
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```

## 11. Agregar el repositorio de jenkins dentro de las configuraciones de repositorios de "apt"

```
sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

## 12. Actualizar los repositorios

```
apt update
```

## 13. Instalar Jenkins

```
apt install jenkins -y
```

## 14. Verificar el estatus de Jenkins

```
systemctl status jenkins
```

## 15. Agregar el usuario de jenkins al grupo docker

Lo hacemos para darle permiso de ejecutar comandos de docker a Jenkins

```
usermod -aG docker jenkins
```

## 16. Reiniciar jenkins

```
systemctl restart jenkins
```

## 17. Copiar el password que se genero en el archivo

```
cat /var/lib/jenkins/secrets/initialAdminPassword
```

## 18. Ingresar a la interfaz grafica e ingresar el password que se auto genero

```
Chrome: http://<mi ip>:8080
```

## 19. Seleccionar Install Suggested plugins

```
Suggested plugins
```

## 20. Configurar los datos para el usuario administrador

- Username
- Password
- Confirmar password
- Full name
- E-mail address

## 21. Confirmar la url de jenkins

Corroborar la url para Jenkins

## 22. Crear un nuevo Item

Click en nuevo item desde la interfaz grafica

## 23. Definir un nombre

```
FrontEnd Pipeline
```

## 24. Seleccionar la opcion

```
Multibranch Pipeline
```

## 25. Dar 

```
OK
```

## 26. Configurar con los siguientes datos

- Display name: Frontend pipeline
- Branch sources : Github
- Repository url : https://github.com/alejandrobernalcollazos/abernal
- Behaviours     : Discover branches
- Build configuration : Jenkinsfile
- Leave other as default 


Instalar SonarQube

## 27. Actualizar el Sistema Operativo

```
sudo apt-get update -y
sudo apt-get upgrade -y
```

## 28. Instalar Java

```
sudo add-apt-repository ppa:openjdk-r/ppa && sudo apt-get update -q && sudo apt install -y openjdk-11-jdk
```

## 29. Verificar version de java

```
java -version
```

## 30. Instalar

```
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'
wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O - | sudo apt-key add -
sudo apt-get update -y
sudo apt-get install postgresql postgresql-contrib
sudo systemctl status postgresql
```

## 31. Configurar postgresql

```
su - postgres
createuser sonar
psql
```

## 32. Configurar postgresql dentro de la consola de psql

```
ALTER USER sonar WITH ENCRYPTED password 'password';
CREATE DATABASE sonar OWNER sonar;
\q
exit
```

## 33. Instalar SonarQube

```
sudo adduser sonar
apt install unzip
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.0.zip
unzip sonarqube-8.0.zip
sudo cp -r sonarqube-8.0 /opt/sonarqube
sudo chown -R sonar:sonar /opt/sonarqube
``` 

## 34. Modificar el archivo sonar.sh

```
sudo nano /opt/sonarqube/bin/linux-x86-64/sonar.sh
```

Modificar la linea 

```
RUN_AS_USER=sonar
```

## 35. Modificar el archivo sonar.properties

```
sudo nano /opt/sonarqube/conf/sonar.properties
```

Agregar las siguientes lineas al final del archivo

```
sonar.jdbc.username=sonar
sonar.jdbc.password=password
sonar.jdbc.url=jdbc:postgresql://localhost/sonar
sonar.web.host=0.0.0.0
sonar.search.javaOpts=-Xms1024m  -Xmx1024m
```

## 36. Crear el archivo sonar.service

```
sudo nano /etc/systemd/system/sonar.service
```

Agregar el siguiente contenido

```
[Unit]
Description=SonarQube service
After=syslog.target network.target

[Service]
Type=forking

ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start
ExecStop=/opt/sonarqube/bin/linux-x86-64/sonar.sh stop

LimitNOFILE=65536
LimitNPROC=4096

User=sonar
Group=sonar
Restart=always

[Install]
WantedBy=multi-user.target
```

## 37. Iniciar el servicio de sonar y habilitarlo

```
sudo systemctl start sonar
sudo systemctl enable sonar
```

## 38. Verificar el estado de sonarqube

```
sudo systemctl status sonar
```

