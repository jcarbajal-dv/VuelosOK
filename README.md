# Base de Datos de Gestión de Vuelos

Este archivo describe la estructura de las tablas de la base de datos de gestión de vuelos, el diccionario de datos y el diagrama entidad-relación (DER).

## Diagrama Entidad-Relación (DER)

```mermaid
erDiagram
    VUELOS {
        int id PK
        string origen
        string destino
        int duracion
    }

    PERSONA {
        int id PK
        string nombre
        string apellido
    }

    PASSENGERS {
        int id PK
        string nombre
        string apellido
        int fk_vuelo FK
    }

    AEROPUERTOS {
        int id PK
        string code
        string city
    }

    VUELOS ||--o{ PASSENGERS : tiene
    AEROPUERTOS ||--o{ VUELOS : opera
    PERSONA ||--o{ PASSENGERS : viaja
```

## Diccionario de Datos

### Tabla: `VUELOS`

Esta tabla almacena información sobre los vuelos disponibles, incluyendo el origen, destino y duración.

| Campo       | Tipo de Dato | Descripción                                             |
|-------------|--------------|---------------------------------------------------------|
| `id`        | Integer      | Identificador único del vuelo (clave primaria).         |
| `origen`    | String       | Nombre de la ciudad de origen del vuelo.                |
| `destino`   | String       | Nombre de la ciudad de destino del vuelo.               |
| `duracion`  | Integer      | Duración del vuelo en minutos.                          |

### Tabla: `PERSONA`

Esta tabla almacena información sobre las personas registradas en el sistema.

| Campo       | Tipo de Dato | Descripción                                             |
|-------------|--------------|---------------------------------------------------------|
| `id`        | Integer      | Identificador único de la persona (clave primaria).     |
| `nombre`    | String       | Nombre de la persona.                                   |
| `apellido`  | String       | Apellido de la persona.                                 |

### Tabla: `PASSENGERS`

Esta tabla representa a los pasajeros que están asociados a un vuelo específico, además de contener información básica de los pasajeros.

| Campo       | Tipo de Dato | Descripción                                             |
|-------------|--------------|---------------------------------------------------------|
| `id`        | Integer      | Identificador único del pasajero (clave primaria).      |
| `nombre`    | String       | Nombre del pasajero.                                    |
| `apellido`  | String       | Apellido del pasajero.                                  |
| `fk_vuelo`  | Integer      | ID del vuelo en el que viaja el pasajero (clave foránea, referencia a `VUELOS.id`). |

### Tabla: `AEROPUERTOS`

Esta tabla contiene información sobre los aeropuertos operativos en el sistema.

| Campo       | Tipo de Dato | Descripción                                             |
|-------------|--------------|---------------------------------------------------------|
| `id`        | Integer      | Identificador único del aeropuerto (clave primaria).    |
| `code`      | String       | Código IATA del aeropuerto (tres letras).               |
| `city`      | String       | Ciudad a la que pertenece el aeropuerto.                |
