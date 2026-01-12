
# 🛡️ Fail2Ban Auto-Setup für CloudPanel

Dieses Skript installiert und konfiguriert Fail2Ban automatisch auf **CloudPanel** (Nginx/Ubuntu) Servern.
Es schützt vor Bot-Netzwerken, DOS-Angriffen und Scannern, indem es Angreifer auf Firewall-Ebene blockiert.


## ⚙️ Features
- ✅ **Installation:** Installiert Fail2Ban & IPtables automatisch.
- ✅ **Autostart:** Aktiviert den Dienst dauerhaft (`systemctl enable`).
- ✅ **Schutz:** Erstellt Filter gegen:
    - Aggressive POST-Requests / Spam.
    - HTTP-Fehlerfluten (400, 500, 502, etc.).
    - Scans nach sensiblen Dateien (`.env`, `.git`, `config.php`, etc.).
- ✅ **Universal:** Überwacht automatisch **alle** Webseiten/User in CloudPanel (`/home/*/logs/nginx/access.log`).

## 🛠️ Wichtige Befehle

| Aktion | Befehl |
|--------|--------|
| **Status & Bans prüfen** | `fail2ban-client status nginx-cloudpanel-dos` |
| **IP manuell entbannen** | `fail2ban-client set nginx-cloudpanel-dos unbanip <IP-ADRESSE>` |
| **Live Logs sehen** | `tail -f /var/log/fail2ban.log` |
| **Service Neustart** | `systemctl restart fail2ban` |

## 📝 Konfiguration anpassen
Die Einstellungen (Bann-Dauer, Versuche) befinden sich nach der Installation in:
`/etc/fail2ban/jail.d/nginx-cloudpanel.conf`
```
