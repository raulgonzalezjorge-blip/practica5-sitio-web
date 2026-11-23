# Scrum: daily y cierre de sprint

Sprints de **1 semana**. El jefe de proyecto modera el daily y escribe el resumen de final de sprint.

## Daily (máx. 15 min)
Cada desarrollador responde:
1. ¿Qué hice ayer? (tarjetas movidas a DONE / PR abiertos)
2. ¿Qué voy a hacer hoy? (tarjeta que pasa a DOING)
3. ¿Tengo algún bloqueo?

Plantilla para apuntarlo:
```
Daily dd/mm/aaaa
- Adrián:    ayer ... | hoy ... | bloqueos ...
- Cristiana: ayer ... | hoy ... | bloqueos ...
Acciones del jefe: ...
```

## Al final de cada sprint (lo hace el jefe)
1. Revisar y fusionar los Pull Request pendientes en `develop`.
2. Crear el PR `develop` → `main`, fusionarlo y etiquetar la versión (`v0.1-sprint1`, `v0.2-sprint2`...).
3. Mover a BACKLOG lo que no se terminó; dividir las tareas `high` que entren en el siguiente sprint y pasarlas a TO DO.
4. Hacer captura de la pizarra.
5. Actualizar la **Definición de Hecho** en la página principal de la wiki.
6. Escribir el resumen del sprint en el PDF: tareas estimadas y finalizadas, previsión del siguiente sprint,
   definición de hecho, reparto del trabajo y errores con Git.
