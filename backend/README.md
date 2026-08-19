# Backend

API de RedVital construida con Spring Boot.

## Organizacion por modulos

El backend es un monolito modular. Cada carpeta bajo
`src/main/java/co/edu/javeriana/redvital/` corresponde a un modulo funcional
del SRS y constituye un limite interno.

| Carpeta | Modulo |
| --- | --- |
| `shared` | Codigo transversal: configuracion, seguridad, auditoria, excepciones |
| `donantes` | M1 Gestion de Donantes |
| `gamificacion` | M2 Motivacion y Gamificacion |
| `campanas` | M3 Gestion de Campanas |
| `trazabilidad` | M4 Trazabilidad y Ciclo de Vida |
| `inventario` | M5 Inventario y Alertas |
| `transferencias` | M6 Red de Transferencias |
| `territorial` | M7 Administracion Territorial |
| `analitica` | M8 Analitica e Indicadores |

Regla de dependencia: un modulo no accede a las entidades ni a las tablas de
otro modulo. La comunicacion entre modulos se hace a traves de sus servicios
publicos. Las clases compartidas viven en `shared`.

## Ejecutar en local

```bash
docker compose up -d db     # desde la raiz del repositorio
./mvnw spring-boot:run
```
