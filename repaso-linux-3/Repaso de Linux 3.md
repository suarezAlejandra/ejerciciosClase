# REPASO DE LINUX. CAPÍTULO 4: GRUPOS, USUARIOS Y PERMISOS

[TOC]



## ¿Qué es el superusuario?

El **superusuario, administrador del sistema** o simplemente el **`root`** es un usuario especial que tiene privilegios para cambiar la configuración, borrar y crear ficheros en cualquier directorio, crear nuevos grupos y usuarios, etc.

**ES PELIGROSO TRABAJAR COMO SUPERUSUARIO porque se puede dañar el sistema de forma irreversible. El lector debe estar seguro de lo que hace cuando trabaje como superusuario.**

```bash
$ sudo touch /etc/prueba.txt
```

![image-20251002164949885](./Repaso%20de%20Linux%203.assets/image-20251002164949885.png)

Se intenta crear el fichero `prueba.txt` en `/etc` como usuario normal y se obtiene un error de "Permiso denegado", lo que quiere decir que un usuario sin privilegios no puede hacer eso. A continuación, se intenta como administrador usando el comando `sudo`, esta vez sí se consigue.



## Permisos

La información sobre grupos, usuarios y permisos se obtiene mediante el comando `ls` junto con la opción `-l`. Vamos a ver los permisos que tiene establecidos el fichero `whatis` que se encuentra en el directorio `/usr/bin`:

```bash
$ ls -l /usr/bin/whatis
```

![image-20251002165327263](./Repaso%20de%20Linux%203.assets/image-20251002165327263.png)

En la primera columna aparecen los permisos, en la tercera se indica el usuario y en la cuarta aparece el nombre del grupo. A continuación se muestra qué significan los caracteres de la primera columna:

![image-20251002165436263](./Repaso%20de%20Linux%203.assets/image-20251002165436263.png)

El tipo de fichero se indica en la siguiente tabla:

![image-20251002165503820](./Repaso%20de%20Linux%203.assets/image-20251002165503820.png)



## ¿Quiénes somos?

### Comando `whoami`

Antes de empezar a crear usuarios, grupos y cambiar permisos, debemos saber quiénes somos y a qué grupo/grupos pertenecemos. En principio entraremos al sistema como un determinado usuario, pero podemos utilizar `su` para ejecutar comandos como otro usuario distinto, siempre y cuando sepamos la contraseña de ese otro usuario:

```bash
$ whoami
$ su usuario
```

![image-20251002165810334](./Repaso%20de%20Linux%203.assets/image-20251002165810334.png)

Para volver al usuario original basta con utilizar el comando `exit`.

```bash
$ exit
```



### Comando `groups`

Se puede ver a qué grupo pertenecemos.

```bash
$ groups
```

![image-20251002170018709](./Repaso%20de%20Linux%203.assets/image-20251002170018709.png)

Se pueden especificar uno o más usuarios detrás de `groups`. Eso nos dirá a qué grupos pertenece cada uno de ellos.

```bash
$ groups usuario root
```



## Comandos para gestión de grupos (`groupadd`, `groupdel`, `groupmod`)

Los comandos `groupadd`, `groupdel` y `groupmod` permiten crear, borrar y modificar grupos respectivamente.

Vamos a crear los grupos `oficina_malaga`, `oficina_jaen` y `oficina_madrid`:

```bash
$ sudo groupadd oficina_malaga
$ sudo groupadd oficina_jaen
$ sudo groupadd oficina_madrid
```

![image-20251002170529001](./Repaso%20de%20Linux%203.assets/image-20251002170529001.png)

Si se escribiese mal el nombre de un grupo, se puede solucionar con el comando `groupmod`:

```bash
$ sudo groupmod -n oficina_madrit oficina_madrid
```

![image-20251002170802187](./Repaso%20de%20Linux%203.assets/image-20251002170802187.png)

Se puede borrar con `groupdel`:

```bash
$ sudo groupdel oficina_madrit
```

![image-20251002170859310](./Repaso%20de%20Linux%203.assets/image-20251002170859310.png)



## Comandos para gestión de usuarios (`adduser`, `userdel`, `usermod`)

