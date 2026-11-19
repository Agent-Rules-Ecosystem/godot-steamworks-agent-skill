# Checklist de Auditoría — `$steam:audit`

- [ ] `Engine.has_singleton('Steam')` + `steamInitEx()` con fallback gracioso.
- [ ] `Steam.run_callbacks()` ejecutado en `_process()`.
- [ ] `Steam.storeStats()` llamado tras `setAchievement()` / `setStat*()`.
- [ ] `steam_appid.txt` excluido de Git y de builds de release.
- [ ] Señal `overlay_toggled` conectada para pausar gameplay.
