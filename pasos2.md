**1) Crear un repositorio**

    git init.
    
**2) Crear un archivo git-nuestro.md con el contenido: **
    
    nano git-nuestro.md
    cat git-nuesro.md
    Git nuestro 
    Git nuestro que estas en los repos 
    Comprimidos sean tus commits 
    Venga a nosotros tu log 
    En el local como en el remote 
    Danos hoy nuestro pull de cada día 
    Perdona nuestros conflictos 
    Como también perdonamos los de otros geeks 
    No nos dejes caer en detached HEAD 
    y líbranos de SVN 
    git commit --amend 
    

**3) Añadir git-nuestro.md al staging area**

    git add git-nuestro.md
    
**4) Mover lo que hay en el staging area al repositorio**

    git commit -m "Initial commit"
    
**5) Crear una rama llamada “styled”**

    git bracnh styled
    
**6) Listar las ramas que hay en el repositorio**

    git branch
    
**7) Moverse a la rama “styled”**

    git checkout styled
    
**8) Comprobar que se está en la rama correcta**

    git branch
    
**9) Modificar en el archivo git-nuestro.md:**

    nano git-nuestro.md
    cat git-nuestro.md
    *Git* nuestro que estas en los repos 
    Comprimidos sean tus *commits* 
    Venga a nosotros tu *log* 
    En el local como en el *remote* 
    Danos hoy nuestro *pull* de cada día 
    Perdona nuestros *conflictos* 
    Como también perdonamos los de otros geeks 
    No nos dejes caer en *detached HEAD* 
    y líbranos de *SVN*
    `git commit --amend` 
    
**10) Añadir los cambios al staging área y luego pasarlos al repositorio**

    git add git-nuestro.md
    git commit
    
**11) Deshacer el último commit (perdiendo los cambios realizados en el working copy)**

    git reset --hard HEAD~1

**12) Rehacer el último commit (el que acabamos de deshacer)**

    git reset --hard 9dfd8c6

**13) Hacer un merge con ‘master’ (styled absorbe a master)**
    
    git merge master
    Already up to date.

**14) Volver a la rama master**

    git checkout master

**15) Crear una nueva rama llamada “htmlify”**

    git branch htmlify
    
**16) Cambiar a la rama htmlify**

    git checkout htmlify
    
**17) Modificar en el archivo git-nuestro.md:**

    nano git-nuestro.md
    cat git-nuestro.md
  	<p> <em> Git </em> nuestro que estas en los repos <br />
	  Comprimidos sean tus <em> commits </em><br/> 
	  Venga a nosotros tu <em> log </em> <br />
	  En el local como en el <em> remote </em> <br />
	  Danos hoy nuestro <em> pull </em> de cada día <br />
	  Perdona nuestros <em> conflictos </em> <br />
	  Como también perdonamos los de otros geeks <br />
	  No nos dejes caer en <em> detached HEAD </em> <br />
	  y líbranos de <em> SVN </em> <br />
	  <code>git commit --amend </code> </p>

**18) Hacer un commit**

    git add .
    git commit -m "add html style"
    
**19) Hacer un merge de “htmlify” en “styled” (styled absorbe a htmlify)**

    git checkout styled
    git merge htmlify
    Auto-merging git-nuestro.md
    CONFLICT (content): Merge conflict in git-nuestro.md
    Automatic merge failed; fix conflicts and then commit the result.

**20) Si hay conflictos, deberemos resolverlos quedándonos con el contenido de la rama “styled”.**

    nano git-nuestro.md
    git add .
    git commit
    
**21) Desde “master”, hacer un merge con “styled”**

    git checkout master
    git merge styled   
    Updating 8373ab7..6cd5b71
    Fast-forward
    git-nuestro.md | 19 +++++++++----------
    1 file changed, 9 insertions(+), 10 deletions(-)

**22) Crear una rama “title” y cambiarse a esa rama**

    git branch title
    git checkout title

**23) Añadir un título (a tu gusto) al archivo git-nuestro.md y hacer un commit.**

    nano git-nuestro.md
    git add git-nuestro.md
    git commit -m "add title"

**24) Volver a la rama master**

    git checkout master

**25) Dibujar el diagrama**

    git log --graph --abbrev-commit --pretty=oneline
    
**26) Hacer un merge “no fast-forward” de “title” en “master” (master absorbe a title)**

    git merge --no-ff title

**27) Deshacer el merge (sin perder los cambios del working copy)**

    git reset HEAD~1

**28) Descartar los cambios**

    git checkout --git-nuestro.md

