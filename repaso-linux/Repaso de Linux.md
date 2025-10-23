# REPASO DE LINUX. CAPÍTULO 2: FICHEROS Y DIRECTORIOS 

[TOC]



<div style="page-break-after: always;"></div>

## Estructura de directorios

Tabla con los directorios más importantes de un sistema Linux:

<img src="C:/Users/2dawv07/AppData/Roaming/Typora/typora-user-images/image-20250925175153452.png" alt="image-20250925175153452" style="zoom:70%;" />


<div style="page-break-after: always;"></div>

## Comandos de visualización, creación y cambio de directorios

### Comando `pwd`

Muestra cuál es el directorio de trabajo actual, es decir, dónde se encuentra el usuario dentro de la estructura de directorios del sistema.

```bash
$ pwd
```

![image-20250925175444806](./Repaso%20de%20Linux.assets/image-20250925175444806.png)



### Comando `ls`

Muestra el contenido del directorio actual aunque, por defecto, los archivos ocultos no se muestran.

```bash
$ ls
```

![image-20250925175642327](./Repaso%20de%20Linux.assets/image-20250925175642327.png)

Aunque se le pueden añadir opciones al comando `ls`, como por ejemplo:

- `ls -a` muestra todos los archivos, incluyendo los ocultos.

  ```bash
  $ ls -a
  ```

  ![image-20250925180145070](./Repaso%20de%20Linux.assets/image-20250925180145070.png)

  

- `ls -l` muestra un listado detallado, con la última fecha de modificación de cada archivo, el tamaño, etc.

  ```bash
  $ ls -l
  ```

  ![image-20250925180301132](./Repaso%20de%20Linux.assets/image-20250925180301132.png)

  

- `ls -h` muestra el tamaño de los ficheros en bytes, Kb, Mb, etc.

  ```bash
  $ ls -h
  ```

  ![image-20250925180413632](./Repaso%20de%20Linux.assets/image-20250925180413632.png)

Todas las opciones disponibles tanto para el comando `ls` como para el resto de comandos se pueden consultar mediante las páginas del manual, con el comando `man` seguido del comando del que se quiere obtener información:

```bash
$ man ls
```

Para salir del manual basta con pulsar la tecla `q`.



### Comando `cd`

Permite cambiar de directorio. Si se utiliza sin ningún tipo de argumento, cambia al directorio de trabajo personal.

```bash
$ cd
```

Si se utiliza seguido de una ruta, cambia al directorio indicado.

```bash
$ cd /etc
```

![image-20250925181125103](./Repaso%20de%20Linux.assets/image-20250925181125103.png)

Las rutas pueden ser de dos tipos:

- **Ruta absoluta:** comienza por el carácter `/`.

  ```bash
  $ cd /usr/local/
  ```

  

- **Ruta relativa:** comienza por cualquier otro carácter.

  ```bash
  $ cd Music
  ```

  

### Comando `mkdir`

Con este comando se pueden crear directorios. Por ejemplo, para crear una estructura de carpetas donde un estudiante guardará información sobre sus asignaturas según el siguiente esquema:

![image-20250925182130861](./Repaso%20de%20Linux.assets/image-20250925182130861.png)

Se tendría que hacer lo siguiente:

![image-20250926163045909](./Repaso%20de%20Linux.assets/image-20250926163045909.png)



## Comandos para visualización de ficheros

### Comando `cat`

Muestra por pantalla el contenido de un fichero y, cuando termina, el usuario está otra vez de vuelta en la línea de comandos. Por ejemplo:

```bash
$ cat /var/log/dmseg
```

Muestra el contenido del fichero `dmesg` que se encuentra en el directorio `/var/log`.

![image-20250929155959521](./Repaso%20de%20Linux.assets/image-20250929155959521.png)



### Comando `more`

Hace lo mismo que el comando `cat`, a diferencia de que muestra el fichero pantalla a pantalla, es decir, llena de texto la pantalla y espera a que el usuario pulse la tecla <espacio> para pasar a la siguiente.

