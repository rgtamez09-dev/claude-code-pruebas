# ¡Bienvenido al repositorio claude-code-pruebas!

**Repositorio:** `rgtamez09-dev/claude-code-pruebas`  
**Fecha:** 8 de mayo de 2026

¡Hola! Este repositorio está pensado para explorar y experimentar con GitHub Actions y Claude Code. Esperamos que este espacio sea útil para aprender, probar y construir flujos de trabajo inteligentes.

---

## 5 Consejos Clave para GitHub + Claude Code

### 1. Configura un `CLAUDE.md` en la raíz del repositorio
Este archivo actúa como guía de instrucciones para Claude Code. Define las convenciones del proyecto, los comandos de build/test, las restricciones de estilo y cualquier contexto importante. Claude lo lee automáticamente en cada sesión, lo que garantiza respuestas coherentes y alineadas con tu proyecto.

### 2. Usa ramas de trabajo dedicadas por issue
Nombra tus ramas de forma descriptiva: `feature/nombre-feature`, `fix/descripcion-bug`, `claude/issue-N-fecha`. Esto facilita la trazabilidad y permite que Claude Code opere en un contexto aislado sin afectar `main`.

### 3. Aprovecha los triggers de `@claude` en issues y PRs
Puedes invocar a Claude directamente en comentarios de issues o pull requests con `@claude`. Claude leerá el contexto del PR/issue, hará cambios y actualizará el comentario con progreso en tiempo real. Es ideal para revisiones de código, generación de archivos y resolución de bugs.

### 4. Define permisos explícitos en tu workflow de GitHub Actions
En tu archivo de workflow (`.github/workflows/`), configura correctamente los `permissions` del job de Claude:
```yaml
permissions:
  contents: write
  pull-requests: write
  issues: write
```
Esto garantiza que Claude pueda crear commits, comentar y abrir PRs sin errores de autorización.

### 5. Itera con PRs pequeños y bien descritos
En lugar de hacer cambios masivos, trabaja en PRs atómicos con un propósito claro. Pide a Claude que incluya en cada PR: una descripción del cambio, referencia al issue original y un plan de pruebas. Esto hace el historial de git limpio y las revisiones más eficientes.

---

## Best Practices: Limpieza, Seguridad y Eficiencia

### Limpieza
- **Elimina ramas obsoletas** después de hacer merge: `git branch -d nombre-rama` o usa la opción automática en GitHub Settings → "Automatically delete head branches".
- **Mantén el historial limpio** con commits descriptivos siguiendo [Conventional Commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `docs:`, `chore:`, etc.
- **Revisa y archiva repositorios** que ya no estés usando activamente para reducir el ruido en tu organización.

### Seguridad
- **Nunca cometas secretos** (API keys, tokens, contraseñas) directamente en el código. Usa GitHub Secrets (`Settings → Secrets and variables → Actions`) y refiérelos como `${{ secrets.MI_SECRET }}` en tus workflows.
- **Habilita Dependabot** para recibir alertas y PRs automáticos cuando tus dependencias tengan vulnerabilidades conocidas.
- **Revisa los permisos de workflows**: usa siempre el principio de mínimo privilegio. Si un job solo necesita leer, no le otorgues permisos de escritura.
- **Activa la protección de rama `main`**: requiere PRs aprobados antes de hacer merge y evita pushes directos.

### Eficiencia
- **Usa caché en tus Actions** para dependencias (`actions/cache`) y así acelerar los tiempos de build.
- **Paraleliza jobs independientes** en tu workflow con múltiples `jobs` en lugar de un solo job secuencial.
- **Configura `on: push` con filtros de rutas** (`paths:`) para que los workflows solo se disparen cuando cambian archivos relevantes, ahorrando minutos de Actions.
- **Aprovecha los `workflow_dispatch`** para poder disparar workflows manualmente cuando sea necesario, facilitando debugging y re-ejecuciones puntuales.

---

> Generado con [Claude Code](https://claude.ai/code) · claude-sonnet-4-6
