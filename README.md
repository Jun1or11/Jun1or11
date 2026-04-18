flowchart TD
    subgraph Cliente
        Frontend[Frontend: Capa de Presentación]
    end

    subgraph Backend - API (FastAPI)
        Routers[Paquete: Routers]
        Schemas[Paquete: Schemas]
        Services[Paquete: Services]
        CRUD[Paquete: CRUD]
        Models[Paquete: Models]
        Core[Paquete: Core]
    end

    subgraph Gestor de BD
        DB[(PostgreSQL)]
    end

    %% Mostrar dependencias mediante flechas
    Frontend -->|Peticiones HTTP/REST| Routers
    Routers -->|Valida peticiones con| Schemas
    Routers -->|Delega procesos complejos a| Services
    Routers -->|Solicita datos a| CRUD
    Services -->|Consulta/Guarda usando| CRUD
    CRUD -->|Aplica consultas sobre| Models
    Models -->|Mapea tablas en| DB
    
    %% Paquete transversal
    Routers -.->|Valida seguridad y tokens| Core

