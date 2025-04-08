## Actividad 02 

Del código a la producción: Infraestructura, contenedores, despliegue y observabilidad

### Parte 1

#### A. Infraestructura como Código
1. __Introducción a IaC__

    - __Definición:__ Explicar qué es IaC y por qué es un cambio de paradigma frente a la configuración manual.

      IaC es un enfoque para gestionar y configurar infraestructuras de TI mediante reglas en código, en lugar de configuraciones manuales, gracias a esto podemos tener un archivo de configuración, en el definimos las configuraciones, con esto podemos reproducirse la infraestructura en distintos entornos (desarrollo, pruebas, producción), siguiendo ciertos principios fundamentales, _Reproducibilidad_, _Idempotencia_, _Composabilidad_ y _Evolución controlada_, Los beneficios de estos son;consistencia en la configuración, control de versiones, automatización y reducción de errores humanos.

      Y es un cambio de paradigma, debido a que modifica la gestión y administración de las infraestructuras de TI que se hacia de forma manual.

2. __Escritura de IaC__

    - __Herramientas populares:__ Nombrar algunas como Terraform, Ansible, Pulumi o AWS CloudFormation.

      otras herramientas que no se mencionan en la lista son:

      - Chef:  Utiliza __Ruby DSL__ para definir configuraciones, es un modelo cliente-servidor, donde un "Chef Server" almacena configuraciones y los nodos las descargan.
      - Puppet: Usa su propio lenguaje __Puppet DSL__ basado en Ruby, es un modelo cliente-servidor, donde los "Puppet Agents" se conectan a un "Puppet Master".
      - SaltStack: Usa YAML y Jinja2 para definir configuraciones, 
      - Google Cloud Deployment Manager: IaC específico para Google Cloud Platform (GCP), es una modelo Declarativo que usa YAML, Python o Jinja2 para definir plantillas, estas permiten definir infraestructura en archivos de configuración y desplegarla automáticamente en GCP.

3. __Patrones para módulos__

    - Modularización: Separar los recursos en módulos lógicos (por ejemplo, redes, bases de datos, servidores de aplicaciones) para facilitar la reutilización.

    - Estructura: Mostrar ejemplos de cómo se organizan los módulos en carpetas y archivos.

4. __Patrones para dependencias__

    - Gestión de dependencias: Cómo enlazar módulos que se relacionan (por ejemplo, un módulo de base de datos que debe suministrar credenciales a un módulo de aplicación).

    - Outputs y inputs: Uso de salidas (outputs) en un módulo para alimentarlos como entradas (inputs) en otro módulo.

#### B. Contenerización y despliegue de aplicaciones modernas

1. __Contenerización de una aplicación con Docker__

    - __¿Qué son los contenedores?:__ Diferencia con máquinas virtuales (VMs), aislamiento de procesos y ligereza.

      Los contenedores son un forma de virtualizar capas de software, en las cuales podemos empaquetados software con todas las dependencias necesario para ejecutarlo, estas dependencias incluyen elementos como bibliotecas del sistema, paquetes de código externos de terceros y otras aplicaciones a nivel del sistema operativo.
      
      La diferencia con las maquinas virtuales, es que el contenedor virtualiza solo la capa de software mientras que la MV virtualiza todo una maquina, es decir, capa de software y hardware.

      Esto hace que el contenedor sean más ligeros y portátiles, con una sobrecarga significativamente menor y cada contenedor se ejecuta en su propio entorno, como si estuvieran solos,  pero comparten los recursos del host anfitrión.

    
    - __Dockerfile:__ Estructura básica de un Dockerfile (FROM, RUN, CMD/ENTRYPOINT, etc.).
      
      Un dockerfile es un archivo que contiene las instrucciones para la creación de una imagen de Docker, un ejemplo de ello:

      ```Dockerfile
      # Imagen base de Node.js
      FROM node:18

      # variables de entorno disponibles en tiempo de ejecución
      ENV NODE_ENV=production \
          AP_VERSION=1.0.0

      # Establece el directorio de trabajo dentro del contenedor
      WORKDIR /app

      # Copia archivos que empiecen con package y terminen con .json
      COPY package*.json ./

      # Instala las dependencias
      RUN npm install

      # Copia el resto del código de la aplicación
      COPY . .

      # Expone el puerto en el que corre la app (por ejemplo, 3000)
      EXPOSE 3000

      # Comando para ejecutar la app
      CMD ["npm", "start"]

      ```

    - __Imagen vs Contenedor:__ Diferencias y uso en entornos de desarrollo y producción.

      Una Imagen es un archivo donde están todo lo necesario para que una aplicación funciones, código, librerías, configuraciones, instrucciones, etc.

      Mientras que el Contenedor es una instancia de ejecución de la imagen.

      Esto dos ayudan en entornos de desarrollo y producción ya que podemos tener una imagen actualizada en cualquier momento con los cambios realizados, y ejecutar dichas imágenes con ayuda de contenedores, y en producción, tener imágenes versionadas para la ejecución de una version en especifica si es necesario.


