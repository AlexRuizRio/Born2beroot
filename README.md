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
