En esta segunda parte del laboratorio, comenzarás a usar Inteligencia Artificial, como la usan grandes empresas y startups alrededor de todo el mundo.

¿Sabías que los computadores ya son capaces de "ver"? La inteligencia artificial busca dotar a las máquinas de capacidades que consideramos "inteligentes", con lo cual pueden hacer cosas como escuchar, leer textos e incluso identificar objetos y personas como vas a verlo en este laboratorio.
|  |  |
|--|--|
| ![Rekognition Icon](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/rekognitionIcon.png) | **Amazon Rekognition**: Es un servicio que permite reconocer objetos, personas, textos, escenas y actividades dentro de imágenes o videos |
|  |  |
---

**Este workshop es una continuación del despliegue de tu propio blog con hugo y amplify que puedes encontrar [acá](https://github.com/hernangarcia/how-to-hugo-aws-amplify/).**

## **Crea una página web**

Dentro de tu entorno de *Cloud9* existente vamos a crear una nueva página donde pondremos el código para reconocer rostros.

Dentro del proyecto existente da clic en la carpeta *static* y allí selecciona *New File*

![New File](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/cloud9NewFile.png)

Digita como nombre de archivo *"rekognition-hoc.html"* (sin las comillas). Este archivo html contendrá el código fuente para nuestro proyecto.

![New File Name](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/newFileName.png)

Una vez creado el archivo da doble-clic sobre este para editarlo, y en la nueva ventana que se abre, copia y pega el código contenido en el archivo [rekognition-hoc.html](https://github.com/duvierZ/howto-rekognition-hoc2020/blob/master/src/rekognition-hoc.html).

Luego de copiar el código, graba tus cambios.

![Save File](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/saveFile.png)

## **Un vistazo al código**

El archivo que acabas de crear es una página web en html, que contiene código JavaScript que se comunica con el servicio *Amazon Rekognition* para realizar la detección de caras en una imagen y detectar características de estos rostros, como edad aproximada, si usa o no lentes, o incluso si hay barbas :).

Dale una mirada al código, en particular acá tenemos algunas secciones importantes, específicamente relacionadas a como integramos las capacidades de inteligencia artificial en nuestras aplicaciones.

Para conectarnos de forma segura a los servicios de AWS se deben usar credenciales, pero no es buena idea dejarlas embebidas en el código, por lo cual solicitaremos al usuario que las ingrese en nuestra página a través de un formulario (*En este caso usaremos el Access Key y Secret Access Key. Si estás en un evento de AWS puedes encontrar tus credenciales en el enlace facilitado [acá](https://dashboard.eventengine.run/)*.

![Code AccessKeys](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/codeAccessKeys.png)

Luego prestemos atención al código que inicia en la línea 54. Acá establecemos las credenciales de conexión a **AWS** e invocamos al servicio *Amazon Rekognition*, para que nos ayude a detectar rostros dentro de la imagen con el método *detectFaces*.

![Code DetectFaces](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/codeRekognitionCall.png)

Una vez detectados los rostros, procesamos también las características que la Inteligencia Artificial detectó en esos rostros, tales como edad aproximada o el estado de ánimo probable. Este procesamiento lo puedes ver a partir de la línea 91

![Code ProcessFeatures](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/codeRekognitionFeatures.png)

Una vez termines de revisar el código, vamos a desplegarlo y verlo en acción.

## **Prueba en Cloud9 con HUGO**

Al haber creado el archivo dentro de la carpeta *static*, Hugo mostrará el html al usuario. Si ya tenías corriendo previamente el servidor de Hugo este deberá tomar automáticamente el cambio (puedes revisar la ventana de terminal). Si no tienes tu servidor de Hugo corriendo, lo puedes iniciar, recuerda usar el baseURL correcto de acuerdo a tu entorno de Cloud9

	hugo server -p 8080 --bind=0.0.0.0 --baseURL=https://xxxxxxxxx.vfs.cloud9.us-east-1.amazonaws.com

![Hugo Server Running](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/runHugoServer.png)

Con esto ya estamos listos para probar nuestro reconocedor de rostros. Ve al menú *Preview* y da clic en *Preview Running Application*

![Preview running App](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/previewRunningApp.png)

Se te desplegará la ventana de tu blog, que creaste en el anterior laboratorio. Para ver tu nueva página web, ve a la barra de dirección url y al final anexa el texto *"/rekognition-hoc.html"* (sin las comillas) y presiona *Enter*

![Fix URL](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/previewRunningUrl.png)

Se desplegará una página web, en la cual puedes ingresar las credenciales de AWS que tienes y donde puedes cargar una foto que contenga rostros

![App Running](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/appMainPage.png)

Cuando cargues la imagen vas a obtener los resultados que encontró *Amazon Rekognition*. Puedes probar a subir tus propias fotos y combinaciones (bigotes, gafas, barba, etc)

![Rekognition Results](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/rekognitionResults.png)

**Nota:** Puedes acceder también a la aplicación desde el navegador de tu celular y tomarte una foto allí :)

## **Despliegue en Amplify**

Finalmente ya que tenemos nuestra aplicación lista, vamos a enviar nuestros cambios al repositorio de *GitHub* para que *AWS Amplify* la deje lista en Internet.

Vamos a editar la configuración de *AWS Amplify* para que use la misma versión de Hugo que usamos en nuestro entorno *Cloud9*. Para esto vamos a hacer clic en la consola, en el menú de la izquierda llamado *App Settings*, seleccionamos *Build Settings*

![Build Settings Menu](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/amplifyBuildSettingsMenu.png)

Esto despliega a la derecha una ventana con los comandos usados para configurar nuestro sitio web. En esa ventana a la derecha seleccionamos el botón *Edit*

![Build Settings Edit](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/amplifyBuildSettingsEdit.png)

Y remplazamos el texto existente por el contenido del archivo [amplify.yml](https://github.com/duvierZ/howto-rekognition-hoc2020/blob/master/src/amplify.yml) y después damos clic al botón *Save*.

![Build Settings Save](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/amplifyBuildSettingsSave.png)

Una vez que está listo nuestro entorno, vamos a añadir nuestros cambios (si tus carpetas tienen otro nombre recuerda cambiarlo en el comando)

	cd ~/environment/myblog 

Anexamos nuestros cambios al repositorio

	git add .
	git commit -m "Rekognition page added"
	git push -u origin master

En uno o dos minutos el servicio *Amplify* detectará los cambios e iniciará el proceso de despliegue, puedes fijarte en el avance en la ventana

![Amplify Building](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/amplifyBuilding.png)

Espera unos minutos hasta que el proceso haya terminado y el indicador de *Verify* se encuentre en verde

![Amplify Verify](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/amplifyVerify.png)

Listo, ya tu aplicación está desplegada. Puedes accederla desde el navegador haciendo clic en tu url (la puedes encontrar debajo de la sección master)

![Amplify Mater URL](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/amplifyMasterURL.png)

algo similar a

	https://master.xxxxxxxx.amplifyapp.com/

y agregando al final de la url el nombre de tu página HTML

	/rekognition-hoc.html

![AmplifyRekognitionURL](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/amplifyRekognitionURL.png)

**:clap: :clap: Ya tienes tu aplicación de reconocimiento de rostros en internet :clap: :clap:**

## Solución de Problemas

Si tu página de reconocimiento no carga y por el contrario te sigue llevando a tu blog original, puedes intentar dos cosas

1. Limpia el caché de tu navegador. Es posible que por algún motivo tu navegador no esté tomando los cambios, entonces limpia el historial del día y el caché de páginas

2. En la consola de *Amplify* selecciona en el menú de la izquierda *Rewrites and Redirects* y en la ventana que se despliega a la derecha selecciona el botón *Edit* y elimina las reglas que allí encuentras

![AmplifyRedirects](https://raw.githubusercontent.com/duvierZ/howto-rekognition-hoc2020/master/images/amplifyRedirects.png)
