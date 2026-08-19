# Definicion de Terminado

Una historia de usuario se considera terminada cuando cumple todos los puntos siguientes. Si falta alguno, permanece en progreso, sin importar que la funcionalidad ya opere.

## Funcionalidad

- [ ] Cumple todos los criterios de aceptacion definidos en la historia.
- [ ] Funciona de extremo a extremo sobre datos sinteticos.
- [ ] Los defectos encontrados durante el desarrollo estan corregidos o registrados en el backlog.

## Codigo

- [ ] Fusionado a `main` mediante Pull Request aprobado.
- [ ] Sin credenciales ni datos sensibles versionados.
- [ ] Respeta los limites entre modulos.
- [ ] El CI pasa en verde.

## Pruebas

- [ ] Tiene pruebas automatizadas sobre la logica principal.
- [ ] Si trata datos de donante o de unidades, tiene caso de prueba de confidencialidad (RNF-01).
- [ ] Si expone informacion por jurisdiccion, tiene caso de prueba de control de acceso (RNF-02).

## Documentacion

- [ ] Los diagramas C4 afectados estan actualizados.
- [ ] Si hubo una decision arquitectonica, existe el ADR correspondiente.
- [ ] Las migraciones de base de datos estan versionadas.

## Trazabilidad

- [ ] La rama, los commits y el Pull Request referencian el identificador de la historia.
- [ ] Las horas trabajadas quedaron registradas en la herramienta de gestion del proyecto.
