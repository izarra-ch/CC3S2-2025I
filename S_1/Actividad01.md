## Actividad 01

  Introducción a DevOps

### Parte 1

1. __Lectura y reflexión__

    Análisis sobre lectura proporcionada (Lectura 1):

    - __¿Que es DevOps?__

      Es una metodología integral que agrupan equipos de desarrollo (desarrollo, QA, operaciones) para un proceso colaborativo continuo entre los equipos, con la finalidad de agilizar el ciclo de desarrollo y acortar los ciclos de entrega de software.

    - __Historia y antecedentes de DevOps__

      Los antecedentes de DevOps surge cuando se busca resolver las desventajas del proceso de desarrollo de software tradicional, en la cual cada equipo trabajaba de forma individual, esto genera una mala comunicación entre los equipos y también generaba conflictos sobre la responsabilidad de cada equipo cuando surgía algún problema; todo estos hacia que los tiempos de desarrollo y entrega sean extensos

    - __Diferencias entre los equipos de desarrollo y operaciones en el pasado.__

      La diferencia radica que el primero, es el encarga del proceso de desarrollo del software, mientras qué operaciones, se encargue de la infraestructura, despliegue, monitoreo y mantenimiento del software.

    - __Principios fundamentales de DevOps__

      Enfocando al cliente, DevOps toma decisiones con base en los requerimientos del cliente, y tiene como objetivo entregar software alineado a sus necesidades y de calidad de manera rápida.

      Enfocado a automatización, DevOps permite reducir errores humanos, acelerar pruebas y despliegues automatizado proceso como CI/CD, pruebas, alertas y otros.

    - __Qué NO es DevOps__

      DevOps no es solo una herramienta, no solo es una cultura y no solo es un proceso, es decir que DevOps es todo el conjunto.

2. __Preguntas de reflexión__

    Respondiendo las preguntas con base en la lectura

    1. __¿Por qué surgió la necesidad de DevOps en el desarrollo de software?__

        Como ya se menciono, el desarrollo convencional consistía en 3 grupos principales, equipo de desarrollo, equipo QA y equipo de operaciones, cada uno trabajando de manera separada, este tipo de desarrollo de software, era ineficiente por diversas razones (que ya se menciono anteriormente), por ello requerían de un tiempo prolongado para que el software pase por cada equipo antes de ser entregado, y podría haber errores cometidos por los equipos y no tener software de alta calidad. Para solucionar esto, surge DevOps con la cual se agiliza todos los procesos del desarrollo, garantizando calidad del código, estabilidad del software y evitando aislamiento de los equipos en el desarrollo.

    2. __Explica cómo la falta de comunicación y coordinación entre los equipos de desarrollo y operaciones en el pasado llevó a la creación de DevOps.__

        Como los equipos no tenían una comunicación efectiva, cada equipo trabaja bajo sus propias normas, por ello cuando el software pasaba por cada equipo, estos no estaban debidamente preparados para realizar su trabajo sobre el software, y esto genera mas costo de desarrollo, tiempo y no garantiza la calidad del producto, mencionamos un ejemplo de esto:

        El equipo de desarrollo, entrega código sin considerar la infraestructura de producción, utilizan una versión distinta a la que esta en producción (version de NodeJS), por lo cual tienen utilizando módulos compatibles con la versión utilizado, al entregarse a operaciones, estos podrían tener problemas al pasar a producción, ya que hay incompatibilidad de versiones, o simplemente paso a producción sim problemas, pero luego surge problemas con los módulos incompatibles con la version de herramientas utilizados (version de node), y todo esto trae el problema de responsabilidades entre los equipos, por ello el surgimiento de DevOps. 

    3. __Describe cómo el principio de mejora continua impacta tanto en los aspectos técnicos como en los culturales de una organización.__

        En la parte técnica, optimiza procesos de entrega, monitoreo de métricas clave, estandarización de procesos y incrementa calidad de software .

        En la parte organizacional, fomenta la comunicación y colaboración, esto impulsa el aprendizaje en la organización

    4. __¿Qué significa que DevOps no se trata solo de herramientas, individuos o procesos?__

      Como ya se menciono, DevOps es el conjunto de cultura, herramientas y procesos, ya que no solo es utilizar herramientas o tener un cambio organizacional a nivel de cultura o procesos, sino es la combinación de todos ellos.

    5. __Según el texto, ¿cómo contribuyen los equipos autónomos y multifuncionales a una implementación exitosa de DevOps?__

      Los equipos autónomos y multifuncionales elimina la barrera que existen entre los equipos, ya que tenemos individuos con distintas habilidades reduce la dependencia en los equipos, y se trabaja de manera mas integral involucrándose en todo el proceso de desarrollo de software, ademas esto hace que el personal de cada equipo colabore con los demás y se de el intercambio de conocimiento y resolución conjunta de problemas que surjan. 

### Parte 2

