# Prueba de entrada

La prueba de entrada consiste en un proyecto completo: Juego de Trivia con FastAPI, PostgreSQL y DevOps.

Esto se realizara por tareas que se realizaran por día, y se ira registrando paso a paso.

El proyecto consta con una [descripción] detallada de los pasos a seguir, y los avances se irán subiendo al [repositorio] del proyecto.

## Seguimiento de tareas:

### day-1

  **Pull Request**: [feature/day-1]

  - Definimos la estructura del proyecto que utilizaremos.

      ```bash
      trivia-app/
      │
      ├── src/
      │   ├── main.py
      │   ├── db.py
      │   └── ...
      │
      ├── .gitignore
      ├── Dockerfile          
      ├── docker-compose.yml
      ├── requirements.txt
      └── README.md
      ```

  - Comandos utilizados para la creación del proyecto e inicializaron de git.

    ```bash
    # Creamos el directorio del proyecto y navegamos a el
    mkdir trivia-app && cd trivia-app

    # Creamos el directorio que contendrá el app
    mkdir src

    # creamos los archivos iniciales
    touch src/main.py src/db.py Dockerfile docker-compose.yml README.md .gitignore

    # creamos el entorno virtual
    python3 -m venv venv

    # activamos entorno virtual
    source venv/bin/active

    # instalamos dependencias
    pip install fastapi uvicorn asyncpg databases

    # generamos un archivo con dependencias exactas
    pip freeze > requirements.txt

    # Inicializamos repositorio
    git init

    # iniciando commit para el historial
    git add README.md
    git commit -m "inicio de proyecto"

    # Agregamos el repositorio remoto
    git remote add origin url_repositorio_remoto

    # Subimos cambios al repositorio remoto
    git push -u origin master

    # Creamos la rama de trabajo para day-1
    git checkout -b feature/day-1

    # continuamos agregando commits por los cambios realizados
    git add .
    git commit -m "configurando el entorno virtual"

    # repetimos para todos los cambios
    ```
    
  - Contenido de .gitignore para no subir archivos innecesarios al repositorio remoto

    ```bash
    # No se requiere subir la carpeta del entorno virtual por muchas razones
    # Solo es valido en el SO que se creo, ocupa espacio, es fácil de construir
    # Solo requerimos las dependencias instaladas que ya están en requirements.txt
    venv/
    
    # Carpeta creada por python, no es necesario
    **/__pycache__

    # Archivo para manejar las variables de entorno, no se sube por seguridad.
    # Exponer datos sensibles
    .env
    ```

  - Contenido del Docker file con los pasos asta el momento (Avance).

    ```Dockerfile
    FROM python:3.11-slim

    # Establecer directorio de trabajo
    WORKDIR /src

    # Copiamos el archivos de requerimientos
    COPY requirements.txt .

    # Instalación limpia de dependencias
    RUN pip install --no-cache-dir -r requirements.txt

    # Copiar código de aplicación
    COPY ./src ./src

    # Ejecutamos nuestra app
    CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]
    ```

  - Contenido del docker-compose.yaml según lo pedido (Avance).

    ```yaml
    services:
      db:
        image: postgres:15
        container_name: trivia_db
        environment:
          POSTGRES_USER: admin
          POSTGRES_PASSWORD: admin
          POSTGRES_DB: trivia
        ports:
          - "9000:5432"
        volumes:
          - postgres_data:/var/lib/postgresql/data

      web:
        build: .
        container_name: trivia_app
        ports:
          - "8000:8000"
        # Garantiza que primero se construya el contenedor de DB
        depends_on:
          - db

    volumes:
      postgres_data:
    ```

  - Contenido de main.py para ejecutar el servidor y poder corroborar que app se ejecuta

    ```python
    from fastapi import FastAPI

    app = FastAPI()

    # endpoint raíz para comprobar que el servicio este ejecutando
    @app.get('/')
    def home():
      return {"server": "Servidor iniciado"}

    ```

    Para ejecutar el app lo hacemos con el comando `uvicorn src.main:app`, utilizando el entorno virtual.

    Otra manera es utilizar docker compose, lo hacemos con el comando `docker compose up`, no es necesario el entorno virtual.

  - evidencia para ejecutar la aplicación con docker compose
    
    Ejecutado el comando de `docker compose up`

    ![](img/prueba1.png)

    Verificando que los contenedores se estén ejecutando, con el comando `docker ps`

    ![](img/prueba2.png)

    Verificamos desde un navegador que la aplicación este funcionando

    ![](img/prueba3.png)



[feature/day-1]: https://github.com/izarra-ch/trivia-app/pull/1
[Descripción]: Enunciado_Prueba_Entrada
[repositorio]: https://github.com/izarra-ch/trivia-app