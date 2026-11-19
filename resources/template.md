# Plantilla Canónica — SteamManager Autoload

```gdscript
extends Node

signal achievement_unlocked(api_name: String)

var is_ready: bool = false

func unlock(api_name: String) -> void:
	if not is_ready:
		return
	Steam.setAchievement(api_name)
	Steam.storeStats()
	achievement_unlocked.emit(api_name)
```
