
# Comandos de Git y GitHub


&nbsp;
## Contenido

-   [Instalación](#instalación)
-   [Comandos básicos terminal ](#comandos-básicos-terminal)
-   [Comandos básicos git ](#comandos-básicos-git)
-   [Configuración Git ](#configuración-git)
-   [Git remote (Para primera vez subiendo el proyecto)](#git-remote-para-primera-vez-subiendo-el-proyecto)
-   [Configuración de llaves SSH en Windows y Linux](#configuración-de-llaves-ssh-en-windows-y-linux)
-   [Repositorio remoto](#repositorio-remoto)
-   [Corregir último commit](#corregir-último-commit)
-   [Branches y checkout](#branches-y-checkout)
-   [Interfaz gráfica gitk](#interfaz-gráfica-gitk)
-   [Restore para sacar de staging y directorio de trabajo](#restore-para-sacar-de-staging-y-directorio-de-trabajo)
-   [Eliminar archivos con git rm](#eliminar-archivos-con-git-rm)
-   [Volver en el tiempo con git reset](#volver-en-el-tiempo-con-git-reset)
-   [Análisis de cambios](#análisis-de-cambios)
-   [Ver TODA la historia](#ver-toda-la-historia)
-   [Alias](#alias)
-   [Tags](#tags)
-   [Escribiendo la historia con rebase (MALA PRACTICA)](#escribiendo-la-historia-con-rebase-mala-practica)
-   [Memoria temporal con stash](#memoria-temporal-con-stash)
-   [Limpiar el working directory](#limpiar-el-working-directory)
-   [Traer commit antigüo como HEAD con cherry-pick (MALA PRACTICA)](#traer-commit-antigüo-como-head-con-cherry-pick-mala-practica)
-   [Buscando en archivos y commits de Git](#buscando-en-archivos-y-commits-de-git)
-   [Mas información](#mas-información)



## Instalación:
En el siguiente link puedes realizar la instalación de git: https://git-scm.com/downloads


&nbsp;


## Comandos básicos terminal

|  *Comando* |  *Descripción*  |
| :------------: | :------------: |
| *pwd*  | Muestra la ruta de carpetas en la que nos encontramos |
| *mkdir*  | Permite crear carpetas (Ejemplo: mkdir nombreCarpeta) |
| *touch* | Permite crear archivos (Ejemplo: touch file.txt) |
| *rm* | Permite borrar un archivo o carpeta (Ejemplo: rm archivo.txt). Cuidado con este comando |
| *cat* | Ver el contenido de un archivo (Ejemplo: cat fileName.txt) |
| *ls* | Permite ver los archivos de la carpeta donde estamos ahora mismo |
| *ls -la* | Muestra todos los archivos de la carpeta donde estamos ahora mismo incluyendo los ocultos como una lista |
| *cd* | Permite navegar entre carpetas. Por sí solo nos permite ir a la ruta de usuario |
| *cd carpeta/subcarpeta* | Navega a una ruta dentro de la carpeta donde estamos ahora mismo |
| *cd ..* | (cd + dos puntos) Vamos una carpeta hacia atrás  |
| *cd .* | (cd + un punto) Representa el directorio en el que nos encontramos ahora mismo |
| *history* | Vemos los últimos comandos que ejecutamos y un número especial con el que podemos repetir su ejecución |
| *!num* | Ejecutar algún comando donde num es un número que nos muestra el comando history |
| *clear* | Limpia la terminal. También podemos usar los atajos de teclado Ctrl + L o Command + L |


&nbsp;


## Comandos básicos git

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git init* | Inicializa un repositorio de GIT en la carpeta donde se ejecute el comando |
| *git add nameArchivo* | Añade los archivos especificados al área de preparación (staging) |
| *git add .* | Añade todos los archivos tracked al área de preparación (staging) |
| *git commit -m “commit description”* | Confirma los archivos que se encuentran en el área de preparación y los agrega al repositorio local |
| *git commit -am “commit description”* | Añade al staging area y hace un commit mediante un solo comando. (No funciona con archivos nuevos) |
| *git status* | Ofrece una descripción del estado de los archivos (untracked, ready to commit, nothing to commit) |


&nbsp;


## Configuración Git

| *Comando* | *Descripción* |
| :---: | :---: |
| *git config \--list* | Lista las configuraciones |
| *git config \--list \--show-origin* | Muestra donde están guardadas las configuraciones |
| *git config \--global user.email tuEmail* | Configura el email |
| *git config \--global user.name tuNombre* | Configura el nombre (Este será el que se verá en los commits) |
| *git config \--global \--replace-all user.name “nombre modificado”* | Modifica un atributo (en este caso el username) |

| *Modificar atributo eliminandolo y volviendolo a añadir* |
| :------------: |
| *git config --global --unset-all user.name* |
| *git config --global --add user.name “tu nombre”* |


&nbsp;


## Git remote Para primera vez subiendo el proyecto

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git remote add origin HTTPS/SSH* | Conectamos nuestro git repository al repositorio remoto (GitHub) con una url de HTTPS o SSH (SSH es más seguro y se debe hacer el procedimiento de la siguiente tabla) |
| *git pull origin main \--allow-unrelated-histories* | Traemos la version del repositorio remoto y hacemos merge para crear un commit con los archivos de ambas partes(local y remoto) |
| *git remote remove origin* | Elimina la conexión con el repositorio remoto |
| *git remote set-url origin newHTTPS/SSH* | Cambia la url del repositorio remoto origin |
| *git remote -v* | Lista las conexiones existentes |


&nbsp;


## Configuración de llaves SSH en Windows y Linux

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *ssh-keygen -t rsa -b 4096 -C "tuCorreo"* | Generamos una llave pública y privada para conectarnos de manera más segura y rápida a GitHub |
|  | Copiamos el contenido de la llave pública generada y esto lo pegamos en GitHub en Settings/SSH and GPG keys/New SSH key |
| *eval $(ssh-agent -s)* | Encendemos el servidor de llaves SSH de nuestra computadora |
| *ssh-add rutaDondeGuardasteTuLlavePrivada* | Añadimos la llave SSH al "servidor" (Ejemplo: ssh-add ~/.ssh/id_rsa) |


&nbsp;


## Repositorio remoto

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git clone HTTPS/SSH* | Clona el repositorio remoto (GitHub) de manera que podamos trabajar en nuestra máquina local. Para esto, debemos copiar la url HTTPS o SSH (esta última requiere que hayas hecho la conexión vía SSH con GitHub) |
| *git fetch* | Descarga los cambios del repositorio remoto al git repository pero no los copia al working directory |
| *git merge* | Fusiona los archivos del git repository con los de nuestro working directory |
| *git merge nameBranch* | Fusiona la rama en la que nos encontramos (a donde apunta el HEAD) con nameBranch |
| *git merge branchX \--allow-unrelated-histories* | Obliga a fusionar branchX con la actual (a donde apunta el HEAD) |
| *git pull* | Descarga los cambios del repositorio remoto (GitHub) a nuestro git repository y working directory fusionandolos con ambos |
| *git pull origin nameBranch* | Descarga cambios del repositorio remoto (GitHub) de la rama nameBranch y los fusiona a la rama actual |
| *git pull origin nameBranch \--allow-unrelated-histories* | Obliga a descargar cambios del repositorio remoto (GitHub) de la rama nameBranch y fusionarlos a la rama actual |
| *git push* | Envía los commits al repositorio remoto |
| *git push origin nameBranch* | Envía la rama nameBranch al repositorio remoto |
| *git push origin \--tags* | Envía los tags al repositorio remoto |
| *git push origin nameBranch \--tags* | Envía los tags de la rama nameBranch al repositorio remoto |
| *git push origin :refs/tags/nameTag* | Elimina un tag nameTag del repositorio remoto |
| *git push origin \--delete nameBranch* | Elimina la rama remota nameBranch |


&nbsp;


## Corregir último commit

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git commit \--amend* | Permite realizarle un cambio al último commit hecho. Para ello, el cambio que se nos olvido hacer lo realizamos y lo ponemos en STAGING con git add. Una vez estando en staging ejecutamos el comando |
| *git commit \--amend -m "mensaje"* | Comando anterior pero añadimos un mensaje |


&nbsp;


## Branches y checkout

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git branch nameNewBranch* | Crea una nueva rama nameNewBranch |
| *git branch -m actualName newName* | Renombra rama actualName por newName |
| *git branch* | Lista las ramas locales |
| *git branch -r* | Lista las ramas remotas (GitHub) |
| *git branch -a* | Lista todas las ramas |
| *git branch -d nameBranch* | Elimina la rama nameBranch |
| *git branch -D nameBranch* | Obliga a eliminar la rama nameBranch |
| *git push origin \--delete nameBranch* | Elimina la rama remota nameBranch |
| *git stash branch nameBranch* | Crea una rama nameBranch partiendo del stash guardado y nos posiciona en ella |
| *git checkout branch/commit_name* | Ir a otra rama/commit |
| *git checkout -b newBranch* | Crea rama newBranch y vamos a ella |
| *git checkout hashCommit nameFile.txt* | Permite regresar el archivo nameFile.txt a la versión del commit del hash |


&nbsp;


## Interfaz gráfica gitk

En Windows y en Mac ya viene junto con la instalación de GIT.

| *Instalación en Ubuntu* |
| :------------: |
| *sudo apt-get update* |
| *sudo apt-get upgrade* |
| *sudo apt install gitk* |

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *gitk* | Permite visualizar de manera gráfica las ramas y cambios en nuestro repositorio local |


&nbsp;


## Restore para sacar de staging y directorio de trabajo

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git restore \--staged nameFile* | Saca archivo nameFile del área de staging |
| *git restore nameFile* | Descarta cambios de nameFile en el directorio de trabajo |


&nbsp;


## Eliminar archivos con git rm

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git rm \--cached archivo/s* | Elimina el/los archivo/s del área de Staging pero los mantiene en nuestro disco duro. (Igual que git restore \--staged nameFile) |
| *git rm \--force archivo/s* | Elimina el/los archivo/s de Git y del disco duro |


&nbsp;


## Volver en el tiempo con git reset

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git reset \--hard hashCommit* | Se elimina lo que está en staging y en el directorio de trabajo y el HEAD apuntará al hashCommit |
| *git reset \--soft hashCommit* | Los cambios actuales que tengamos se agregarán al staging y el HEAD apuntará al hashCommit |
| *git reset HEAD~* | HEAD retrocede una posición (Hacia donde apunta) |
| *git reset HEAD@{3}* | Regresa múltiples posiciones (en este caso 3) manteniendo los cambios en nuestro directorio |


&nbsp;


## Análisis de cambios

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git log* | Lista de manera descendente los commits realizados |
| *git log \--stat* | Además de listar los commits, muestra la cantidad de bytes añadidos y eliminados en cada uno de los archivos modificados |
| *git log \--all \--graph \--decorate \--oneline* | Muestra de manera comprimida toda la historia del repositorio de manera gráfica y embellecida |
| *git log \--graph \--abbrev-commit \--decorate \--format=format:'%C(magenta)%h%C(reset) - %C(bold green)(%ar) - %C(reset)%C(white)%s%C(reset)%C(bold blue) - %an%C(reset) %C(bold yellow)%d%C(reset)' \--all \--date=relative* | Historial con git log muchísimo más organizado |
| *git show fileName* | Permite ver la historia de los cambios en fileName |
| *git diff* | Compara diferencias entre working directory y staging area |
| *git diff hashCommit1 hashCommit2* | Compara diferencias entre commits |
| *git shortlog* | Ver los commits hechos por una persona |
| *git shortlog -sn* | Ver solamente la cantidad de commits hechos por una persona |
| *git shortlog -sn \--all* | Todo lo anterior incluyendo los commits eliminados |
| *git shortlog -sn \--all \--no-merges* | Todo lo anterior sin incluir los merges |
| *git blame nameFile* | Ver quién modificó qué en nameFile |
| *git blame nameFile -L5,15* | Ver quién modificó qué en nameFile en un rango específico de líneas (En este caso de la 5 a la 15) |
| *git show-branch \--all* | Ver branches y su historia |


&nbsp;


## Ver TODA la historia

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git reflog* | Permite ver absolutamente todo lo que ha pasado con la historia del proyecto (incluyendo commits eliminados...) |


&nbsp;


## Alias

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git config \--list &#124; grep alias* | Ver alias |
| *git config \--global \--unset alias.nameAlias* | Eliminar alias nameAlias |
| *git config \--global alias.tree "log \--graph \--abbrev-commit \--decorate \--format=format:'%C(magenta)%h%C(reset) - %C(bold green)(%ar) - %C(reset)%C(white)%s%C(reset)%C(bold blue) - %an%C(reset) %C(bold yellow)%d%C(reset)' \--all \--date=relative"* | Crear alias. En este caso un alias llamado tree para visualizar el log organizado. Para ejecutarlo sería: *git tree* |


&nbsp;


## Tags

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git tag -a nombreTag -m "Mensaje" hashCommit* | Crear un tag y asignarlo a un commit |
| *git tag -d nameTag* | Elimina un tag nameTag del git repository |
| *git push origin :refs/tags/nameTag* | Elimina un tag nameTag del repositorio remoto |
| *git tag -l* | Lista los tags existentes |
| *git push origin nameBranch \--tags* | Envía los tags de la rama nameBranch al repositorio remoto |
| *git show-ref \--tags* | Lista los tags existentes con sus respectivos commits |

| *Pasos para renombrar una etiqueta* |
| :------------: |
| *git tag tagNuevo tagViejo* |
| *git tag -d tagViejo* |
| *git push origin :refs/tags/tagViejo* |
| *git push \--tags* |


&nbsp;


## Escribiendo la historia con rebase (MALA PRACTICA)

Lo siguiente funciona, por ejemplo, cuando no queremos hacer merge de una rama al main sino que dicha rama quede en la historia pero como si "no hubiera pasado nada". Esta es una muy mala práctica. En caso de hacerla, solo hacerlo localmente:

| *Comandos paso a paso* |
| :------------: |
| *git checkout nameBranch* |
| *git rebase main* |
| *git checkout main* |
| *git rebase nameBranch* |

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git rebase nameBranch* | Permite reescribir los commits de nameBranch con los de nuestra rama actual |
| *git rebase -i HEAD~4* | Permite hacer un rebase interactivo. Esto nos abrirá Vim o Nano y nos mostrará las opciones por elegir (por ejemplo, cambiar orden de commits, aplastar commits, entre otras opciones). En este caso seleccionamos los últimos 4 commits de la rama actual |


&nbsp;


## Memoria temporal con stash

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git stash* | Guarda lo que llevabamos en una "memoria temporal" para poder pasar a otras ramas... |
| *git stash save "nameStash"* | Guardarlo con nombre |
| *git stash list* | Permite ver los stash que tenemos (funciona como una pila) |
| *git stash pop* | Recupera el último stash que añadimos (se guardará en la rama en la que nos encontremos) |
| *git stash drop* | Borra el último stash |
| *git stash drop stash@{num_stash}* | Borrar stash específico (conocido por git stash list) |
| *git stash clear* | Borra todos los elementos guardados en stash |
| *git stash pop stash@{num_stash}* | Aplica los cambios de un stash específico y se elimina del stash |
| *git stash apply stash@{num_stash}* | Retoma los cambios de una posición específica del stash |
| *git stash branch nameBranch* | Crea una rama y le aplica el stash mas reciente |
| *git stash branch nameBranch@{num_stash}* | Crea una rama y le aplica un stash específico |
| *git stash -u* | Crea un stash con todos los archivos (Incluyendo los untracked) |


&nbsp;


## Limpiar el working directory

Este se encarga de eliminar los archivos untracked que no forman parte de nuestro trabajo (hay cosas que en ocasiones nos toca eliminar manualmente)

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git clean \--dry-run* | Lista los archivos a eliminar |
| *git clean -f* | Elimina |
| *git clean -x* | Elimina incluyendo los archivos que se encuentran en el .gitignore |
| *git clean -X* | Eliminar solamente los archivos ignorados por git |


&nbsp;


## Traer commit antigüo como HEAD con cherry pick (MALA PRACTICA)

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git cherry-pick hashCommit* | Permite traernos un commit antiguo (incluso de otra rama) al head de donde nos encontramos |


&nbsp;


## Buscando en archivos y commits de Git 

grep &rarr; para archivos
log &rarr; para commits

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *git grep word* | Busca la palabra word en todos nuestros archivos |
| *git grep -n word* | Le añade la línea en la que se encuentra |
| *git grep -c word* | Cuenta cuántas veces está la palabra word |
| *git log -S word* | Busca word en los commits |


&nbsp;


## Mas información

| *Comando* | *Descripción* |
| :------------: | :------------: |
| *command \--help* | Nos abrirá una ventana dandonos más detalles acerca de command |
