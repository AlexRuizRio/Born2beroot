# Born2beroot
Apuntes de una configuración de un servidor con Debían  sin interfaz gráfica.

## Elección sobre el sistema operativo sobre Debian o Rocky

**Debian** es una de los SO mas antiguos, se lanzo por primera vez en 1993 y se desarrolla de manera mas comunitaria. 
Se enfoca en un sistema universal que funciona en una amplia variedad de dispositivos (Servidores, Estaciones de trabajo, Sistemas embebidos). 
Su objetivo principal es ser estable y configurable basado en software libre.

Las versiones se lanzan cuando se consideran lo suficientemente probadas y testeadas.

**Debian** es conocido por ser la base de otras distribuciones y tiene relación estrecha con otros proyectos de software libre.

En cambio, **Rocky** es relativamente nuevo ya que se anuncio en 2020 como un esfuerzo de llenar el vació de CentOS Linux y esta destinada a ser una distribución comunitaria de nivel empresarial y con compatibilidad con RHEL (Red Hat Enterprise Linux).

En resumen Debian es un sistema universal centrado en la estabilidad y **Rocky** se centra en una alternativa para entornos empresariales.


## Diferencias entre aptitude y apt

La interfaz **apt** es mas sencilla y directa. Proporcionando un conjunto de comandos básicos (buscar, instalar, actualizar y eliminar paquete). Realiza una resolución de dependencias simple, no manteniendo un historial de las acciones realizadas. Útil para usuarios que desean un enfoque rápido y eficiente.

En **aptitude** tiene un interfaz mas interactiva y amigable. Proporcionando características adicionales como por ejemplo: navegar por los paquetes, ver dependencias, resolver conflictos...
Por ultimo **aptitude** si que cuenta con un historial completo de las acciones realizadas.


## Que son SELinux y AppArmor

SELinux (Security-Enhanced Linux) y AppArmor son dos sistemas de seguridad para el control de acceso obligatorio en Linux, que ayudan a restringir lo que los procesos pueden hacer en el sistema.

SELinux: Es un sistema de seguridad basado en políticas que implementa un modelo de control de acceso obligatorio (MAC). Utiliza un modelo basado en etiquetas (labels) para controlar el acceso de los procesos a los recursos del sistema. Es más flexible y granular, permitiendo políticas de seguridad detalladas, pero es más complejo de configurar y mantener. Se usa principalmente en distribuciones como Red Hat, Fedora y CentOS.

AppArmor: Funciona con un enfoque más simple, utilizando perfiles basados en rutas de archivos para controlar el acceso de las aplicaciones. Es más fácil de usar y configurar, con menor impacto en el rendimiento, pero menos flexible y granular que SELinux. Viene habilitado por defecto en distribuciones como Ubuntu y Debian.

Dado que mi sistema operativo es Debian deberia venir instalado, por lo que para verificar que este instaladoy se inicie automaticamente utilizaremos el siguiente comando:
```bash
systemctl status apparmor
```


## Servicio SSH

SSH (Secure Shell) es un protocolo de red que permite a los usuarios conectarse de forma segura a otro ordenador a través de una red, como Internet, que puede no estar completamente asegurada. Se utiliza principalmente para acceder de forma remota a sistemas y ejecutar comandos, así como para transferir archivos de manera segura. Un resumen sencillo de cómo funciona SSH:

1 Conexión: El cliente SSH inicia una conexión al servidor SSH remoto a través del puerto 22.

2 Autenticación: El cliente y el servidor se autentican mutuamente usando claves criptográficas o contraseñas.

3 Cifrado: Una vez autenticado, se establece un canal de comunicación cifrado, asegurando que toda la información esté protegida contra interceptaciones.

4 Sesión: El cliente puede ejecutar comandos en el servidor remoto, transferir archivos y realizar otras tareas, todo a través de la conexión segura.

5 Interacción: Todo el tráfico entre el cliente y el servidor está encriptado, garantizando la privacidad y seguridad de la información transmitida.

Para coloborar que este servicio este en funcionamiento podemos ejecutar:

```bash
sudo service ssh status
```

Y en el caso de que queramos cambiar la configuracion del servicio SSH, tenemos 2 archivos a modificar. En el caso de queramos cambiar algo de la configuracion del cliente SSH modificaremos este archivo:

```bash
sudo nano /etc/ssh/ssh_config
```
Y si queremos cambiar la configuracion del servidor SSH seria este archivo:

```bash
sudo nano /etc/ssh/sshd_config
```
En el caso de que me quiera conectar desde la termnal del pc anfitrion pondremos en la terminal de dicho ordenador:

```bash
ssh gemartin@localhost -p 4343
```

## Firewall UFW
UFW (Uncomplicated Firewall) es una herramienta de configuración de firewall en sistemas basados en Linux, especialmente diseñada para facilitar la administración de reglas de firewall para usuarios que no son expertos en seguridad de redes. UFW simplifica la gestión de reglas de firewall y permite a los usuarios controlar el acceso a servicios y puertos de manera más sencilla.
Para comprobar que el servicio este activo:

```bash
sudo ufw status
```

Para que nuestro firewall peremita las conexiones utilizaremos:

```bash
sudo ufw allow 4242
```

Y si lo queremos eliminar añadiendo numbered al comando sudo ufw status saldran unos numeros al principio de cada regla, asi que pordemos utilizar este comando poniendo el numero como parametro:

```bash
sudo ufw delete 1
```
