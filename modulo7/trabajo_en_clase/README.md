# Actividad en clase

## Requierimientos

- Una terminal para conectarse por ssh

## 1. Conectarse a una maquina remota

```
ssh -i <path a la llave privada> root@<ip de la maquina>
```

## 2. Actualizar los paquetes del sistema operativo

```
apt-get update
```

## 3. Instalar curl, zip, unzip and python3

```
apt-get install curl zip unzip python3-pip -y
```

## 4. Descargar el binario de terraform

```
wget https://releases.hashicorp.com/terraform/0.12.9/terraform_0.12.9_linux_amd64.zip
```

## 5. Descomprimir el binario de terraform

```
unzip terraform_0.12.9_linux_amd64.zip 
```

## 6. Poner el binario dentro de el path /src/bin

```
mv terraform_0.12.9_linux_adm64 /src/bin
```

## 7. Crear el usuario "desarrollo"

```
adduser desarrollo
```

## 8. Entrar en el home del usuario

```
cd ~
```

## 9. Instalar AWS CLI

```
pip3 install awscli --upgrade --user
```

## 10. Configurar aws con las credenciales que te debe proveer el instructor

```
aws configure
```

Ingresar los datos proveidos 
- Access Key
- Secret Access Key

## 11. Crear la carpeta terraform

```
mkdir terraform
```

## 12. Entrar en la carpeta "terraform"

```
cd terraform
```

## 13. Crear el archivo main.tf

```
nano main.tf
```

## 14. Copiar el siguiente contenido

```
provider "aws" {
  profile    = "default"
  region     = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-2757f631"
  instance_type = "t2.micro"
}
```

## 15. Ejecutar el comando terraform init

```
terraform init
```

## 16. Ejecutar el comando terraform plan

```
terraform plan
```

## 17. Ejecutar el comando terraform apply

```
terraform apply
```
