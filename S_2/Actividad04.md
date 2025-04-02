### Git

1. Configuramos git con el comando `git config`

    ```bash
    git config --global user.name "Elmer Izarra"
    git config --global user.email "eizarrac@uni.pe"
    git config --global user.username "izarra-ch"
    ```

2. Mostramos la configuración hecha con el comando `git config --list`

    ![alt text](image.png)

3. Creamos un nuevo repositorio en git, de manera local con el comando `git init`, esto se puede realizar de dos maneras:

    ```
    // crear una carpeta, moverse al directorio e iniciar git
    mkdir my-repositorio && cd my-repositorio && git init

    // crear el repositorio directamente
    git init my-repositorio
    ```

    ![alt text](image-1.png)

4. Agregamos nuestor primer archivo al repositorio, podemos realizarlo utilizando un editor de texto o utilizar la consola para ello, en este caso lo realizamos por consola utilizando `nano`.

    ```bash
    nano README.md
    ```

    ![alt text](image-2.png)

5. Como README.md es un nuevo archivo para git, utilizamos `git state` para visualizar, como lo reconoce.

    ![alt text](image-3.png)

6. Para el archivo aun no esta rastreado por git, utilizamos el comando `git add` para que el archivo este en un estado rastreado para git.

    ![alt text](image-4.png)

7. Como el archivo ya esta preparado(staged), necesitamos registrar estos cambios (confirmar cambios), para esto utilizamos el comando `git commit -m "message"`, al ejecutar el comando, los cambios ya estan confirmado, y al utilizar `git status`, ya no tengremos cambios a rastrear, y si queremos her el commit registrado, utilizamos el comando `git log`, esto nos muestra el historial de commits ralizados.

    ![alt text](image-5.png)

