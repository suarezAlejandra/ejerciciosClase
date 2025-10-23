# 01 - EJERCICIO DE GIT - FORTY - LOCAL Y REMOTO

[TOC]



## TRABAJO EN LOCAL

1. Inicializa un nuevo repositorio Git en una carpeta llamada `"forty"` y agrega los archivos proporcionados en el aula virtual.

   ```bash
   # Inicializar
   git init
   
   # Agregar archivos
   git add .
   ```

   ![image-20251016172321539](./Ejercicio%20Git%20-%20Forty.assets/image-20251016172321539.png)

   
<div style="page-break-after: always;"></div>
2. Renombra la rama master a `main`

   En mi caso la rama ya estaba nombrada como `main`:

   ![image-20251016172358707](./Ejercicio%20Git%20-%20Forty.assets/image-20251016172358707.png)

   Si no, se haría de la siguiente forma:

   ```bash
   git branch -M master main
   ```

   

3. Haz que los ficheros `README.txt`, `LICENSE.txt` y `passwords.txt` sean ignorados por el control de versiones.

   ```bash
   notepad .gitignore
   git add .gitignore
   git rm --cached README.txt
   git rm --cached LICENSE.txt
   git ls-files --others -i --exclude-standard
   git commit -m "confirmación ignorar README y LICENSE"
   ```

   ![image-20251016174854683](./Ejercicio%20Git%20-%20Forty.assets/image-20251016174854683.png)

   
<div style="page-break-after: always;"></div>
4. Crea el archivo `passwords.txt`. Comprueba que el control de versiones lo ignora.

   ```bash
   # Crear archivos 
   touch passwords.txt
   
   # Comprobar que el control de versiones lo ignora
   git ls-files --others -i --exclude-standard
   ```

   ![image-20251016175115312](./Ejercicio%20Git%20-%20Forty.assets/image-20251016175115312.png)

   

5. Crea una rama llamada `"feature-content"`. Muévete a esa rama. Cambia, en la línea 3477, el `font-size` por `1.5em` en el archivo `main.css`. Ver los logs de la forma más gráfica posible.

   ```bash
   # Crear rama 
   git branch feature-content
   
   # Moverse a la rama
   git checkout feature-content
   ```

   ![image-20251016175449428](./Ejercicio%20Git%20-%20Forty.assets/image-20251016175449428.png)

   Cambiamos `font-size`:

   ![image-20251016175727549](./Ejercicio%20Git%20-%20Forty.assets/image-20251016175727549.png)

   ```bash
   # Añadir cambios y hacer commit
   git add .
   git commit -m "cambiado font-size a 1.5em en línea 3477 de main.css"
   
   # Ver logs
   git log --onleine --graph --all --decorate
   ```

   ![image-20251016180027691](./Ejercicio%20Git%20-%20Forty.assets/image-20251016180027691.png)

   

6. Elimina el archivo llamado `"passwords.html"` en la carpeta `forty`. Verifica el estado del repositorio. ¿Hay cambios pendientes?

   ```bash
   # Eliminar archivo
   rm passwords.txt
   
   # Verificar estado del repositorio
   git status
   ```

   ![image-20251016180611143](./Ejercicio%20Git%20-%20Forty.assets/image-20251016180611143.png)

   No, no hay cambios pendientes.

   
<div style="page-break-after: always;"></div>
7. Crea un nuevo archivo llamado `"about.html"`, partiendo del archivo `generic.html` y agrégalo al repositorio.

   ```bash
   # Crear archivo partiendo de generic.html
   cp generic.html about.html
   
   # Agregarlo al repositorio y hacer commit
   git add about.html
   git commit -m "añadido about.html creado partiendo de generic.html"
   ```

   ![image-20251016181320368](./Ejercicio%20Git%20-%20Forty.assets/image-20251016181320368.png)

   

8. Cambia a la rama `main`. Examina los logs del repositorio de forma gráfica.

   ```bash
   # Cambiar a rama main
   git checkout main
   
   # Examinar logs
   git log --oneline --graph --all --decorate
   ```

   ![image-20251016181450958](./Ejercicio%20Git%20-%20Forty.assets/image-20251016181450958.png)

   
<div style="page-break-after: always;"></div>
9. Modifica algo en el archivo `generic.html`, comprueba que hay cambios, y realiza otro commit. Examina los logs del repositorio de forma gráfica.

   ```bash
   # Comprobar cambios
   git status
   
   # Añadir cambios y hacer commit
   git add .
   git commit -m "modificado archivo generic.html"
   
   # Examinra logs
   git log --oneline --graph --all --decorate
   ```

   ![image-20251016181714825](./Ejercicio%20Git%20-%20Forty.assets/image-20251016181714825.png)

   
