**¿Qué comando utilizaste en el paso 11?**

    git reset --hard HEAD~1
    
**¿Por qué?**

La opción HARD modifica el working area, por lo que perdemos las modificaciones que hemos realizado.

    8373ab7 (HEAD -> styled, master) HEAD@{0}: reset: moving to HEAD~1
    9dfd8c6 HEAD@{1}: commit: Modify git-nuestro.md adding some style
    8373ab7 (HEAD -> styled, master) HEAD@{2}: checkout: moving from master to styled
    8373ab7 (HEAD -> styled, master) HEAD@{3}: commit (initial): Initial commit

**¿Qué comando o comandos utilizaste en el paso 12?**

    git reset --hard  9dfd8c6

**¿Por qué?** 

Primero me equivoqué e hice un reset sin la opción hard, volví al repositorio original pero el working copy no vario 
por lo que el contenido del repositorio no correspondia al working area. Volví a hacer el reset HEAD~1 y esta vez 
si que puse la opción hard para que modificara el working copy con lo que habia después del commit.

**El merge del paso 13, ¿Causó algún conflicto?**

No

    git merge master
    Already up to date.

**¿Por qué?**

En realidad la rama style podria ser perfectamente la rama master no hay commits de la rama master que difiera de la 
style, siguen una única secuencia.

**El merge del paso 19, ¿Causó algún conflicto?**

Si. 

**¿Por qué?**

La rama htmlify tiene contenido diferente al de styled, styled tiene tags de markdown mientras que el htmlify 
tiene tags html.

**El merge del paso 21, ¿Causó algún conflicto?**

No. 

**¿Por qué?**

Cuando unimos las ramas htmlify con styled nos quedamos con los cambios que habiamos hecho en styled, y en realidad 
son los mismos que habian cuando haciamos el merge en el paso 13.  

**¿Qué comando o comandos utilizaste en el paso 25?**

    git log --graph --abbrev-commit --pretty=oneline
    *   6cd5b71 (HEAD -> master, title, styled) Merge branch 'htmlify' into styled
    |\
    | * fcd7a3a (htmlify) Add some html style
    * | 9dfd8c6 Modify git-nuestro.md adding some style
    |/
    * 8373ab7 Initial commit

**El merge del paso 26, ¿Podría ser fast forward?**

Si

**¿Por qué?**

El commit podia seguir una misma línea por lo que se hubiera podido hacer moviendo el puntero directamente.

**¿Qué comando o comandos utilizaste en el paso 27?**

    git reset HEAD~1
    
**¿Qué comando o comandos utilizaste en el paso 28?**

    git checkout -- git-nuestro.md
    
**¿Qué comando o comandos utilizaste en el paso 29?**

    git branch -D title
    
**¿Qué comando o comandos utilizaste en el paso 30?**

    git reset aeb50ac
    
No he aplicado la opción --hard y el working copy no se ha modificado por lo que en el working copy 
no hay lo mismo que en el repositorio. Si hacemos un <git diff HEAD> nos da el sigueinte resultado:

    diff --git a/git-nuestro.md b/git-nuestro.md
    index a9c6ce6..960b12a 100644
    --- a/git-nuestro.md
    +++ b/git-nuestro.md
    @@ -1,4 +1,3 @@
    -#GIT NUESTRO
     *Git* nuestro
     Git nuestro que estas en los repos
     Comprimidos sean tus *commits*
     
Deberiamos haber hecho un <reset --hard> o bien ahora hacer un <checkout -- git-nuestro.md>
NOTA: he hecho finalemente el checkout --.

**¿Qué comando o comandos usaste en el paso 32?**

Primero un reflog para averiguar cual es el primer commit. Una vez ayado hacemos un reset 

    git reset 8373ab7
    
**¿Qué comando o comandos usaste en el punto 33?**

El mismo reflog ya me ha mostrado el commit

    git reset aeb50ac
