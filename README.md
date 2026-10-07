# Vorlesung-Sync

Vorlesungen aufnehmen und mit den Folien verknüpfen: Folien mitklicken, Stellen markieren
(★ klausurrelevant, ? nicht verstanden, ≡ Definition), mit dem Stift auf die Folie
schreiben. Nach der Vorlesung transkribiert die App lokal mit Whisper und ordnet jeden
Satz seiner Folie zu. Dazu ein Reader für Pflichtlektüre mit Fristen – und Claude als
Lernbegleiter, der auf all das zugreifen kann. Nichts verlässt den Rechner, ausser was
man Claude im Gespräch selbst zeigt.

Hier liegen die fertigen Versionen für Mac und Windows; die App aktualisiert sich von hier.

## Herunterladen

Unter [Releases → neueste Version](https://github.com/timix0513/vorlesung-sync-releases/releases/latest):

| Datei | wofür |
|---|---|
| `Vorlesung-Sync-<v>-mac.dmg` | Mac (Apple Silicon), zum Installieren |
| `Vorlesung-Sync-<v>-windows-setup.exe` | Windows, zum Installieren |
| `Vorlesung-Sync-<v>-mac.zip` | nur für die Updates der App, nicht von Hand nötig |

## Installieren

**Mac:** Die `.dmg` öffnen, Vorlesung-Sync in „Programme“ ziehen und von dort starten
(aus „Downloads“ heraus funktionieren die Updates nicht). Die App ist nicht bei Apple
notarisiert, deshalb meldet macOS beim ersten Öffnen, sie sei nicht überprüft:
Systemeinstellungen → Datenschutz & Sicherheit → ganz unten „Dennoch öffnen“.

**Windows:** Den Installer ausführen, Adminrechte braucht er nicht. Windows SmartScreen
zeigt einmal eine Warnung: „Weitere Informationen“ → „Trotzdem ausführen“. Die
Transkription läuft unter Windows auf der CPU und ist deutlich langsamer als auf dem Mac.

Beim ersten Aufnehmen fragt die App nach dem Mikrofon und lädt das Whisper-Modell
(`large-v3-turbo`, 1.5 GB) einmalig herunter.

## Updates

Die App schaut beim Öffnen der Übersicht (höchstens alle 6 Stunden) hier nach einer
neueren Version; dann steht oben „Version X ist da“. Sofort geht es über das Menü:
Vorlesung-Sync → „Nach Updates suchen …“ (Windows: Hilfe → „Nach Updates suchen …“).
Ein Klick lädt das Update, die App schliesst sich und startet neu. Während einer
Aufnahme oder Transkription wird nie aktualisiert.

Die Vorlesungen liegen getrennt von der App und bleiben bei Updates und beim
Deinstallieren erhalten:

| | Datenordner |
|---|---|
| Mac | `~/Library/Application Support/Vorlesung-Sync` |
| Windows | `%LOCALAPPDATA%\Vorlesung-Sync` |

Ablage (Windows: Datei) → „Datenordner zeigen“ öffnet ihn. Das Log steht dort unter
`logs/app.log`.

## Mit Claude lernen (MCP)

Die App ist das Gedächtnis des Semesters, Claude der Tutor. Über einen MCP-Server, der in
der App steckt, liest Claude Vorlesungen, Folien, Transkripte, markierte Stellen,
Stundenplan und Lektüre – und schreibt zurück: offene Fragen als geklärt markieren (mit
Erklärung), Begriffe anlegen, Lese-Aufgaben aus einem Syllabus anlegen, Anki-Karten mit
ihrer Stelle verknüpfen. Alles, was Claude ändert, ist in der App als „von Claude“ zu
sehen und lässt sich einzeln zurücknehmen.

Es sind zwei MCP-Server, beide laufen nur lokal und Claude startet sie selbst:

- **vorlesung-sync** – in der App enthalten (ab 0.4.2; Lernfortschritt ab 0.5.0). Die App
  muss offen sein, solange Claude damit arbeitet.
- **Anki** (optional) – das Anki-Add-on „Anki MCP Server“. Damit legt Claude Karten direkt
  in Anki an und meldet den Lernstand an die App; die Startseite zeigt ihn dann als
  Lernfortschritt pro Kurs.

Gebraucht wird [Claude Desktop](https://claude.ai/download) oder
[Claude Code](https://claude.com/claude-code).

### 1. Vorlesung-Sync einrichten

Der Server liegt im App-Paket:

| | Pfad |
|---|---|
| Mac | `/Applications/Vorlesung-Sync.app/Contents/Resources/server/vorlesung-sync-server` |
| Windows | `%LOCALAPPDATA%\Programs\Vorlesung-Sync\resources\server\vorlesung-sync-server.exe` |

**Claude Desktop:** Claude → Einstellungen → Entwickler → „Konfiguration bearbeiten“.
Das öffnet `claude_desktop_config.json` (Mac: `~/Library/Application Support/Claude/`,
Windows: `%APPDATA%\Claude\`). Eintragen – stehen dort schon andere Server, nur den
Block `"vorlesung-sync"` dazuschreiben, mit Komma dazwischen:

```json
{
  "mcpServers": {
    "vorlesung-sync": {
      "command": "/Applications/Vorlesung-Sync.app/Contents/Resources/server/vorlesung-sync-server",
      "args": ["--mcp"]
    }
  }
}
```

Windows mit dem vollen Pfad, jeden Backslash doppelt, `NAME` = eigener Benutzername:

```json
{
  "mcpServers": {
    "vorlesung-sync": {
      "command": "C:\\Users\\NAME\\AppData\\Local\\Programs\\Vorlesung-Sync\\resources\\server\\vorlesung-sync-server.exe",
      "args": ["--mcp"]
    }
  }
}
```

Dann Claude ganz beenden (Mac: ⌘Q; Windows: auch das Symbol im Infobereich) und neu
öffnen.

**Claude Code** (gilt dann in allen Projekten), Mac:

```bash
claude mcp add --scope user vorlesung-sync -- /Applications/Vorlesung-Sync.app/Contents/Resources/server/vorlesung-sync-server --mcp
```

Windows (PowerShell):

```powershell
claude mcp add --scope user vorlesung-sync -- "$env:LOCALAPPDATA\Programs\Vorlesung-Sync\resources\server\vorlesung-sync-server.exe" --mcp
```

### 2. Anki einrichten (optional)

1. In Anki: Extras → Erweiterungen → „Erweiterungen herunterladen“, Code `124672614`
   eingeben, Anki neu starten. Solange Anki offen ist, lauscht das Add-on auf
   `http://127.0.0.1:3141` – nur auf diesem Rechner erreichbar.
2. **Claude Desktop:** in denselben `mcpServers`-Block (braucht
   [Node.js](https://nodejs.org) für `npx`):

   ```json
   "anki": {
     "command": "npx",
     "args": ["mcp-remote", "http://127.0.0.1:3141"]
   }
   ```

   **Claude Code:**

   ```bash
   claude mcp add --scope user --transport http anki http://127.0.0.1:3141
   ```

Welches Deck zu welchem Kurs gehört, findet Claude beim ersten „Anki-Stand melden“ selbst
heraus und fragt nur nach, wenn mehrere Decks passen.

So sieht eine vollständige `claude_desktop_config.json` auf dem Mac mit beiden aus:

```json
{
  "mcpServers": {
    "vorlesung-sync": {
      "command": "/Applications/Vorlesung-Sync.app/Contents/Resources/server/vorlesung-sync-server",
      "args": ["--mcp"]
    },
    "anki": {
      "command": "npx",
      "args": ["mcp-remote", "http://127.0.0.1:3141"]
    }
  }
}
```

### 3. Ausprobieren

Vorlesung-Sync (und Anki) öffnen und Claude fragen: *„Was steht diese Woche in
Vorlesung-Sync an?“* Claude antwortet mit den Terminen, offenen Fragen und fälliger
Lektüre. In Claude Code zeigt `claude mcp list` beide Server als „Connected“.

Fertige Abläufe gibt es als Prompts – in Claude Desktop über „+“ im Eingabefeld →
vorlesung-sync, in Claude Code als Befehl:

| Prompt | Claude Code | Was passiert |
|---|---|---|
| Nachbereitung | `/mcp__vorlesung-sync__nachbereitung` | erst aus dem Kopf abrufen, dann Abgleich mit dem Gesagten, offene Fragen klären, Begriffe festhalten |
| Syllabus | `/mcp__vorlesung-sync__syllabus` | Syllabus lesen, Lese-Aufgaben mit Fristen vorschlagen, nach Bestätigung anlegen |
| Anki-Stand melden | `/mcp__vorlesung-sync__anki_stand` | Decks zählen und als Lernfortschritt an die App melden |

Sonst einfach fragen: „Erklär mir meine ?-Stellen aus Mikro VL05“, „Frag mich die
Definitionen von letzter Woche ab“, „Mach Anki-Karten zu den ★-Stellen von gestern“.

### Wenn es nicht klappt

| Meldung / Problem | Abhilfe |
|---|---|
| „Vorlesung-Sync läuft nicht“ / „Keine Verbindung“ | App öffnen. Claude findet sie danach von selbst wieder. |
| „Fehler 404“ | Die App ist zu alt: Vorlesung-Sync → „Nach Updates suchen …“. |
| Server fehlt in Claude Desktop | Meist ein Komma zu viel oder zu wenig in der JSON-Datei. Danach Claude ganz beenden. Log: Mac `~/Library/Logs/Claude/mcp-server-vorlesung-sync.log`, Windows `%APPDATA%\Claude\logs\`. |
| Anki-Werkzeuge fehlen | Ist Anki offen und das Add-on aktiv (Extras → Erweiterungen)? Für Claude Desktop: Node.js installiert? |