**29) Eliminar la rama “title”**

    git branch -D title

**30) Rehacer el merge que hemos deshecho**

    git reflog
    6cd5b71 (HEAD -> master, styled) HEAD@{0}: reset: moving to HEAD~1
    aeb50ac HEAD@{1}: merge title: Merge made by the 'recursive' strategy.
    6cd5b71 (HEAD -> master, styled) HEAD@{2}: checkout: moving from title to master
    2d892ec HEAD@{3}: commit: Add title
    6cd5b71 (HEAD -> master, styled) HEAD@{4}: checkout: moving from master to title
    6cd5b71 (HEAD -> master, styled) HEAD@{5}: checkout: moving from title to master
    6cd5b71 (HEAD -> master, styled) HEAD@{6}: checkout: moving from master to title
    6cd5b71 (HEAD -> master, styled) HEAD@{7}: merge styled: Fast-forward
    8373ab7 HEAD@{8}: checkout: moving from styled to master
    6cd5b71 (HEAD -> master, styled) HEAD@{9}: commit (merge): Merge branch 'htmlify' into styled
    9dfd8c6 HEAD@{10}: checkout: moving from htmlify to styled
    fcd7a3a (htmlify) HEAD@{11}: commit: Add some html style
    8373ab7 HEAD@{12}: checkout: moving from master to htmlify
    8373ab7 HEAD@{13}: checkout: moving from styled to master
    9dfd8c6 HEAD@{14}: reset: moving to 9dfd8c6
    8373ab7 HEAD@{15}: reset: moving to HEAD~1
    9dfd8c6 HEAD@{16}: reset: moving to 9dfd8c6
    8373ab7 HEAD@{17}: reset: moving to HEAD~1
    9dfd8c6 HEAD@{18}: commit: Modify git-nuestro.md adding some style
    8373ab7 HEAD@{19}: checkout: moving from master to styled
    8373ab7 HEAD@{20}: commit (initial): Initial commit
    git reset aeb50ac

**31) Volver a master y eliminar el resto de ramas**

Ya estabamos en master asi que no nos movemos, ejecutamos un <git branch> para asegurarnos y asi ver cuantas ramas tenemos.

    git branch
    git branch -D htmlify
    git branch -D dtyled

**32) Volver al commit inicial cuando se creó el poema**

    git reflog
    aeb50ac (HEAD -> master) HEAD@{0}: reset: moving to aeb50ac
    6cd5b71 HEAD@{1}: reset: moving to HEAD~1
    aeb50ac (HEAD -> master) HEAD@{2}: merge title: Merge made by the 'recursive' strategy.
    6cd5b71 HEAD@{3}: checkout: moving from title to master
    2d892ec HEAD@{4}: commit: Add title
    6cd5b71 HEAD@{5}: checkout: moving from master to title
    6cd5b71 HEAD@{6}: checkout: moving from title to master
    6cd5b71 HEAD@{7}: checkout: moving from master to title
    6cd5b71 HEAD@{8}: merge styled: Fast-forward
    8373ab7 HEAD@{9}: checkout: moving from styled to master
    6cd5b71 HEAD@{10}: commit (merge): Merge branch 'htmlify' into styled
    9dfd8c6 HEAD@{11}: checkout: moving from htmlify to styled
    fcd7a3a HEAD@{12}: commit: Add some html style
    8373ab7 HEAD@{13}: checkout: moving from master to htmlify
    8373ab7 HEAD@{14}: checkout: moving from styled to master
    9dfd8c6 HEAD@{15}: reset: moving to 9dfd8c6
    8373ab7 HEAD@{16}: reset: moving to HEAD~1
    9dfd8c6 HEAD@{17}: reset: moving to 9dfd8c6
    8373ab7 HEAD@{18}: reset: moving to HEAD~1
    9dfd8c6 HEAD@{19}: commit: Modify git-nuestro.md adding some style
    8373ab7 HEAD@{20}: checkout: moving from master to styled
    8373ab7 HEAD@{21}: commit (initial): Initial commit
    git reset 8373ab7

**33) Volver al estado final, cuando pusimos título al poema**

    git reset aeb50ac

**34) Crear los siguientes tags:**

inicial: en el primer commit 

    git tag inicial 8373ab7

styled: modificación del paso 10 

    git tag styled 9dfd8c6

htmlify: modificación del paso 17-18 

    git tag htmlify fcd7a3a

title: modificación del paso 30 

    git tag title (por que estamos apuntando aqui)

**35) Ir al tag htmlify**

    git reset --hard htmlify
