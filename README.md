# Second Brain Template

Eine schlanke Vorlage für ein persönliches Second Brain mit [Obsidian](https://obsidian.md), lokaler Stichwortsuche über [QMD](https://github.com/tobi/qmd) und [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) als Arbeitsassistent.

> Diese Vorlage enthält nur generische Struktur und ausdrücklich fiktive Beispielnotizen. Sie enthält keine echten persönlichen Daten.

## Zweck

- Wissen dauerhaft in einfachen Markdown-Dateien sammeln.
- Claude gezielt suchen und nur passende Notizen lesen lassen, statt den ganzen Vault zu laden.
- Feste Arbeitsregeln für KI-Assistenten in einer `CLAUDE.md` festhalten.

## Architektur

```
Obsidian-Vault (Markdown-Dateien)   ← speichert das Wissen
        │
        ▼
QMD (lokaler Index, Stichwortsuche) ← durchsucht das Wissen
        │
        ▼
Claude Code (liest CLAUDE.md)       ← sucht mit QMD, liest gezielt, antwortet mit Quellen
```

- **Obsidian** speichert das Wissen als Markdown-Dateien in einem Ordner (dem Vault).
- **QMD** indexiert diesen Ordner lokal und durchsucht ihn.
- **Claude Code** folgt den Regeln in `CLAUDE.md`: erst mit QMD suchen, dann nur relevante Abschnitte lesen und die Quelle nennen.
- **Notion** ist optional und eine getrennte Wissensquelle. Es gibt keine automatische Synchronisation zwischen Notion und Obsidian.

### Ordnerstruktur

| Ordner | Zweck |
|---|---|
| `00 Eingang` | Neue, noch unsortierte Inhalte |
| `10 Persönliches` | Kontext über die eigene Person, Werkzeuge, Vorlieben |
| `20 Projekte` | Laufende Vorhaben mit Ziel |
| `30 Wissen` | Dauerhaftes, projektunabhängiges Wissen und Regeln |
| `40 Dokumente` | Originaldokumente und Quellen |
| `90 Archiv` | Abgeschlossenes, das erhalten bleiben soll |

## Voraussetzungen

- macOS (andere Systeme sind möglich, aber hier nicht dokumentiert)
- [Obsidian](https://obsidian.md)
- Node.js ≥ 22 (laut QMD-Dokumentation)
- [QMD](https://github.com/tobi/qmd) als **externe Abhängigkeit**
- [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) mit einem Claude-Konto

### Externe Abhängigkeit: QMD

QMD ist ein eigenständiges Open-Source-Projekt von Dritten: <https://github.com/tobi/qmd>. Es wird als Softwarepaket (`@tobilu/qmd`) installiert. **Der Quellcode von QMD ist in diesem Repository nicht enthalten.** Für Installation, Lizenz und Updates gilt das offizielle QMD-Repository.

## Installation

Kurzfassung (Details in [QUICKSTART.md](QUICKSTART.md)):

```bash
npm install -g @tobilu/qmd
git clone https://github.com/<GITHUB_NUTZER>/second-brain-template.git "<VAULT_PFAD>"
qmd collection add "<VAULT_PFAD>" --name second-brain
```

Danach den Ordner `<VAULT_PFAD>` in Obsidian als Vault öffnen.

## Nutzung

Stichwortsuche:

```bash
qmd search "<Suchbegriffe>" -c second-brain
```

Index nach Änderungen an Notizen aktualisieren:

```bash
qmd update
```

Claude Code im Vault starten. Claude liest dann automatisch die `CLAUDE.md`:

```bash
cd "<VAULT_PFAD>" && claude
```

**Zum Einstieg wird nur die Stichwortsuche (`qmd search`) verwendet.** `qmd embed`, `qmd vsearch` und `qmd query` nutzen lokale Sprachmodelle, die beim ersten Gebrauch heruntergeladen werden. Sie sind für dieses Grundsetup nicht nötig.

### Notion (optional)

Notion kann zusätzlich als getrennte Quelle angebunden werden, etwa über den Notion-Konnektor des Claude-Kontos. Diese Vorlage richtet keine Notion-Verbindung ein und synchronisiert nichts automatisch. Notion-Inhalte werden nur auf ausdrücklichen Auftrag lokal gespeichert, mit Quellenlink.

## Grenzen

- **Eine Tokenersparnis wurde nicht gemessen.** Gezieltes Suchen soll unnötigen Kontext vermeiden, belegt ist das für dieses Setup nicht.
- Die Stichwortsuche findet nur Begriffe, die in den Notizen vorkommen. Keine Treffer bedeutet nicht, dass die Information fehlt: andere Suchbegriffe versuchen.
- Kostenpflichtige Dienste sind für das dokumentierte Grundsetup nicht erforderlich. Die Nutzung von Claude unterliegt dem jeweiligen Tarif.
- Keine Backups, keine Verschlüsselung, keine Synchronisation zwischen Geräten. Darum muss man sich selbst kümmern.
- Die Regeln in `CLAUDE.md` sind Anweisungen an den Assistenten, keine technische Zugriffssperre.

## Datenschutz

Diese Vorlage ist für den Start gedacht. Ein damit befüllter persönlicher Vault sollte **nicht** in ein öffentliches Repository hochgeladen werden. Die `.gitignore` schließt Obsidian-Einstellungen, Suchindizes und Modelle aus, schützt aber nicht vor privaten Inhalten in Notizen.

## Lizenz

Die Vorlagendateien in diesem Repository stehen unter der [MIT-Lizenz](LICENSE). QMD, Obsidian, Claude Code und Notion unterliegen ihren eigenen Lizenzen und Bedingungen.
