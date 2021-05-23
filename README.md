Notas del curso de Git y Github de Platzi
=====================

Introducción
-------------
Curso tomado en [Platzi](https://platzi.com/clases/git-github/), aqui se expone una serie de notas personales tomadas del curso. La idea del README es ayudar a recordar una serie de temas importantes y comprender el uso e importancia de dominar Git y Github.

Configuración inicial
-------------
| Comando en consola                                        | Descripción del comando                   |
| --------------------------------------------------------- | ------------------------------            | 
| `$ git config --list`					                    | Configuración por defecto de git en local | 
| `$ git config --list --show-origin`	                    | Ubicación de los archivos                 | 
| `$ git config --global user.name "Nombre del Usuario"`    | Agregar o editar el usuario               | 
| `$ git config --global user.email "correo@usuario.com"`   | Agregar o editar el correo del usuario    | 


Comandos generales de git
-------------
| Comando en consola                                        | Descripción del comando                    |
| --------------------------------------------------------- | ------------------------------------------ |
| `$ git init` 							                    | Creación de un repositorio |
| `$ git status`						                    | Estado del proyecto del repositorio |
| `$ git add nombreArhivo.txt`			                    | Agregar un archivo al staging del repositorio |
| `$ git rm --cached nombreArhivo.txt `	                    | Quitar el archivo del repositorio |
| `$ git add .`							                    | Agregar todos los archivos al repositorio |
| `$ git commit -m "Mensaje de los cambios en el proyecto"` | Guardar los cambios del proyecto agregando un mensaje |
| `$ git log nombreArhivo.txt`			                    | Ver los commit registrados en el archivo.| 
| `$ git show nombreArhivo.txt`			                    | Muestra los commit y los cambios en las diversas líneas del archivo. | 
| `$ git diff agregarIdCommit agregarOtroIdCommit`          | Al agregar los id commit, se muestra los cambios que se han realizado | 
| `$ git reset agregarIdCommit --hard`	                    | Todo regresa al estado del commit seleccionado | 
| `$ git reset agregarIdCommit --soft`	                    | Todo regresa al estado del commit seleccionado en el directorio de trabajo, pero lo que esta en Staging aún se conserva | 
| `$ git checkout agregarIdCommit nombreArhivo.txt`         | Cambio del archivo a una versión específica con el commit, si se realiza un commit se guardarian estos cambios | 
| `$ git checkout master nombreArhivo.txt`                  | Regresa a la versión mas actual del master | 
| `$ git rm --cached`					                    | Elimina los archivos del área de Staging y del próximo commit pero los mantiene en directorio de trabajo
| `$ git rm --force`					                    | Elimina los archivos del área de Staging y del directorio de trabajo | 
| `$ git reset --hard`					                    | Elimina toda la información de los commits y del área de Staging se borra del historial | 
| `$ git reset --soft`					                    | Elimina todo el historial y los registros de Git pero se guardan los cambios que se tengan en Staging | 
| `$ git reset HEAD`					                    | Elimina los cambios del área de Staging, evitando enviarlos al commit | 
| `$ git commit -am "Mensaje de los cambios"`			    | Se realiza el commit y el add en una sola linea de comando | 
| `$ git log --all --graph --decorate --oneline`            | De manera visual crea un esquema resumido de todos los cambios que se han dado en el repositorio | 
| `$ alias nombreAlias="git log --all --graph --decorate --oneline"` | De esta manera se puede crear un alias para poder ejecutar el comando largo anterior | 

Estados de los archivos en Git
-------------
| Estado: Untracked     | Estado: tracked               | Estado: agregado por defecto a master                    |
| -------------         | --------------                |---------------- |
| nombreArhivo.txt      | `$ git add nombreArhivo.txt`  | `$ git commit -m "mensaje"` | 
| Directorio de trabajo	| Staging                       | Repositorio | 

Tags
-------------
| Comando en consola                                        | Descripción del comando                    |
| -------------                                             | ------------------------------ |
| `$ git tag -a v0.0.1 -m "Mensaje sobre el tag que se ha creado"` | Creación de nuevo tag | 
| `$ git tag`							                    | Mostrar los tag existentes en el proyecto | 
| `$ git tag -d nombreDelTag`			                    | Elimina un tag especifíco del servidor local | 
| `$ git push origin :refs/tags/nombreDelTag`               | Elimina un tag especifíco del servidor remoto | 

Ramas
-------------
| Comando en consola                                        | Descripción del comando                    |
| -------------                                             | ------------------------------ |
| `$ git branch`						                    | Muestra las ramas que existen | 
| `$ git show-branch --all`				                    | Muestra un historial y todas ramas existentes en el proyecto | 
| `$ git branch nombreRama`				                    | Creación de una nueva rama | 
| `$ git checkout nombreRama`			                    | Cambio de rama de trabajo en git | 
| `$ git merge nombreRama`				                    | Fusión de la rama seleccionada a la actual | 
| `$ git pull origin nombreRama`		                    | Se descarga o actuliza la rama seleccionada del repositorio remoto | 
| `$ git push origin nombreRama`		                    | Subir la rama seleccionada al repositorio remoto | 
| fix-typo							                        | Ejemplo de nombre a rama que se utilizara para cambios por ortografía al contenido del proyecto | 

Colaboradores en un proyecto:
-------------
- Ir al respositorio (remoto) 
- Seleccionar la pestaña de `Settings` del proyecto
- Seleccionar la sección de `Manage access` del menu lateral
- Dar click en el botón `Invite a collaborator` 
- Buscar por username, full name or email y seleccionar el usuario.
- Dar click al botón de `Add nombreUsuario to this repository`

Configuración de llave SSH en local
-------------
| Comando en consola                                        | Descripción del comando                    |
| -------------                                             | ------------------------------ |
| `$ ssh-keygen -t rsa -b 4096 -C "corre@repositorioGithub.com"` | Creación de la llave SSH, agregar el correo del repositorio al que se realizara la conexión | 
| `$ eval $(ssh-agent -s)`				                    | Verificación que el servidor de SSH esta corriendo | 
| `$ ssh-add ~/.ssh/id_rsa`				                    | Agregar la llave SSH al servidor local
| `$ git remote -v`						                    | Ver las url del repositorio remoto | 
| `$ git remote set-url origin urlSSHdeGithub`              | Editar la url del repositorio remoto | 
| `/home/usernamePC/.ssh/id_rsa`			                | Your identification has been saved | 
| `/home/usernamePC/.ssh/id_rsa.pub`		                | Your public key has been saved | 
	
Repositorio remoto
-------------
| Comando en consola                                        | Descripción del comando                    |
| -------------                                             | ------------------------------ |
| `$ git clone url`						                    | Realiza una copia del directorio de trabajo y repositorio local (todo el historico del proyecto almancenado)
| `$ git fetch`							                    | Actualiza el repositorio local del repositorio remoto
| `$ git pull origin main`				                    | Actualiza el repositorio local y el directorio de trabajo del repositorio remoto
| `$ git remote add origin urlGitHub`	                    | Agregar el repositorio de GitHub 
| `$ git push origin master:main`		                    | Subir los cambios al repositorio remoto (master:main se agrega por el cambio de nombre a la rama master a main en Github)
| `$ git pull origin main --allow-unrelated-histories`      | Fusion de la rama main del repositorio remoto al repositorio local master, con el ultimo parametro obliga a git a fusionar las historias de ambos repositorios
| `$ git remote add upstream urlRepositorioRemoto`          | Una nueva rama o repositorio remoto para actualizar el repositorio local

Una buena practica antes de subir cambios es realizar un `$ git pull origin main` para actualizar el repositorio local y luego el `$ git push origin master:main` para subir al repositorio remoto los nuevos cambios.

Ignorar archivos
-------------
- Clase en curso

Extras 
-------------
- La rama master o main normalmente esta bloqueada (rama que se subirá al servidor de producción)
- La rama de testing se le conoce como Staging Develop (rama que se subira al servidor de pruebas)
- DevOps (administrador del entorno de desarrollo)