[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

# 🧪 Awesome Skills

### KI-Coding-Assistant-Skills für Forscher


<br/>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-12-orange)](#skills-table)

<br/>

### 🎯 Erklären Sie Ihre Forschung nicht jedes Mal der KI neu.<br/>Schreiben Sie den Skill einmal. Erhalten Sie für immer perfekte Ergebnisse.

</div>

---

### 💡 Was ist das?

**Awesome Skills** ist eine kuratierte Sammlung von [KI-Coding-Assistant-Skills](https://kimi.ai) — wiederverwendbare Anweisungsdateien, die Ihrem KI-Assistenten beibringen, Forschungsaufgaben *genau* so auszuführen, wie Sie es möchten.

Anstatt immer wieder denselben Prompt zu schreiben, schreiben Sie **einmal einen Skill** — und Ihr KI-Assistent folgt ihm jedes Mal perfekt.

---

### 😤 Vorher vs Nachher

<table>
<tr>
<th width="50%">❌ Ohne Skills</th>
<th width="50%">✅ Mit Skills</th>
</tr>
<tr>
<td>

**Sie:** "Helfen Sie mir, eine LaTeX-Arbeit zu schreiben"

**KI:**
- Generiert eine generische LaTeX-Vorlage
- Fehlende `\usepackage` für Ihr Fachgebiet
- Keine zeitschriftenspezifische Formatierung
- Zitate im falschen Format
- Abbildungen nicht korrekt referenziert

*Sie verbringen 30 Minuten mit Korrekturen...*

</td>
<td>

**Sie:** "Schreiben Sie meine Arbeit mit dem Skill `latex-paper`"

**KI:**
- Verwendet die exakte Vorlage der Zielzeitschrift
- Korrektes Zitierformat (APA/IEEE/Nature)
- Korrekte `\label` und `\ref` für alle Abbildungen
- Statistische Tests korrekt berichtet
- Code kompiliert beim ersten Versuch fehlerfrei

*In 5 Minuten einreichungsbereit* ✨

</td>
</tr>
<tr>
<td>

**Sie:** "Analysieren Sie diese CSV-Daten"

**KI:**
- Führt ein einfaches `describe()` und ein Balkendiagramm aus
- Kein Normalitätstest, keine Effektgröße
- Fehlende Konfidenzintervalle
- Falscher statistischer Test für Ihren Datentyp
* Sie führen die gesamte Analyse manuell durch

</td>
<td>

**Sie:** "Analysieren Sie mit dem Skill `statistical-analysis`"

**KI:**
- Überprüft zuerst die Datenverteilung
- Wählt den richtigen Test (parametrisch vs nichtparametrisch)
- Berichtet Effektgrößen und KIs
- Erzeugt publikationsreife Abbildungen
- Ergebnisbereich in APA-Format

</td>
</tr>
</table>

---

### 🚀 Schnellstart

Skills sind einfach **Anweisungsdateien**, die Ihrem KI-Assistenten sagen, wie er sich verhalten soll. Legen Sie sie in Ihr Projekt und die KI folgt den Anweisungen automatisch.

#### Cursor (.cursorrules)

```bash
# Skill in den Projektstamm kopieren
cp skills/latex-paper.md .cursorrules

# Oder an bestehende Regeln anhängen
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# Skill in den Projektstamm kopieren
cp skills/latex-paper.md CLAUDE.md

# Oder an bestehende Anweisungen anhängen
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# Skill in den Projektstamm kopieren
cp skills/latex-paper.md AGENTS.md

# Oder an bestehende Anweisungen anhängen
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **Profi-Tipp:** Sie können mehrere Skills kombinieren, indem Sie sie in eine einzige Datei zusammenfügen!

---

<a name="skills-table"></a>

### 📚 Skill-Katalog

#### 📝 Akademisches Schreiben

| Skill | Beschreibung | Wann verwenden |
|-------|-------------|----------|
| [`latex-paper`](skills/latex-paper.md) | LaTeX-Artikelschreiben mit zeitschriftenspezifischer Formatierung | Schreiben von Zeitschriften- oder Konferenzartikeln |
| [`research-proposal`](skills/research-proposal.md) | Förderanträge und Dissertationsschreiben | Bewerbung um Fördermittel oder Verfassen von Vorschlägen |
| [`literature-review`](skills/literature-review.md) | Systematische Literaturrecherche und Synthese | Überblick über ein Forschungsgebiet oder Verfassen von Related Work |
| [`academic-english`](skills/academic-english.md) | Akademisches Englisch: Polishing und Grammatik | Verbesserung nicht-muttersprachlicher englischer Texte |

#### 📊 Datenanalyse

| Skill | Beschreibung | Wann verwenden |
|-------|-------------|----------|
| [`statistical-analysis`](skills/statistical-analysis.md) | Statistische Tests mit Voraussetzungsprüfungen | Analyse experimenteller Daten |
| [`data-visualization`](skills/data-visualization.md) | Publikationsreife Abbildungen (matplotlib/seaborn/plotly) | Erstellung von Abbildungen für Arbeiten |
| [`ml-experiment`](skills/ml-experiment.md) | ML-Experiment-Tracking mit korrekten Baselines | Durchführung von Machine-Learning-Experimenten |

#### 📖 Literaturverwaltung

| Skill | Beschreibung | Wann verwenden |
|-------|-------------|----------|
| [`zotero-integration`](skills/zotero-integration.md) | Zotero-Bibliografie-Integration | Verwaltung von Referenzen mit Zotero |
| [`citation-management`](skills/citation-management.md) | Zitationsformatierung über verschiedene Stile | Formatierung von Referenzen für verschiedene Zeitschriften |

#### 🔬 Experiment-Tools

| Skill | Beschreibung | Wann verwenden |
|-------|-------------|----------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | Saubere Jupyter-Notebook-Workflows | Ausführung und Organisation von Notebooks |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | Reproduzierbare Forschungsumgebungen | Einrichtung reproduzierbarer Experimente |

#### 📬 Paper-Einreichung

| Skill | Beschreibung | Wann verwenden |
|-------|-------------|----------|
| [`conference-submission`](skills/conference-submission.md) | Checkliste und Formatierung für Konferenzeinreichungen | Einreichung bei NeurIPS, ICML, CVPR usw. |

---

### 🎬 Anwendungsbeispiele

#### Beispiel 1: Eine vollständige Arbeit schreiben

```bash
# 1. Laden Sie den latex-paper Skill
cp skills/latex-paper.md CLAUDE.md

# 2. Fragen Sie Ihren KI-Assistenten
"Write a LaTeX paper for IEEE TPAMI on my transformer attention mechanism.
Include: abstract, introduction, related work, method, experiments, conclusion.
Use IEEE citation format. Reference figures as Fig. 1, Fig. 2, etc."
```

#### Beispiel 2: Experimentdaten analysieren

```bash
# 1. Laden Sie den statistical-analysis Skill
cp skills/statistical-analysis.md .cursorrules

# 2. Fragen Sie Ihren KI-Assistenten
"Analyze the data in results.csv. Compare model A vs model B performance.
Check normality, run appropriate tests, report effect sizes and CIs.
Generate a box plot for Figure 1."
```

#### Beispiel 3: Kompletter Forschungs-Workflow

Siehe [`examples/research-workflow.md`](examples/research-workflow.md) für einen vollständigen End-to-End-Workflow mit mehreren Skills.

---

### ❓ FAQ

<details>
<summary><b>F: Mit welchen KI-Assistenten funktionieren diese Skills?</b></summary>

Diese Skills funktionieren mit jedem KI-Coding-Assistenten, der benutzerdefinierte Anweisungen unterstützt:
- [Cursor](https://cursor.sh) über `.cursorrules`
- [Claude Code](https://claude.ai/code) über `CLAUDE.md`
- [Kimi Code](https://kimi.ai) über `AGENTS.md`
- [Windsurf](https://windsurf.ai) über `.windsurfrules`
- [Cline](https://github.com/cline/cline) über `.clinerules`
- [Aider](https://aider.chat) über `.aider.conf.yml`
- Jeder Assistent, der Anweisungsdateien liest

</details>

<details>
<summary><b>F: Kann ich mehrere Skills kombinieren?</b></summary>

Ja! Verketten Sie einfach die Skill-Dateien:

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

Oder verwenden Sie sie selektiv basierend auf Ihrer aktuellen Aufgabe.

</details>

<details>
<summary><b>F: Wie unterscheiden sich diese Skills von einfachen Prompts?</b></summary>

Skills sind:
- **Persistent** — in Ihrem Projekt gespeichert, nicht zwischen Sitzungen verloren
- **Versionskontrolliert** — Änderungen mit git nachverfolgbar
- **Wiederverwendbar** — mit Ihrem Team teilbar
- **Kombinierbar** — mehrere Skills zusammenstellbar
- **Getestet** — durch echte Forschungs-Workflows verfeinert

</details>

<details>
<summary><b>F: Kann ich die Skills für mein Fachgebiet anpassen?</b></summary>

Natürlich! Skills sind nur Markdown-Dateien. Forken Sie dieses Repository und passen Sie es an Ihre Forschungsrichtung, Zeitschriftenanforderungen oder Laborrichtlinien an.

</details>

<details>
<summary><b>F: Funktionieren diese Skills für nicht-englische Arbeiten?</b></summary>

Ja! Skills wie `latex-paper` und `academic-english` können für Chinesisch (中文), Japanisch (日本語) und andere Sprachen konfiguriert werden. Siehe die Dokumentation jedes Skills für Sprachoptionen.

</details>

---

### 🔗 Siehe auch

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — Kuratierte Sammlung von KI-Coding-Assistant-Regeln und Konfigurationen
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — Validieren Sie die Ausgabequalität Ihres KI-Assistenten
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai) (commit-ai) — KI-gesteuerte Convention-Commit-Nachrichten
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Model Context Protocol Server-Sammlung

---

### 🤝 Mitwirken

Beiträge sind willkommen! Siehe [CONTRIBUTING.md](CONTRIBUTING.md) für Richtlinien.

**Möglichkeiten zum Mitwirken:**
- 🆕 Fügen Sie einen neuen Skill für Ihr Forschungsgebiet hinzu
- 🐛 Beheben Sie Bugs oder verbessern Sie bestehende Skills
- 📖 Verbessern Sie die Dokumentation
- 💡 Schlagen Sie neue Skill-Ideen über [Issues](https://github.com/liangzhengtao/awesome-skills/issues) vor

---

### 📄 Lizenz

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ Zurück nach oben](#-awesome-skills)**

---
