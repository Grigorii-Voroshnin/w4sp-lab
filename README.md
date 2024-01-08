# ИСТОРИЯ

1. Первая версия настоящего проекта находится [здесь](https://github.com/w4sp-book/w4sp-lab/wiki/Lab-Installation).
2. Вторая версия настоящего проекта находится [здесь](https://medium.com/@vaibjav2raj/setting-up-the-w4sp-lab-in-2020-d4df6a3d2a5e).
Во второй версии настойщий проект был переписан с python2 на python3.
3. Третье версией является проект, в котором вы сейчас находитесь.
4. 
ANTECEDENTES.

    La primera versión de este proyecto puede consultarse [aquí](https://github.com/w4sp-book/w4sp-lab/wiki/Lab-Installation).
    La segunda versión del presente proyecto se puede encontrar [aquí](https://medium.com/@vaibjav2raj/setting-up-the-w4sp-lab-in-2020-d4df6a3d2a5e). En la segunda versión, el presente proyecto fue reescrito de python2 a python3.
    La tercera versión es el proyecto en el que se encuentra actualmente.

INTRODUCCIÓN.

Este es el entorno de laboratorio para el libro Wireshark for Security Professionals: Using Wireshark and the Metasploit Framework. Puedes referirte al Capítulo 2 de ese libro para una fácil referencia al laboratorio. El laboratorio está construido sobre Docker y Kali Linux y proporciona una red realista con numerosos servicios útiles para aprender los fundamentos de la seguridad utilizando Wireshark.
Instalación
¡CUIDADO!

    Las pruebas de rendimiento se realizaron sólo en Kali Linux 2023.3. Puede funcionar en versiones posteriores.
    Debido a la inestable situación geopolítica para los usuarios rusos durante toda la instalación es necesario utilizar VPN. VPN debe estar habilitado en la máquina virtual o en el host si la máquina virtual está conectada a través de NAT.
 
## Iniciar instalación

3. Después de haber configurado la máquina virtual Kali. Crea un nuevo usuario.
```
sudo useradd -m w4sp-lab -s /bin/bash -G sudo -U
```
4. Establezca la contraseña
```
sudo passwd w4sp-lab
```
5. Cierre la sesión y cambie al usuario w4sp-lab, luego descargue el entorno de laboratorio real.
Navega a la carpeta de descargas y luego al directorio descargado.
Instale primero los programas necesarios para el trabajo.
```
sudo apt install -y python3-docker
sudo apt install wireshark net-tools ethtool xterm
```
6. Ahora la parte más importante. Esto llevará mucho tiempo y parecerá que la descarga se ha colgado, pero no mates el proceso y simplemente espera.
```
sudo python3 w4sp_webapp.py
```
7. Una vez cargadas todas las imágenes, el navegador puede abrirse automáticamente o no. No te asustes. abre una pestaña de Firefox o hromium y escribe esta dirección.
```
http://127.0.0.1:5000
```
8. Debería aparecer el laboratorio. Pulsa el botón SETUP. 
9. Puede haber un fallo. Lo sentimos, pero ahora sólo tienes que introducir algunos comandos más para que las cosas funcionen.
Mata el proceso, cierra la pestaña. Luego en el terminal.
```
sudo usermod -aG docker w4sp-lab
sudo systemctl enable docker
```
10. Ahora ejecuta de nuevo el script de Python
```
sudo python3 w4sp_webapp.py
```
11. Escribe en el navegador
```
http://127.0.0.1:5000
```
12. Pulsa el botón SETUP.
Tu laboratorio está listo y funcionando.

