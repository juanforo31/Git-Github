# GIT & GITHUB

## QUE ES GIT?
---
Git es un control de versiones de archivos de texto plano, el cual ayuda a controlar las modificaciones y adiciones que se le puedan hacer a un mismo archivo, esto permite mantener un mejor orden y además de este, ayuda a que varias personas puedan trabajar en un mismo proyecto.

## CÓMO CONFIGURAR MI NOMBRE Y EMAIL EN GIT
---
Esta configuración es muy importante ya que no se hace desde un comienzo es muy posible que no deje realizar envíos del directorio al repositorio local, para realizar estas modificaciones es necesario usar estos comandos.

~~~
## Este configurará el nombre en git
$ git config --global user.name "name"

## Este configurará el email en git
$ git config --global user.email "email"
~~~
## CÓMO INICIAR UN REPOSITORIO LOCAL
---
  Para iniciar un repositorio en git es necesario posicionarse en la carpeta del proyecto en la sección de comandos, esta puede ser desde la misma consola de comandos que instala git, llamada **git bash**, o también desde la consola del ordenador, siempre y cuando se haya realizado la configuración previa para este. Luego de estar en la carpeta se llamará el comando ***git init*** el cual iniciará el repositorio local, este añadirá una carpeta oculta llamada **/.git** .

~~~
$ cd E:\juanDavid\ESTUDIO PROPIO\GIT & GITHUB\Proyecto 1

$ git init
~~~

Al iniciar el repositorio local, este creara dos espacios, el primero de ellos será el ***STAGING*** el cual será el espacio en memoria RAM donde se añadirán los cambio antes de ser subidos al repositorio local, y el segundo es el repositorio en donde se guardara la información de cada una de las adiciones o modificaciones que se le haya realizado a cada uno de los archivos, también añadiendo el nombre, la fecha, el email, y un mensaje de quien realizo esto cambios.

## CÓMO ADICIONAR CAMBIOS AL REPOSITORIO LOCAL DESDE UNA MISMA RAMA
---
Para este existen dos opciones de añadir los cambios realizados en el directorio:

1. El primero es de una manera segura pero larga, primero que todo es necesario saber que archivos fueron modificados, y esto lo sabremos con el comando ***git status***, además de decirnos que archivos fueron modificados no dirá si estos cambios ya fueron añadidos a el espacio de ***STAGING***.

~~~
$ git status
~~~

2. Luego de conocer los archivos modificados los añadiremos con el comando ***git add name_file.txt*** en caso de querer añadir archivo por archivo, pero en caso de querer añadir todos al mismo tiempo se utiliza el comando ***git add .***, estos comandos harán que los cambios pasen del directorio a el área de ***STAGING***.

~~~
## Este comando es para añadir un archivo en especifico
$ git add name_file.txt

## Este comando sirve para añadir todos los archivs modificados al mismo tiempo
$ git add .
~~~

* En caso de que se desee eliminar un archivo que se haya añadido con el ***git add*** se puede utilizar el comando ***git -rm --cached name_file.txt***, esta acción lo sacaría de ***STAGING*** y no será añadido al repositorio local.

~~~
$ git -rm --cached name_file.txt
~~~

3. Después de añadir los cambios al área de ***STAGING*** es necesario llevar esos cambios al repositorio local, este se realiza con el comando ***git commit -m "message"***, este comando añade los cambios con un mensaje y la información de la persona que lo realizó.

~~~
$ git commit -m "message"
~~~

En este punto los cambios ya se encontrarían en el repositorio local, pero aún existe una forma de subir los cambios al repositorio de una manera más rápida, este se realiza usando el comando ***git commit -am "message"*** el cual fusiona el comando ***git add .*** con el comando ***git commit -m "message"***, de esta manera se subirían los cambios de una manera más rápida.

~~~
$ git commit -am "message"
~~~

