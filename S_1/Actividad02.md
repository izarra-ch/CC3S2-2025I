## Actividad 02 

Del código a la producción: Infraestructura, contenedores, despliegue y observabilidad

### Parte 1

#### A. Infraestructura como Código
1. __Introducción a IaC__

    - __Definición:__ Explicar qué es IaC y por qué es un cambio de paradigma frente a la configuración manual.

    - __Beneficios:__ Consistencia en la configuración, control de versiones, automatización y reducción de errores humanos.
2. __Escritura de IaC__

    - __Herramientas populares:__ Nombrar algunas como Terraform, Ansible, Pulumi o AWS CloudFormation.

    - __Buenas prácticas:__ Nombres claros de recursos, uso de variables, modularización del código, uso de repositorios de control de versiones (Git).

3. __Patrones para módulos__

    - Modularización: Separar los recursos en módulos lógicos (por ejemplo, redes, bases de datos, servidores de aplicaciones) para facilitar la reutilización.

    - Estructura: Mostrar ejemplos de cómo se organizan los módulos en carpetas y archivos.

4. __Patrones para dependencias__

    - Gestión de dependencias: Cómo enlazar módulos que se relacionan (por ejemplo, un módulo de base de datos que debe suministrar credenciales a un módulo de aplicación).

    - Outputs y inputs: Uso de salidas (outputs) en un módulo para alimentarlos como entradas (inputs) en otro módulo.

#### B. Contenerización y despliegue de aplicaciones modernas

1. __Contenerización de una aplicación con Docker__

    - __¿Qué son los contenedores?:__ Diferencia con máquinas virtuales (VMs), aislamiento de procesos y ligereza.
    
    - __Dockerfile:__ Estructura básica de un Dockerfile (FROM, RUN, CMD/ENTRYPOINT, etc.).
    - __Imagen vs Contenedor:__ Diferencias y uso en entornos de desarrollo y producción.

2. __Orquestación con Kubernetes__

    - __Introducción a Kubernetes:__ Explicar los componentes principales (pods, services, deployments, replica sets).

    - __Manifiestos en YAML:__ Presentar la estructura básica (apiVersion, kind, metadata, spec) y los campos más relevantes (replicas, selector, template).

    - __Estrategias de despliegue en Kubernetes:__ Rolling Updates, Canary Releases, Blue-Green Deployments.

3. __Desplegando código__

    - __Ciclo de vida del despliegue:__ Desarrollo → Build → Test → Deploy.

    - __Herramientas:__ Explicar brevemente cómo Docker y Kubernetes se integran en pipelines de despliegue continuo.


#### C. Observabilidad y Troubleshooting

1. __Concepto de observabilidad__

    - __Más allá del monitoreo:__ Logs, métricas, trazas.
    
    - __Ventajas:__ Detección temprana de errores, optimización de recursos, insights de negocio.

2. __Herramientas clave__

    - __Prometheus:__ Recolección de métricas (CPU, memoria, peticiones HTTP, etc.) y lenguaje de consultas (PromQL).
    
    - __Grafana:__ Visualización de métricas, paneles personalizados, alertas.

    __Otros sistemas:__ ELK (ElasticSearch, Logstash, Kibana) para logs, Jaeger para trazas distribuidas, etc.

3. __Estrategias de troubleshooting__

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

    __Manejo de entornos:__ Dev, Staging, Producción.