Igual que en la gestión de grupos se exige que los comandos se ejecuten con privilegios de administrador del sistema. Se puede escribir `sudo` antes de cada comando o:

```bash
$ sudo bash
```

Ahora se mostrará un carácter `#`en lugar de `$`. Para volver al usuario inicial se hace con el comando `exit`.

```bash
# adduser pedro --ingroup oficina_malaga
# adduser ana --ingroup oficina_malaga
# adduser berta --ingroup oficina_jaen
# adduser laura --ingroup oficina_malaga
# adduser laura oficina_jaen
```

Se han creado los usuarios y se han incluido dentro de sus grupos correspondientes al mismo tiempo. `Laura`pertenece a dos grupos. Al crear los usuarios se piden las claves, éstas se pueden cambiar con el comando `passwd`:

```bash
# passwd pedro
# passwd ana
# passwd laura
```



## Comandos para cambio de grupo y de dueño (`chown`, `chgrp`)

Tanto `chown` como `chgrp` se pueden usar con la opción `-R` para cambiar el dueño o grupo en un directorio completo, de forma recursiva.



## Cambio de privilegios (comando `chmod`)

Sirve para cambiar los permisos de uno o varios ficheros. Esos permisos se pueden ver con `ls -l`.

```bash
$ chmod +x hola_mundo.rb
```

En la siguiente tabla se muestran de forma esquemática los parámetros del comando `chmod`:

![image-20251002172218158](./Repaso%20de%20Linux%203.assets/image-20251002172218158.png)

Ahora vamos a quitar el permiso de ejecución para el resto de usuarios (others) y daremos permiso de escritura (write) a los usuarios del mismo grupo (group).

```bash
$ chmod o-x hola_mundo.rb
$ chmod g+w hola_mundo.rb
```

A este método, que utiliza los caracteres `rwx` se le denomina método simbólico. Podemos utilizar de forma análoga el método numérico.

<img src="./Repaso%20de%20Linux%203.assets/image-20251002172514734.png" alt="image-20251002172514734" style="zoom:80%;" />

De esta forma, la siguiente línea:

```bash
$ chmod 755 hola_mundo.rb
```

Equivale a estas tres:

```bash
$ chmod u+rwx hola_mundo.rb
$ chmod g+rx-w hola_mundo.rb
$ chmod o+rx-w hola_mundo.rb
```


<div style="page-break-after: always;"></div>
## Ejercicios

1. Completa la siguiente tabla:

   | Método numérico | Método simbólico |
   | --------------- | ---------------- |
   | **654**         | rw-r-xr--        |
   | 766             | **rwxrw-rw-**    |
   | 777             | **rwxrwxrwx**    |
   | **520**         | r-x-w----        |
   | **764**         | rwxrw-r--        |
   | 440             | **r--r-----**    |

   

2. Crea los grupos `oficina1` y `oficina2`.

   ```bash
   $ sudo groupadd oficina1
   $ sudo groupadd oficina2
   ```

   ![image-20251006172834015](./Repaso%20de%20Linux%203.assets/image-20251006172834015.png)

   

3. Crea los usuarios `paco` y `pablo`. Estos usuarios deben pertenecer únicamente al grupo `oficina1`.

   ```bash
   $ sudo useradd -m -g oficina1 paco
   $ sudo useradd -m -g oficina1 pablo
   ```

   ![image-20251006172927684](./Repaso%20de%20Linux%203.assets/image-20251006172927684.png)

   

4. Crea los usuarios `alba` y `nerea`. Estos usuarios deben pertenecer únicamente al grupo `oficina2`.

   ```bash
   $ sudo useradd -m -g oficina2 alba
   $ sudo useradd -m -g oficina2 nerea
   ```

   ![image-20251006173009988](./Repaso%20de%20Linux%203.assets/image-20251006173009988.png)

   

5. Como usuario `paco` crea un fichero con nombre `topsecret.txt` en su directorio de trabajo al que únicamente él tenga acceso, tanto de lectura como de escritura.

   ```bash
   $ su paco
   $ cd
   $ touch top_secret.txt
   $ chmod 600 top_secret.txt
   ```

   

