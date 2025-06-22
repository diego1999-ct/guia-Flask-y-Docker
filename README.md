# Guia-Flask-y-Docker

Esta es una aplicación básica hecha con [Flask]

# Requisitos

- Python 3.x
- pip
- Flask

sudo su

Este comando se utiliza para obtener privilegios de superusuario en la terminal.
sudo: permite ejecutar comandos como superusuario (root).
su: cambia al usuario root.
Combinados, te otorgan una sesión completa como root, lo que te permite ejecutar comandos sin anteponer sudo en cada línea

pip3 install flask
Este comando instala el framework web Flask utilizando pip, el gestor de paquetes de Python 3.
pip3: gestiona paquetes para Python 3.
install flask: descarga e instala la librería Flask desde PyPI

![image](https://github.com/user-attachments/assets/e597c0cd-91fc-4dbe-baa1-ac79026c1240)

![1](https://github.com/user-attachments/assets/04382e0a-058f-4146-823e-4a4bbb298faf)

luego de instaladas las librerias 

root@labvm:/home/devasc# ls
Desktop  Documents  Downloads  labs  snap
root@labvm:/home/devasc# cd labs/
root@labvm:/home/devasc/labs# ls
devnet-src
root@labvm:/home/devasc/labs# cd devnet-src
root@labvm:/home/devasc/labs/devnet-src# ls
ansible        jenkins   parsing  python      school-library  unittest
coding-basics  mapquest  ptna     sample-app  security        webex-teams
root@labvm:/home/devasc/labs/devnet-src# cd sample-app/
root@labvm:/home/devasc/labs/devnet-src/sample-app# ls
sample_app.py  sample-app.sh  static  templates

deberia de verse algo asi

![image](https://github.com/user-attachments/assets/941e6e3d-dd42-410c-a264-604d2220c4e4)

posteriormente al ingresar a 
root@labvm:/home/devasc/labs/devnet-src/sample-app# nano sample_app.py
(Este archivo suele contener una pequeña aplicación web escrita con Flask, un microframework de Python.)
 
escribimos lo siguiente 

from flask import Flask

from flask import request

sample  = Flask(__name__)

@sample.route("/")
def main():
        return "Tu direccion Ip es : " +request.remote_addr + "\n"

if  __name__ =="__main__":
     sample.run(host="0.0.0.0", port= 8000)

Luego CTRL+O
ENTER
CTRL+X (para salir)

![2](https://github.com/user-attachments/assets/4ad1d724-ac33-44a6-b38c-b8b73032d023)

from flask import Flask
from flask import request

 Estas líneas importan Flask (para crear la app) y request (para obtener la IP del cliente que se conecta).

sample = Flask(__name__)

Aquí se crea una instancia de la aplicación web.
El nombre sample es el nombre de tu app Flask. Puedes llamarla app, web, myapp, etc.

  @sample.route("/")
def main():
    return "Tu direccion Ip es : " + request.remote_addr + "\n"  

Esto define una ruta (endpoint).
Cuando alguien abre http://[tu_ip]:8000/, se ejecuta la función main().
request.remote_addr obtiene la IP del visitante.
El mensaje "Tu direccion Ip es : " se concatena con esa IP y se devuelve como respuesta.
     
if __name__ == "__main__":
    sample.run(host="0.0.0.0", port=8000)

Esta línea lanza el servidor Flask solo si ejecutas este archivo directamente (python3 sample_app.py).
host="0.0.0.0": permite que Flask escuche en todas las interfaces de red (no solo localhost).
port=8000: especifica que el servidor debe correr en el puerto 8000.  

ejecutamos 
root@labvm:/home/devasc/labs/devnet-src/sample-app# python3 sample_app.py 

![image](https://github.com/user-attachments/assets/83a77d60-283d-43d7-adc7-a70e858a58d8)

presionamos click derecho y abrir link
![image](https://github.com/user-attachments/assets/fa8a93e7-7bb9-48e0-b314-0c089a925ac3)


Esto abrir el navegador y debera mostrar esto
![9](https://github.com/user-attachments/assets/88024d99-f1d5-457a-a0d2-bbd99f00aeba)

![4 5](https://github.com/user-attachments/assets/908c067c-871c-4b33-8c71-80cf09f34358)

luego nis salimos y ehecutamos 
netstat -tnlp  y    netstat -tnap

  Significado de cada opción:
-t	Muestra solo conexiones TCP
-n	Muestra direcciones IP y puertos sin resolver nombres (más rápido)
-l	Muestra solo puertos en modo LISTEN (esperando conexiones)
-p	Muestra el PID y nombre del programa asociado

Solo puertos TCP que están escuchando en el sistema (por ejemplo, servidores web, SSH, Flask).

-a	Muestra todas las conexiones (LISTEN, ESTABLISHED, TIME_WAIT, etc.)

Todas las conexiones TCP activas, tanto las que están escuchando (LISTEN) como las que están establecidas, cerrándose, et

![image](https://github.com/user-attachments/assets/656277b7-ee23-4fad-b864-5ecc3436bd3a)


![8](https://github.com/user-attachments/assets/2a6edf5a-e731-477c-8675-9ad86b1f5965)

