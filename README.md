## **Configuremos tu ambiente de desarrollo en AWS Cloud9**

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

Si no tienes una cuenta, completa el formulario de registro con el nombre de usuario que desees,
un correo válido y una contraseña.

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.29.46.png)

Una vez que inicies sesión, en el menú de la izquierda, presiona el botón verde "*New*".
![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.32.04.png)

En la pantalla "*Create a New Repository*", en "Repository name" ingresa el nombre
que desees (por ejemplo "hoc-bogota-2020")

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.33.41.png)

Deja abierta la siguiente pantalla, más adelante vas a necesitar los comandos que ahí aparecen:

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.36.58.png)

## **Vamos a crear tu nuevo Blog**
Regresa a tu ambiente de desarrollo en la consola de AWS, en la barra superior selecciona "Window" y presiona 
"*New terminal*".

**Instala HUGO:**
Ejecuta los siguientes comando en tu terminal

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

Agreguemos algunos datos de prueba a tu blog, ejecutando estos comandos:

    cp themes/gohugo-theme-ananke/exampleSite/config.toml .
    cp -R themes/gohugo-theme-ananke/exampleSite/content/* ./content
    cp -R themes/gohugo-theme-ananke/exampleSite/static/* ./static
    cp themes/gohugo-theme-ananke/static/images/gohugo-default-sample-hero-image.jpg ./static/images/

Vamos a editar la configuración de  tu nuevo website para que use estos datos de prueba:

 **1.** Abre el archivo de configuración de HUGO usando el comando más
    abajo: `nano config.toml`
    
![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2018.48.32.png)

 **2.** Cambia el valor del parámetro "title" por el nombre que quieras colocarle a tu blog. Por 
ejemplo "Mi querido blog".
 **3.** Elimina la linea donde se encuentra el parámetro "*themesDir*"
 **4.** Presiona la tecla "*control*" + la tecla con la letra "*o*" y luego la tecla "*control*" + la tecla con la letra "*x*"

Probemos cómo se ve tu nuevo blog. En el menú superior de tu ambiente de desarrollo, presiona "*Preview*" y luego "*Preview Running Application*"

De la ventana que se abre, copia el url que está en la barra de navegación; uno parecido a este:

    https://xxxxxxxxx.vfs.cloud9.us-east-1.amazonaws.com

En el siguiente comando, reemplaza el valor de "*--baseURL*" con el url que copiaste anteriormente,
y ejecuta en tu terminal:

    hugo server --bind=0.0.0.0 --baseURL=https://xxxxxxxxx.vfs.cloud9.us-east-1.amazonaws.com -p 8080

Refresca la ventana de "*Preview*". Deberías ver tu nuevo website :clap: :confetti_ball: :clap:

## **Vamos a crear tu primer post.**

Regresa a tu ambiente de desarrollo, presiona el icono "+" y luego "*New Terminal*". En este nuevo terminal, ejecuta los siguientes comandos:

    cd myblog
    hugo new posts/hoc-bog-2020.md
    nano /home/ubuntu/environment/myblog/content/posts/hoc-bog-2020.md

Edita tu nuevo post con la información que quieras:

![enter image description here](https://raw.githubusercontent.com/hernangarcia/how-to-hugo-aws-amplify/master/images/Screenshot%202020-02-19%2019.10.20.png)
Usando el atributo "featured_image", puedes agregar una imagen en el tope de tu publicación.

Usa los elementos [en este enlace](https://www.markdownguide.org/cheat-sheet/) para escribir el contenido de la manera que desees. 
Por ejemplo, puedes usar `![alt text](url-to-the-image.jpg)` para agregar una imagen donde quieras.

Ejecuta el siguiente comando de nuevo para visualizar tus cambios (recuerda usar el baseURL correcto):

    hugo server --bind=0.0.0.0 --baseURL=https://xxxxxxxxx.vfs.cloud9.us-east-1.amazonaws.com -p 8080

Vamos a guardar los cambios en tu repositorio de manera permanente:

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
	
Configura los ajustes para construir tu website, ingresando el nombre que desees. 

Presiona "*Next*", revisa tu configuración y luego presiona "*Save and Deploy*".

Espera que el indicador de progreso esté en "*Verify*". Luego, presiona el enlace al final
de la sección "Frontend Environments", uno parecido a este:

    https://master.xxxxxxxx.amplifyapp.com/

Si encuentras algún error relacionado a las imágenes en tu blog, sigue los siguientes pasos:

 1. Ve a tu ambiente de desarrollo y edita el archivo de configuración de tu website, usando
el siguiente comando: `nano config.toml`
 2. Una vez que abras el archivo, reemplaza el valor de "*baseURL*" con el URL de Amplify. Quedará
algo como esto: `baseURL = "https://master.xxxxxxxxx.amplifyapp.com"`

Presiona la tecla "*control*" + la tecla con la letra "*o*" y luego la tecla "*control*" + la tecla con la letra "*x*".

Ejecuta los siguientes comandos para publicar tus cambios en la internet:

    git add .
    git commit -m "changed baseURL"
    git push -u origin master

Ingresa tus credenciales de github si son solicitadas.

Regresa a la consola de Amplify en tu navegador web. Espera que el indicador de progreso esté en "*Verify*". Luego, presiona el enlace al final de la sección "Frontend Environments", uno parecido a este:

    https://master.xxxxxxxx.amplifyapp.com/

**:clap: :clap: Ya tienes tu propio Blog en la internet :clap: :clap:**
