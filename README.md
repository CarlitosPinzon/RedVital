# RedVital

Plataforma para la gestion del ciclo de vida de la donacion de sangre en Colombia: registro de donantes, trazabilidad de unidades, inventario, campanas de donacion y coordinacion entre bancos de sangre por nivel territorial.

Proyecto academico desarrollado por Arkhe Software S.A.S. para el curso de Arquitectura de Software Empresarial, Pontificia Universidad Javeriana.

## Que resuelve

Colombia capta menos sangre de la que necesita cada ano, y el deficit se agrava de forma estacional. RedVital no interviene en el proceso clinico: coordina la informacion entre bancos de sangre, prioriza la redistribucion del inventario ya captado antes de convocar nuevos donantes, y da a las entidades territoriales visibilidad sobre los bancos de su jurisdiccion.

## Stack

| Capa | Tecnologia |
| --- | --- |
| Backend | Java 21, Spring Boot, Spring Data JPA, Spring Security, Spring Scheduler |
| Frontend | TypeScript, React |
| Base de datos | PostgreSQL 16 |
| Migraciones | Flyway |
| Entorno local | Docker Compose |
| Integracion continua | GitHub Actions |

La justificacion de cada eleccion esta en [ADR-001](docs/adr/ADR-001-seleccion-del-stack-tecnologico.md).

## Arquitectura

El sistema es un **monolito modular**: una sola aplicacion desplegable, con limites internos estrictos entre modulos. Cada carpeta bajo `backend/src/main/java/co/edu/javeriana/redvital/` corresponde a un modulo funcional del SRS.

Regla de dependencia: ningun modulo accede directamente a las tablas ni a las entidades de otro. La comunicacion entre modulos pasa por sus servicios publicos.

El razonamiento detras de esta decision esta en [ADR-002](docs/adr/ADR-002-monolito-modular.md).

## Estructura del repositorio

```
redvital/
├── backend/            API Spring Boot, organizada por modulos
├── frontend/           Aplicacion React
├── docs/
│   └── adr/            Registros de Decision Arquitectonica
├── .github/            Workflows de CI y plantillas
└── docker-compose.yml  Base de datos para desarrollo local
```

## Requisitos

- Java 21
- Node.js 20 o superior
- Docker y Docker Compose

## Puesta en marcha

```bash
# 1. Clonar y configurar variables de entorno
git clone <url-del-repositorio>
cd redvital
cp .env.example .env

# 2. Levantar la base de datos
docker compose up -d db

# 3. Backend
cd backend
./mvnw spring-boot:run

# 4. Frontend, en otra terminal
cd frontend
npm install
npm run dev
```

El backend queda en `http://localhost:8080` y el frontend en `http://localhost:5173`.

## Como trabajamos

Las reglas de ramas, commits, Pull Requests y revision estan en [CONTRIBUTING.md](CONTRIBUTING.md). Los criterios para dar una tarea por terminada estan en [DEFINITION_OF_DONE.md](DEFINITION_OF_DONE.md).

El despliegue del ambiente de demostracion es automatico a partir de `main`, gestionado por el proveedor de alojamiento. No requiere un workflow adicional en este repositorio.

## Equipo

| Rol | Integrante |
| --- | --- |
| Product Owner | Alexander Aponte |
| Scrum Master / Project Manager | Carlos Santiago Pinzon Caicedo |
| Arquitecto de Software | |

## Licencia

[MIT](LICENSE).
