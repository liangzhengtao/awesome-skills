[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md)

# 🧪 Awesome Skills

### Compétences d'assistant de codage IA pour les chercheurs


<br/>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-12-orange)](#catalogue-des-compétences)

<br/>

### 🎯 Arrêtez d'expliquer votre workflow de recherche à l'IA à chaque fois.<br/>Écrivez la compétence une seule fois. Obtenez des résultats parfaits pour toujours.

---

### 💡 Qu'est-ce que c'est ?

**Awesome Skills** est une collection curatée de [compétences d'assistant de codage IA](https://kimi.ai) — des fichiers d'instructions réutilisables qui apprennent à votre assistant IA comment exécuter des tâches de recherche *exactement* comme vous le souhaitez.

Au lieu de rédiger le même prompt encore et encore, vous écrivez **une compétence une seule fois** — et votre assistant IA la suit parfaitement à chaque fois.

---

### 😤 Avant vs Après

<table>
<tr>
<th width="50%">❌ Sans compétences</th>
<th width="50%">✅ Avec compétences</th>
</tr>
<tr>
<td>

**Vous :** "Aide-moi à rédiger un article LaTeX"

**L'IA :**
- Génère un modèle LaTeX générique
- Manque les `\usepackage` de votre domaine
- Pas de formatage spécifique à la revue
- Citations dans le mauvais format
- Figures non correctement référencées

*Vous passez 30 min à tout corriger...*

</td>
<td>

**Vous :** "Rédige mon article avec la compétence `latex-paper`"

**L'IA :**
- Utilise le modèle exact de votre revue cible
- Format de citation correct (APA/IEEE/Nature)
- `\label` et `\ref` corrects pour toutes les figures
- Tests statistiques rapportés correctement
- Code compile sans erreur du premier coup

*Prêt à soumettre en 5 min* ✨

</td>
</tr>
<tr>
<td>

**Vous :** "Analyse ces données CSV"

**L'IA :**
- Exécute un `describe()` basique et un diagramme en barres
- Pas de test de normalité, pas de taille d'effet
- Intervalles de confiance manquants
- Mauvais test statistique pour votre type de données
- Vous refaites toute l'analyse manuellement

</td>
<td>

**Vous :** "Analyse avec la compétence `statistical-analysis`"

**L'IA :**
- Vérifie d'abord la distribution des données
- Sélectionne le bon test (paramétrique vs non paramétrique)
- Rapporte les tailles d'effet et les IC
- Génère des figures de qualité publication
- Produit la section résultats au format APA

</td>
</tr>
</table>

---

### 🚀 Démarrage rapide

Les compétences sont simplement des **fichiers d'instructions** qui indiquent à votre assistant IA comment se comporter. Ajoutez-les à votre projet et votre IA suivra les instructions automatiquement.

#### Cursor (.cursorrules)

```bash
# Copier la compétence dans la racine du projet
cp skills/latex-paper.md .cursorrules

# Ou ajouter aux règles existantes
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# Copier la compétence dans la racine du projet
cp skills/latex-paper.md CLAUDE.md

# Ou ajouter aux instructions existantes
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# Copier la compétence dans la racine du projet
cp skills/latex-paper.md AGENTS.md

# Ou ajouter aux instructions existantes
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **Astuce pro :** Vous pouvez combiner plusieurs compétences en les concaténant dans un seul fichier !

---

<a name="catalogue-des-compétences"></a>

### 📚 Catalogue des compétences

#### 📝 Rédaction académique

| Compétence | Description | Quand l'utiliser |
|------------|-------------|-----------------|
| [`latex-paper`](skills/latex-paper.md) | Rédaction d'articles LaTeX avec formatage par revue | Rédaction d'articles pour revues ou conférences |
| [`research-proposal`](skills/research-proposal.md) | Rédaction de propositions de subvention et de thèse | Demande de financement ou rédaction de propositions |
| [`literature-review`](skills/literature-review.md) | Revue systématique de littérature et synthèse | Exploration d'un domaine de recherche ou rédaction d'état de l'art |
| [`academic-english`](skills/academic-english.md) | Polissage de l'anglais académique et correction grammaticale | Perfectionnement de textes rédigés par des non-natifs |

#### 📊 Analyse de données

| Compétence | Description | Quand l'utiliser |
|------------|-------------|-----------------|
| [`statistical-analysis`](skills/statistical-analysis.md) | Tests statistiques avec vérification des hypothèses | Analyse de données expérimentales |
| [`data-visualization`](skills/data-visualization.md) | Figures de qualité publication (matplotlib/seaborn/plotly) | Création de figures pour articles |
| [`ml-experiment`](skills/ml-experiment.md) | Suivi d'expériences ML avec baselines appropriées | Réalisation d'expériences de machine learning |

#### 📖 Gestion de la littérature

| Compétence | Description | Quand l'utiliser |
|------------|-------------|-----------------|
| [`zotero-integration`](skills/zotero-integration.md) | Intégration bibliographique Zotero | Gestion des références avec Zotero |
| [`citation-management`](skills/citation-management.md) | Formatage des citations multi-styles | Formatage des références pour différentes revues |

#### 🔬 Outils d'expérimentation

| Compétence | Description | Quand l'utiliser |
|------------|-------------|-----------------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | Workflows Jupyter Notebook propres | Exécution et organisation de notebooks |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | Environnements de recherche reproductibles | Mise en place d'expériences reproductibles |

#### 📬 Soumission d'articles

| Compétence | Description | Quand l'utiliser |
|------------|-------------|-----------------|
| [`conference-submission`](skills/conference-submission.md) | Liste de contrôle et formatage pour soumission à conférence | Soumission à NeurIPS, ICML, CVPR, etc. |

---

### 🎬 Exemples d'utilisation

#### Exemple 1 : Rédaction d'un article complet

```bash
# 1. Charger la compétence latex-paper
cp skills/latex-paper.md CLAUDE.md

# 2. Demander à votre assistant IA
"Rédige un article LaTeX pour IEEE TPAMI sur mon mécanisme d'attention Transformer.
Inclure : résumé, introduction, état de l'art, méthode, expériences, conclusion.
Utiliser le format de citation IEEE. Référer aux figures comme Fig. 1, Fig. 2, etc."
```

#### Exemple 2 : Analyse de données expérimentales

```bash
# 1. Charger la compétence statistical-analysis
cp skills/statistical-analysis.md .cursorrules

# 2. Demander à votre assistant IA
"Analyse les données de results.csv. Compare les performances du modèle A vs modèle B.
Vérifie la normalité, exécute les tests appropriés, rapporte les tailles d'effet et les IC.
Génère un box plot pour la Figure 1."
```

#### Exemple 3 : Workflow de recherche complet

Consultez [`examples/research-workflow.md`](examples/research-workflow.md) pour un workflow de bout en bout combinant plusieurs compétences.

---

### ❓ FAQ

<details>
<summary><b>Q : Avec quels assistants IA ces compétences fonctionnent-elles ?</b></summary>

Ces compétences fonctionnent avec tout assistant de codage IA supportant les instructions personnalisées :
- [Cursor](https://cursor.sh) via `.cursorrules`
- [Claude Code](https://claude.ai/code) via `CLAUDE.md`
- [Kimi Code](https://kimi.ai) via `AGENTS.md`
- [Windsurf](https://windsurf.ai) via `.windsurfrules`
- [Cline](https://github.com/cline/cline) via `.clinerules`
- [Aider](https://aider.chat) via `.aider.conf.yml`
- Tout assistant lisant des fichiers d'instructions

</details>

<details>
<summary><b>Q : Puis-je combiner plusieurs compétences ?</b></summary>

Oui ! Il suffit de concaténer les fichiers de compétences :

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

Ou utilisez-les sélectivement selon votre tâche actuelle.

</details>

<details>
<summary><b>Q : En quoi est-ce différent de simplement écrire des prompts ?</b></summary>

Les compétences sont :
- **Persistantes** — sauvegardées dans votre projet, pas perdues entre les sessions
- **Versionnées** — suivi des modifications avec git
- **Réutilisables** — partageables avec votre équipe
- **Composables** — combinaison de plusieurs compétences
- **Testées** — perfectionnées à travers de vrais workflows de recherche

</details>

<details>
<summary><b>Q : Puis-je modifier les compétences pour mon domaine ?</b></summary>

Absolument ! Les compétences ne sont que des fichiers markdown. Fork ce dépôt et personnalisez-les pour votre domaine de recherche, vos exigences de revue ou les conventions de votre laboratoire.

</details>

<details>
<summary><b>Q : Ces compétences fonctionnent-elles pour des articles non anglophones ?</b></summary>

Oui ! Des compétences comme `latex-paper` et `academic-english` peuvent être configurées pour le chinois (中文), le japonais (日本語) et d'autres langues. Consultez la documentation de chaque compétence pour les options linguistiques.

</details>

---

### 🔗 Voir aussi

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — Collection curatée de règles et configurations d'assistants de codage IA
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — Validez la qualité de sortie de votre assistant IA
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai) (commit-ai) — Messages de commit conventionnels propulsés par l'IA
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Collection de serveurs Model Context Protocol

---

### 🤝 Contribuer

Les contributions sont les bienvenues ! Consultez [CONTRIBUTING.md](CONTRIBUTING.md) pour les directives.

**Comment contribuer :**
- 🆕 Ajouter une compétence pour votre domaine de recherche
- 🐛 Corriger des bugs ou améliorer les compétences existantes
- 📖 Améliorer la documentation
- 💡 Suggérer de nouvelles idées de compétences via [Issues](https://github.com/liangzhengtao/awesome-skills/issues)

---

### 📄 Licence

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ Retour en haut](#-awesome-skills)**

---
