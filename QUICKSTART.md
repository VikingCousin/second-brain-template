# Quickstart (macOS)

Platzhalter in dieser Anleitung:

- `<VAULT_PFAD>`: Ordner, in dem dein Vault liegen soll, z. B. `~/Documents/Second Brain`
- `<GITHUB_NUTZER>`: GitHub-Konto, unter dem die Vorlage liegt

## 1. Voraussetzungen prüfen

```bash
node --version
```

QMD verlangt laut seiner Dokumentation Node.js ≥ 22. Fehlt Node.js, installiere es z. B. von <https://nodejs.org>. Die QMD-Dokumentation nennt für macOS zusätzlich Homebrew-SQLite (`brew install sqlite`); prüfe dort den aktuellen Stand.

Obsidian gibt es unter <https://obsidian.md>, Claude Code unter <https://docs.claude.com/en/docs/claude-code/overview>.

## 2. QMD installieren (externe Abhängigkeit)

```bash
npm install -g @tobilu/qmd
```

```bash
qmd --version
```

QMD ist ein externes Projekt: <https://github.com/tobi/qmd>. Sein Quellcode ist hier nicht enthalten.

## 3. Vorlage holen

Entweder auf GitHub „Use this template“ wählen oder klonen:

```bash
git clone https://github.com/<GITHUB_NUTZER>/second-brain-template.git "<VAULT_PFAD>"
```

Willst du deinen Vault später nicht mit Git verwalten, entferne den Ordner `.git` im neuen Vault.

## 4. In Obsidian öffnen

Obsidian starten → „Ordner als Vault öffnen“ → `<VAULT_PFAD>` wählen. Obsidian legt dabei seinen eigenen Ordner `.obsidian` an.

## 5. Suchindex anlegen

```bash
qmd collection add "<VAULT_PFAD>" --name second-brain
```

```bash
qmd search "Beispiel" -c second-brain
```

Die fiktiven Beispielnotizen sollten als Treffer erscheinen.

## 6. Claude Code im Vault nutzen

```bash
cd "<VAULT_PFAD>" && claude
```

Claude Code liest die `CLAUDE.md` im Vault und arbeitet nach ihren Regeln.

## 7. Aufräumen

Lösche die als „Beispiel“ markierten Notizen, sobald du eigene Inhalte hast. Nach Änderungen:

```bash
qmd update
```

## Nicht Teil des Grundsetups

- `qmd embed`, `qmd vsearch`, `qmd query`: laden lokale Modelle herunter.
- Notion-Anbindung: optional, ohne automatische Synchronisation.
