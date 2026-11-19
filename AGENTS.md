---
name: godot-steamworks-agent-skill
description: GodotSteam steamInitEx(), Steam.run_callbacks(), Achievements/Stats, Steam Cloud, Lobbies and release build hygiene.
---

# Godot 4 Steamworks (GodotSteam) Agent Skill — Directiva de Habilidad

## Bootstrap de la Habilidad

Al detectar el trigger `$steam` o archivos del dominio, cargar en orden:
1. `.skill/godot-steamworks-agent-skill/SKILL.md`
2. `.skill/godot-steamworks-agent-skill/core/commands.md`
3. `.skill/godot-steamworks-agent-skill/core/brain.md`
4. `.skill/godot-steamworks-agent-skill/core/path_map.md`

## Reglas Canónicas

1. **Validar `Steam.steamInitEx()`**: Comprobar `status == 0` y ofrecer fallback gracioso cuando Steam no esté corriendo (editor/CI).
2. **Ejecutar `Steam.run_callbacks()` en `_process()`**: Indispensable en el Autoload `SteamManager` para recibir señales de logros, lobbies y overlays.
3. **Persistir logros con `Steam.storeStats()`**: Llamar `storeStats()` tras `setAchievement()` o `setStatInt()` para sincronizar con los servidores de Steam.
4. **Nunca empaquetar `steam_appid.txt` en builds de release**: Solo existe en desarrollo local; en producción usar `restartAppIfNecessary(APP_ID)`.
5. **Desacoplar mediante `SteamManager` Autoload**: Ninguna escena de gameplay debe llamar directamente al singleton `Steam` sin wrapper.
6. **Inviolabilidad de `.skill/`**: Nunca editar archivos dentro de `.skill/godot-steamworks-agent-skill/` desde el proyecto cliente; registrar mejoras en `overview/learning.md` vía `$learnskill godot-steamworks-agent-skill [propuesta]`.
