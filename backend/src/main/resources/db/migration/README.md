# Migraciones de base de datos

Los cambios de esquema se aplican con Flyway. No se modifica el esquema a mano
en ningun ambiente.

Convencion de nombres:

```
V<numero>__<descripcion_en_snake_case>.sql
```

Ejemplos:

```
V1__crear_tabla_donante.sql
V2__crear_tabla_unidad_sangre.sql
V3__agregar_indice_tipo_sangre.sql
```

Reglas:

- Una migracion ya aplicada nunca se edita. Si hay que corregirla, se crea una nueva.
- El numero de version es consecutivo y unico. Antes de crear una, verificar la
  ultima existente para evitar colisiones entre ramas.
- Toda migracion debe poder ejecutarse sobre una base vacia sin errores.
