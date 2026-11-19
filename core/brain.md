# Brain — Godot 4 Steamworks

- **Autoload**: Centralizar en `scripts/autoloads/steam_manager.gd` con `Engine.has_singleton('Steam')` para que el proyecto corra también en exports sin GodotSteam.
- **Cloud Save**: Validar cuotas con `Steam.getQuota()` antes de escribir archivos grandes.
- **Auditoría**: `$steam:audit` inspecciona `scripts/autoloads/` y `export_presets.cfg`.
