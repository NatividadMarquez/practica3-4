Natividad Márquez Baena

# Práctica 3.4: Despliegue de una aplicación una aplicación React en Netlify (PaaS)

1.Introducción
2.Creación de nuestra aplicación
3.Aplicación para Netlify
4.Proceso de despliegue en Netlify
5.Despliegue mediante CLI
6.Despliegue mediante conexión con Github

## Introducción

En esta práctica se tiene como objetivo desplegar una aplicación React en Netlify, una plataforma Platform as a Service (PaaS), utilizando un repositorio de GitHub como fuente. Esto simula el proceso real de pasar una aplicación del entorno local de desarrollo a producción. El despliegue se realizará de dos formas: mediante el CLI de Netlify y con un repositorio enlazado desde GitHub.

## Creación de nuestra aplicación

Como primer paso, nos logeamos en la máquina principal emplenado la dirección IP de la virtual, con SSH.

![alt text](image.png)

A continuacion se creará un directorio para albergar la aplicación con el nombre que elijamos. En ese directorio, crearemos los 3 archivos: `head.html`,`tail.html`,`aplicación.js` que conformarán una sencilla aplicación de ejemplo con la que vamos a trabajar. A continuación se presenta su contenido.

![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)

A continuación se inicializa un proyecto y se creará el archivo `package.json`. En el proceso tendremos que aportar ciertos datos:

![alt text](image-4.png)

Para ejecutar la aplicación se usará el comando `node aplicacion.js`.

Una vez hecho esto, se comprueba que la aplicación funciona correctamente visitando desde la máquina anfitriona `http://IP-maq-virtual:8080`. Si funciona debería dar el siguiente resultado:

![alt text](image-5.png)
![alt text](image-6.png)

## Aplicación para Netlify

Primeramente, pare desplegar la aplicación en Netlify, es necesarios clonar el repositorio que nos han porporcionado para la práctica.

![alt text](image-7.png)

## Proceso de Despliegue en Netlify

El despliegue de la apliación se realizá de dos maneras diferentes. Una es un despliegue manual desde el CLI de Netlify, es decir, desde el terminal, a partir de un directorio local de nuestra máquina Otra es un despliegue desde un código publicado en uno de nuestros repositorios de Github.

Previamente se ha accedido a la web de Netlify,un proveedor de alojamiento en la nube enfocado en sitios estáticos. Es preciso logearse para crear una cuenta. 
Para el despliegue en Netlify, primero es necesario acceder a la página y generar un token que usaremos en el despliegue.

![alt text](image-8.png)

Una vez registrados, debemos instalar el CLI de Netlify para ejecutar sus comandos desde el terminal, es decir, con `netlify-cli` estamos instalando un paquete  CLI oficial de Netlify, una herramienta que permite interactuar con Netlify directamente desde la terminal, ya que carece de entorno gráfico.

![alt text](image-9.png)

Netlify nos solicitará una autenticación, a continuación solicitará el login:

![alt text](image-10.png)

Se muestra una pantalla del navegador para que concedamos la autorización pertinente:

![alt text](image-11.png)

![alt text](image-12.png)

Indicamos el token con `NETLIFY_AUTH_TOKEN`(establecemos como variable de ambiente)

![alt text](image-13.png)

Ahora se instala npm en la aplicación:

![alt text](image-14.png)

Cuando ya las tengamos instaladas podemos proceder a realizar el build:

![alt text](image-15.png)

Se creará una nueva carpeta llamada build que contendrá la aplicación que debemos desplegar. 

Se responderán unas preguntas donde se configurará un nuevo sitio. El Team se dejará por defecto. Además se escoge un nombre para el sitio y el directorio de despliegue será `./build`.
![alt text](image-16.png)

![alt text](image-17.png)

Visitando el sitio web que nos indica el enlace, comprobamos que la aplicación se ha desplegado correctamente.

![alt text](image-18.png)

## Despliegue Mediante Conexión con Github

Para desplegar la aplicación desde Github, se elimina el site que hemos desplegado antes en Netlif, evitando así posibles conflictos:

![alt text](image-19.png)

Además se deberá borrar el directorio donde se halla el repositorio clonado anteriormente:

![alt text](image-20.png)

Nos descargaremos las fuentes en formato `.zip`

![alt text](image-21.png)

 Posteriormente creamos una carpeta nueva y descomprimimos dentro el zip que hemos descargado:

 ![alt text](image-22.png)

Entraremos en la carpeta creada, inicializaremos un repositorio previamente creado, llamado `practicaTresCuatro` y subiremos el contenido del zip, es decir, la aplicación a desplegar.

 ![alt text](image-23.png)

Una vez subido el código a GitHub, se debe enlazar nuestra cuenta de Github con la de Netlify para que éste último pueda tomar el código, hacer el build y desplegarlo. Así pues, entramos en nuestro dashboard de Netlify y le damos a importar proyecto existente de git:

![alt text](image-24.png)
![alt text](image-25.png)

Accedemos al enlace:

![alt text](image-26.png)

Comprobamos que evidentemente, la aplicación se despliega:

![alt text](image-27.png)

Tras esto, se podría suponer que cualquier cambio que hagamos en el proyecto y del que hagamos commit y push en Github, automáticamente genere un nuevo despliegue en Netlify.

Para comprobar que esto ocurrirá correctamente, se accede a la carpeta public encontramos el archivo `robots.txt` ( indica a los rastreadores de los buscadores a qué URLs del sitio pueden acceder). 
Se modificará el archivo para determinar a que URLs de sitios web se puede acceder:

![alt text](image-28.png)

Se debería realizar un commit y un push para comprobar que efecticamente, los cambios se pueden subir.

![alt text](image-29.png)

![alt text](image-30.png)

De esta manera, y para finalizar, si se accede a la dirección `https://sitio-natividad.netlify.app/robots.txt`, se podrá visualizar el archivo modificado.

![alt text](image-32.png)