2. __Orquestación con Kubernetes__

    - __Introducción a Kubernetes:__ Explicar los componentes principales (pods, services, deployments, replica sets).

      Kubernetes organiza los contenedores en unidades llamadas Pods, que pueden estar compuestos por uno o varios contenedores, y se gestiona a través de recursos como ReplicaSets y Deployments, explicamos los componentes principales puntos.

      - **Pods**: Son la unidad mínima de despliegue encapsulando uno o varios contenedores que comparten red y almacenamiento.
      - **Service**: Expone los Pods para la comunicación entre Pods y el acceso desde fuera 
      - **Deployment**: Define cómo se despliegan y actualizan los Pods, permiten realizar rollbacks si es necesario, gestionando versiones de la aplicación de forma declarativa.
      - **ReplicaSet**: Garantiza el número de Pods correctos estén en ejecución, para esto crea o elimina los Pods.

    - __Manifiestos en YAML:__ Presentar la estructura básica (apiVersion, kind, metadata, spec) y los campos más relevantes (replicas, selector, template).

      Mostramos el ejemplo que se da en *Lectura2*, un archivo YAML para definir un Deployment de una aplicación basada en Nginx 

      ```yaml
      # Version del recurso
      apiVersion: apps/v1
      # Tipo de recurso, Deployment, Service, Pod, etc.
      kind: Deployment
      # Información identificadora del recurso
      metadata:
        name: mi-deployment
      # Configuración del recurso
      spec:
        # numero de replicas (Pods)
        replicas: 3
        # Método de selección de Pods del recurso
        selector:
          matchLabels:
            app: mi-app
        # Describe cómo deben ser los Pods que se crearán
        template:
          metadata:
            labels:
              app: mi-app
          spec:
            # Lista de contenedores que se ejecutarán
            containers:
            - name: contenedor-web
              image: nginx:latest
      ```

    - __Estrategias de despliegue en Kubernetes:__ Rolling Updates, Canary Releases, Blue-Green Deployments.

      - **Rolling Updates** (default): Kubernetes reemplaza Pods gradualmente, las versiones antiguas del Pods por las nuevas, esto lo hace apagando Pods viejos y encendiendo nuevos, asta completar la actualización, en este proceso hay disponibilidad del servicio.
      - **Canary Releases**: Conocido como lanzamiento tipo Canario, despliega una versión nueva a un subconjunto de usuarios para pruebas, mientras que el resto de usuarios sigue usando la version anterior.
      - **Blue-Green Deployments**: Mantiene dos entornos paralelos, uno activo (Blue), otro en espera (Green), esto para cuando estén listo los cambios, podamos cambiar el trafico a la nueva version, y si algo falla, podemos volver al la version anterior aun disponibles.

3. __Desplegando código__

    - __Ciclo de vida del despliegue:__ Desarrollo → Build → Test → Deploy.

      - **Desarrollo**: Fase en la cual se escribe el código de la aplicación, se hacen cambios, mejoras o se agregan nuevas funcionalidades, ejemplo: registra los cambios utilizando git.
      - **Build**: Fase en la cual, a partir del código listo, se construye la imagen de Docker como una nueva version de la aplicación, ejemplo: build de Dockerfile para nueva version.
      - **Test**: Se ejecutar pruebas en entornos similar a producción, ademas de realizar pruebas de funcionalidades especificas, de integración, de rendimiento, etc. para asegurar el correcto funcionamiento, ejemplo: utilizar docker compose para ejecutar el test en un ambiente de pruebas.
      - **Deploy**: Pase a ambiente productivo, ejemplo: Actualizar el deployment en Kubernetes.


    - __Herramientas:__ Explicar brevemente cómo Docker y Kubernetes se integran en pipelines de despliegue continuo.

      Con la herramienta de Docker lo que realizamos es tomar el código (nuevo) de nuestra aplicación, con esto tenemos una imagen listo empaquetado; Kubernetes, toma esta imagen y se encarga del despliegue y gestionar la imagen según lo declarado en el manifiesto (archivo yaml), y todo este flujo, viene a ser el pipeline para el despliegue continuo, que se configura en git por ejemplo para que cuando ingrese un nuevo cambio se dispare todo el flujo.


#### C. Observabilidad y Troubleshooting

1. __Concepto de observabilidad__
    
    La observabilidad tiene como pilar el monitoreo, logging y trazabilidad, con los cuales podemos detectar problemas posibles de la aplicación que podrían afectar al cliente.

2. __Herramientas clave__

    Para implementar la observabilidad se utilizan ciertas herramientas clave como son las mencionadas:

    - __Prometheus:__ Recolección de métricas (CPU, memoria, peticiones HTTP, etc.) y lenguaje de consultas (PromQL).
    
    - __Grafana:__ Visualización de métricas, paneles personalizados, alertas.

    __Otros sistemas:__ Otros a mencionar son ELK (ElasticSearch, Logstash, Kibana) para logs, Jaeger para trazas distribuidas, etc.

3. __Estrategias de troubleshooting__

    Se refiere a los métodos que se utilizan para encontrar posibles problemas y sus causas, para poder solucionarlos de forma efectiva.

    - __Triage de problemas:__ Uso de dashboards y alertas.

    - __Diagnóstico:__ Revisión de logs, métricas en tiempo real, correlación de sucesos.

    - __Resolución:__ Rollback a una versión estable, escalado manual, cambios en la configuración de infraestructura.

#### D. CI/CD (Integración continua / Despliegue continuo)

1. __Conceptos fundamentales__

    - __Integración continua (CI):__ Automatizar la construcción y pruebas de la aplicación con cada commit.
    - __Despliegue continuo (CD):__ Entregar automáticamente las nuevas versiones a entornos de prueba o producción una vez pasen las pruebas.
    - __Herramientas:__ Jenkins, GitLab CI, GitHub Actions, CircleCI, etc.

3. __Diseñando un pipeline__

    - __Fases:__ Build, Test, Análisis de calidad (lint, coverage, security scans), Deploy.
    - __Jobs y Stages:__ Cómo agrupar tareas, en qué orden deben ejecutarse.
    - __Manejo de entornos:__ Dev, Staging, Producción.