<div style="page-break-after: always;"></div>
10. Modifica algo en el fichero `elements.html`. Confirma los cambios, pero no hagas commit.

    ```bash
    git add .
    ```

    ![image-20251016181841147](./Ejercicio%20Git%20-%20Forty.assets/image-20251016181841147.png)

    

11. Mira las diferencias de `elements.html`. Los cambios no nos gustan, deshaz los cambios de `elements.html`. Comprueba que no hay cambios pendientes.

    ```bash
    # Comprobar diferencias
    git diff --staged elements.html
    
    # Deshacer cambios
    git restore elements.html
    
    # Comprobar estado
    git status
    ```

    ![image-20251016182117559](./Ejercicio%20Git%20-%20Forty.assets/image-20251016182117559.png)

    
<div style="page-break-after: always;"></div>
12. Muestra las diferencias entre la rama actual y la rama principal.

    ```bash
    git diff feature-content
    ```

    ![image-20251016182230100](./Ejercicio%20Git%20-%20Forty.assets/image-20251016182230100.png)

    

13. Fusiona la rama `"feature-content"` con la rama principal (main). Muestra los logs del repositorio de una forma gráfica y completa.

    ```bash
    # Fusionar rama main y feature-content
    git merge feature-content
    
    # Mostrar logs
    git log --oneline --graph --all --decorate
    ```

    ![image-20251016182603088](./Ejercicio%20Git%20-%20Forty.assets/image-20251016182603088.png)

    
<div style="page-break-after: always;"></div>
14. Crea una nueva rama llamada `"hotfix"` y en ella, corrige un error crítico en el archivo `"index.html"`. (Por ejemplo, añade el enlace a la nueva página *about.html*).

    ```bash
    # Crear rama y moverse a ella
    git branch hotfix
    git checkout hotfix
    ```

    ![image-20251016182734650](./Ejercicio%20Git%20-%20Forty.assets/image-20251016182734650.png)

    

15. Fusiona la rama `"hotfix"`con la rama principal y verifica el historial de commits de forma que se vean todas las ramas gráficamente. ¿Borrarías la rama `hotfix`? ¿En qué caso? ¿Cómo?

    ```bash
    # Moverse a rama main y fusionar con hotfix
    git checkout main
    git merge hotfix
    git log --oneline --graph --all --decorate
    ```

    ![image-20251016182929674](./Ejercicio%20Git%20-%20Forty.assets/image-20251016182929674.png)

    
<div style="page-break-after: always;"></div>
16. Muestra el historial de cambios limitado a los últimos 3 commits.

    ```bash
    git log -3
    ```

    ![image-20251016183007019](./Ejercicio%20Git%20-%20Forty.assets/image-20251016183007019.png)

    

17. Etiqueta el commit actual como "v1.0" y muestra las etiquetas existentes.

    ```bash
    # Etiquetar commit 
    git tag v1.0
    
    # Mostrar etiquetas existentes
    git tag
    ```
    
    ![image-20251016183101572](./Ejercicio%20Git%20-%20Forty.assets/image-20251016183101572.png)


<div style="page-break-after: always;"></div>
## TRABAJO EN REMOTO

1. Sube al remoto los ficheros de tu repositorio local. (Es necesario crear previamente en GitHub un repositorio llamado Forty. NO crear archivo README.md en el remoto)

   ![image-20251020165740605](./Ejercicio%20Git%20-%20Forty.assets/image-20251020165740605.png)

   ```bash
   # Subir al repositorio remoto los ficheros del repositorio local
   git remote add origin https://github.com/suarezAlejandra/forty.git
   git branch -M main
   git push -u origin main
   ```

   ![image-20251020170013681](./Ejercicio%20Git%20-%20Forty.assets/image-20251020170013681.png)

   

2. En local, crea una rama `feature-head`. Cambia el título en la sección `head` de `index.html`, borra los comentarios del `head`, o previos, también. Confirma y sube los cambios al remoto.

   ```bash
   # Crear rama feature-head y moverse a ella
   git branch feature-head
   git checkout feature-head
   
   # Añadir cambios y hacer commit
   git add .
   git commit -m "actualizado título del head de index.html"
   
   # Subir cambios al repositorio remoto
   git push -u origin feature-head
   ```

   ![image-20251020171459622](./Ejercicio%20Git%20-%20Forty.assets/image-20251020171459622.png)

   ![image-20251020171546635](./Ejercicio%20Git%20-%20Forty.assets/image-20251020171546635.png)

   

