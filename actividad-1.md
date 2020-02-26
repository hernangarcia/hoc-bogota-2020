En este laboratorio, aprenderás a utilizar las herramientas y tecnologías que usan mujeres y hombres en empresas como Nasa, Nike, Spotify, Pinterest, para crear experiencias digitales que son usadas por millones de personas alrededor del mundo.

| | |
|--|--|
|![github](https://desktop.github.com/images/desktop-icon.svg)|Github: te permitirá almacenar el código fuente de las aplicaciones o websites que crees.|
| ![Cloud9](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/cloud9.png)| Cloud9: es un ambiente de desarrollo integrado (IDE) basado en la nube que te permite escribir, ejecutar y depurar tu código sólo con un navegador web. |
|![Hugo](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/hugo.png)|Hugo: es un generador de contenido estático para construir websites y aplicaciones en internet.|
| ![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/stackedit.png) | StackEdit: El editor para crear y dar formato a tu código fuente. |
| ![amplify](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/amplify.png) | AWS Amplify: es una plataforma de desarrollo para la creación y publicación de aplicaciones móviles y web. |

---

**Sigue los pasos a continuación para completar el workshop.**

## **Configura tu cuenta de AWS**

Si estás en un evento de AWS:

 1. Solicita a los facilitadores de la actividad el código de acceso de tu equipo.
 2. Navega a [esta dirección](https://dashboard.eventengine.run/) y
 3. Una vez allí, presiona "*AWS Console*".

## **Configura tu ambiente de desarrollo en AWS Cloud9**
Una vez que estés en la consola web de AWS, en la barra de herramientas superior, a la izquierda, despliega el menú "*Servicios*". Ingresa "*Cloud9*" en el campo de búsqueda y haz click sobre el primer resultado que aparezca.

![](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2017.11.12.png)

Una vez en la consola de *Cloud9*, presiona el botón color naranja "*Create Environment*"

Al cargar la siguiente pantalla, completa los datos solicitados. Ingresa un nombre para tu ambiente de desarrollo (por ejemplo "HoC Bogotá 2020"). La descripción es opcional.

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2017.24.39.png)

Presiona el botón "*Next Step*"

En la pantalla "*Configure Settings*", usa la siguiente configuración:

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2017.28.22.png)

Presiona el botón "*Next Step*". Revisa la configuración y presiona el botón "*Create environment*".

Tu ambiente de desarrollo para hacer y deshacer :smirk: estará listo en unos dos minutos. Mientras tanto...

## **Configuremos tu repositorio de código fuente**

En tu navegador de internet, visita [github.com](https://github.com)

Si no tienes una cuenta, completa el formulario de registro con el nombre de usuario que desees, un correo válido y una contraseña. 

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.29.46.png)

Luego de ingresar tus datos, presiona el botón "*Verify*" en la siguiente pantalla, resuelve el acertijo y presiona el botón azul con el texto "*Next: Select a plan*":

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-24%2023.39.08.png)

En la siguiente pantalla, presiona el botón azul que dice "*Choose free*"

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-24%2023.39.42.png)

Y por última, en la siguiente pantalla, presional el enlace con el texto "Skip this step" para terminar con el proceso de creación de la cuenta de Github.

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-24%2023.40.11.png)

En la pantalla "*Create a New Repository*", en "Repository name" ingresa el nombre que desees (por ejemplo "hoc-bogota-2020"). Deja el resto de los valores por defecto y presiona "*Create Repository*"

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.33.41.png)

Deja abierta la siguiente pantalla, más adelante vas a necesitar los comandos que ahí aparecen:

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.36.58.png)

## **Vamos a crear tu nuevo Blog**
Regresa a tu ambiente de desarrollo en la consola de AWS, en la barra superior selecciona "Window" y presiona "*New terminal*".

**Instala HUGO:**
Ejecuta los siguientes comandos en tu terminal para descargar la última versión de Hugo e instalarla en tu ambiente de desarrollo. Es mejor si los ejecutas uno por uno para no equivocarte.

    wget https://github.com/gohugoio/hugo/releases/download/v0.64.1/hugo_0.64.1_Linux-64bit.deb
    
    sudo dpkg -i hugo_0.64.1_Linux-64bit.deb

Verifica que HUGO está instalado, usando este comando:

    hugo version

Crea tu nuevo website, usando el siguiente comando (puedes cambiar "myblog" por el nombre que quieras):

    hugo new site myblog

