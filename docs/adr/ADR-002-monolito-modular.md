# ADR-002: Monolito modular en lugar de microservicios

- **Estado:** Aceptada
- **Fecha:** 2026-08-18
- **Responsable de implementar:** Arquitecto de Software
- **Fecha de revision:** Cierre del proyecto

## Contexto

El sistema se compone de ocho modulos funcionales con responsabilidades
diferenciadas. Es necesario definir si se despliegan de forma independiente o
como una sola aplicacion.

## Opciones consideradas

1. **Microservicios.** Cada modulo se despliega y escala de forma
   independiente.
2. **Monolito modular.** Una sola aplicacion desplegable, con limites internos
   estrictos entre modulos.

## Trade-off evaluado

Escalabilidad frente a simplicidad operativa. Los microservicios ofrecen
independencia de despliegue, a cambio de coordinacion entre servicios,
observabilidad distribuida y manejo de consistencia entre bases de datos
separadas.

## Decision

Monolito modular. Los modulos se separan dentro del codigo mediante paquetes
con limites explicitos, sin desplegarse por separado.

## Justificacion

El costo operativo de los microservicios no es asumible en 5 sprints con un
equipo sin experiencia previa en operarlos. El monolito modular entrega los
mismos limites internos de responsabilidad sin ese costo. Ademas, la
trazabilidad de unidades requiere transacciones que atraviesan varios modulos,
lo que en una arquitectura distribuida obligaria a implementar consistencia
eventual sin necesidad real.

## Consecuencias

- Todos los modulos comparten un mismo despliegue y una misma base de datos.
- Se establece como regla de construccion que ningun modulo accede
  directamente a las tablas de otro. Esta regla se verifica en la revision de
  codigo.
- Si en el futuro se requiere separar un modulo, los limites internos ya
  definidos permiten extraerlo sin rediseñar el dominio.
