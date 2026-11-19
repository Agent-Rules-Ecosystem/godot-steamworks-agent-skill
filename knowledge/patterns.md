# Patrones — GodotSteam en Godot 4

## 1. Logros Idempotentes
```gdscript
func unlock_achievement(api_name: String) -> void:
	if not is_steam_ready:
		return
	var status: Dictionary = Steam.getAchievement(api_name)
	if not status.get("achieved", false):
		Steam.setAchievement(api_name)
		Steam.storeStats()
```

## 2. Overlay y Pausa
Conectar `Steam.overlay_toggled` para pausar automáticamente el juego cuando el jugador abre el Steam Overlay.
