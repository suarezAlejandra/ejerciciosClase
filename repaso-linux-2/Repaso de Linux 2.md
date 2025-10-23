# REPASO DE LINUX. CAPÍTULO 3: FICHEROS Y DIRECTORIOS II

[TOC]

## Caracteres comodín

Se pueden crear patrones utilizando **símbolos comodín** para no tener que escribir todos y cada uno de los ficheros. 

- Para mostrar cada uno de los ficheros que comienzan por `docu` seguido de un número del 1 al 6 se puede utilizar un patrón:

  ```bash
  $ cat fich[1-6]
  ```

  

- Para mostrar el contenido de todos los ficheros que comienzan por `fich` se puede hacer:

  ```bash
  $ cat fich*
  ```

  dónde `*` representa cualquier combinación de caracteres, incluso la cadena vacía. 

  

- El carácter `*` se puede colocar en cualquier lugar. Por ejemplo, para mostrar todos los ficheros que comienzan por la letra "a" y terminan por la letra "s" dentro del directorio `/usr/bin`:

  ```bash
  $ ls /usr/bin/a*s
  ```

  
<div style="page-break-after: always;"></div>
- El símbolo `?` representa un carácter cualquiera. De esta forma, la siguiente sentencia muestra todos los ficheros del directorio `/usr/bin` cuyo nombre comienza por "g", sigue cualquier carácter, a continuación sigue una "o" y termina con cualquier cadena de caracteres incluida la cadena vacía.

  ```bash
  $ ls /usr/bin/g?o*
  ```

  

- Los **corchetes** se utilizan de forma parecida al carácter `?` aunque, a diferencia de éste, permiten especificar un poco más. Por ejemplo, `[adfg]`significa cualquiera de los caracteres `a`, `d`, `f` o `g`. `[Hh]`ola es un patrón que encaja tanto con "Hola" como con "hola". `[a-z]*` representa cualquier cadena de caracteres que comienza con una letra minúscula.



## Comandos para copia y borrado de ficheros

### Comando `cp`

Sirve para copiar ficheros. Se puede copiar un único fichero o muchos. Se pueden copiar tanto ficheros como directorios. Por supuesto, se pueden utilizar símbolos comodín.

En el proceso de copia intervienen 3 factores: lo que se copia, la ruta de origen y la ruta de destino. 

Por ejemplo, la siguiente sentencia copia el ficheros `hosts`, que se encuentra en el directorio `/etc` al directorio `/home/alumno/pruebas/`.

```bash
$ cp /etc/hosts /home/alumno/pruebas/
```

