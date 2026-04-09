# proyecto-wordpress
subiendo mi proycetoooo
#  AAPHAL - Despliegue de WordPress en AWS EC2

## 📋 Descripción del Proyecto
Despliegue de un servidor web en Amazon Web Services (EC2) con WordPress para la **Asociación de Agricultores de Palta en Huamanpali - Alto Larán (AAPHAL)**.

##  Datos del Estudiante
- **Nombre:** Alexis Rejas
- **Usuario Linux:** alexis_rejas
- **Curso:** Análisis de Sistemas

##  Tecnologías Utilizadas
- Amazon Web Services (EC2)
- Ubuntu Server 22.04 LTS
- Apache2
- MySQL
- PHP
- WordPress 6.9.4
- UFW Firewall
- GitHub

##  URL del Sitio
http://100.54.146.73

##  Pasos Resumidos

### 1. Creación de instancia EC2
- AMI: Ubuntu Server 22.04 LTS
- Tipo: t2.micro (Free Tier)
- Puertos abiertos: 22 (SSH), 80 (HTTP), 443 (HTTPS)

### 2. Conexión SSH
```bash
ssh -i "mi-clave-wordpress.pem" ubuntu@100.54.146.73
```

### 3. Creación de usuario Linux
```bash
sudo adduser alexis_rejas
sudo usermod -aG sudo alexis_rejas
```

### 4. Instalación de servidor web
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y
sudo apt install mysql-server -y
sudo apt install php libapache2-mod-php php-mysql -y
```

### 5. Configuración de base de datos
```bash
sudo mysql
CREATE DATABASE wordpress_db;
CREATE USER 'alexis_rejas'@'localhost' IDENTIFIED BY 'admin123';
GRANT ALL PRIVILEGES ON wordpress_db.* TO 'alexis_rejas'@'localhost';
FLUSH PRIVILEGES;
```

### 6. Instalación de WordPress
```bash
cd /var/www/html
sudo wget https://wordpress.org/latest.tar.gz
sudo tar -xzf latest.tar.gz
sudo mv wordpress/* .
sudo chown -R www-data:www-data /var/www/html
```

### 7. Configuración de Firewall UFW
```bash
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
sudo ufw status
```

##  Seguridad
-  Usuario personalizado: `alexis_rejas`
-  Firewall UFW activo
- ✅ Sin uso de root

## 📁 Estructura del Repositorio
