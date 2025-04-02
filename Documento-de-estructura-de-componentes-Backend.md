# Estructura de Componentes BackEnd 

Este documento describe la organización de los principales paquetes y componentes del backend de la aplicación.

---

## Estructura General

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
        │   └── queries
        ├── jpa
        │   ├── entities
        │   └── repositories
        └── BackendVentasApplication.java
└── resources
```
## Paquetes y Componentes
- **ucr.ac.cr.BackendVentas:** Es el paquete raíz del proyecto. Contiene todos los submódulos organizados de acuerdo con su responsabilidad dentro de la arquitectura.
- **api:** Contiene los componentes expuestos al exterior, principalmente los controladores y definiciones de tipos usados en las APIs.
    - **exceptions:** Manejo de excepciones personalizadas que pueden ser lanzadas por la lógica de negocio o por errores específicos de la aplicación.
    - **rests:** Controladores REST que gestionan las peticiones HTTP entrantes y delegan la lógica a los manejadores (handlers).
    - **types:** Clases que representan objetos de transferencia de datos (DTOs), usados en las peticiones y respuestas de la API.
- **handlers:** Se encarga de la lógica de negocio mediante una separación por responsabilidad.
    - **commands:** Manejadores que ejecutan operaciones que modifican el estado del sistema (crear, actualizar, eliminar).
    - **queries:** Manejadores que procesan operaciones de lectura o consulta del sistema, sin modificar el estado.
- **jpa:** Responsable del acceso a la base de datos mediante JPA (Java Persistence API).
    - **entities:** Clases que representan las tablas de la base de datos. Son los modelos persistentes de la aplicación.
    - **repositories:** Interfaces que extienden JpaRepository u otras, para manejar la persistencia de las entidades de forma abstracta.
- **resources:** Contiene archivos de configuración y recursos estáticos como application.properties o application.yml, necesarios para la ejecución del backend.