Si no se especifica ningún directorio origen, se toma por defecto el directorio actual. El siguiente ejemplo copia todos los archivos con la extensión òdt` del directorio actual al directorio `textos`.

```bash
$ cp *.odt textos/
```

Cuando se quiere especificar como directorio destino el directorio actual se utiliza el carácter `.`

El siguiente ejemplo copia todos los ficheros del directorio `/usr/bin` que comienzan por la letra "g" al directorio actual.

```bash
$ cp /usr/bin/g*
```



### Comando `mv`

Sirve para dos cosas, para mover y para cambiar de nombre. Se puede hacer cualquiera de las dos cosas por separado o las dos cosas al mismo tiempo. Por ejemplo:

```bash
$ mi_texto.txt carta.txt
```

Le cambia el nombre a `mi_texto.txt` y pasa a llamarse `carta.txt`

En cambio:

```bash
$ mv carta.txt Documentos/
```

mueve `carta.txt` al directorio `Documentos`

Se pueden hacer dos cosas a la vez, mover y cambiar el nombre:

```bash
$ cd Documentos/
/Documentos$ mkdir correspondencia
/Documentos$ mv carta.txt correspondencia/carta01.txt
```



### Comando `rm`

Se utiliza para borrar ficheros, aunque estos no se envían a la papelera así que **no se pueden recuperar una vez borrados.** Por ejemplo:

```bash
$ rm *.txt
```

Borra todos los archivos con la extensión `txt` del directorio actual.

![image-20251002161349368](./Repaso%20de%20Linux%202.assets/image-20251002161349368.png)



## Comandos para copia y borrado de directorios

De la misma forma que se copian, borran o mueven ficheros, se puede hacer lo mismo con directorios. Hay que tener en cuenta que los directorios pueden contener muchos ficheros y otros directorios que a su vez pueden contener otros ficheros y directorios. 

### Comando `cp`

Sirve para copiar directorios. Si se quiere copiar un fichero completo con todo lo que incluye en su interior hay que indicarlo con la opción `-R` ("copiar de forma recursiva"). Por ejemplo:

```bash
$ mkdir multimedia2
$ cp multimedia/* multimedia2
```

Se hace una copia del contenido del directorio `multimedia` al directorio `multimedia2`.



### Comando `mv`

Funciona de forma análoga a `cp`, pero mueve en lugar de copiar. Cuando se trata de renombrar, funciona igual que con ficheros. Por ejemplo:

```bash
$ mv multimedia2 multimedia_copia
```

![image-20251002162339173](./Repaso%20de%20Linux%202.assets/image-20251002162339173.png)

Esto cambia el nombre del directorio `multimedia2` a `multimedia_copia`. El contenido de ese directorio permanece intacto.



### Comando `rm`

Se pueden borrar directorios. Por ejemplo:

```bash
$ rm multimedia_copia/
```

![image-20251002162542390](./Repaso%20de%20Linux%202.assets/image-20251002162542390.png)

Se obtiene un error porque hay que borrar el contenido de forma recursiva:

```bash
$ rm -Rf multimnedia_copia/
```

![image-20251002162646996](./Repaso%20de%20Linux%202.assets/image-20251002162646996.png)

Además de la opción `-R` se incluye la opción `-f` que hace que nos pida confirmación por cada elemento que se quiera borrar.



## Ejercicios

1. Muestra todos los archivos del directorio actual que son imágenes `jpg`.

   ```bash
   $ ls *.jpg
   ```

   

2. Muestra todos los archivos del directorio `/usr/bin` que empiecen por la letra`j`.

   ```bash
   $ ls /usr/bin/j*
   ```

   ![image-20251006155325273](./Repaso%20de%20Linux%202.assets/image-20251006155325273.png)

   

3. Muestra los archivos que empiecen por `k` y tengan una `a` en la tercera posición, dentro del directorio `/usr/bin`.

   ```bash
   $ ls /usr/bin/k?a*
   ```

   
<div style="page-break-after: always;"></div>
4. Muestra los archivos del directorio `/bin` que terminen en `n`.

   ```bash
   $ ls /bin/*n
   ```

   ![image-20251006155424592](./Repaso%20de%20Linux%202.assets/image-20251006155424592.png)

   
<div style="page-break-after: always;"></div>
5. Muestra todos los archivos que hay en `/etc` y todos los que hay dentro de cada subdirectorio, de forma recursiva.

   ```bash
   $ ls -R /etc
   ```

   ![image-20251006155652364](./Repaso%20de%20Linux%202.assets/image-20251006155652364.png)

   

6. Crea un directorio en tu directorio de trabajo con nombre `prueba`. Copia el archivo `gzip` del directorio `/bin` al directorio `prueba`. Crea un duplicado de `gzip` con nombre `gzip2` dentro de `prueba`.

   ```bash
   $ mkdir prueba
   $ cp /bin/gzip prueba/
   $ cp prueba/gzip prueba/gzip2
   ```

   ![image-20251006160040934](./Repaso%20de%20Linux%202.assets/image-20251006160040934.png)

   
<div style="page-break-after: always;"></div>
7. Cambia el nombre de `prueba` a `prueba2`. Crea `prueba3` en el mismo nivel que `prueba2` y mueve todos los ficheros de `prueba2` a `prueba3`. Borra `prueba2`.

   ```bash
   $ mv prueba prueba2
   $ mkdir prueba3
   $ mv prueba2/* prueba3/
   $ rmdir prueba2
   ```

   ![image-20251006160247983](./Repaso%20de%20Linux%202.assets/image-20251006160247983.png)

   

8. Crea un fichero vacío con nombre `*?Hola caracola?*`. ¿Se puede? En caso de que se pudiera, ¿sería recomendable poner nombres así? Razona la respuesta.

   ```bash
   $ touch '*?Hola caracola?*'
   ```

   ![image-20251006160348515](./Repaso%20de%20Linux%202.assets/image-20251006160348515.png)

   Sí se puede, si se pon el nombre entre comillas, aunque no es recomendable.

   
<div style="page-break-after: always;"></div>
9. Crea un directorio con nombre `multimedia_pruebas` y copia en él todo el contenido del directorio `multimedia`. A continuación crea en `multimedia/video/` dos ficheros, uno con nombre `peliculas.txt` y otro con nombre `actores.txt`. Edita el fichero `peliculas.txt` e introduce el nombre de tu película favorita. A continuación, crea en `multimedia_pruebas/video/` otro fichero que también tenga por nombre `peliculas.txt`, edítalo y esta vez escribe el nombre de tus cinco películas favoritas. Ahora haz una copia de todo el contenido de `multimedia` en `multimedia_prueba` de tal forma que sólo se copien los contenidos nuevos, es decir, si hay coincidencia en el nombre de un archivo se respetará el que se haya modificado más recientemente. Para comprobar que se ha hecho todo correctamente, basta mirar si en `multimedia_prueba/video` está el archivo vacío `actores.txt` y además el archivo `peliculas.txt` debe contener 5 películas y no 1.

   ```bash
   $ mkdir multimedia_pruebas
   $ cp multimedia/* multimedia_pruebas/
   $ cd multimedia/video/
   $ mkdir peliculas.txt actores.txt
   $ nano peliculas.txt
   $ cd ..
   $ cd multimedia_pruebas/video/
   $ mkdir peliculas.txt
   $ nano peliculas.txt
   $ cd ..
   $ cp multimedia/* multimedia_pruebas/
   ```

   

10. Borra el directorio `multimedia/imagenes/otras`. El sistema debe pedir al usuario que confirme el borrado.

    ```bash
    $ rm -ri multimedia/imagenes/otras
    ```

    ![image-20251006160613955](./Repaso%20de%20Linux%202.assets/image-20251006160613955.png)

    

11. Mueve el archivo `peliculas.txt`, que está dentro de `multimedia/video`, al directorio que está justo a un nivel superior. Ahora el archivo debe llamarse `mis_peliculas.txt` en lugar de `peliculas.txt`.

    ```bash
    $ mv multimedia/video/peliculas.txt multimedia/mis_peliculas.txt
    ```

    