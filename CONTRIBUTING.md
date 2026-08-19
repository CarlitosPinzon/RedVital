# Como contribuir

Reglas de trabajo de este repositorio. Provienen del Documento de Herramientas, Politicas y Lineamientos del proyecto; si algo difiere, ese documento tiene precedencia.

## Idioma

El codigo se escribe en ingles: nombres de clases, metodos, variables y ramas. La documentacion funcional, los comentarios de negocio y los mensajes al usuario se escriben en espanol.

## Ramas

- `main` siempre debe estar en estado desplegable. Nadie escribe directamente sobre ella.
- Una rama por historia de usuario: `feature/HU-nnn-descripcion-corta`.
- Para defectos: `fix/descripcion-corta`.

## Commits

Formato: `tipo(alcance): descripcion`

Tipos: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`.

```
feat(donors): registro anonimo de donante
fix(inventory): corregir calculo de fecha de vencimiento
docs(adr): registrar decision sobre monolito modular
```

Se sube trabajo al repositorio al menos una vez al dia. No se acumulan cambios locales durante varios dias.

## Pull Requests

- Todo cambio entra a `main` mediante Pull Request. Sin excepciones.
- Requiere aprobacion de al menos un integrante distinto del autor.
- El autor no aprueba su propio Pull Request.
- Un Pull Request no deberia superar aproximadamente 400 lineas modificadas. Si las supera, se divide.
- El CI debe estar en verde antes de fusionar.
- Una revision se responde dentro del mismo dia habil, para no bloquear al equipo.

## Limites entre modulos

Cada modulo del backend corresponde a un modulo funcional del SRS. Un modulo no accede a las entidades ni a las tablas de otro; la comunicacion pasa por servicios publicos. El codigo transversal vive en `shared`.

Este punto se verifica en la revision de codigo. Un Pull Request que cruce limites de modulo se devuelve.

## Decisiones de arquitectura

Toda decision arquitectonica relevante se delibera en la Mesa de Arquitectura y se registra como ADR en `docs/adr/` antes de implementarse. Una decision no registrada no se implementa.

## Base de datos

Los cambios de esquema se aplican mediante migraciones de Flyway versionadas, ubicadas en `backend/src/main/resources/db/migration/`. No se modifica el esquema a mano en ningun ambiente. Una migracion ya aplicada no se edita: se crea una nueva.

## Secretos

Ninguna credencial, clave o token se versiona. Usar `.env.example` como referencia y mantener el `.env` local fuera del control de versiones. En el ambiente desplegado, las credenciales se configuran como variables de entorno en la plataforma.

## Datos

Se trabaja unicamente con datos sinteticos. No se cargan ni se procesan datos reales de salud de personas en ningun ambiente, ni siquiera en local.

## Restricciones que no se negocian

Dos reglas del dominio condicionan el codigo y no admiten excepcion:

1. Ninguna funcionalidad expone la causa clinica por la que una unidad fue marcada como no apta.
2. Ningun mecanismo de reconocimiento al donante puede tener contraprestacion economica, directa ni indirecta.