```bash
$ more /var/log/dmesg
```

![image-20250929160136644](./Repaso%20de%20Linux.assets/image-20250929160136644.png)



### Comando `less`

Es el comando más versátil de los tres ya que permite moverse hacia delate y hacia atrás dentro del fichero, utilizando los cursores o las teclas `AvPág`  y `RePág`.

```bash
$ less /var/log/dmesg
```

Puede interrumpirse la visualización en cualquier momento y volver al símbolo del sistema pulsando la letra `q`.



### Comandos `head` y `tail`

Permiten mostrar de forma parcial el contenido de un fichero. Como su nombre indica, el comando `head` muestra las primeras líneas del fichero (la cabecera) y el comando `tail` muestra las últimas líneas (la cola). 

```bash
$ head /boot/grub/menu.lst
```

```bash
$ tail /boot/grub/menu.lst
```

Por defecto, tanto `head` como `tail` muestran 10 líneas, pero eso puede cambiarse con la opción `-n`.

```bash
$ tail -n4 /boot/grub/menu.lst
```

En este caso, solo muestra 4 líneas.



## Comandos de edición de ficheros

### Comando `touch`

Permite crear un fichero vacío. Con cualquier editor de texto se puede crear un fichero vacío, pero con `touch`es especialmente cómodo y rápido. En el siguiente ejemplo se crea el archivo `prueba.txt` vacío:

```bash
$ touch prueba.txt
```

![image-20250929162521194](./Repaso%20de%20Linux.assets/image-20250929162521194.png)



### Editor`ee`

El programa `ee` es un editor muy rudimentario pero al mismo tiempo efectivo. Se puede editar el archivo anterior y escribir alguna frase:

```bash
$ ee prueba.txt
```


<div style="page-break-after: always;"></div>
### Editor`nano`

Es otro editor muy simple. Recomendado.

**Comandos y atajos básicos:**

- `Ctrl + G`: Muestra la ayuda del editor.
- `Ctrl + O`: Guarda el archivo.
- `Ctrl + X`: Sale del editor y pregunta si deseas guardar los cambios.
- `Ctrl + W`: Busca texto en el archivo.
- `Ctrl + U`: Copia el texto seleccionado.
- `Ctrl + K`: Corta el texto.
- `Ctrl + Y`: Pega el texto.



**¿Cómo iniciar y usar `nano`?**

1. **Abre la terminal** en tu sistema.
2. Escribe `nano` seguido del nombre del archivo que deseas editar o crear (por ejemplo, `nano mi_archivo.txt`) y presiona Enter.
3. **Escribe o edita tu texto** usando el teclado.
4. **Utiliza los atajos** de teclado para las acciones deseadas.
5. **Guarda y sal** presionando `Ctrl + O` para guardar y luego `Ctrl + X` para salir.



### Editor`mcedit`

Editor algo más sofisticado que `ee` o `nano`. 

```bash
$ mcedit prueba.txt
```

![image-20250929165031736](./Repaso%20de%20Linux.assets/image-20250929165031736.png)

Con la tecla `F2`se guardan los cambios y con dos pulsaciones de ESC (o con la tecla `F10`) sen sale del programa.



### Editor `joe`

Para usar Joe en Linux, escribe `joe nombre_archivo` en la terminal para abrir un archivo o crearlo. Las operaciones básicas incluyen guardar con `Ctrl + K` y `x`, y salir sin guardar con `Ctrl + C`. Joe es un editor de texto basado en la consola, similar a **WordStar**, y se configura a través de un archivo `joerc`.

**¿Cómo usar `joe`?**

1. **Abrir o crear un archivo:** En la terminal, escribe `joe`seguido del nombre del archivo que quiere editar.
2. **Escribir y editar texto:** Escribe tu texto directamente en la pantalla. Joe funciona como un editor clásico.
3. **Guardar el archivo:** Pulsa `Ctrl + K`y luego `x` para guardar el archivo y salir del editor.
4. **Salir sin guardar:** Si quieres salir sin guardar los cambios, pulsa `Ctrl + C`y luego `y` o `n` para confirmas la elección.
5. **Ayuda:** Para ver las combinaciones de teclas y más opciones, se puede usar `Ctrl + K`seguido de `h`.



