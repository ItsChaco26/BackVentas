# Estructura de Componentes BackEnd 

Este documento describe la organización de los principales paquetes y componentes del backend de la aplicación. El proyecto está diseñado siguiendo los principios de arquitectura por capas y separación de responsabilidades, además utiliza el patrón CQRS, esto permite que el proyecto posea una estructura modular, mantenible y escalable.

---
## Configuración del entorno
#TODO
---

## Estructura General del Proyecto

```
main
└── java
    └── ucr.ac.cr.BackendVentas
        ├── api
        │   ├── exceptions
        │   ├── rests
        │   └── types
        ├── handlers
        │   ├── commands
        │   │   ├── impl     
        │   └── queries
        │       └── impl
        ├── jpa
        │   ├── entities
        │   └── repositories
        └── BackendVentasApplication.java
└── resources
```
---
## Paquetes y Componentes
- **ucr.ac.cr.BackendVentas:** Es el paquete raíz del proyecto. Contiene todos los submódulos organizados de acuerdo con su responsabilidad dentro de la arquitectura.
- **api:** Contiene los componentes expuestos al exterior, principalmente los controladores y definiciones de tipos usados en las APIs.
    - **exceptions:** Manejo de excepciones personalizadas que pueden ser lanzadas por la lógica de negocio o por errores específicos de la aplicación.
    - **rests:** Controladores REST que gestionan las peticiones HTTP entrantes y delegan la lógica a los manejadores (handlers).
    - **types:** Clases que representan objetos de transferencia de datos (DTOs), usados en las peticiones y respuestas de la API.
- **handlers:** Se encarga de la lógica de negocio mediante una separación por responsabilidad.
    - **commands:** Manejadores que ejecutan operaciones que modifican el estado del sistema (crear, actualizar, eliminar).
         - **impl:** Implementaciones específicas de los comandos.
    - **queries:** Manejadores que procesan operaciones de lectura o consulta del sistema, sin modificar el estado.
        - **impl:** Implementaciones específicas de las consultas.
- **jpa:** Responsable del acceso a la base de datos mediante JPA (Java Persistence API).
    - **entities:** Clases que representan las tablas de la base de datos. Son los modelos persistentes de la aplicación.
    - **repositories:** Interfaces que extienden JpaRepository u otras, para manejar la persistencia de las entidades de forma abstracta.
- **models:** Contiene clases de modelo de dominio que encapsulan reglas de negocio o estructuras reutilizables dentro del sistema. Estas clases pueden ser independientes de la persistencia o la exposición vía API.
- **services:** Contiene la lógica de negocio reutilizable y centralizada que puede ser utilizada tanto por controladores (api/rests) como por comandos o queries. Ayuda a mantener una lógica más limpia y desacoplada del resto del sistema.
- **resources:** Contiene archivos de configuración y recursos estáticos como application.properties o application.yml, necesarios para la ejecución del backend.
---
## Bibliografía
- A. Factor, “Qué es la arquitectura en capas: descubre sus ventajas y ejemplos,” Latam Tech - Transformación Digital, Sep. 14, 2023. https://latamtech-sac.com/que-es-la-arquitectura-en-capas-descubre-sus-ventajas-y-ejemplos/
- K. P. Singh, “System design: Command and Query Responsibility Segregation (CQRS),” DEV Community, Sep. 15, 2022. https://dev.to/karanpratapsingh/system-design-command-and-query-responsibility-segregation-cqrs-1kl1