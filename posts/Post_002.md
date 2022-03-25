[*volver al inicio*](../index.md)
# Entornos virtuales en Python
## con *virtualenv*
25/3/2022
---
Lo que sigue, es una breve reseña sobre la implementación de un entorno virtual en Python, utilizando Windows 10 y Visual Studio Code.

En Visual Studio Code, acceder a una nueva terminal (ctrl + mayús + ñ)

Eventualmente, también podría  hacerse  directamente desde la consola.

Verificar qué versión de Python está instalada ...

`python --version`

En mi caso devolvió

>>> Python 3.10.0

Instalar en forma global -es decir, no solo para el entorno vitual específico que queremos crear- el paquete de gestión de entornos virtuales ***virtualenv***

`pip install virtualenv`

Para el caso de que ya estuviese instalado, es posible que la respuesta sea:

WARNING: You are using pip version 22.0.3; however, version 22.0.4 is available.
You should consider upgrading via the 'C:\Usuario\python.exe -m pip install --upgrade pip' command.

En tal caso, convendría actualizarlo.

Lo de la ruta no es importante, porque se supone que Pythn está en el PATH, con lo que puede invocarse desde cualquier lado.

En tal caso, entonces, en la consola el siguiente comando.

`pip install --upgrade pip`

La respuesta...

ERROR: Could not install packages due to an OSError: [WinError 5] Acceso denegado: 'C:\Usuario\MyNombreDeUsuarioDeWindows\AppData\Local\Temp\pip-uninstall-_envxwcn\pip.exe'
Consider using the `--user` option or check the permissions.

Entonces, agregué `--user` resultando el siguiente comando.

`pip install --upgrade pip --user`

La respuesta fue

Requirement already satisfied: pip in c:\users\usuario\appdata\local\programs\python\python310\lib\site-packages (22.0.4)

Obsérvese que antes tenía instalado el pip 22.0.3 y ahora el pip 22.0.4, por lo que de momento, la cosa viene avanzando.

Ahora si, correspondería nuevamente instalar o actualizar el paquete virtualenv

`pip install virtualenv`

La respuesta fue

Requirement already satisfied: virtualenv in c:\users\usuario\appdata\local\programs\python\python310\lib\site-packages (20.13.1)
Requirement already satisfied: platformdirs<3,>=2 in c:\users\usuario\appdata\local\programs\python\python310\lib\site-packages (from virtualenv) (2.4.1)
Requirement already satisfied: filelock<4,>=3.2 in c:\users\usuario\appdata\local\programs\python\python310\lib\site-packages (from virtualenv) (3.4.2)
Requirement already satisfied: six<2,>=1.9.0 in c:\users\usuario\appdata\local\programs\python\python310\lib\site-packages (from virtualenv) (1.16.0)
Requirement already satisfied: distlib<1,>=0.3.1 in c:\users\usuario\appdata\local\programs\python\python310\lib\site-packages (from virtualenv) (0.3.4)

Para crear un envortno virtual:

virtualenv + nombre_que_le_quiero_poner_al_entorno_virtual

(reemplazar ombre_que_le_quiero_poner_al_entorno_virtual por un nombre, lo mas corto posible, según comento seguidamente)

Posibles nombres estándar para envornos virtuales:

env
.env
enviroment

Eventualmente, si se que estoy trabajando o voy a trabajar con mas de un entorno virtual, entonces podría ser env1, env2, env3 etc.

En este ejemplo, voy a utilizar `env`

A su vez, voy a crear una carpeta para ese entorno virtual.

En mi caso, será dentro de la ruta:

`C:\Users\Usuario\dropbox\code`

La carpeta específica, en esa ruta, será entorno:

`C:\Users\usuario\dropbox\code\entorno`

Por lo tanto, ya posicionado en esa nueva carpeta, en la terminal (en este caso en el powershell desde VSC) ejecuto el siguiente comando.

`virtualenv env`

Devolvió como respuesta

created virtual environment CPython3.10.0.final.0-64 in 5954ms
  creator CPython3Windows(dest=C:\Users\usuario\Dropbox\Code\entorno\env, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=C:\Users\MiNombreDeUsuarioDeWindows\AppData\Local\pypa\virtualenv)
    added seed packages: pip==22.0.4, setuptools==60.9.3, wheel==0.37.1
  activators BashActivator,BatchActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator

A su vez, si inspecciono la carpeta entorno, se observa que se creó una carpeta env que dentro tiene dos subcarpetas /Lib y otra /Scripts y ademas tiene dos archivos.

Para activar el entorno virtual:

Mediante el powershell no me fucionó, pero si directamente en consola, así que lo detallo a continuación:

Directamente en la consola de windows, posicionado dentro de la carpeta Scripts  ejecutar el siguiente comando:

`activate`

Notar que hay un activate.bat en la consola y es eso lo que se está ejecutando.

Como respuesta, el símbolo de sistema informará que hay un ambiente activado al mostrarse así:

(env) c:\Users\usuario\Dropbox\Code\entorno\env\Scripts>

El efecto de tener activado el entorno virtual, es que los paquetes que se instalen (via pip) mientras ello se mantenga, se instalarán dentro de ese entorno virtual.

A tal fin, a modo de ejemplo, voy a instalar flask.

`pip install flask`

La respuesta es larga, pero en concreto, se instalaron varios paquetes y dependencias que integran el conjunto necesario para trabajar flask.

Ahora, para conocer que paquetes están instalados en el entorno, se debe ejecutar el siguiente comando.

Estando posicionado en la consola preferentemente en la carpeta raíz del entorno virtual.

`pip freeze`

La respuesta fue:

click==8.0.4
colorama==0.4.4
Flask==2.0.3
itsdangerous==2.1.1
Jinja2==3.0.3
MarkupSafe==2.1.1
Werkzeug==2.0.3

Pero también puedo hacer que esa información, en vez de presentarse en pantalla, se genere un archivo y salga esa información como su contenido.

El estandar para ello es

`pip freeze > requeriments.txt`

Como respuesta, se generó el archivo.

Para desactivar el entorno virtual

`deactivate`

Y para deshacerme de los paquetes instalados, se borra y listo el pollo.


---
### *Páginas en markdown para todes*
#### *Por cualquiercosateaveriguo@gmail.com*