[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

# 🧪 Awesome Skills

### Навыки ИИ-ассистента кодирования для исследователей


<br/>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-12-orange)](#skills-table)

<br/>

### 🎯 Перестаньте объяснять свой исследовательский workflow ИИ каждый раз.<br/>Напишите навык один раз. Получайте идеальные результаты навсегда.

</div>

---

### 💡 Что это?

**Awesome Skills** — тщательно подобранная коллекция [навыков ИИ-ассистента кодирования](https://kimi.ai) — многоразовые файлы инструкций, которые учат вашего ИИ-ассистента выполнять исследовательские задачи *точно* так, как вы хотите.

Вместо того чтобы писать один и тот же промпт снова и снова, вы пишете **навык один раз** — и ваш ИИ-ассистент следует ему идеально каждый раз.

---

### 😤 До и После

<table>
<tr>
<th width="50%">❌ Без навыков</th>
<th width="50%">✅ С навыками</th>
</tr>
<tr>
<td>

**Вы:** "Помогите мне написать статью в LaTeX"

**ИИ:**
- Генерирует общий шаблон LaTeX
- Отсутствует `\usepackage` для вашей области
- Нет форматирования для конкретного журнала
- Цитаты в неправильном формате
- Рисунки неправильно оформлены

*Вы тратите 30 минут на исправление всего...*

</td>
<td>

**Вы:** "Напишите мою статью, используя навык `latex-paper`"

**ИИ:**
- Использует точный шаблон целевого журнала
- Правильный формат цитирования (APA/IEEE/Nature)
- Корректные `\label` и `\ref` для всех рисунков
- Статистические тесты указаны правильно
- Код компилируется с первой попытки

*Готово к отправке за 5 минут* ✨

</td>
</tr>
<tr>
<td>

**Вы:** "Проанализируйте эти CSV-данные"

**ИИ:**
- Запускает базовый `describe()` и столбчатую диаграмму
- Нет теста нормальности, нет размера эффекта
- Отсутствуют доверительные интервалы
- Неправильный статистический тест для типа данных
* Вы переделываете весь анализ вручную

</td>
<td>

**Вы:** "Проанализируйте, используя навык `statistical-analysis`"

**ИИ:**
- Сначала проверяет распределение данных
- Выбирает правильный тест (параметрический vs непараметрический)
- Указывает размеры эффекта и ДИ
- Генерирует рисунки публикационного качества
- Выводит раздел результатов в формате APA

</td>
</tr>
</table>

---

### 🚀 Быстрый старт

Навыки — это просто **файлы инструкций**, которые говорят вашему ИИ-ассистенту, как себя вести. Поместите их в проект, и ИИ будет следовать инструкциям автоматически.

#### Cursor (.cursorrules)

```bash
# Скопируйте навык в корень проекта
cp skills/latex-paper.md .cursorrules

# Или добавьте к существующим правилам
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# Скопируйте навык в корень проекта
cp skills/latex-paper.md CLAUDE.md

# Или добавьте к существующим инструкциям
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# Скопируйте навык в корень проекта
cp skills/latex-paper.md AGENTS.md

# Или добавьте к существующим инструкциям
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **Совет:** Вы можете комбинировать несколько навыков, объединяя их в один файл!

---

<a name="skills-table"></a>

### 📚 Каталог навыков

#### 📝 Академическое письмо

| Навык | Описание | Когда использовать |
|-------|-------------|----------|
| [`latex-paper`](skills/latex-paper.md) | Написание статей в LaTeX с форматированием журнала | Написание статей для журналов или конференций |
| [`research-proposal`](skills/research-proposal.md) | Написание грантовых заявок и диссертационных предложений | Подача на финансирование или написание предложений |
| [`literature-review`](skills/literature-review.md) | Систематический обзор литературы и синтез | Обзор исследовательской области или написание обзора |
| [`academic-english`](skills/academic-english.md) | Полировка и грамматика академического английского | Полировка текста не на родном языке |

#### 📊 Анализ данных

| Навык | Описание | Когда использовать |
|-------|-------------|----------|
| [`statistical-analysis`](skills/statistical-analysis.md) | Статистические тесты с проверкой предпосылок | Анализ экспериментальных данных |
| [`data-visualization`](skills/data-visualization.md) | Рисунки публикационного качества (matplotlib/seaborn/plotly) | Создание рисунков для статей |
| [`ml-experiment`](skills/ml-experiment.md) | Отслеживание ML-экспериментов с правильными бейзлайнами | Проведение экспериментов машинного обучения |

#### 📖 Управление литературой

| Навык | Описание | Когда использовать |
|-------|-------------|----------|
| [`zotero-integration`](skills/zotero-integration.md) | Интеграция с библиографией Zotero | Управление ссылками через Zotero |
| [`citation-management`](skills/citation-management.md) | Форматирование цитат в разных стилях | Оформление ссылок для разных журналов |

#### 🔬 Инструменты экспериментов

| Навык | Описание | Когда использовать |
|-------|-------------|----------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | Чистые workflow Jupyter notebook | Запуск и организация ноутбуков |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | Воспроизводимые исследовательские среды | Настройка воспроизводимых экспериментов |

#### 📬 Отправка статей

| Навык | Описание | Когда использовать |
|-------|-------------|----------|
| [`conference-submission`](skills/conference-submission.md) | Чек-лист и форматирование для подачи на конференции | Отправка на NeurIPS, ICML, CVPR и др. |

---

### 🎬 Примеры использования

#### Пример 1: Написание полной статьи

```bash
# 1. Загрузите навык latex-paper
cp skills/latex-paper.md CLAUDE.md

# 2. Спросите вашего ИИ-ассистента
"Write a LaTeX paper for IEEE TPAMI on my transformer attention mechanism.
Include: abstract, introduction, related work, method, experiments, conclusion.
Use IEEE citation format. Reference figures as Fig. 1, Fig. 2, etc."
```

#### Пример 2: Анализ данных экспериментов

```bash
# 1. Загрузите навык statistical-analysis
cp skills/statistical-analysis.md .cursorrules

# 2. Спросите вашего ИИ-ассистента
"Analyze the data in results.csv. Compare model A vs model B performance.
Check normality, run appropriate tests, report effect sizes and CIs.
Generate a box plot for Figure 1."
```

#### Пример 3: Полный исследовательский workflow

См. [`examples/research-workflow.md`](examples/research-workflow.md) для полного workflow, объединяющего несколько навыков.

---

### ❓ FAQ

<details>
<summary><b>В: С какими ИИ-ассистентами работают эти навыки?</b></summary>

Эти навыки работают с любым ИИ-ассистентом кодирования, поддерживающим пользовательские инструкции:
- [Cursor](https://cursor.sh) через `.cursorrules`
- [Claude Code](https://claude.ai/code) через `CLAUDE.md`
- [Kimi Code](https://kimi.ai) через `AGENTS.md`
- [Windsurf](https://windsurf.ai) через `.windsurfrules`
- [Cline](https://github.com/cline/cline) через `.clinerules`
- [Aider](https://aider.chat) через `.aider.conf.yml`
- Любой ассистент, читающий файлы инструкций

</details>

<details>
<summary><b>В: Можно ли комбинировать несколько навыков?</b></summary>

Да! Просто объедините файлы навыков:

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

Или используйте их выборочно в зависимости от текущей задачи.

</details>

<details>
<summary><b>В: Чем навыки отличаются от обычных промптов?</b></summary>

Навыки:
- **Постоянные** — сохраняются в проекте, не теряются между сессиями
- **Версионируемые** — отслеживайте изменения через git
- **Многоразовые** — делитесь с командой
- **Компонуемые** — объединяйте несколько навыков
- **Проверенные** — улучшены через реальные исследовательские workflow

</details>

<details>
<summary><b>В: Можно ли изменить навыки под свою область?</b></summary>

Конечно! Навыки — это просто markdown-файлы. Форкните этот репозиторий и настройте под вашу область исследований, требования журнала или лабораторные соглашения.

</details>

<details>
<summary><b>В: Работают ли эти навыки для неанглоязычных статей?</b></summary>

Да! Навыки вроде `latex-paper` и `academic-english` можно настроить для китайского (中文), японского (日本語) и других языков. Смотрите документацию каждого навыка для доступных языков.

</details>

---

### 🔗 Также смотрите

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — Коллекция правил и настроек ИИ-ассистентов кодирования
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — Проверка качества вывода вашего ИИ-ассистента
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai) (commit-ai) — Сообщения коммитов на основе ИИ
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Коллекция серверов Model Context Protocol

---

### 🤝 Участие

Приветствуются вклады! Смотрите [CONTRIBUTING.md](CONTRIBUTING.md) для руководства.

**Способы участия:**
- 🆕 Добавьте новый навык для вашей области исследований
- 🐛 Исправьте ошибки или улучшите существующие навыки
- 📖 Улучшите документацию
- 💡 Предложите идеи новых навыков через [Issues](https://github.com/liangzhengtao/awesome-skills/issues)

---

### 📄 Лицензия

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ Наверх](#-awesome-skills)**

---
