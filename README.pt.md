[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

# 🧪 Awesome Skills

### Habilidades de Assistente de Código com IA para Pesquisadores


<br/>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-12-orange)](#skills-table)

<br/>

### 🎯 Pare de explicar seu fluxo de pesquisa para a IA toda vez.<br/>Escreva a habilidade uma vez. Obtenha resultados perfeitos para sempre.

</div>

---

### 💡 O que é isso?

**Awesome Skills** é uma coleção curada de [habilidades de assistente de código com IA](https://kimi.ai) — arquivos de instruções reutilizáveis que ensinam seu assistente de IA a realizar tarefas de pesquisa *exatamente* como você deseja.

Em vez de escrever o mesmo prompt repetidamente, você escreve **uma habilidade uma vez** — e seu assistente de IA segue perfeitamente todas as vezes.

---

### 😤 Antes vs Depois

<table>
<tr>
<th width="50%">❌ Sem Habilidades</th>
<th width="50%">✅ Com Habilidades</th>
</tr>
<tr>
<td>

**Você:** "Me ajude a escrever um artigo em LaTeX"

**IA:**
- Gera template LaTeX genérico
- Faltam `\usepackage` para sua área
- Sem formatação específica do periódico
- Citações no formato errado
- Figuras não referenciadas corretamente

*Você gasta 30 min corrigindo tudo...*

</td>
<td>

**Você:** "Escreva meu artigo usando a habilidade `latex-paper`"

**IA:**
- Usa o template exato do periódico alvo
- Formato de citação correto (APA/IEEE/Nature)
- `\label` e `\ref` adequados para todas as figuras
- Testes estatísticos reportados corretamente
- Código compila sem erros na primeira tentativa

*Pronto para submeter em 5 min* ✨

</td>
</tr>
<tr>
<td>

**Você:** "Analise estes dados CSV"

**IA:**
- Executa `describe()` básico e um gráfico de barras
- Sem teste de normalidade, sem tamanho do efeito
- Faltam intervalos de confiança
- Teste estatístico errado para seu tipo de dados
- Você refaz toda a análise manualmente

</td>
<td>

**Você:** "Analise usando a habilidade `statistical-analysis`"

**IA:**
- Verifica a distribuição dos dados primeiro
- Seleciona o teste correto (paramétrico vs não paramétrico)
- Reporta tamanhos de efeito e ICs
- Gera figuras com qualidade de publicação
- Seção de resultados formatada em APA

</td>
</tr>
</table>

---

### 🚀 Início Rápido

Habilidades são apenas **arquivos de instrução** que dizem ao seu assistente de IA como se comportar. Coloque-as em seu projeto e a IA seguirá as instruções automaticamente.

#### Cursor (.cursorrules)

```bash
# Copie a habilidade para a raiz do projeto
cp skills/latex-paper.md .cursorrules

# Ou anexe às regras existentes
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# Copie a habilidade para a raiz do projeto
cp skills/latex-paper.md CLAUDE.md

# Ou anexe às instruções existentes
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# Copie a habilidade para a raiz do projeto
cp skills/latex-paper.md AGENTS.md

# Ou anexe às instruções existentes
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **Dica profissional:** Você pode combinar múltiplas habilidades concatenando-as em um único arquivo!

---

<a name="skills-table"></a>

### 📚 Catálogo de Habilidades

#### 📝 Escrita Acadêmica

| Habilidade | Descrição | Quando Usar |
|-------|-------------|----------|
| [`latex-paper`](skills/latex-paper.md) | Escrita de artigos LaTeX com formatação específica do periódico | Escrever artigos para periódicos ou conferências |
| [`research-proposal`](skills/research-proposal.md) | Escrita de propostas de financiamento e dissertação | Candidatar-se a financiamento ou escrever propostas |
| [`literature-review`](skills/literature-review.md) | Revisão sistemática da literatura e síntese | Revisar uma área de pesquisa ou escrever trabalhos relacionados |
| [`academic-english`](skills/academic-english.md) | Polimento e gramática do inglês acadêmico | Polir escrita em inglês de não nativos |

#### 📊 Análise de Dados

| Habilidade | Descrição | Quando Usar |
|-------|-------------|----------|
| [`statistical-analysis`](skills/statistical-analysis.md) | Testes estatísticos com verificações de pressupostos | Analisar dados experimentais |
| [`data-visualization`](skills/data-visualization.md) | Figuras com qualidade de publicação (matplotlib/seaborn/plotly) | Criar figuras para artigos |
| [`ml-experiment`](skills/ml-experiment.md) | Acompanhamento de experimentos ML com baselines adequados | Executar experimentos de machine learning |

#### 📖 Gestão de Literatura

| Habilidade | Descrição | Quando Usar |
|-------|-------------|----------|
| [`zotero-integration`](skills/zotero-integration.md) | Integração com bibliografia Zotero | Gerenciar referências com Zotero |
| [`citation-management`](skills/citation-management.md) | Formatação de citações em diferentes estilos | Formatar referências para diferentes periódicos |

#### 🔬 Ferramentas de Experimentos

| Habilidade | Descrição | Quando Usar |
|-------|-------------|----------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | Fluxos de trabalho limpos com Jupyter notebook | Executar e organizar notebooks |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | Ambientes de pesquisa reproduzíveis | Configurar experimentos reproduzíveis |

#### 📬 Submissão de Artigos

| Habilidade | Descrição | Quando Usar |
|-------|-------------|----------|
| [`conference-submission`](skills/conference-submission.md) | Checklist e formatação para submissão em conferências | Submeter a NeurIPS, ICML, CVPR, etc. |

---

### 🎬 Exemplos de Uso

#### Exemplo 1: Escrevendo um Artigo Completo

```bash
# 1. Carregue a habilidade latex-paper
cp skills/latex-paper.md CLAUDE.md

# 2. Pergunte ao seu assistente de IA
"Write a LaTeX paper for IEEE TPAMI on my transformer attention mechanism.
Include: abstract, introduction, related work, method, experiments, conclusion.
Use IEEE citation format. Reference figures as Fig. 1, Fig. 2, etc."
```

#### Exemplo 2: Analisando Dados de Experimentos

```bash
# 1. Carregue a habilidade statistical-analysis
cp skills/statistical-analysis.md .cursorrules

# 2. Pergunte ao seu assistente de IA
"Analyze the data in results.csv. Compare model A vs model B performance.
Check normality, run appropriate tests, report effect sizes and CIs.
Generate a box plot for Figure 1."
```

#### Exemplo 3: Fluxo de Pesquisa Completo

Veja [`examples/research-workflow.md`](examples/research-workflow.md) para um fluxo completo de ponta a ponta combinando múltiplas habilidades.

---

### ❓ FAQ

<details>
<summary><b>P: Com quais assistentes de IA essas habilidades funcionam?</b></summary>

Essas habilidades funcionam com qualquer assistente de código com IA que suporte instruções personalizadas:
- [Cursor](https://cursor.sh) via `.cursorrules`
- [Claude Code](https://claude.ai/code) via `CLAUDE.md`
- [Kimi Code](https://kimi.ai) via `AGENTS.md`
- [Windsurf](https://windsurf.ai) via `.windsurfrules`
- [Cline](https://github.com/cline/cline) via `.clinerules`
- [Aider](https://aider.chat) via `.aider.conf.yml`
- Qualquer assistente que leia arquivos de instrução

</details>

<details>
<summary><b>P: Posso combinar múltiplas habilidades?</b></summary>

Sim! Basta concatenar os arquivos de habilidade:

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

Ou use-as seletivamente com base na sua tarefa atual.

</details>

<details>
<summary><b>P: Como essas habilidades diferem de apenas escrever prompts?</b></summary>

Habilidades são:
- **Persistentes** — salvas no seu projeto, não perdidas entre sessões
- **Versionadas** — acompanhe mudanças com git
- **Reutilizáveis** — compartilhe com sua equipe
- **Componíveis** — combine múltiplas habilidades
- **Testadas** — refinadas através de fluxos de pesquisa reais

</details>

<details>
<summary><b>P: Posso modificar as habilidades para minha área?</b></summary>

Claro! Habilidades são apenas arquivos markdown. Faça um fork deste repositório e personalize para sua área de pesquisa, requisitos do periódico ou convenções do laboratório.

</details>

<details>
<summary><b>P: Essas habilidades funcionam para artigos em outros idiomas?</b></summary>

Sim! Habilidades como `latex-paper` e `academic-english` podem ser configuradas para chinês (中文), japonês (日本語) e outros idiomas. Consulte a documentação de cada habilidade para opções de idioma.

</details>

---

### 🔗 Veja Também

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — Coleção curada de regras e configurações para assistentes de código com IA
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — Valide a qualidade da saída do seu assistente de IA
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai) (commit-ai) — Mensagens de commit convencionais com IA
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Coleção de servidores Model Context Protocol

---

### 🤝 Contribuição

Contribuições são bem-vindas! Consulte [CONTRIBUTING.md](CONTRIBUTING.md) para as diretrizes.

**Formas de contribuir:**
- 🆕 Adicione uma nova habilidade para sua área de pesquisa
- 🐛 Corrija bugs ou melhore habilidades existentes
- 📖 Melhore a documentação
- 💡 Sugira novas ideias de habilidades via [Issues](https://github.com/liangzhengtao/awesome-skills/issues)

---

### 📄 Licença

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ Voltar ao Topo](#-awesome-skills)**

---
