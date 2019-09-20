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
apt install apt-transport-https ca-certificates curl software-properties-common -y
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
apt install docker-ce -y
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

## 12. Instalar docker componse

##### 12.1

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

#### 12.2 

```
sudo chmod +x /usr/local/bin/docker-compose
```

# Parte 2

## 1. Instalar Mongo DB

```
apt install -y mongodb
```

Check el servicio

```
systemctl status mongodb
```

## 2. Impersonarse como el usuario desarrollo

```
sudo su desarrollo
```

## 3. Ir al home del usuario desarrollo 

```
cd 
```

## 4. Clonar los repositorios de Dieguito del frontend

```
git clone https://github.com/e-dmolina/front_vida_sin_tacc.git
```

## 5. Clonar los repositorios de Dieguito del backend

```
git clone https://github.com/e-dmolina/back_vida_sin_tacc.git
```

## 6. Entrar en el repositorio del backend

```
cd back_vida_sin_tacc
```

## 7. Crear una imagen de docker para el backend

```
docker build -t backend:v1 .
```

## 8. Entrar en el repositorio del frontend

```
cd ~/front_vida_sin_tacc
```

## 9. Crear una imagen de docker para el frontend

```
docker build -t frontend:v1 .
```