## CÓMO CONCER EL HISTORIAL DE UN ARCHIVO Y LAS MODIFICACIONES QUE SE LE HAN REALIZADO?
---
* Para este caso podemos encontrar dos tipos de comandos que nos regala git para poder ver los registros de un archivo el primero de estos es el ***git show*** una comparación ente el ultimo commit con el anterior a este, este nos regala información importante con tal de conocer los cambios que se le realizaron a un archivo en casos de tener errores u otros inconvenientes.

~~~
$ git show
~~~

También si se desea ver la comparación de un archivo en particular es tan sencillo como usar ***git show name_file.txt*** y así se compararán los últimos commit en donde se haya modificado el archivo especifico seleccionado.

~~~
$ git show name_file.txt
~~~

* En caso de solo querer ver la información general se puede utilizar el comando ***git log*** el cual mostrara todos los commit que se hayan realizado en rama ubicada, en este se mostrara el id de cada uno de los commit, el mensaje anexado, el nombre de la persona que lo realizo y el email.

~~~
$ git log name_file.txt
~~~

* Por último si se desea comparar dos archivos que se encuentren en dos versiones distintas se puede realizar el comando ***git diff idCommitA idCommitB*** y así se podría visualizar los cambios que se realizaron entre los dos archivos.

~~~
$ git diff idCommitA idCommitB
~~~

## CÓMO VIAJAR ENTRE LAS VERSIONES O EN EL TIEMPO
---
A veces en nuestros proyectos nosotros podemos subir unos cambios los cuales rompan algunos archivos que ya existían en la versión anterior, gracias a **git** podemos volver en el tiempo con tal irnos a versiones anteriores y eliminar los cambios realizados o también nos permite volver a una versión en específico para ver su contenido y luego volver al trabajo actual para poder solucionar los inconvenientes, para lograr hacer este se usarán los comandos ***git checkout IdCommit name_file.txt***, este nos permitirá ver de qué manera era la versión de ese archivo en ese commit para analizar en donde pudieron estar los errores cometidos, y luego de esto es posible regresar a la versión actual usando el comando ***git checkout rama_principal***, pero en caso de que deseáramos volver sin necesidad de regresar a la versión futura se podría manejar el comando ***git reset IdCommit --hard***, de esta manera la versión actual (**HEAD**) será el commit al que se le haya colocado en el comando.

~~~
## Volver al pasado con posibilidad de regresar al futuro
$ git checkout IdCommit name_file.txt
## Volver a la version actual en la que se habia dejado
$ git checkout rama_principal

## Volver al pasado sin posibilidad de volver al futuro
$ git reset IdCommit --hard
~~~

## CÓMO SE MANEJAN LAS RAMAS EN GIT
---
Al iniciar un repositorio local se inicia la rama **(master)** la cual será la rama principal del proyecto, en casos de un proyecto grande casi siempre la rama master es la que manejara el código funcional y sin fallos para ser visto por los clientes. En estos mismos se crean gran cantidad de ramas con tal de llevar un orden de organización para las personas que se involucran en el proyecto, en la mayoría de los proyectos esta rama es llamada **develop**. y por último en la mayoría de los proyectos se mande una rama llamada **hotfix** que es en donde se controlarían y se arreglarían todos los bugs que llegara a tener el proyecto.

Con las ramas se pueden realizar gran variedad de cosas, como renombrarlas, eliminarlas, fusionar unas ramas con otras y muchas cosas más.

### CÓMO RENOMBRAR UNA RAMA EN EL REPOSITORIO LOCAL
---
Para renombrar una rama es tan sencillo como utilizar el comando ***git branch -m newname***, este puede ser utilizado en su mayoría para no tener problemas con las conexiones con *GitHub* ya que en ciertas ocasiones *git* y *github* nos piden tener como rama principal el mismo nombre.

~~~
$ git branch -m newname
~~~

### CÓMO CREAR UNA RAMA NUEVA EN UN REPOSITORIO LOCAL
---

Para crear una rama nueva rama en el repositorio local es tan simple como escribir el comando ***git branch name_branch***, de esta manera se creará una nueva rama con el nombre establecido, y para cambia a esta rama es necesario utilizar el comando ***git checkout name_branch***, esta nueva rama hará una copia de los archivos que existan de la última versión de la rama en la que se está ubicado.