Agrega un theme a tu nuevo website para que se vea mucho mejor. Ingresa al directorio de tu nuevo website:

    cd myblog

Descarga el componente que transforma tu nuevo site en un Blog:

    git init
    
    git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/gohugo-theme-ananke

Agreguemos algunos datos de prueba a tu blog, ejecutando estos comandos. Es mejor si los ejecutas uno por uno para no equivocarte.

    cp themes/gohugo-theme-ananke/exampleSite/config.toml .

    cp -R themes/gohugo-theme-ananke/exampleSite/content/* ./content

    cp -R themes/gohugo-theme-ananke/exampleSite/static/* ./static

    cp themes/gohugo-theme-ananke/static/images/gohugo-default-sample-hero-image.jpg ./static/images/

Tu ambiente de desarrollo debería lucir como la siguiente imagen. A la izquierda verás los directorios que conforman tu website. En esa estructura de directorios es donde vamos a estar trabajando.

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/aux2.png)

Vamos a editar la configuración de  tu nuevo website para que use estos datos de prueba:

 **1.** En el listado de archivos a tu izquierda, abre el archivo de configuración de HUGO haciendo click en el que se llama "*config.toml*"

 **2.** Cambia el valor del parámetro "title" por el nombre que quieras colocarle a tu blog. Por ejemplo "Mi querido blog".
 
 **3.** Elimina la linea donde se encuentra el parámetro "*themesDir*"
 
 Deja el resto de los valores por defecto. Presiona las teclas "*control*" y la tecla con la letra "*s*" al mismo tiempo para guardar el archivo. Usa la siguiente imagen como ejemplo:
 
![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-24%2016.41.48.png)

Probemos cómo se ve tu nuevo website. En el menú superior de tu ambiente de desarrollo, presiona "*Preview*" y luego "*Preview Running Application*"

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/aux3.png)

De la ventana que se abre, copia el url que está en la barra de navegación; uno parecido a este:

    https://xxxxxxxxx.vfs.cloud9.us-east-1.amazonaws.com

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/aux4.png)

En el siguiente comando, reemplaza el valor de "*--baseURL*" con el url que copiaste anteriormente, y ejecuta en tu terminal:

    hugo server --bind=0.0.0.0 --baseURL=https://xxxxxxxxx.vfs.cloud9.us-east-1.amazonaws.com -p 8080

Refresca la ventana de "*Preview*". Deberías ver tu nuevo website :clap: :confetti_ball: :clap:

## **Vamos a crear tu primer post.**

En el listado de archivos a tu izquierda, abre la carpeta llamada "*content*" y luego abre la carpeta llamada "*post*". Con el cursor del mouse sobre la carpeta "*post*", haz un click derecho para desplegar el menú auxiliar y presiona "*New File*".

![enter image description here](https://github.com/hernangarcia/how-to-hugo-aws-amplify/blob/master/images/Screenshot%202020-02-24%2016.48.09.png?raw=true)

Cuando se agregue el nuevo archivo, dale el nombre que desees, por ejemplo "*hoc-bog-2020.md*" y presiona la tecla "*enter*" (recuerda, el nombre puede ser el que desees, sim embargo la extensión debe ser "*.md*").

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-24%2016.52.06.png)

Para crear el contenido de tu primera publicación de manera visual, vamos a usar StackEdit. En una nueva ventana en tu navegador web, ingresa a stackedit.io y presiona "*Start Writing*".

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-24%2016.56.22.png)

StackEdit es un editor visual de Markdown. Markdown es un lenguaje que permite crear publicaciones usando un formato de texto plano, fácil de leer y fácil de escribir, y que luego puede ser convertido a HTML para publicar en internet. Empresas como Amazon, Nasa y Nike usan Markdown para generar contenido.

Una vez que esté abierto el editor de StackEdit, vas a encontrar una pantalla como la siguiente:

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-24%2017.55.12.png)

Como en la imagen anterior, a tu mano izquierda vas a encontrar contenido de ejemplo escrito usando Markdown; ahí es donde vas a crear tu primera publicación. A tu derecha, puedes ver cómo lucirá el contenido en realidad.

Borra todo el contenido del editor: con el cursor en la ventana de edición, presiona el botón derecho de tu mouse, luego selecciona "*Select All*" y presiona la tecla de borrar en tu teclado.

En otra pestaña de tu navegador, ingresa a <a href="https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/markdown-samples/sample-1.md" target="_blank">este enlace</a> y copia el contenido que ves; para esto selecciona todo el texto, presiona el botón derecho de tu mouse y selecciona "*Copy*".

Regresa a la ventana de StackEdit y, en la ventana de edición, pega el texto que copiaste en el paso anterior usando el botón derecho de tu mouse para desplegar el menú de acciones y seleccionando "*Paste*".

**¡Usa tu imaginación y modifica la publicación con el contenido que desees!**

Regresa a la ventana del navegador donde está tu ambiente de desarrollo, busca el archivo que creaste para tu nueva publicación (puedes haber usado "*hoc-bog-2020.md*" como nombre). Una vez esté ahí el cursor de tu mouse, presiona el botón derecho y selecciona "*Paste*".

Para ver como quedó, guarda la publicación presionando las teclas "*control*" y "*s*" al mismo tiempo.

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-24%2023.28.06.png)

Ejecuta el siguiente comando de nuevo para visualizar tus cambios (recuerda usar el baseURL correcto):

    hugo server --bind=0.0.0.0 --baseURL=https://xxxxxxxxx.vfs.cloud9.us-east-1.amazonaws.com -p 8080

Si está todo bien, en la misma venta donde donde ejecutaste el comando anterior, presiona las teclas "control" y "c" para detener la visualización de tu website. 

Finalmente, guardemos la publicación en tu repositorio de manera permanente ejecutando los siguientes comandos. Es mejor si los ejecutas uno por uno para no equivocarte.

    git add .
    
    git commit -m "mi primer post"
    
    git remote add origin https://github.com/<github-username>/<github-repository-name>.git
    
    git push -u origin master

En el comando anterior sustituye *github-username* y *github-repository-name* con los valores
de tu cuenta de github:

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.36.58%20copy.png)

Cuando se pregunte por ellos, ingresa tu nombre de usuario de github y la contraseña.

## **Vamos a publicar tu website en la internet:**

En tu navegador web, regresa a la consola de AWS, despliega el menú "*Services*" y busca  "*Amplify*" en la barra de búsquedas. Al mostrar la consola de Amplify, presiona "*Get Started*" bajo el titulo "*Deploy*"

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2019.23.36.png)

**Conectemos el repositorio de código de tu website:**

En la siguiente pantalla, selecciona el servicio proveedor de tu repositorio de código (en este momento, GitHub):

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2019.27.20.png)

Presiona "Continue" y a continuación, selecciona el repositorio que creamos al inicio de esta guía (*github-repository-name*), selecciona el branch "*master*" y presiona "*Next*":

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2019.31.19.png)
	
Configura los ajustes para construir tu website, ingresando el nombre que desees. Deja el resto de los valores por defecto y presiona el botón "*Next*".

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-25%2000.08.42.png)

Luego presiona "*Save and Deploy*" y espera que el indicador de progreso esté en "*Verify*". 

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-25%2000.03.44.png)

Ahora que tu website está en internet, para visitarlo presiona el enlace al final de la sección "*master*", uno parecido a este:

    https://master.xxxxxxxx.amplifyapp.com/

Luego de inspeccionar tu website, si encuentras algún error relacionado a las imágenes en tu blog, sigue los siguientes pasos:

 1. En el listado de archivos a tu izquierda, abre el archivo de configuración de HUGO haciendo click en el que se llama "*config.toml*"

 2. Una vez que abras el archivo, reemplaza el valor de "*baseURL*" con el URL de Amplify. Quedará algo como esto: 

    `baseURL = "https://master.xxxxxxxxx.amplifyapp.com"`

Presiona la tecla "*control*" + la tecla con la letra "*s*", al mismo tiempo, para guardar la modificación.

Ejecuta los siguientes comandos, uno por uno, para publicar tus cambios en la internet:

    git add .

    git commit -m "changed baseURL"

    git push -u origin master

Ingresa tus credenciales de github si son solicitadas.

Regresa a la consola de Amplify en tu navegador web. Espera que el indicador de progreso esté en "*Verify*". 

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-25%2000.03.44.png)

Verifica de nuevo tu website, presionando el enlace al final de la sección "*master*", uno parecido a este:

    https://master.xxxxxxxx.amplifyapp.com/

**:clap: :clap: Ya tienes tu propio Blog en la internet :clap: :clap:**
