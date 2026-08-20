[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

# 🧪 Awesome Skills

### 研究者向け AI コーディングアシスタントスキル


<br/>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-12-orange)](#スキル一覧)

<br/>

### 🎯 もう毎回 AI に研究ワークフローを説明する必要はない。<br/>スキルを一度書けば、ずっと完璧な結果が得られる。

---

### 💡 これは何？

**Awesome Skills** は、[AI コーディングアシスタントスキル](https://kimi.ai)のキュレーションコレクションです——あなたの AI アシスタントに、研究タスクを*あなたの望む通りに*実行する方法を教える再利用可能な指示ファイルです。

同じプロンプトを何度も書く代わりに、**一度スキルを書けば**——AI アシスタントは毎回完璧に従います。

---

### 😤 使用前 vs 使用後

<table>
<tr>
<th width="50%">❌ スキルなし</th>
<th width="50%">✅ スキルあり</th>
</tr>
<tr>
<td>

**あなた：** "LaTeX 論文を書いて"

**AI：**
- 汎用テンプレートを生成
- あなたの分野に必要な `\usepackage` が不足
- ジャーナル固有のフォーマットなし
- 引用形式が間違っている
- 図が正しく参照されていない

*あなたは 30 分かけて修正...*

</td>
<td>

**あなた：** "`latex-paper` スキルで論文を書いて"

**AI：**
- ターゲットジャーナルの正確なテンプレートを使用
- 正しい引用形式（APA/IEEE/Nature）
- すべての図に適切な `\label` と `\ref`
- 統計検定が正しく報告される
- 初回コンパイルでエラーなし

*5 分で投稿準備完了* ✨

</td>
</tr>
<tr>
<td>

**あなた：** "この CSV データを分析して"

**AI：**
- 基本的な `describe()` と棒グラフを実行
- 正態性検定なし、効果量なし
- 信頼区間が不足
- データタイプに合わない統計検定
- 全分析を手動でやり直し

</td>
<td>

**あなた：** "`statistical-analysis` スキルで分析して"

**AI：**
- まずデータ分布を確認
- 正しい検定を選択（パラメトリック vs ノンパラメトリック）
- 効果量と信頼区間を報告
- 出版品質の図表を生成
- APA 形式の結果セクションを出力

</td>
</tr>
</table>

---

### 🚀 クイックスタート

スキルは AI アシスタントの振る舞い方を指示する**指示ファイル**にすぎません。プロジェクトに入れれば、AI が自動的に指示に従います。

#### Cursor (.cursorrules)

```bash
# スキルをプロジェクトルートにコピー
cp skills/latex-paper.md .cursorrules

# 既存のルールに追加
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# スキルをプロジェクトルートにコピー
cp skills/latex-paper.md CLAUDE.md

# 既存の指示に追加
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# スキルをプロジェクトルートにコピー
cp skills/latex-paper.md AGENTS.md

# 既存の指示に追加
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **プロのヒント：** 複数のスキルを結合して 1 つのファイルにまとめることができます！

---

<a name="スキル一覧"></a>

### 📚 スキルカタログ

#### 📝 学術執筆

| スキル | 説明 | 使用場面 |
|--------|------|----------|
| [`latex-paper`](skills/latex-paper.md) | ジャーナル固有のフォーマットで LaTeX 論文を執筆 | ジャーナルや会議論文の執筆 |
| [`research-proposal`](skills/research-proposal.md) | 基金申請と学位論文の研究計画書の執筆 | 資金申請または研究計画書の執筆 |
| [`literature-review`](skills/literature-review.md) | 体系的文献レビューと総合 | 研究分野の調査または関連研究の執筆 |
| [`academic-english`](skills/academic-english.md) | 学術英語の推敲と文法修正 | 非ネイティブ英語の推敲 |

#### 📊 データ分析

| スキル | 説明 | 使用場面 |
|--------|------|----------|
| [`statistical-analysis`](skills/statistical-analysis.md) | 適切な仮定確認を伴う統計検定 | 実験データの分析 |
| [`data-visualization`](skills/data-visualization.md) | 出版品質の図表（matplotlib/seaborn/plotly） | 論文用図表の作成 |
| [`ml-experiment`](skills/ml-experiment.md) | 適切なベースラインを伴う ML 実験管理 | 機械学習実験の実行 |

#### 📖 文献管理

| スキル | 説明 | 使用場面 |
|--------|------|----------|
| [`zotero-integration`](skills/zotero-integration.md) | Zotero 文献データベース連携 | Zotero での文献管理 |
| [`citation-management`](skills/citation-management.md) | 複数形式の引用管理 | 異なるジャーナル向け引用のフォーマット |

#### 🔬 実験ツール

| スキル | 説明 | 使用場面 |
|--------|------|----------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | クリーンな Jupyter Notebook ワークフロー | Notebook の実行と整理 |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | 再現可能な研究環境 | 再現可能な実験環境の構築 |

#### 📬 論文投稿

| スキル | 説明 | 使用場面 |
|--------|------|----------|
| [`conference-submission`](skills/conference-submission.md) | 会議投稿チェックリストとフォーマット | NeurIPS、ICML、CVPR などへの投稿 |

---

### 🎬 使用例

#### 例 1：フルペーパーの執筆

```bash
# 1. latex-paper スキルを読み込む
cp skills/latex-paper.md CLAUDE.md

# 2. AI アシスタントに依頼
"IEEE TPAMI 向けに Transformer 注意力メカニズムの LaTeX 論文を書いて。
含めるもの：要旨、序論、関連研究、手法、実験、結論。
IEEE 引用形式を使用。図の参照は Fig. 1, Fig. 2 等とする。"
```

#### 例 2：実験データの分析

```bash
# 1. statistical-analysis スキルを読み込む
cp skills/statistical-analysis.md .cursorrules

# 2. AI アシスタントに依頼
"results.csv のデータを分析。モデル A とモデル B の性能を比較。
正態性を確認し、適切な検定を実行、効果量と信頼区間を報告。
図 1 のボックスプロットを生成。"
```

#### 例 3：完全な研究ワークフロー

複数のスキルを組み合わせた完全なエンドツーエンドワークフローは [`examples/research-workflow.md`](examples/research-workflow.md) を参照してください。

---

### ❓ FAQ

<details>
<summary><b>Q：これらのスキルはどの AI アシスタントで使えますか？</b></summary>

これらのスキルは、カスタム指示をサポートするすべての AI コーディングアシスタントで動作します：
- [Cursor](https://cursor.sh) `.cursorrules` 経由
- [Claude Code](https://claude.ai/code) `CLAUDE.md` 経由
- [Kimi Code](https://kimi.ai) `AGENTS.md` 経由
- [Windsurf](https://windsurf.ai) `.windsurfrules` 経由
- [Cline](https://github.com/cline/cline) `.clinerules` 経由
- [Aider](https://aider.chat) `.aider.conf.yml` 経由
- 指示ファイルを読み込むすべてのアシスタント

</details>

<details>
<summary><b>Q：複数のスキルを組み合わせられますか？</b></summary>

はい！スキルファイルを結合するだけです：

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

または現在のタスクに基づいて選択的に使用できます。

</details>

<details>
<summary><b>Q：プロンプトを書くのとはどう違うのですか？</b></summary>

スキルには以下の特徴があります：
- **永続的** — プロジェクトに保存され、セッション間で失われない
- **バージョン管理対応** — git で変更を追跡
- **再利用可能** — チームと共有
- **合成可能** — 複数のスキルを組み合わせ
- **テスト済み** — 実際の研究ワークフローで磨き上げられた

</details>

<details>
<summary><b>Q：自分の分野に合わせてスキルを変更できますか？</b></summary>

もちろんです！スキルは単なる Markdown ファイルです。このリポジトリをフォークして、あなたの研究分野、ジャーナル要件、またはラボの規約に合わせてカスタマイズしてください。

</details>

<details>
<summary><b>Q：非英語論文でも使えますか？</b></summary>

はい！`latex-paper` や `academic-english` などのスキルは、中国語（中文）、日本語（日本語）、その他の言語に設定できます。各スキルのドキュメントで言語オプションを確認してください。

</details>

---

### 🔗 関連プロジェクト

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — AI コーディングアシスタントのルールと設定のキュレーションコレクション
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — AI アシスタントの出力品質を検証
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai)（commit-ai）— AI 搭載の Conventional Commit メッセージ
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Model Context Protocol サーバーコレクション

---

### 🤝 コントリビュート

コントリビューションを歓迎します！ガイドラインは [CONTRIBUTING.md](CONTRIBUTING.md) をご覧ください。

**コントリビュートの方法：**
- 🆕 あなたの研究分野のスキルを追加
- 🐛 バグ修正や既存スキルの改善
- 📖 ドキュメントの改善
- 💡 [Issues](https://github.com/liangzhengtao/awesome-skills/issues) で新しいスキルのアイデアを提案

---

### 📄 ライセンス

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ トップに戻る](#-awesome-skills)**

---
