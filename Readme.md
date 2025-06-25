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

📁 Navegación a la carpeta del proyecto

cd /home/devasc/labs/devnet-src/sample-app/

Al ejecutar ls, deberías ver lo siguiente:

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

🌐 Ejecución de la aplicación

python3 sample_app.py

Abre el navegador y ve a http://[tu_IP]:8000Debería mostrar algo como:

Tu dirección IP es: [IP del cliente]

🔍 Verificación de conexiones

netstat -tnlp
netstat -tnap

Significado de las opciones:

-t: muestra solo conexiones TCP

-n: muestra direcciones IP y puertos sin resolver nombres

-l: muestra solo puertos en modo LISTEN

-p: muestra el PID y nombre del programa asociado

-a: muestra todas las conexiones TCP activas

🖍️ Cambios de configuración

Editamos nuevamente sample_app.py para cambiar el puerto a 8181:

sample.run(host="0.0.0.0", port=8181)

🎨 Edición de estilos y plantilla

static/style.css

Editamos el archivo con:

nano static/style.css

templates/index.html

Contiene la plantilla base con:

<p>Tu IP es: {{ ip }}</p>
<link rel="stylesheet" href="../static/style.css">

✅ Verificación final en el navegador

Al abrir http://127.0.0.1:8181, se visualiza correctamente la IP y los estilos aplicados.

📊 Comprobación del estado del servidor Flask

Comandos útiles:

python3 sample_app.py
netstat -tnlp

La terminal debería mostrar que Flask está corriendo en el puerto 8181.

⚙️ Script Bash sample-app.sh para automatización con Docker

Este script:

Crea un directorio temporal

Copia los archivos de la app

Genera un Dockerfile dinámico

Expone el puerto 8181

🐳 Creación de imagen Docker y verificación

Al ejecutar el script, se crea una imagen etiquetada (por ejemplo, rduarte) lista para ejecutarse con Docker.

🌐 Comprobación de la interfaz docker0

Verificamos que la interfaz virtual docker0 esté activa, lo que confirma que Docker está instalado correctamente.

✅ Conclusión

Este proyecto demuestra cómo:

Desarrollar una aplicación básica con Flask

Verificar su funcionamiento con herramientas de red

Automatizar su despliegue usando un script Bash y Docker

👥 Integrantes

Diego Calderón

Ricardo Duarte

Raúl Vergara

