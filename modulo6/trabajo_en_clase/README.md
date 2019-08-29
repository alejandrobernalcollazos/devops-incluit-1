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
Impersonarme como el usuario desarrollo
```
sudo su desarrollo
```

## 7. Ir al home del usuario desarrollo

```
cd ~
```
