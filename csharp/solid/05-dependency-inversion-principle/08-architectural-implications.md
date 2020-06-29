# Architectural implications

By inverting dependencies you create bounds between software modules.

- Plugins can be deployed and developed independently
- Divide the system by boundaries and invert the depdendencies that cross those boundaries.
- Plugins define the boundaries of a system.

## Data-Centric model

- Utils ----------|
- UI -------------|-> Database
- Business Logic -|

- The data and schema rule the world.
- Logic in SQL Stored procedures.
- SQL is suited for tuples processing, not for modeling objects relationships.

## Domain-Centric Model

- Utils ------|
- UI ---------|-> Domain and BL
- Database ---|

- Domain is the Core
- Domain is Stable

# Enlarged Domain-Centric Model

- Ports and Adapters architecture
- Ports are seams we introduce by extracting interfaces
- Adapters are plugins which come from the boundary of a system
- Strive to keep the graph as flat as you can

Who is responsible for keeping the control over the dependencies instantiation and their
lifetime?

Answer: "Main partition as the infrastructural point".

- Conforms to "Single Choice" principle.
- Only the main partition knows about dependencies and their relationships.
