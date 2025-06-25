🐍 Guia Flask y Docker

Este proyecto demuestra cómo desarrollar, probar y contenerizar una aplicación básica utilizando Flask.

📋 Requisitos

Python 3.x

pip

Flask

🧑‍💻 Comandos Iniciales

sudo su

Este comando se utiliza para obtener privilegios de superusuario en la terminal:

sudo: permite ejecutar comandos como superusuario (root).

su: cambia al usuario root.

Combinados, otorgan una sesión completa como root, lo que permite ejecutar comandos sin anteponer sudo en cada línea.


📦 Instalación de Flask

pip3 install flask

Este comando instala el framework web Flask utilizando pip, el gestor de paquetes de Python 3.

pip3: gestiona paquetes para Python 3.

install flask: descarga e instala la librería Flask desde PyPI.

![image](https://github.com/user-attachments/assets/e597c0cd-91fc-4dbe-baa1-ac79026c1240)

![1](https://github.com/user-attachments/assets/04382e0a-058f-4146-823e-4a4bbb298faf)

📁 Navegación a la carpeta del proyecto

cd /home/devasc/labs/devnet-src/sample-app/

Al ejecutar ls, deberías ver lo siguiente:
![4 5](https://github.com/user-attachments/assets/908c067c-871c-4b33-8c71-80cf09f34358)

sample_app.py  sample-app.sh  static  templates

📝 Edición de sample_app.py

Abrimos el archivo:

nano sample_app.py

Escribimos lo siguiente:

from flask import Flask
from flask import request

sample = Flask(__name__)

@sample.route("/")
def main():
    return "Tu dirección IP es: " + request.remote_addr + "\n"

if __name__ == "__main__":
    sample.run(host="0.0.0.0", port=8000)

Guardamos y salimos:

CTRL + O

ENTER

CTRL + X

![2](https://github.com/user-attachments/assets/4ad1d724-ac33-44a6-b38c-b8b73032d023)


🌐 Ejecución de la aplicación

python3 sample_app.py

Abre el navegador y ve a http://[tu_IP]:8000Debería mostrar algo como:

Tu dirección IP es: [IP del cliente]
![9](https://github.com/user-attachments/assets/88024d99-f1d5-457a-a0d2-bbd99f00aeba)



🔍 Verificación de conexiones

netstat -tnlp
netstat -tnap

Significado de las opciones:

-t: muestra solo conexiones TCP

-n: muestra direcciones IP y puertos sin resolver nombres

-l: muestra solo puertos en modo LISTEN

-p: muestra el PID y nombre del programa asociado

-a: muestra todas las conexiones TCP activas

![image](https://github.com/user-attachments/assets/656277b7-ee23-4fad-b864-5ecc3436bd3a)


![8](https://github.com/user-attachments/assets/2a6edf5a-e731-477c-8675-9ad86b1f5965)

🖍️ Cambios de configuración

Editamos nuevamente sample_app.py para cambiar el puerto a 8181:
![2 1](https://github.com/user-attachments/assets/858dc02f-9aa7-4748-a4c3-a8b981414346)


sample.run(host="0.0.0.0", port=8181)

🎨 Edición de estilos y plantilla

static/style.css

Editamos el archivo con:

nano static/style.css

templates/index.html

Contiene la plantilla base con:
![2 4](https://github.com/user-attachments/assets/885e2705-371c-4c8d-8aed-6ee699027bc1)


<p>Tu IP es: {{ ip }}</p>
<link rel="stylesheet" href="../static/style.css">

✅ Verificación final en el navegador

Al abrir http://127.0.0.1:8181, se visualiza correctamente la IP y los estilos aplicados.
![muestra de ip](https://github.com/user-attachments/assets/049c461c-ca3d-4b16-88fe-9d55976664a8)

📊 Comprobación del estado del servidor Flask

Comandos útiles:

python3 sample_app.py
netstat -tnlp

La terminal debería mostrar que Flask está corriendo en el puerto 8181.

![Comprobacion de la parte 3](https://github.com/user-attachments/assets/43885eed-a18b-4940-a35d-e12759a7cb98)

⚙️ Script Bash sample-app.sh para automatización con Docker

Este script:

Crea un directorio temporal

Copia los archivos de la app

Genera un Dockerfile dinámico

Expone el puerto 8181

![Codigo de el sample sh](https://github.com/user-attachments/assets/6638962b-40ba-4ea2-8496-4d0de412a469)


🐳 Creación de imagen Docker y verificación

Al ejecutar el script, se crea una imagen etiquetada (por ejemplo, rduarte) lista para ejecutarse con Docker.

![parte 3 final cuando se crea el docker](https://github.com/user-attachments/assets/031f72c5-c6d3-4bfd-b7e7-dc759399d023)


🌐 Comprobación de la interfaz docker0

Verificamos que la interfaz virtual docker0 esté activa, lo que confirma que Docker está instalado correctamente.
![comprobaciond el docker0](https://github.com/user-attachments/assets/3418882c-170f-450a-b0b4-6671173cf941)

✅ Conclusión

Este proyecto demuestra cómo:

Desarrollar una aplicación básica con Flask

Verificar su funcionamiento con herramientas de red

Automatizar su despliegue usando un script Bash y Docker

👥 Integrantes

Diego Calderón

Ricardo Duarte

Raúl Vergara

