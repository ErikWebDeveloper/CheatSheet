# Creación de directorio SFTP en una unidad USB en Linux
## Prerequisitos
Antes de comenzar, es esencial asegurarse de tener instalado SSH en su sistema. Puede verificar la existencia de SSH ejecutando el comando `ssh -V` en la terminal.

### Descripción
Este documento explica cómo crear un directorio SFTP en una unidad USB o unidad montada en el sistema en Linux. La creación de un directorio SFTP facilita la transferencia segura de archivos entre dispositivos en la misma red.

### Identificación de la unidad USB
Antes de crear el directorio SFTP, primero necesitas identificar la unidad USB en tu sistema. Puedes hacerlo ejecutando el siguiente comando en la terminal:
```bash
lsblk
```
Este comando mostrará una lista de todas las unidades de almacenamiento en tu sistema, incluidas las unidades USB conectadas. Busca la entrada correspondiente a tu unidad USB, que generalmente tendrá el prefijo `/dev/sdX`, donde "X" es una letra que identifica la unidad.

### Montaje de la unidad USB

Si la unidad USB no está montada automáticamente, necesitarás montarla manualmente. Puedes hacerlo utilizando el siguiente comando en la terminal:

```bash
sudo mount /dev/sdX /mnt
```
Asegúrate de reemplazar `/dev/sdX` con la identificación de tu unidad USB y `/mnt` con el directorio de montaje deseado.


### Creación del directorio SFTP

Una vez montada la unidad USB, puedes crear el directorio SFTP en ella. Ejecuta el siguiente comando en la terminal para crear un directorio llamado "sftp" en la raíz de la unidad USB:

```bash
sudo mkdir /mnt/sftp
```
Este comando creará un directorio llamado "sftp" en la raíz de la unidad USB montada en "/mnt".
## Permisos y configuración de SFTP

A continuación, necesitarás establecer los permisos adecuados para el directorio SFTP y configurar el servidor SFTP en tu sistema. Para configurar un servidor SFTP en Linux, puedes usar herramientas como OpenSSH.

Es importante configurar los permisos del directorio SFTP de manera adecuada para garantizar que solo los usuarios autorizados tengan acceso y puedan transferir archivos de forma segura. Puedes establecer los permisos utilizando el comando `chmod`. Por ejemplo, para otorgar permisos de lectura, escritura y ejecución al propietario y permitir solo la ejecución a otros usuarios, puedes ejecutar:

```bash
sudo chmod 755 /mnt/sftp
```
## Configuración de Usuario y Acceso SSH

1. Crear un usuario:

```bash
sudo useradd -m -d /mnt/sdX/nombre_usuario -s /bin/bash nombre_usuario
sudo passwd nombre_usuario
```

Esto creará un usuario llamado nombre_usuario con la carpeta home en /mnt/sftp/nombre_usuario y asignará una contraseña.

2.  Crear un grupo SFTP:

```bash
sudo groupadd sftp
```

3. Agregar tu usuario al grupo SFTP:
```bash
sudo usermod -aG sftp_users nombre_usuario
```

4. Edita el archivo de configuración de SSH:
```bash
sudo nano /etc/ssh/sshd_config
```
Asegúrate de tener configuraciones seguras, por ejemplo:

```bash
PermitRootLogin no
PasswordAuthentication 
```

Añade:
```bash
Match group sftp
	ChrootDirectory %h
	X11Forwarding no
	AllowTcpForwarding no
	ForceCommand internal-sftp
```

5. Reiniciar el servicio SSH:
Guarda los cambios y reinicia el servicio SSH:

```bash
sudo service ssh 
```