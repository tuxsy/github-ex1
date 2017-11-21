# Práctica del curso de git, gitHub y Sourcetree

## Ejercicio 1

### Dibujos del Grafo de Git
#### Después del punto 25
![](https://github.com/tuxsy/github-ex1/blob/master/snapshot-25.jpg =400x)
#### Al final del ejercicio
![](https://github.com/tuxsy/github-ex1/blob/master/snapshot-final.jpg =400x)

### Preguntas y respuestas
**Pregunta: ¿Qué comando utilizaste en el paso 11? ¿Por qué?**
`git reset --hard HEAD~1`
Con este comando muevo el HEAD (puntero actual de mi *working copy*) un paso hacia atrás.

Con el modificador `--hard` dejo mi *working copy* tal y como estaba ene ese commit.
De este modo consigo deshacer el último cambio.

**Pregunta: ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?**
En este caso quería volver a un commit que no estaba accesible en mi grafo de Git.
Por ese motivo uso `git reflog` para ver todo lo que he hecho en el repositorio.

Localizo el commit correspondiente al paso que he deshecho anteriormente por lo
que uso su identificador *SHA abreviado* para restaurarlo, mediante el comando
`git reset --hard 2c813ae`. Aquí vuelvo a usar el modificador `--hard` ya que me
interesa aplicar los cambios a mi *working copy*

**Pregunta: El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?**
No, se ha podido hacer un *fast-forward* sin problemas. El motivo es que, mientras
que hemos modificado el fichero en la rama `styled`, la rama `master` ha permanecido
intacta, y Git no ha tenido ninguna duda sobre cual era la versión definitiva del fichero.
Basicamente la de la rama `styled` ya que está más avanzada `master`.

**Pregunta: El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?**
Sí, se producen conflictos. La causa es que se han modificado las mismas zonas
del mismo fichero en dos ramas distintas (`htmlify` y `styled`), en *commits hermanos*. En este caso Git
me pregunta con qué versión del fichero me quiero quedar.

**Pregunta: El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?**
Ningún conflicto. En este caso la rama `styled` estaba más avanzada que la rama
`master`, pero ninguno de los cambios hechos afectaba a ningún fichero/region modificada
en `master` (básicamente porque esta rama estaba intacta). En este caso la estrategia
de Git para mergear ha sido la de *fast-forward*.

**Pregunta: ¿Qué comando o comandos utilizaste en el paso 25?**
Para dibujar el diagrama me he apoyado de la utilidad `gitk` que dibuja el grafo.
Aunque también hubiera podido usar 'git log --graph', pero estoy acostumbrado a
trabajar a diario con la utilidad anterior.

También me he apoyado con `git reflog` para sacar las versiones abreviadas de
los *SHA* sin tener que ir contando.

**Pregunta: El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?**
Sí, hubiera podido ser *fast-forward* sin problema, ya que incorporamos los cambios
de la rama `title` sin haber modificado el fichero en la rama `master`.

**Pregunta: ¿Qué comando o comandos utilizaste en el paso 27?**
Simplemente `git reset HEAD~1` sin comerme demasiado la cabeza ya que básicamente
lo que se pedía era retroceder HEAD un paso (antes del merge).

**Pregunta: ¿Qué comando o comandos utilizaste en el paso 28?**
Simplemente `git checkout -- git-nuestro.md`. Al haber retrocedido un paso sin
el modificador `--hard` la copia de trabajo contenía un cambio pendiente de pasar
al área de *stage*. Sólo era necesario anularlo.

**Pregunta: ¿Qué comando o comandos utilizaste en el paso 29?**
`git branch -D title`. Es importante el modificador `-D` en vez de `-d` ya que la
rama `title` estaba sin mergear.

**Pregunta: ¿Qué comando o comandos utilizaste en el paso 30?**
Al borrar la rama `title` el commit al que debía volver estaba inaccesible, por
lo que uso `git reflog` para bichear y localizar el commit deseado. Luego me cambio
usando `git reset --hard e836606`.

**Pregunta: ¿Qué comando o comandos usaste en el paso 32?**
Uso `git log` para ver cual es el modificador del primer commit (mejor dicho el
  primer commit que se pide en el ejercicio). luego me voy a él con `git checkout 1be431543367e7e4c3d9b6bf1d58541f8e28f7a2`

**Pregunta: ¿Qué comando o comandos usaste en el punto 33?**
Simplemente `git checkout master` ya que el commit al que se pedía ir coincidía
con la posición del puntero de dicha rama.
