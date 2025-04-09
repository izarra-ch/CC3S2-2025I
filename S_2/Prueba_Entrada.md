# Prueba de entrada

La prueba de entrada consiste en un proyecto completo: Juego de Trivia con FastAPI, PostgreSQL y DevOps.

Esto se realizara por tareas que se realizaran por día, y estos se ira registrando paso a paso.

- Detalles del proyecto: [aquí](https://github.com/kapumota/DS/blob/main/2025-1/Prueba_entrada_CC3S2.md)
- Repositorio del proyecto: [aquí](https://github.com/izarra-ch/trivia-app)

## Seguimiento de tareas:

### day-1

  - Definimos la estructura del proyecto que utilizaremos.

      ```bash
      trivia-app/
      │
      ├── src/
      │   ├── main.py
      │   ├── db.py
      │   └── ...
      ├── venv/
      │
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
      touch src/main.py src/db.py Dockerfile docker-compose.yml README.md

      # creamos el entorno virtual
      python3 -m venv venv

      # activamos entorno virtual
      source venv/bin/active

      # instalamos dependencias
      pip install fastapi uvicorn asyncpg databases

      # generamos un archivo con dependencias exactas
      pip freeze > requirements.txt

      ```
  - Comandos git utilizados

    ```bash
    # Ejecución en el directorio raíz del proyecto
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
    
  - Contenido del Docker file con los pasos asta el momento (Avance).

    ```Dockerfile
    FROM python:3.11-slim

    # Establecer directorio de trabajo
    WORKDIR /src

    # Copiamos el archivos de requerimientos
    COPY requirements.txt .

    # Instalamos las dependencias
    RUN pip install -r requirements.txt

    # Copiar código de aplicación
    COPY src .
    ```
  - Contenido del docker-compose.yaml según lo pedido (Avance).

    ```yaml
    services:
      db:
        image: postgres:15
        environment:
          POSTGRES_USER: admin
          POSTGRES_PASSWORD: admin
          POSTGRES_DB: trivia_db
        ports:
          - "5432:5432"
        volumes:
          - postgres_data:/var/lib/postgresql/data

      web:
        build: .
        ports:
          - "8000:8000"
        environment:
          DATABASE_URL: postgres://admin:admin@db:5432/trivia_db
        depends_on:
          - db

    volumes:
      postgres_data:
    ```