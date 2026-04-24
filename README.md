# 🍺 Schurli — die Kellner-App für den Vereinsbetrieb

Eine mobile Web-App zur Bestellaufnahme und Tischabrechnung, entwickelt für den täglichen Betrieb im Vereinsgasthaus. Läuft komplett offline im lokalen WLAN — kein Cloud-Abo, keine monatlichen Kosten.

---

## ✨ Features

- **Tischverwaltung** mit zwei Bereichen: Drinnen 🏠 und Gastgarten 🌳
- **Bestellaufnahme** mit Kategorien, Emojis und Notiz pro Position
- **Bondruck** direkt an Epson TM-m30 über WLAN (ESC/POS)
- **Abrechnung mit Splitting** — mehrere Rechnungen pro Tisch
- **Tagesabschluss** mit Umsatz, Top-Artikeln und Bon-Druck
- **Speisekarte-Editor** mit Kategorien, Artikeln und Emojis
- **Verlauf** mit Tages- und Gesamtumsatz
- **Backup & Restore** — Speisekarte und Einstellungen als JSON
- **CSV-Export** für jede Buchhaltung
- PWA-fähig — installierbar am iPhone Home-Bildschirm

---

## 📱 Setup in 4 Schritten

### 1. App bereitstellen
Lade `index.html` in dieses Repository hoch — GitHub Pages stellt sie automatisch unter  
`https://DEIN-USERNAME.github.io/schurli` bereit.

### 2. Print-Bridge am iPad starten
```bash
# a-Shell App auf dem iPad öffnen
python3 schurli_server.py
```
Das Script zeigt die iPad-IP und den Port an.

### 3. App am iPhone öffnen
Im Safari die angezeigte URL öffnen (z.B. `http://192.168.1.50:8080`)  
→ Teilen → **Zum Home-Bildschirm** → fertig.

### 4. Einstellungen konfigurieren
In Schurli: **Menü-Tab → ⚙ Einstellungen**
- Vereinsname, Tischanzahl pro Bereich
- Print-Bridge IP (iPad-IP)
- Drucker-IP (Epson TM-m30)

---

## 🛠️ Technische Details

| Was | Wie |
|---|---|
| Frontend | Vanilla HTML/CSS/JS, keine Abhängigkeiten |
| Datenspeicherung | localStorage im Browser |
| Druckprotokoll | ESC/POS über TCP Port 9100 |
| Print-Bridge | Python 3 (läuft in a-Shell auf iPad) |
| Drucker | Epson TM-m30 (ePOS-fähig, feste IP empfohlen) |

```
iPhone (Safari)
    ↓ HTTP/WLAN
iPad (a-Shell, python3 schurli_server.py)
    ↓ TCP 9100
Epson TM-m30
```

---

## 📂 Dateien

| Datei | Beschreibung |
|---|---|
| `index.html` | Die komplette Schurli-App |
| `schurli_server.py` | Print-Bridge + Web-Server für das iPad |
| `README.md` | Diese Datei |

---

## 💾 Backup

Schurli kennt zwei Backup-Typen:

- **Vollständiges Backup** — Speisekarte + Einstellungen + gesamte Bestellhistorie  
  → täglich beim Tagesabschluss empfohlen
- **Speisekarte & Einstellungen** — nur Menü und Konfiguration, ohne Historie  
  → einmalig nach dem Einrichten sichern, bei Gerätewechsel wiederherstellen

Beide Backups sind einfache JSON-Dateien die du lokal speicherst.

---

## 📋 Täglicher Betrieb

```
Abend starten:   iPad → a-Shell → python3 schurli_server.py
Bestellen:       Tisch → + Bestellen → Artikel → Bon senden
Abrechnen:       Tisch → Tisch abrechnen → Positionen wählen → Rechnung drucken
Abschluss:       Oben rechts 🌙 → Tagesabschluss drucken → CSV exportieren
Stoppen:         a-Shell → Ctrl+C
```

---

## ⚙️ Drucker-IP herausfinden

Am Epson TM-m30 beim Einschalten den **Feed-Knopf** gedrückt halten →  
der Drucker druckt ein Statusblatt mit seiner IP-Adresse.  
Eine **feste IP** im Router-DHCP empfehlen, damit sich die IP nach Neustart nicht ändert.

---

*Gebaut für den Vereinsbetrieb — mit Lederhose und Gilet.* 🍺