### Editor `vi`

Es el programa más difícil de utilizar y muy potente. No recomendado.



### Instalación de editores

En el caso de no tener instalado estos editores, basta con teclear `sudo apt-get install` seguido del nombre del programa que se desea instalar. Por ejemplo, si se desea instalar `ee`:

```bash
$ sudo apt-get install ee
```

![image-20250929163055088](./Repaso%20de%20Linux.assets/image-20250929163055088.png)



## EJERCICIOS

1. ¿En qué directorio se encuentran los ficheros de configuración del sistema?

   ```bash
   $ /etc
   ```

   

2. Para entrar en un sistema Linux hace falta: **a)**nombre de usuario, contraseña y dirección IP, **b)**nombre de usuario y contraseña o **c)**únicamente una contraseña.

   **b)** Nombre de usuario y contraseña

   

3. Muestra el contenido del directorio actual.

   ```bash
   $ ls
   ```

   ![image-20250929174139359](./Repaso%20de%20Linux.assets/image-20250929174139359.png)

   
<div style="page-break-after: always;"></div>
4. Muestra el contenido del directorio que está justo a un nivel superior.

   ```bash
   $ ls ..
   ```

   ![image-20250929174228014](./Repaso%20de%20Linux.assets/image-20250929174228014.png)

   

5. ¿En qué día de la semana naciste?, utiliza la instrucción `cal` para averiguarlo.

   ```bash
   $ cal MES AÑO
   ```

   ![image-20250929174411236](./Repaso%20de%20Linux.assets/image-20250929174411236.png)

   
<div style="page-break-after: always;"></div>
6. Muestra los archivos del directorio `/bin`.

   ```bash
   $ ls /bin
   ```

   <img src="./Repaso%20de%20Linux.assets/image-20250929174513247.png" alt="image-20250929174513247" style="zoom:50%;" />

   
<div style="page-break-after: always;"></div>
7. Suponiendo que te encuentras en tu directorio personal (`/home/nombre`), muestra un listado del contenido de `/usr/bin`...

   **a)** con una sola línea de comando.

   ```bash
   $ ls /usr/bin
   ```

   <img src="./Repaso%20de%20Linux.assets/image-20251002173138478.png" alt="image-20251002173138478" style="zoom:50%;" />

   **b)** moviéndote paso a paso por los directorios.

   ```bash
   $ cd /usr
   $ cd bin
   $ ls
   ```

   <img src="./Repaso%20de%20Linux.assets/image-20251002173221324.png" alt="image-20251002173221324" style="zoom:50%;" />
<div style="page-break-after: always;"></div>
   **c)** con dos líneas de comandos.

   ```bash
   $ cd /usr/bin
   $ ls
   ```

   <img src="./Repaso%20de%20Linux.assets/image-20251002173253985.png" alt="image-20251002173253985" style="zoom:50%;" />

   

8. Muestra todos los archivos que hay en `/etc` y todos los que hay dentro de cada subdirectorio, de forma recursiva (con un solo comando).

   ```bash
   $ ls -R /etc
   ```

   <img src="./Repaso%20de%20Linux.assets/image-20251002173331862.png" alt="image-20251002173331862" style="zoom:50%;" />

   
<div style="page-break-after: always;"></div>
9. Muestra todos los archivos del directorio `/usr/X11R6/bin` ordenados por tamaño (de mayor a menor). Sólo debe aparecer el nombre de cada fichero, sin ninguna otra información adicional.

   ```bash
   $ ls -S usr/X11R6/bin
   ```

   ![image-20251002184612207](./Repaso%20de%20Linux.assets/image-20251002184612207.png)

   

10. Muestra todos los archivos del directorio `/etc` ordenados por tamaño (de mayor a menor) junto con el resto de características, es decir, permisos, tamaño, fechas de la última actualización, etc. El tamaño de cada fichero debe aparecer en un formato "legible", o sea, expresado en Kb, Mb, etc.

    

    

