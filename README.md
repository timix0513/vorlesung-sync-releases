# Vorlesung-Sync

Vorlesungen aufnehmen und mit den Folien verknüpfen: Folien mitklicken, Stellen markieren
(★ klausurrelevant, ? nicht verstanden, ≡ Definition), mit dem Stift auf die Folie
schreiben. Nach der Vorlesung transkribiert die App lokal mit Whisper und ordnet jeden
Satz seiner Folie zu. Dazu ein Reader für Pflichtlektüre mit Fristen – und Claude als
Lernbegleiter, der auf all das zugreifen kann. Nichts verlässt den Rechner, ausser was
man Claude im Gespräch selbst zeigt.

Hier liegen die fertigen Versionen für Mac und Windows; die App aktualisiert sich von hier.

**Inhalt:** [Herunterladen](#herunterladen) · [Installieren](#installieren) ·
[So läuft eine Vorlesung](#so-läuft-eine-vorlesung) · [Startseite, Stundenplan und Kurse](#startseite-stundenplan-und-kurse) ·
[Aufnehmen](#aufnehmen) · [Auswertung](#auswertung) · [Nachhören](#nachhören) ·
[Lektüre und Reader](#lektüre-und-reader) · [Lernfortschritt](#lernfortschritt) ·
[Updates und Daten](#updates-und-daten) · [Mit Claude lernen (MCP)](#mit-claude-lernen-mcp)

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

Beim ersten Aufnehmen fragt die App nach dem Mikrofon. Das Whisper-Modell
(`large-v3-turbo`, 1.5 GB) lädt sie bei der ersten Transkription einmalig herunter.

## So läuft eine Vorlesung

1. **Einmal pro Semester:** Stundenplan als `.ics` importieren und den Kursen zuordnen,
   pro Kurs den Ordner angeben, in dem die Folien landen.
2. **Im Hörsaal:** Auf der Startseite steht der laufende Termin – „Aufnahme starten“.
   Folien-PDF anhängen (oder später nachreichen), mitklicken, markieren, schreiben.
3. **Danach:** „Stop & speichern“, in der Auswertung „Transkription starten“. Das
   Transkript steht dann pro Folie, die markierten Stellen mit dem, was dazu gesagt wurde.
4. **Lernen:** Nachhören, exportieren, oder Claude die Vorlesung mit dir nachbereiten
   lassen.

## Startseite, Stundenplan und Kurse

**Startseite.** Oben die Karte *Jetzt / Als Nächstes*: der laufende Termin (ab 10 Minuten
vor Beginn rot) mit „Aufnahme starten“, sonst der nächste. Laufen zwei Kurse gleichzeitig,
steht der andere darunter. Darunter die nächsten fälligen Lektüren mit Restzeit, der
Lernfortschritt, die Woche als Raster (✓ aufgenommen, blass verpasst, gestrichelt
Hinweise wie Prüfungen) und die Kurse als Kacheln. Ein Klick auf einen Termin holt ihn in
die Karte, `×` zurück zum aktuellen.

**Stundenplan.** „Stundenplan importieren…“ über der Woche liest eine Kalenderdatei
(UniPortal, Google, iCloud, Outlook). Danach ordnest du jeden Titel einem Kurs zu – als
**Vorlesung** (aufnehmbar), **Hinweis** (Prüfung, Frist) oder **ausblenden**. Die App
schlägt die Zuordnung vor, auch bei abweichenden Namen. „Neu importieren“ ersetzt die
Termine und behält die Zuordnung, „Zuordnung“ ändert sie später. Eine Aufnahme aus dem
Kalender heisst automatisch z.B. „VL05 Nachfrage I“ (Nummer + Thema).

**Kurse.** Ein Klick auf die Kachel öffnet die Kursseite: nächste Termine, Vorlesungen,
Lektüre, „Plan & Ordner“, Umbenennen, Entfernen.

- „● Aufnahme“ legt die nächste Vorlesung an (höchste VL-Nummer + 1) und nimmt sofort auf.
- „+ Kurs“ legt einen Kurs an, auch bevor es eine Vorlesung dazu gibt. Heisst ein Kurs
  nach dem Umbenennen wie ein anderer, werden beide zusammengelegt. Entfernen lässt die
  Vorlesungen stehen, nur ohne Kurs.
- „+ Vorlesung“ auf der Startseite legt eine Vorlesung von Hand an, mit oder ohne PDF.
  PowerPoint vorher als PDF exportieren. „Bearbeiten“ an einer Vorlesung ändert Titel und
  Kurs.
- **Plan & Ordner:** der Ordner, in dem die Folien des Kurses landen, und Wochentermine
  für Kurse, die nicht im Stundenplan stehen. Mit Kursordner zeigt der Recorder die
  neuesten PDFs daraus (bis zwei Ebenen tief); ein Klick hängt sie an – bewusst nicht
  automatisch, sonst landen die Folien von letzter Woche an der neuen Vorlesung.

## Aufnehmen

Der Prof klickt, du folgst – deshalb ist der Sprung zu einer Foliennummer wichtiger als
das Weiterblättern. Eine Folie darf mehrfach und in beliebiger Reihenfolge dran sein.

| Taste | Wirkung |
|---|---|
| `→` / `Leertaste` | nächste Folie |
| `←` | vorherige Folie |
| Zahl + `Enter` | direkt zu Folie N springen |
| `Home` / `End` | erste / letzte Folie |
| `M` | Stelle als klausurrelevant markieren (★) |
| `F` | Stelle als nicht verstanden markieren (?) |
| `D` | Stelle als Definition markieren (≡) |
| `⏎` / `⌫` direkt nach einem Marker | ein paar Worte dazuschreiben / Marker zurücknehmen |
| `B` / `Esc` | ins Notizfeld / zurück zu den Folien |
| `R` | Platz zum Schreiben an/aus (Rand und Papier um die Folie) |
| `V` | Fokus: nur die Folie, ohne Folienstreifen, Hinweise und Notizfeld |
| `Z` | die letzten 90 Sekunden als Text (`Esc` schliesst) |
| `Strg/⌘ Z` | letzten Strich rückgängig |

**Ohne Tastatur** (Surface mit Stift, Tablet): Leiste unten rechts mit ‹ ›, der
Foliennummer (antippen und Nummer eingeben springt), Notizfeld und Fokus; rechts mittig
die drei Marker ★ ? ≡.

**Marker.** Gedrückt wird, *nachdem* es gesagt wurde. Danach steht ein paar Sekunden eine
Bestätigung neben den Marker-Knöpfen: `⏎` bzw. „Text“ für ein paar Worte dazu („Warum
fällt die Kurve?“), `⌫` bzw. „Zurück“ nimmt den Marker zurück. Thumbnails und
Zeitstempel zeigen, wo Marker gesetzt sind.

**Notizen** stehen rechts neben der Folie, pro Folie, und werden automatisch gespeichert.
Das Feld lässt sich ausblenden (`×`); dann holt `B` es kurz her. Ein Punkt am
Notiz-Knopf zeigt, dass zur Folie etwas dasteht.

**Zeichnen.** Mit dem Stift direkt auf die Folie (Surface, Grafiktablett, zur Not die
Maus). Leiste unten links: Stift (druckempfindlich), Textmarker, Radierer, Farben,
Rückgängig. Finger zeichnen nicht, der Handballen bleibt also folgenlos. Radierer-Ende
und Seitentaste des Stifts radieren immer. Ein roter Punkt am Thumbnail zeigt Folien mit
Zeichnung.

**Platz zum Schreiben.** `R` oder der letzte Knopf der Leiste legt die Folie auf ein
weisses, kariertes Blatt mit Rand links und rechts und Papier darunter – für Herleitungen
und Tafelanschrieb. Das Blatt scrollt mit Trackpad, Mausrad oder Finger und wächst beim
Schreiben nach rechts und unten mit. Ein roter Punkt am Knopf zeigt, dass daneben oder
darunter etwas steht.

**Zoomen.** Zwei Finger, Trackpad-Pinch oder Strg/⌘ + Mausrad. Der Knopf oben rechts
(zeigt die Prozent) setzt zurück.

**Rückspulen (`Z`).** Kurz abgelenkt? `Z` zeigt die letzten 90 Sekunden als Text über der
Folie, mit „vor 40 s“ an jedem Satz; nochmal `Z` holt den neuesten Stand. „als ?
markieren“ an einem Satz setzt dort einen ?-Marker. Der Text ist nur zum Wiedereinsteigen
da; das richtige Transkript entsteht nach der Vorlesung. Auf dem Mac dauert das gut 3
Sekunden, unter Windows länger. Das kleine Modell dafür (Mac 466 MB) lädt die App beim
ersten Öffnen des Recorders im Hintergrund.

**Kein Ton.** Kommt 20 Sekunden lang nichts vom Mikrofon an oder ist es weg (Headset
abgezogen), erscheint oben eine rote Warnung, auch im Fenstertitel. „Mikrofon neu
verbinden“ holt das aktuelle Standardmikrofon, die Aufnahme läuft ohne Unterbrechung
weiter.

**Ohne Folien.** Kommen die Folien erst nach der Vorlesung: ohne PDF starten und die
Foliennummer vom Beamer eintippen. Ins Feld daneben ein paar Stichworte, was auf der
Folie steht („Malthus Kriege Tabelle“) – daran findet die App die Folie später in der
PDF. Auf der Fläche liegt leeres kariertes Papier zum Schreiben, eins pro Nummer. „Folien hinzufügen“ hängt
die PDF an, auch mitten in der Vorlesung; das Papier wandert dann unter die zugeordnete
Folie.

**Pause und später weiter.** „Pause“ hält die Aufnahme an. „Später weiter“ sichert alles
und beendet die Sitzung – die App darf zu, der Rechner neu starten. Die Vorlesung steht
dann als *pausiert* in der Übersicht, „Fortsetzen“ macht an derselben Folie und Uhrzeit
weiter. Das geht auch nach einem Absturz (*Aufnahme unterbrochen*) und über „Weiter
aufnehmen“ in der Auswertung nach einem Stop (ein vorhandenes Transkript wird dann
verworfen). Gespeichert wird laufend alle paar Sekunden – ein Absturz kostet Sekunden,
nicht die Vorlesung.

„Stop & speichern“ fragt vorher nach, damit ein Fehlklick neben „Pause“ die Vorlesung
nicht beendet. Wird ein Fenster während der Aufnahme geschlossen, warnt die App.

## Auswertung

Nach dem Stop öffnet sich die Auswertung der Vorlesung (später über die Übersicht oder
die Kursseite).

- **Transkription:** Sprache wählen, „Transkription starten“. Läuft lokal mit Whisper; auf
  dem Mac rechnet man mit etwa einem Siebtel der Aufnahmedauer, unter Windows länger. Sie
  läuft weiter, auch wenn man die Seite verlässt.
  „Neu transkribieren“ (z.B. mit anderer Sprache) ersetzt das Transkript.
- **Pro Folie:** Thumbnail, Marker, Redezeit, das Gesagte und deine Notizen. Ein Klick
  öffnet die einzelnen Sätze mit Zeitstempel (Klick spielt ab), den Satz davor und danach
  und den Folientext. Sortierbar „nach Folie“ oder „nach Redezeit“. Jeder Satz landet
  ganz bei der Folie, auf der er zur Hälfte gesagt wurde – nichts wird mitten im Satz
  zerschnitten.
- **Markierte Stellen:** alle ★ ? ≡, offene Fragen zuerst, mit Folie und dem Gesagten der
  20 Sekunden davor; ▶ spielt ab dort.
- **Folien fehlen noch:** PDF einspielen oder aus dem Kursordner wählen. Das Transkript
  wird nur neu zugeschnitten, nicht neu transkribiert.
- **Folienzuordnung:** Wurde ohne Folien aufgenommen, schlägt die App vor, welche
  PDF-Seite zu welcher getippten Nummer gehört (aus Stichworten, Gesagtem und
  Reihenfolge) – bitte prüfen, Seitenzahl ändern, „Zuordnung übernehmen“.
- **Transkript exportieren:** Markdown pro Folie, mit Notizen, Markern und Stichworten –
  gut für Obsidian, Notion oder als Vorlage für Lernkarten.
- **PDF mit Zeichnungen:** die Folien-PDF mit allen Strichen und Notizen als echte
  PDF-Anmerkungen (in Vorschau, Acrobat, GoodNotes einzeln lösch- und ausblendbar). Seiten
  mit Platz zum Schreiben werden um den beschriebenen Rand grösser, kariert wie in der App.

## Nachhören

„▶ Nachhören“ in der Auswertung: Audio mit mitlaufender Folie, Zeichnungen und
Transkript (Folie und Zeichnungen gehen auch schon ohne Transkript). Klick auf einen Satz
springt dorthin. Tempo und Stelle merkt sich die App pro Vorlesung.

| Taste | Wirkung |
|---|---|
| `Leertaste` | Abspielen / Pause |
| `←` / `→` | 10 s zurück / vor |
| `↑` / `↓` | vorige / nächste Folie |
| `+` / `-` | schneller / langsamer (1–2×) |
| `Esc` | zurück zur Auswertung |

## Lektüre und Reader

Pflichttexte lesen, markieren und die Fristen im Blick haben. Auf der Kursseite steht
dafür der Abschnitt **Lektüre**: oben die Aufgaben nach Frist mit Fortschritt und
Restzeit, darunter die Texte.

- **Texte aufnehmen:** „+ PDF“, „Aus Kursordner…“ oder PDFs auf den Abschnitt ziehen.
  Auch ein Scan mit 600 Seiten ist sofort da – Seiten entstehen erst beim Ansehen.
- **Aufgabe anlegen:** „+ Aufgabe“ – Text, PDF-Seiten von–bis und die Sitzung, bis zu der
  er gelesen sein soll. Verschiebt sich der Termin im Stundenplan, wandert die Frist mit.
  Aus einem Syllabus legt Claude die Aufgaben an (siehe [Prompts](#3-ausprobieren)).
- **Reader:** „Scrollen“ oder „Blättern“, Zoom mit −/+, Strg/⌘ + Mausrad oder Pinch. Der
  Bereich der Aufgabe ist links markiert, der Balken oben zeigt gelesene Seiten und
  Restzeit, „Weiter bei S. …“ springt zur ersten ungelesenen. Seitenzahl eintippen +
  `Enter` springt, „PDF“ öffnet das Original.
- **Markieren:** mit Maus oder Stift ein Rechteck aufziehen, dann die Art wählen – geht
  auch bei Scans ohne Text. Notiz optional, `Enter` speichert, `Esc` verwirft. Rechts
  stehen alle Stellen mit Status und gegebenenfalls Claudes Erklärung; dort lassen sie
  sich auf geklärt / offen / „im Tutorat fragen“ setzen oder entfernen.

| Taste | Wirkung |
|---|---|
| `M` / `F` / `D` | nach dem Aufziehen: ★ klausurrelevant / ? nicht verstanden / ≡ Definition |
| `T` / `E` | These / Einwand |
| `→` `Leertaste` / `←` | beim Blättern: nächste / vorige Seite |
| `Home` / `End` | erste / letzte Seite |

**Lesetempo und Restzeit.** Der Reader zählt, wie lange jede Seite im Blick ist – nur
solange das Fenster sichtbar ist und in den letzten 3 Minuten gescrollt, getippt oder
die Maus bewegt wurde. Gelesen ist eine Seite ab 15 Sekunden. Das Tempo lernt die App pro
Text (am Anfang 2,5 min pro Seite); Restzeit = ungelesene Seiten × Tempo.

## Lernfortschritt

Auf der Startseite pro Kurs: Anki-Karten nach Stufe (neu, lernend, jung, reif) und heute
fällig, ?-Stellen offen/geklärt, Begriffe, Vorlesungen und die Aktivität der letzten 14
Tage. Die Anki-Zahlen liest die App nicht selbst – Claude meldet sie über den MCP-Server
(Prompt „Anki-Stand melden“, siehe unten).

## Updates und Daten

Die App schaut beim Öffnen der Übersicht (höchstens alle 6 Stunden) hier nach einer
neueren Version; dann steht oben „Version X ist da“ mit „Was ist neu?“. Sofort geht es
über das Menü: Vorlesung-Sync → „Nach Updates suchen …“ (Windows: Hilfe → „Nach Updates
suchen …“). Ein Klick lädt das Update, die App schliesst sich und startet neu. Während
einer Aufnahme oder Transkription wird nie aktualisiert.

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