3. En ***remoto***, crea una rama `feature-articulo`. Duplica la página `generic`, nómbrala como `articulo.html`, y añade como contenido un artículo sobre Git. Confirma los cambios y realiza un commit. Muestra los commits del repositorio tal como se ven en GitHub.

   **CREAR RAMA:**

   ![image-20251020171732013](./Ejercicio%20Git%20-%20Forty.assets/image-20251020171732013.png)
<div style="page-break-after: always;"></div>
   **DUPLICAR PÁGINA generic, NOMBRARLA COMO articulo.html Y AÑADIR CONTENIDO:**

   ![image-20251020173534067](./Ejercicio%20Git%20-%20Forty.assets/image-20251020173534067.png)
<div style="page-break-after: always;"></div>
   **CONFIRMAR CAMBIOS Y REALIZAR COMMIT:**

   <img src="./Ejercicio%20Git%20-%20Forty.assets/image-20251020173642792.png" alt="image-20251020173642792" style="zoom:50%;" />

   **MOSTRAR COMMITS:**

![image-20251020173912698](./Ejercicio%20Git%20-%20Forty.assets/image-20251020173912698.png)


<div style="page-break-after: always;"></div>
4. En el repositorio local examina los cambios. Actualiza el repositorio con el remoto. Fusiona en `main` las dos ramas `feature`. Crea la etiqueta `v2.0`. Muestra los logs, commits, etiquetas y ramas actuales, en local y en remoto.

   ```bash
   # Examinar cambios
   git status
   
   # Actualizar repositorio con el remoto
   git fetch origin
   git checkout -b feature-articulo origin/feature-articulo
   git pull
   
   # Fusionar en main las 2 ramas feature
   git checkout main
   git merge feature-head
   git merge feature-articulo
   
   # Crear etiqueta v2.0
   git tag v2.0
   
   # Mostrar logs, commits y ramas actuales
   git log --oneline --graph --all --decorate
   ```

   ![image-20251020175004346](./Ejercicio%20Git%20-%20Forty.assets/image-20251020175004346.png)

   ![image-20251020175050585](./Ejercicio%20Git%20-%20Forty.assets/image-20251020175050585.png)

   
<div style="page-break-after: always;"></div>
5. En tu copia local, crea una rama `nueva`. En la rama nueva, cambia los enlaces de la página `index.html` para que apunten correctamente a la nueva página `articulo.html`. Confirma los cambios.

   ```bash
   # Crear rama y moverse a ella
   git checkout -b nueva
   ```

   ![image-20251020175219595](./Ejercicio%20Git%20-%20Forty.assets/image-20251020175219595.png)

   **CAMBIAR ENLACES:**

   ![image-20251020175416212](./Ejercicio%20Git%20-%20Forty.assets/image-20251020175416212.png)

   ```bash
   # Confirmar cambios
   git add .
   git commit -m "creada rama nueva y añadidos cambios a index.html"
   ```

   ![image-20251020175717382](./Ejercicio%20Git%20-%20Forty.assets/image-20251020175717382.png)

   
<div style="page-break-after: always;"></div>
6. Muestra los logs de forma que se vean las ramas en tu copia local.

   ```bash
   git log --oneline --graph --all --decorate
   ```

   ![image-20251020175809047](./Ejercicio%20Git%20-%20Forty.assets/image-20251020175809047.png)

   

7. Te gusta el resultado de los cambios. Incorpora los cambios de la rama nueva a la principal.

   ```bash
   git checkout main
   git merge nueva
   ```

   ![image-20251020180357788](./Ejercicio%20Git%20-%20Forty.assets/image-20251020180357788.png)

   
<div style="page-break-after: always;"></div>
8. Sube los cambios al remoto borrando la rama `nueva`, si es necesario. Comprueba primero con un comando en local, las ramas que hay en el repositorio remoto.

   ```bash
   # Comprobar ramas en remoto
   git branch -r
   
   # Subir cambios al remoto y borrar rama nueva
   git push -u origin
   git branch -d nueva
   ```

   ![image-20251020180924399](./Ejercicio%20Git%20-%20Forty.assets/image-20251020180924399.png)

   ![image-20251020180709586](./Ejercicio%20Git%20-%20Forty.assets/image-20251020180709586.png)

   

9. Muestra en local los cambios en el archivo `index.html` entre la versión actual y la anterior.

   ```bash
   git diff index.html
   ```

   
<div style="page-break-after: always;"></div>
10. En el repositorio en GitHub, navega hasta el archivo `index.html` y selecciona la opción `History`.

    ![image-20251020181227597](./Ejercicio%20Git%20-%20Forty.assets/image-20251020181227597.png)