~~~
## Para crear una rama 
$ branch name_branch

## Para cambiar a la rama creada 
$ git checkout name_branch
~~~

TIP: En caso de recordar el nombre de la rama a la que se desea ir, puede usar el comando ***git branch --list***, este comando mostrará todas las ramas que se encuentran en el repositorio local, además de en cual se encuentra en ese momento.

~~~
$ git branch --list
~~~

### CÓMO FUSIONAR DOS RAMAS
---
Para fusionar ramas toca dejar claro primero una cosa, las dos ramas deben tener los últimos commit actualizados ya que no quisiéramos fusionarlos con una versión que no es, desde de tener esto en cuenta es necesario estar en la rama a la cual se le aplicaran los cambios y luego escribir el siguiente comando ***git merge nombre_ramaAfusionar***, de esta manera se creara una nueva versión en la rama en la cual se encuentra actualmente como si fuera un commit solo que en este caso se fusiona la rama en la que se está ubicado con la rama que se añadió en el comando.

~~~
$ git merge git merge nombre_ramaAfusionar
~~~

En algunos casos al correr este comando pueden ocurrir ciertos conflictos, uno de estos se da porque en las dos ramas se modificaron los mismos espacios de código, para solucionar este conflicto **Visual Studio Code** nos permite ver en qué líneas de código ocurrieron los conflictos, acá sería necesario la comunicación para saber que pedazos de código se necesitan dejar y cuales no se dejarían, o en otro caso se organizaría el archivo para que los dos pedazos de código se encuentren en el mismo archivo. luego de esto será necesario añadir los cambios y realizar el commit, al igual que se explicó en el apartado ***CÓMO ADICIONAR CAMBIOS AL REPOSITORIO LOCAL DESDE UNA MISMA RAMA***.

## QUÉ ES GITHUB?
---
GitHub al igual que git es un control de versiones, la pequeña diferencia con esté es que permite guardar la información en un repositorio remoto, y así mismo permite que varias personas puedan hacer cambios y pueda ser más ágil el trabajo.

## CÓMO ME PUEDO TRAER LA INFORMACIÓN O SUBIR CAMBIOS AL REPOSITORIO REMOTO
---

Para subir la información a nuestro repositorio remoto primero que todo es necesario decirle a git que vamos a añadir un origen remoto de nuestros archivos, para hacer esto utilizamos en comando ***git remote add origin UrlREpositorio***.

~~~
$ git remote add origin UrlREpositorio
~~~

Luego de haber añadido el origen remoto de nuestros archivos se deben traer los cambios que tenga el repositorio remoto, ya que en algunas ocasiones el repositorio remoto puede traer algunos archivos como el archivo README.md. Para traernos estos cambios se utiliza el comando ***git pull origin RamaPrincipal***

~~~
$ git pull origin RamaPrincipal
~~~

TIPS: 
1. Actualmente GitHub usa como rama principal (**main**), entonces es necesario para estos casos que la rama principal del repositorio remoto y el repositorio local tengan el mismo nombre así no tendrían inconvenientes por las ramas, para cambiar el nombre de la rama en el repositorio local se puede ir al apartado de ***CÓMO RENOMBRAR UNA RAMA EN EL REPOSITORIO LOCAL***, pero en caso de quererla cambiar en GitHub es necesario ir al apartado de ajustes en donde uno puede personalizar el nombre por defecto de la rama principal.

2. En caso de que el comando anterior mencionando que se rehúsa a fusionar historias no relacionadas se puede usar el comando ***git pull origin RamaPrincipal --allow-unrelated-histories***, de esta manera forzaríamos a que git acepte los archivos que estamos trayendo de GitHub.

~~~
$ git pull origin RamaPrincipal --allow-unrelated-histories
~~~

Luego de haber traído la información de nuestro repositorio remoto a nuestro local, ya podríamos añadir todos los archivos que tenemos en el repositorio remoto, para realizar esta acción utilizamos el comando ***git push origin RamaPrincipal***.

~~~
$ git push origin RamaPrincipal
~~~