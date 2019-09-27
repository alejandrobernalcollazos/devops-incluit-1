# Actividad en clase

## Requierimientos

- Una terminal para conectarse por ssh

## 1. Crear una llave de ssh

## 2. Conectarse a una maquina remota

## 3. Instalar dependencias de Docker

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

## 4. Configurar las llave de GPG para el repositorio de docker

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

## 5. Agregar el repositorio de Docker en los repositorios de APT

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
```

## 6. Limpiar la cache de repositorios

```
apt-cache policy docker-ce
```

## 7. Instalar docker

```
sudo apt install docker-ce
```

## 8. Validar que docker este corriendo

```
sudo systemctl status docker
```

## 9. Instalar Java

```
apt install openjdk-8-jdk
```

## 10. Importar las llaves de GPG dentro del manejador de paquetes de ubuntu "apt"

```
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```

## 11. Agregar el repositorio de jenkins dentro de las configuraciones de repositorios de "apt"

```
sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

## 12. Instalar Jenkins

```
apt install jenkins
```

## 13. Verificar el estatus de Jenkins

```
systemctl status jenkins
```