6. Crea otro fichero, también como usuario `paco`, con nombre `ventas_trimestre.txt` al que tengan acceso, tanto para leer como para escribir todos los usuarios que pertenezcan al mismo grupo. Se deben dejar los permisos que haya por defecto para el dueño y para el resto de usuarios. Comprueba como usuario `pablo` que puedes modificar el fichero.

   ```bash
   $ touch ventas_trimestre.txt
   $ chmod g+rw ventas_trimestre.txt
   $ exit
   $ su pablo
   $ vi /home/paco/ventas_trimestre.txt
   ```

   

7. Como usuario `alba`, crea un fichero con nombre `empleados.txt` al que pueda acceder cualquier usuario para leer su contenido, y cualquier usuario del mismo grupo para leer o escribir.

   ```bash
   $ exit
   $ su alba
   $ cd
   $ touch empleados.txt
   $ chmod 664 empleados.txt
   ```

   

8. Copia el fichero `empleados.txt` al directorio de trabajo de `alumno` (crea también el usuario `alumno` si no está creado). Cambia el propietario y el grupo al que pertenece el fichero, ahora debe ser `alumno`.

   ```bash
   $ exit
   $ sudo cp /home/alba/empleados.txt /home/alumno/
   $ sudo chown alumno /home/alumno/empleados.txt
   $ sudo chgrp alumno /home/alumno/empleados.txt
   ```

   
<div style="page-break-after: always;"></div>
11. Como usuario `pablo`, copia un programa del directorio `/usr/bin` al directorio de trabajo con un nombre diferente. Por ejemplo `xclock` se puede copiar como `reloj`. Mira los permisos de este programa. Comprueba que se pueda ejecutar. Puede que sea necesario dar permiso para que otros usuarios distintos al actual puedan ejecutar aplicaciones en el entorno gráfico, basta con ejecutar como administrador: `xhost +`.

    
    
12. Cambia los permisos de `reloj` de tal forma que sólo lo pueda ejecutar el propietario del archivo.

    ```bash
    $ chmod go-x reloj
    ```

    

11. Crea el usuario `modesto`, perteneciente a `oficina2`. Dentro de su directorio de trabajo, crea un directorio de nombre `compartido_con_todos`.

    ```bash
    $ exit
    $ sudo adduser modesto --ingroup oficina2
    $ su modesto
    $ cd
    $ mkdir compartido_con_todos
    ```

    

14. Cambia de usuario en el entorno gráfico (botón **salir** y botón **cambiar de usuario**) y entra como `modesto`. Crea con **OpenOffice.org Calc** los ficheros `telefono_contactos.ods`, `gastos_marzo.ods` y `compartido_con_todos`.

    Se puede acceder al programa **Calc** mediante Aplicaciones -> Oficina -> OpenOffice.org Cal Hoja de cálculo
    
    

15. Da permiso de lectura a la carpeta `compartido_con_todos` y a todos los ficheros que contenga para todos los usuarios.

    ```bash
    $ chmod -R a+r compartido_con_todos
    ```

    

14. Restringe el acceso de escritura sobre el fichero `telefono_contactos` para que sólo lo puedan modificar los usuarios del grupo al que pertenece su propietario.

    ```bash
    $ cd compartido_con_todos
    $ chmod g+w telefono_contactos.ods
    $ chmod o-w telefono_contactos.ods (en realidad esta línea sería redundante)
    ```

    
<div style="page-break-after: always;"></div>
17. Cambia los permisos de `gastos_marzo` para que sólo pueda modificarlo su propietario y leerlo cualquiera del mismo grupo.

    ```bash
    $ chmod 640 gastos_marzo.ods
    ```

    

18. Cambia los permisos de `sueldos` para que sólo su dueño tenga acceso a él, tanto para lectura como para escritura.

    ```bash
    $ chmod 600 sueldos.ods
    ```

    

19. Si un usuario tiene permiso de lectura sobre un fichero pero ese fichero se encuentra dentro de un directorio sobre el que no tiene permiso de lectura, ¿podría leer el fichero?, haz la prueba. 

    No. Un usuario sin privilegios de lectura sobre un directorio no puede acceder a ficheros contenidos en ese directorio, aunque esos ficheros tengan todos los permisos activados.