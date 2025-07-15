# 🤖 AEGIS Discord Bot

Ein umfassender, mehrsprachiger Discord Bot mit erweiterten Funktionen für Community-Management, Moderation und Unterhaltung.

## 🌟 Hauptfunktionen

### 🔗 Server-Tunnel-System
- **Verbindung mehrerer Discord-Server** - Nachrichten werden automatisch zwischen verbundenen Servern synchronisiert
- **Sichere Webhook-basierte Übertragung** - Keine Bot-Nachrichten, authentische Benutzernamen
- **Tunnel-Management** - Erstellen, beitreten, verwalten und löschen von Server-Tunneln
- **Premium-Features** - Bis zu 20 Spieler in Premium-Servern (sonst 4)

### 💰 Punktesystem (NP-System)
- **Anpassbare Währung** - Serveradmins können die Währung benennen
- **Punkteverwaltung** - Hinzufügen/Entfernen von Punkten für Benutzer oder Rollen
- **Automatische Ranglisten** - Selbst-aktualisierende Leaderboards
- **Transaktionshistorie** - Vollständige Nachverfolgung aller Punkteaktivitäten
- **Maximale Punktegrenze** - Einstellbare Limits pro Server

### 🎯 Code-System
- **Einlösbare Codes** - Zeitlich begrenzte Codes für Punktebelohnungen
- **Automatische Bereinigung** - Abgelaufene Codes werden automatisch entfernt
- **Benutzerhistorie** - Nachverfolgung, wer welche Codes eingelöst hat

### 🕵️ Infiltrator-Spiel
- **Strategiespiel** - Ähnlich wie Mafia/Werewolf mit Discord-Integration
- **Temporäre Spielumgebung** - Automatische Kanal- und Rollenerstellung
- **Abstimmungssystem** - Interaktive Buttons für Spielaktionen
- **Belohnungen** - Gewinner erhalten automatisch Punkte

### 🛡️ Erweiterte Moderation
- **Multi-Layer-Moderation**:
  - **Zone 1**: Spam-Erkennung und Blacklist-Filter
  - **Zone 2**: KI-Textanalyse mit Perspective API
  - **Zone 3**: Lokale Bildanalyse mit NudeNet
- **Automatische Eskalation** - Warnungen → Timeouts → Kicks
- **Anti-Raid-System** - Schutz vor koordinierten Angriffen
- **Konfigurierbare Blacklists** - Wörter und Wildcard-Patterns

### ⚙️ Admin-Dashboard
- **Interaktive Einstellungen** - Button-basierte Konfiguration
- **Mehrsprachige Oberfläche** - Deutsch und Englisch
- **Modulare Aktivierung** - Ein-/Ausschalten von Bot-Funktionen
- **Premium-Schlüssel-Verwaltung** - Aktivierung von Premium-Features

### 🎭 Patreon-Integration
- **Automatische Premium-Aktivierung** - Webhook-Integration für Patreon
- **E-Mail-Versand** - Automatischer Versand von Premium-Schlüsseln
- **Drei Schlüssel-Typen**:
  - **Server Premium** - Erweiterte Server-Features
  - **User Premium** - Persönliche Premium-Features
  - **Developer** - Unbegrenzte Entwickler-Features

### 📞 Kontakt & Support-System
- **Ticket-System** - Vorschläge, Feedback und Support-Anfragen
- **Direkte Kommunikation** - DM-Bridge zwischen Nutzern und Team
- **Thread-basierte Verwaltung** - Organisierte Support-Gespräche
- **Status-Tracking** - Vollständige Nachverfolgung von Tickets

### 🌍 Mehrsprachigkeit
- **Vollständige Lokalisierung** - Deutsch und Englisch
- **Dynamische Sprachumschaltung** - Pro Server konfigurierbar
- **Erweiterbar** - Einfaches Hinzufügen neuer Sprachen

## 📋 Anforderungen

### System-Anforderungen
- **Python 3.9+**
- **MySQL/MariaDB-Datenbank**
- **Discord Bot Token**
- **Ausreichend RAM** (mindestens 512MB empfohlen)

### API-Schlüssel (Optional)
- **Perspective API** - Für KI-Textmoderation
- **Google Safe Browsing API** - Für Link-Überprüfung
- **Patreon API** - Für Premium-Integration

## 🚀 Installation

### 1. Repository klonen
```bash
git clone https://github.com/yourusername/aegis-discord-bot.git
cd aegis-discord-bot
```

### 2. Abhängigkeiten installieren
```bash
pip install -r requirements.txt
```

### 3. Umgebungsvariablen konfigurieren
Erstelle eine `.env`-Datei im Hauptverzeichnis:

```env
# Discord Bot Configuration
DISCORD_TOKEN=your_discord_bot_token

# Database Configuration
DB_HOST=localhost
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_NAME=your_database_name

# Optional API Keys
PERSPECTIVE_API_KEY=your_perspective_api_key
SAFE_BROWSING_API_KEY=your_safe_browsing_api_key
PATREON_WEBHOOK_SECRET=your_patreon_webhook_secret
PATREON_CREATOR_ACCESS_TOKEN=your_patreon_access_token

# Email Configuration (für Premium-Keys)
SENDER_EMAIL=your_email@gmail.com
GMAIL_APP_PASSWORD=your_app_password
```

### 4. Datenbank einrichten
```sql
-- Beispiel-Tabellen (vollständiges Schema separat verfügbar)
CREATE TABLE users (
    id BIGINT PRIMARY KEY,
    server_id BIGINT,
    username VARCHAR(255),
    np INT DEFAULT 0
);

CREATE TABLE server_settings (
    server_id BIGINT PRIMARY KEY,
    language VARCHAR(5) DEFAULT 'de',
    automod_enabled BOOLEAN DEFAULT FALSE,
    max_np INT DEFAULT 3500
);

-- Weitere Tabellen siehe database_schema.sql
```

### 5. Bot starten
```bash
python main.py
```

## 🎮 Verwendung

### Admin-Befehle
- `/settings` - Öffnet das Admin-Dashboard
- `/createcode <code> <punkte> <dauer>` - Erstellt einen neuen Code
- `/mpadd <anzahl> [benutzer] [rolle]` - Fügt Punkte hinzu
- `/mpremove <anzahl> [benutzer] [rolle]` - Entfernt Punkte
- `/mplist <kanal>` - Erstellt eine Rangliste
- `/mpstatus <kanal>` - Erstellt ein Status-Panel

### Benutzer-Befehle
- `/infiltrator` - Startet ein Infiltrator-Spiel
- `/tunnel create <name> <kanal>` - Erstellt einen Server-Tunnel
- `/tunnel join <code> <kanal>` - Tritt einem Tunnel bei
- `/tunnel manage <code>` - Verwaltet einen Tunnel

### Support-Befehle
- `/support-setup <kontakt-kanal> <log-kanal>` - Richtet das Support-System ein

## 🔧 Konfiguration

### Premium-Features aktivieren
1. Patreon-Webhook in `.env` konfigurieren
2. Premium-Schlüssel über `/dangerzone create-key` erstellen
3. Schlüssel über das Dashboard aktivieren

### Moderation konfigurieren
1. Dashboard öffnen mit `/settings`
2. Moderation → Gewünschte Module aktivieren
3. Blacklist-Wörter über Dashboard hinzufügen

### Mehrsprachigkeit
- Sprachdateien in `/languages/` Ordner
- Neue Sprachen durch JSON-Dateien hinzufügbar
- Umschaltung über Dashboard

## 🛡️ Sicherheit

### Sichere Konfiguration
- Umgebungsvariablen für alle Geheimnisse
- Zwei-Faktor-Authentifizierung für kritische Befehle
- Automatische Bereinigung sensibler Daten

### Berechtigungen
- Minimale erforderliche Discord-Berechtigungen
- Rolle-basierte Zugriffskontrolle
- Audit-Logs für alle Admin-Aktionen

## 📊 Monitoring

### Automatische Überwachung
- Speicherverbrauch-Logging
- Datenbank-Verbindungsstatus
- Fehlerprotokollierung mit Rotation

### Performance-Optimierung
- Intelligentes Caching-System
- Asynchrone Datenbankoperationen
- Effiziente Webhook-Verwaltung

## 🤝 Beitragen

1. Repository forken
2. Feature-Branch erstellen (`git checkout -b feature/AmazingFeature`)
3. Änderungen committen (`git commit -m 'Add some AmazingFeature'`)
4. Branch pushen (`git push origin feature/AmazingFeature`)
5. Pull Request erstellen

## 📝 Lizenz

Dieses Projekt steht unter der MIT-Lizenz. Siehe `LICENSE` Datei für Details.

## 🆘 Support

- **Discord Server**: [Einladungslink]
- **Issues**: [GitHub Issues](https://github.com/yourusername/aegis-discord-bot/issues)
- **E-Mail**: support@yourproject.com

## 🙏 Danksagungen

- **Discord.py** - Für die ausgezeichnete Discord-API-Bibliothek
- **NudeNet** - Für die Bildmoderation
- **Perspective API** - Für die Textmoderation
- **Patreon** - Für die Premium-Integration

---

**Entwickelt mit ❤️ von MauntingStudios**

*Powered by MauntingStudios - Ihr Bot für eine bessere Discord-Community*