1. __Lectura y análisis__

    Análisis sobre lectura proporcionada (Lectura 2):

    - __DevSecOps:__ Integración de la seguridad en el ciclo de vida del desarrollo.

      DevSecOps integrar herramientas y prácticas de seguridad desde el inicio del desarrollo de software, por ello integra a un nuevo equipo a los que ya conocíamos anteriormente, este equipo es el de _seguridad_.

    - Infraestructura como Código (IaC): Automatización y gestión de infraestructura mediante código.

      Consiste en la idea de que la infraestructura debe reproducirse en distintos entornos (desarrollo, pruebas, producción), siguiendo ciertos principios fundamentales.
      
      - __Reproducibilidad:__ Definir la infraestructura mediante archivos de configuración, con esto tenemos entorno idéntico en distintos contextos, eliminando discrepancias que surgen de configuraciones manuales.
      - __Idempotencia:__ Aseguran que ejecutar múltiples veces el mismo código no generará cambios adicionales si el estado del sistema ya coincide con la configuración declarada.
      - __Composabilidad:__ La infraestructura se descompone en módulos o componentes reutilizables que pueden ensamblarse de forma flexible para crear arquitecturas más complejas, facilitando la gestión y el escalado.
      - __Evolución controlada:__ versionar cada cambio en los archivos de configuración permite llevar un historial preciso de las modificaciones, facilitando rollbacks y auditorías.

    - Observabilidad: Un enfoque avanzado para monitorear y comprender el estado de los sistemas.

      La observabilidad combina tres pilares principales:
        - __Monitoreo:__ La recolección de métricas del sistema (uso de CPU, memoria, latencia de respuestas, tasa de errores) permite evaluar el estado de salud de la aplicación.
        - Logging: Registro centralizado de logs facilita el análisis de eventos, permitiendo a los equipos identificar anomalías y comportamientos inesperados.
        - Trazabilidad: Capacidad de seguir el recorrido de una petición a través de distintos microservicios o componentes permite detectar cuellos de botella y entender la interacción entre diferentes partes del sistema.

    - Experiencia del desarrollador: Cómo mejorar la satisfacción y productividad de los desarrolladores dentro de un equipo DevOps.

        Como DevOps es una metodología integral que une los equipos de desarrollo, esto fomenta la colaboración entre desarrolladores, optimiza los procesos técnicos e impulsa una cultura de responsabilidad compartida y mejora continua entre los miembros de los equipos de todo el proceso de desarrollo de software.

    - InnerSource: Adopción de prácticas de código abierto dentro de una organización.

        InnerSource es una estrategia de desarrollo de software, en la cual se adopta una cultura de código abierto, para trabajar y colaborar de manera mas efectiva con toda la organización y puedan contribuir en el código.

    - Ingeniería de plataformas: Creación de plataformas internas para facilitar el desarrollo y la operación.

        Esto ayuda a la productividad de los desarrolladores, mejora colaboración entre los equipos ya que tienen a su disposición plataformas con herramientas que apoyan a las necesidades de los desarrolladores.

2. __Preguntas de reflexión__

    Respondiendo las siguientes preguntas con base en la lectura:

    1. __¿Qué significa "desplazar a la izquierda" en el contexto de DevSecOps y por qué es importante?__
        
        Se refiere a la integración desde el comienzo de la seguridad, en el proceso de desarrollo de software, esto permite detectar y corregir vulnerabilidades tempranas y tomar acción sobre ellas.

    2. __Explica cómo IaC mejora la consistencia y escalabilidad en la gestión de infraestructuras.__

        IaC sigue ciertos principios, los cuales ayudan a mejorar la consistencia y escalabilidad en la gestión de infraestructuras, la _reproducibilidad_ e _idempotencia_ mejoran la consistencia en la infraestructura, mientras que la _composabilidad_ y _evaluación controlada_ mejoran la escalabilidad en la gestión de infraestructuras.

    3. __¿Cuál es la diferencia entre monitoreo y observabilidad? ¿Por qué es crucial la observabilidad en sistemas complejos?__

        El monitoreo se encarga de recopilar métricas del sistema como uso de CPU, memoria, latencia de respuestas, tasa de errores, entre otros, mientras que la observabilidad es un enfoque mas completo, que tiene como pilar el monitoreo, logging y trazabilidad, con los cuales podemos detectar problemas posibles que podrían afectar al cliente

    4. __¿Cómo puede la experiencia del desarrollador impactar el éxito de DevOps en una organización?__

        Los desarrolladores experimentados, con los amplios conocimientos que maneja, podrían dar soluciones de automatización o mejora a procesos repetitivos o poco eficientes que se puedan estar dando en la organización, optimizarlas mediante la adopción de DevOps como marco de trabajo u otros.

    5. __Describe cómo InnerSource puede ayudar a reducir silos dentro de una organización.__

        Primero aclaremos a que se refiere con _silos_, los dilos son barreras entre los equipos, que limitan la colaboración entre ellos, sea comunicación, información, entre otros.
        InnerSource ayuda a reducir estos silos, ya que todos los miembros de la organización tienen acceso al código(repositorio), documentación e información adicional manejada por cada equipo, esto reduce la gestión de información entre los equipos, repetir trabajos ya realizados  por otros equipos, permite que otros aprendan y reutilicen soluciones que ya estén implementadas y facilita la colaboración entre los equipos de desarrollo.

    6. __¿Qué rol juega la ingeniería de plataformas en mejorar la eficiencia y la experiencia del desarrollador?__

        La ingeniería de plataformas facilitan el desarrollo y despliegue de software, ya que la infraestructura ya esta creada, configurada y esta en constantemente monitoreo, esto ayuda a la eficiencia y productividad de desarrolladores.
