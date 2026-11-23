# Flujo de trabajo con Git

Todos trabajamos con **fork + rama por tarea + Pull Request**.

### 0. Una sola vez: configurar Git y aceptar la invitación
```
git config --global user.name "Tu Nombre Apellido"
git config --global user.email "el-email-de-tu-cuenta-de-github"
```
Acepta la invitación al repositorio en <https://github.com/raulgonzalezjorge-blip/practica5-sitio-web/invitations> (también llega por email).

### 1. Una sola vez: hacer el fork y clonarlo
1. Entra en <https://github.com/raulgonzalezjorge-blip/practica5-sitio-web> y pulsa **Fork** → **Create fork**. Se crea `TU_USUARIO/practica5-sitio-web`.
2. Clona **tu fork** y enlaza el repositorio oficial como `upstream`:
```
git clone https://github.com/TU_USUARIO/practica5-sitio-web.git
cd practica5-sitio-web
git remote add upstream https://github.com/raulgonzalezjorge-blip/practica5-sitio-web.git
git remote -v
```
`origin` = tu fork (donde subes) · `upstream` = repositorio oficial (de donde bajas lo último).

### 2. Cada tarea: crear la rama
Mueve la tarjeta de la tarea a **DOING** en el tablero. Después:
```
git switch develop
git pull upstream develop
git switch -c feature/1-estructura-index
```

### 3. Mientras trabajas: commits pequeños
```
git status
git add <archivos>
git commit -m "feat(index): crea la estructura base de la página principal (#1)"
```
Repite `add` + `commit` cada vez que termines algo que funcione.

### 4. Subir la rama a tu fork
```
git push -u origin feature/1-estructura-index
```

### 5. Abrir el Pull Request hacia el repositorio oficial
En tu fork aparecerá **Compare & pull request**. Comprueba que pone:
`base repository: raulgonzalezjorge-blip/practica5-sitio-web` · `base: develop` ← `head repository: TU_USUARIO/practica5-sitio-web` · `compare: feature/1-estructura-index`.
En la descripción escribe `Closes #1` para que la tarea se cierre al fusionar. Rellena el checklist.

Con GitHub CLI (opcional) sería:
```
gh pr create --repo raulgonzalezjorge-blip/practica5-sitio-web --base develop --head TU_USUARIO:feature/1-estructura-index --title "Título de la tarea" --body "Closes #1"
```

### 6. Si el jefe pide cambios
Haz los cambios en la **misma rama**, commit y `git push`. El Pull Request se actualiza solo.

### 7. Cuando el jefe fusiona el Pull Request
Mueve la tarjeta a **DONE** (la tarea se cierra sola por el `Closes #1`). Después actualiza tu copia:
```
git switch develop
git pull upstream develop
git push origin develop
git branch -d feature/1-estructura-index
```
Y vuelves al paso 2 con la siguiente tarea.

## Errores frecuentes
| Problema | Solución |
|----------|----------|
| `rejected ... fetch first` al hacer push | `git pull upstream develop` en tu rama, resuelve conflictos, `git push`. |
| Conflicto (`CONFLICT ... Merge conflict in archivo`) | Abre el archivo, elige el código correcto entre `<<<<<<<`, `=======` y `>>>>>>>`, borra las marcas, `git add archivo` y `git commit`. |
| He trabajado en `develop` sin crear rama | `git switch -c feature/<n>-<nombre>`: los cambios se vienen a la rama nueva. |
| Me he equivocado en el último mensaje de commit (sin push) | `git commit --amend -m "mensaje correcto"` |
| `Permission denied` / 403 al hacer push | Estás haciendo push a `upstream`: haz push a `origin` (tu fork). |
| No veo la rama `develop` en mi fork | `git fetch upstream` y `git switch -c develop upstream/develop` |
