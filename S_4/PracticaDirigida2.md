## Exploración y administración avanzada de Git mediante un script interactivo

### Preparando recursos antes de iniciar.

Trabajaremos en carpeta `PD2` para realizar la actividad, para ello copiamos el archivo `git_avanzado.sh` brindado en esta practica dirigida al directorio de trabajo y le damos permisos de ejecución con `chmod +x git_avanzado.sh`.

```bash
nano git_avanzado.sh
chmod +x git_avanzado.sh

# Mostramos contenido de repositorio
ls
```
![](pd_img/image.png)

Creamos un repositorio en GitHub, la cual se utilizara en el desarrollo de esta PD.

![](pd_img/image-2.png)

![](pd_img/image-3.png)

Clonamos el repositorio y movemos el archivo `git_avanzado.sh` al directorio del repositorio

![](pd_img/image-4.png)

### Procedimiento de la actividad

1. Inicio del script

    Iniciamos el script con `./git_avanzado.sh`, mostramos evidencia de la ejecución.

    ![](pd_img/image-1.png)

2. Opción: agregar un submódulo (Opción 2)

    Mostramos la realización del flujo que se pide.

    ![](pd_img/image-5.png)

3. Opción: Gestión de ramas (Opción 4)

    ![](pd_img/image-6.png)

4. Opción: Gestión de git diff (Opción 9)

    ![](pd_img/image-7.png)

    Como no se agrego cambios en la rama `feature/login`, no vemos diferencias entre las ramas, para mostrar un ejemplo de la opción 9, agregamos algunos cambios.

    ![](pd_img/image-8.png)

    Ahora volvemos a realizar los pasos y vemos que nos muestra las diferencias entre las dos ramas, `main` y `feature/login`

    ![](pd_img/image-9.png)

5. Opción: Gestión de hooks (Opción 10)

    ![](pd_img/image-10.png)

    Luego de agregar el `hook`, verificamos si se agrego correctamente, agregando un nuevo cambio y generando un nuevo commit.

    ![](pd_img/image-11.png)

    Como se observa en la salida, antes de realizar el commit, ejecuta el hook de pre-commit agregado anteriormente, y como pasa exitosamente, continua con el registro del commit.
