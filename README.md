**Notas del curso de Git y Github de Platzi (README aun en construcción)**

[TOC]

Introducción
-------------
Curso tomado en [Platzi](https://platzi.com/clases/git-github/), aqui se expone una serie de notas personales tomadas del curso. La idea del README es ayudar a recordar una serie de temas importantes y ayudar a comprender el uso e importancia de dominar Git y Github.

Configuración inicial
-------------
| Comando en consola | Descripción del comando                    |
| ------------- | ------------------------------ |
| `$ git config`						| Se encuentran todas las configuracion de git | 
| `$ git config --list`					| Configuracion por defecto de git | 
| `$ git config --list --show-origin`	| Se muestra la ubicacion de los archivos de la configuracion | 
| `$ git config --global user.name "Nombre del Usuario"`| Se cambia la configuracion del usuario de git | 
| `$ git config --global user.email "correo@usuario.com"`| Se cambia la configuracion del correo de git | 

Comandos generales de git
-------------
| Comando en consola | Descripción del comando                    |
| ------------- | ------------------------------ |
|`$ git init` 							| Creacion de un repositorio |
|`$ git status`						| Estado del proyecto o archivos del repositorio |
|`$ git add nombreArhivo.txt`			| Agregar un archivo al staging del repositorio |
|`$ git rm --cached nombreArhivo.txt `	| Se quita el archivo del repositorio |
|`$ git add .`							| Agrega todos los archivos al repositorio |
|`$ git commit -m "Mensaje anclado al commit o cambios del proyecto"`| Con esto se agrea un mensaje al momento de guardar los cambios en el proyecto |
| `$ git log nombreArhivo.txt`			| Ver los commit registrados en el archivo.| 
| `$ git show nombreArhivo.txt`			| Se muestran los commit y los cambios en las diversas lineas del archivo. | 
| `$ git diff agregarIdCommit agregarOtroIdCommit` | Se agregan los id commit que se quiere comparar que cambios se han sufrido entre ambos | 
| `$ git reset agregarIdCommit --hard`	| Todo regresa al estado anterior, todo vuelve al commit que se le ha pasado | 
| `$ git reset agregarIdCommit --soft`	| Se regresa todo en el directorio de trabajo, pero lo que esta en Staging aun se conserva | 
| `$ git checkout agregarIdCommit nombreArhivo.txt` | Cambio del archivo a una version especifica con el commit, si se realiza un commit se guardarian estos cambios | 
| `$ git checkout master nombreArhivo.txt` | Regresa a la version mas actual del master | 
| `$ git rm --cached`					| Elimina los archivos del area de Staging y del proximo commit pero los mantiene en directorio de trabajo
| `$ git rm --force`					| Elimina los archivos del area de Staging y del directorio de trabajo | 
| `$ git reset --hard`					| Borra todo. Toda la informacion de los commits y del area de Staging se borra del historial | 
| `$ git reset --soft`					| Borramos todo el historial y los registros de Git pero se guardan los cambios que se tengan en Staging | 
| `$ git reset HEAD`					| Saca archivos del area de Staging, solo para que los ultimos cambios de estos archivos no se envien al ultimo commit. | 
| `$ git commit -am`					| Se realiza el commit y el add en una sola linea de comando | 
| `$ git log --all --graph --decorate --oneline` | De manera visual crea un esquema resumido de todos los cambios que se han dado en el repositorio | 
| `$ alias esquema="git log --all --graph --decorate --oneline"` | De esta manera se puede crear un alias para poder ejecutar el comando largo anterior | 

Estados de los archivos en Git
-------------
| Directorio de trabajo | Staging | Repositorio                    |
| ------------- | --------------|---------------- |
| nombreArhivo.txt | `$ git add nombreArhivo.txt` | `$ git commit -m "mensaje"` | 
| Estado: Untracked	| Estado: tracked | Estado: agregado por defecto a master | 

Tags
-------------
| Comando en consola | Descripción del comando                    |
| ------------- | ------------------------------ |
| `$ git tag -a v0.0.1 -m "Mensaje sobre el tag que se ha creado"` | Creacion de nuevo tag | 
| `$ git tag`							| Mostrar los tag existentes en el proyecto | 
| `$ git tag -d nombreDelTag`			| Elimina un tag especifico del servidor local | 
| `$ git push origin :refs/tags/nombreDelTag` | Elimina un tag especifico del servidor remoto | 

Ramas
-------------
| Comando en consola | Descripción del comando                    |
| ------------- | ------------------------------ |
| `$ git branch`						| Muestra las ramas que existen | 
| `$ git show-branch --all`				| Muestra un historial y todas ramas existentes en el proyecto | 
| `$ git branch nombreRama`				| Creacion de una nueva rama | 
| `$ git checkout nombreRama`			| Se cambia de rama de trabajo en git | 
| `$ git merge nombreRama`				| Se hace la fusion de la rama en la que se esta con la rama a la que se llama en el merge | 
| `$ git push origin nombreRama`		| Subir al repositorio remoto una rama | 
| `$ git pull origin nombreRama`		| Se descarga la rama del repositorio remoto | 
| fix-typo							| Nombre a una rama que se utilizaria para realizar cambios de ortografia al contenido del proyecto | 

Para trabajar con varios colaboradores en un proyecto:
> respositorio (remoto) > Settings > Manage access > Invite a collaborator > utilizar username, full name or email


Configuración de llave SSH en local
-------------
| Comando en consola | Descripción del comando                    |
| ------------- | ------------------------------ |
| `$ ssh-keygen -t rsa -b 4096 -C "corre@repositorioGithub.com"` | Creacion de la llave SSH, agregar el correo del repositorio al que se realizara la conexion | 
| `$ eval $(ssh-agent -s)`				| Verificacion que el servidor de SSH esta corriendo | 
| `$ ssh-add ~/.ssh/id_rsa`				| Agregar la llave SSH al servidor local, se ahreha la llave privada
| `$ git remote -v`						| Ver las url del repositorio remoto | 
| `$ git remote set-url origin urlSSHdeGithub` | Aqui se copia la url que se proporciona en el repositorio remoto en Github | 
| `/home/usernamePC/.ssh/id_rsa`			| Your identification has been saved | 
| `/home/usernamePC/.ssh/id_rsa.pub`		| Your public key has been saved | 
	
Repositorio remoto
-------------
| Comando en consola | Descripción del comando                    |
| ------------- | ------------------------------ |
| `$ git clone url`						| Realiza una copia al directorio de trabajo y repositorio local (todo el historico del proyecto almancenado)
| `$ git fetch`							| Actualiza el repositorio local del repositorio remoto
| `$ git pull origin main`				| Actualiza el repositorio local y el directorio de trabajo del repositorio remoto
| `$ git remote add origin urlGitHub`	| Agregar el repositorio de GitHub 
| `$ git push origin master:main`		| Subir los cambios al repositorio remoto, master:main se agrega por el cambio de nombre a la rama master a main en Github
| `$ git pull origin main --allow-unrelated-histories` | Se hace una fusion de la rama main del repositorio remoto al repositorio local master, con el ultimo parametro obliga a git a fusionar las historias de ambos repositorios
| `$ git remote add upstream urlRepositorioRemoto` | Una nueva rama o repositorio remoto para actualizar el repositorio local

Una buena practica antes de subir cambios es realizar un `$ git pull origin main` y luego el `$ git push origin master:main` por si se dieron cambios

Ignorar archivos
-------------
- Clase en curso

Recomendaciones 
-------------
- La rama master o main normalmente esta bloqueada (rama que se subira al servidor de produccion)
- La rama de testing se le conoce como Staging Develop (rama que se subira al servidor de pruebas)
- DevOps (administrador del entorno de desarrollo)