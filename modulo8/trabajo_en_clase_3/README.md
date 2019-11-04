# Actividad en clase

## Requierimientos

- Una terminal para conectarse por ssh

## 1. Crear una llave de ssh

## 2. Conectarse a una maquina remota

## 3. Instalar Node y dependencias de Docker

```
apt update
apt-get install curl -y
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
apt-get install nodejs -y
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
add-apt-repository ppa:openjdk-r/ppa -y
apt-get update -y
apt install -y openjdk-11-jdk
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

## 17. Ingresar a la interfaz grafica e ingresar el password que se auto genero

```
Chrome: http://<mi ip>:8080
```

## 18. Copiar el password que se genero en el archivo e ingresarlo en la interfaz grafica

```
cat /var/lib/jenkins/secrets/initialAdminPassword
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

## 22. Reiniciar jenkins si la pantalla siguiente queda en blanco

```
systemctl restart jenkins
```

## 23. Hacer login en Jenkins luego del restart

```
Usar usuario y password generados en el paso 20
```

## 24. Crear un nuevo Item desde la interfaz de usuario

Click en nuevo item desde la interfaz grafica

## 25. Definir un nombre

```
FrontEnd Pipeline
```

## 26. Seleccionar la opcion

```
Multibranch Pipeline
```

## 27. Dar OK

```
OK
```

## 28. Configurar con los siguientes datos

- Display name           : Frontend pipeline
- Branch sources         : Github
  - Add Credentials      : Jenkis
  - Set github username  : <tu usuario de github>
  - Set github password  : <tu password de github>
  - Set credentials id   : <nombre aleatoria para identificar a la credencial en jenkins> 
- Select credential      : Seleccionar credencial recién creada
- Repository url         : https://github.com/alejandrobernalcollazos/abernal
- Behaviours             : Discover branches
  - Strategy             : All branches
- Build configuration    : Jenkinsfile
- Scan Multibranch Pipeline Triggers
  - Periodically if not otherwise run : Habilitar el checkbox
    - Interval                        : 1 min
- Leave other as default 


# Instalar SonarQube


## 29. Instalar PostgreSQL

```
sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'
wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O - | sudo apt-key add -
apt-get update -y
apt-get install postgresql postgresql-contrib -y
systemctl status postgresql
```

## 30. Configurar PostgreSQL

```
su - postgres
createuser sonar
psql
```

## 31. Configurar PostgreSQL dentro de la consola de psql

```
ALTER USER sonar WITH ENCRYPTED password 'password';
CREATE DATABASE sonar OWNER sonar;
\q
exit
```

## 32. Crear el usuario sonar

```
adduser sonar
```

## 33. Asegurar la cantidad de sectores de memoria para la virtual memory

```
sysctl -w vm.max_map_count=262144
```

## 34. Instalar SonarQube

```
apt install unzip
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.0.zip
unzip sonarqube-8.0.zip
cp -r sonarqube-8.0 /opt/sonarqube
chown -R sonar:sonar /opt/sonarqube
``` 

## 35. Modificar el archivo sonar.sh

```
vim /opt/sonarqube/bin/linux-x86-64/sonar.sh
```

Modificar la linea 

```
RUN_AS_USER=sonar
```

## 36. Modificar el archivo sonar.properties

```
nano /opt/sonarqube/conf/sonar.properties
```

Agregar las siguientes lineas al final del archivo

```
sonar.jdbc.username=sonar
sonar.jdbc.password=password
sonar.jdbc.url=jdbc:postgresql://localhost/sonar
sonar.web.host=0.0.0.0
sonar.search.javaOpts=-Xms1024m  -Xmx1024m
```

## 37. Crear el archivo sonar.service

```
nano /etc/systemd/system/sonar.service
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

LimitNOFILE=262144
LimitNPROC=4096

User=sonar
Group=sonar
Restart=always

[Install]
WantedBy=multi-user.target
```

## 38. Iniciar el servicio de sonar y habilitarlo

```
systemctl start sonar
systemctl enable sonar
```

## 39. Verificar el estado de sonarqube

```
systemctl status sonar
```

## 40. Dentro de Jenkins instalar el plugin de Sonar Qube


Dentro de 

- Click en el icono de Jenkins
- Manage Jenkins
- Manage plugins
- Seleccionar la pestaña de "Plugins : Available"
- Buscar: SonarQube Scanner
- Instalar y reiniciar

## 41. Login en Jenkins

## 42. Acceder al servidor de SonarQube y crear un projecto

- Ir a la url http://<mi ip>:9000
- Dar click en login
- Login en sonarqube
  - username : admin
  - password : admin
- Crear nuevo projecto
  - project key : sonarqube_project
  - display name: sonarqube_project
  - token name  : sonarqube_token
  - Generate
  - Salvar token
  - Continue

## 43. Configurar el servidor de SonarQube dentro de Jenkins

- Click en el icono de Jenkins
- Manage Jenkins
- Configure System
- SonarQube Servers
  - Nombre : sonarqube_server
  - Url    : http://localhost:9000
- Click en Save

## 44. Configurar las credenciales para el servidor de SonarQube en Jenkins

- Click en el icono de Jenkins
- Manage Jenkins
- Configure System
- SonarQube Servers
  - Add : Jenkins
    - Kind   : Secret Text
    - Secret : <token que salvamos en el paso 42>
    - ID     : sonarqube_token
    - ADD
  - Usar las credenciales recien creadas : sonarqube_token

## 45. Dentro de Jenkins configurar la tool de Sonar Qube

Dentro de 

- Click en el icono de Jenkins
- Manage Jenkins
- Global Tool Configuration
- SonarQube Scanner
  - Add sonarqube scanner
    - name : sonarqube_scanner
    - install from maven central
  - Save