11. Muestra todos los archivos del directorio `/bin`ordenados por tamaño (de menor a mayor). Sólo debe aparecer el tamaño y el nombre de cada fichero, sin ninguna otra información adicional. El tamaño de cada fichero debe aparecer en un formato "legible", o sea, expresado en Kb, Mb, etc.

    

12. Muestra el contenido del directorio raíz utilizando como argumento de `ls` una ruta absoluta.

    ```bash
    $ ls /
    ```

    ![image-20251002184736694](./Repaso%20de%20Linux.assets/image-20251002184736694.png)

    

13. Muestra el contenido del directorio raíz utilizando como argumento de `ls` una ruta relativa. Suponemos que el directorio actual es `/home/elena/documentos`.

    

14. Crea el directorio `gastos` dentro del directorio personal.

    ```bash
    $ mkdir /home/alejandra/gastos
    ```

    

15. ¿Qué sucede si se intenta crear un directorio dentro de `/etc`?

    Se obtiene un error.

    
<div style="page-break-after: always;"></div>
16. Muestra el contenido del fichero `/etc/fstab`.

    ```bash
    $ cat /etc/fstab
    ```

    <img src="./Repaso%20de%20Linux.assets/image-20251002185312858.png" alt="image-20251002185312858" style="zoom:200%;" />

    

17. Muestra las 10 primeras líneas del fichero `/etc/bash.bashrc`.

    ```bash
    $ head /etc/bas.bashrc
    ```

    

18. Crea la siguiente estructura de directorios dentro del directorio de trabajo personal:

    <img src="./Repaso%20de%20Linux.assets/image-20250929170712956.png" alt="image-20250929170712956" style="zoom:65%;" />

    ```bash
    $ mkdir multimedia
    $ cd multimedia/
    $ mkdir musica imagenes video presentaciones
    $ cd imagenes/
    $ mkdir personales otras
    ```

    ![image-20251002185804203](./Repaso%20de%20Linux.assets/image-20251002185804203.png)

    

19. Crea un fichero vacío dentro del directorio `musica`, con nombre `estilos_favoritos.txt`

    ```bash
    $ cd multimedia/musica/
    $ touch estilos_favoritos.txt
    ```

    ![image-20251002190413272](./Repaso%20de%20Linux.assets/image-20251002190413272-1759424654476-1.png)

    

20. Utiliza tu editor preferido para abrir el fichero `estilos_favoritos.txt` e introduce los estilos de música que más te gusten. Guarda los cambios y sal.

    ```bash
    $ nano estilos_favoritos.txt
    ```

    ![image-20251002190609144](./Repaso%20de%20Linux.assets/image-20251002190609144.png)

    ![image-20251002190535901](./Repaso%20de%20Linux.assets/image-20251002190535901.png)

    
<div style="page-break-after: always;"></div>
21. Muestra todo el contenido de `estilos_favoritos.txt`

    ```bash
    $ cat estilos_favoritos.txt
    ```

    ![image-20251002191017464](./Repaso%20de%20Linux.assets/image-20251002191017464.png)

    

22. Muestra las 3 primeras líneas de `estilos_favoritos.txt`

    ```bash
    $ head -n 3 estilos_favoritos.txt
    ```

    ![image-20251002190939861](./Repaso%20de%20Linux.assets/image-20251002190939861.png)

    

23. Muestra la última línea de `estilos_favoritos.txt`

    ```bash
    $ tail -n 1 estilos_favoritos.txt
    ```

    ![image-20251002191128120](./Repaso%20de%20Linux.assets/image-20251002191128120.png)

    

24. Muestra todo el contenido del fichero `estilos_favoritos.txt` excepto la primera línea. Se supone que no sabemos de antemano el número de líneas del fichero.

    ```bash
    $ tail -n +2 estilos_favoritos.txt
    ```

    ![image-20251002191233480](./Repaso%20de%20Linux.assets/image-20251002191233480.png)
