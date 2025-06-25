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

 El contenido del archivo sample_app.py siendo editado con el editor de texto nano.
 
 su usa el comando nano sample_app.py para abrir o modificar el archivo
 
 se edita el puerto y pasar ser de 8080 a 81818 
 
![2 1](https://github.com/user-attachments/assets/858dc02f-9aa7-4748-a4c3-a8b981414346)

Edición del archivo static/styke.css

Archivo de estilos CSS editado con el comando nano static/style.css

![2 4](https://github.com/user-attachments/assets/885e2705-371c-4c8d-8aed-6ee699027bc1)

Edición de la plantilla templates/index.html 

Plantilla HTML base usada con Flask

Contiene un marcador {{ ip }} donde se inyecta dinámicamente la IP del cliente. También enlaza el archivo style.css para aplicar estilos.

![2 3](https://github.com/user-attachments/assets/a351b7e7-c2f0-458e-92ad-b9bf7fcfad9d)

Vista incial de la aplicación Flask en el navegador

Vista del navegador de la IP http://127.0.0.1:8181.

Muestra correctamente los textos editados y agregados anteriormente.

![muestra de ip](https://github.com/user-attachments/assets/049c461c-ca3d-4b16-88fe-9d55976664a8)

Verificación de Flask en terminal

visualización del servidor Flask

La terminal muestra Flask corriendo en el puerto 8181

comandos para confirmar que flask esta funcionando correctamente 

python3 sample_app.py

netstat -tnlp

![Comprobacion de la parte 3](https://github.com/user-attachments/assets/43885eed-a18b-4940-a35d-e12759a7cb98)

Script Bash sample.sh para automatización con Docker

Crea un directorio temporal.

Copia los archivos de la app.

Genera un Dockerfile dinámico.

Expone el puerto 8181.

![Codigo de el sample sh](https://github.com/user-attachments/assets/6638962b-40ba-4ea2-8496-4d0de412a469)

Creación de la imagen Docker y verificación

El proceso de construcción se completa exitosamente. Se muestra una nueva imagen etiquetada como rduarte o similar, lista para su ejecución.

![parte 3 final cuando se crea el docker](https://github.com/user-attachments/assets/031f72c5-c6d3-4bfd-b7e7-dc759399d023)

Comprobación del estado de la interfaz docker0

La interfaz virtual docker0 aparece, lo que indica que Docker está instalado.

![comprobaciond el docker0](https://github.com/user-attachments/assets/3418882c-170f-450a-b0b4-6671173cf941)

Conclusión

Este proyecto demuestra cómo desarrollar, probar y contenerizar una aplicación Flask básica. Además, se documenta el proceso completo de despliegue y verificación con herramientas comunes de red y Docker.


Integrantes
Diego Calderon
Ricardo Duerte
Raul Vergara

