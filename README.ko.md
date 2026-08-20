[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

# 🧪 Awesome Skills

### 연구자를 위한 AI 코딩 어시스턴트 스킬


<br/>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-12-orange)](#skills-table)

<br/>

### 🎯 매번 AI에게 연구 워크플로를 설명하지 마세요.<br/>스킬을 한 번 작성하세요. 영원히 완벽한 결과를 얻으세요.

</div>

---

### 💡 이것이 무엇인가요?

**Awesome Skills**는 [AI 코딩 어시스턴트 스킬](https://kimi.ai)의 큐레이션 컬렉션입니다 — AI 어시스턴트에게 연구 작업을 수행하는 방법을 *정확하게* 가르치는 재사용 가능한 지시 파일입니다.

같은 프롬프트를 반복적으로 작성하는 대신 **스킬을 한 번 작성하세요** — AI 어시스턴트가 매번 완벽하게 따릅니다.

---

### 😤 Before vs After

<table>
<tr>
<th width="50%">❌ 스킬 없이</th>
<th width="50%">✅ 스킬과 함께</th>
</tr>
<tr>
<td>

**당신:** "LaTeX 논문 작성을 도와주세요"

**AI:**
- 일반 LaTeX 템플릿 생성
- 분야에 맞는 `\usepackage` 누락
- 저널별 포맷 없음
- 잘못된 인용 형식
- 그림 참조가 올바르지 않음

*30분 동안 모든 것을 수정...*

</td>
<td>

**당신:** "`latex-paper` 스킬로 논문을 작성해 주세요"

**AI:**
- 대상 저널의 정확한 템플릿 사용
- 올바른 인용 형식 (APA/IEEE/Nature)
- 모든 그림에 적절한 `\label`과 `\ref`
- 통계 검정이 정확하게 보고됨
- 첫 번째 시도에 코드 컴파일 성공

*5분 만에 제출 준비 완료* ✨

</td>
</tr>
<tr>
<td>

**당신:** "이 CSV 데이터를 분석해 주세요"

**AI:**
- 기본 `describe()`와 막대 차트 실행
- 정규성 검정 없음, 효과 크기 없음
- 신뢰 구간 누락
- 데이터 유형에 맞지 않는 통계 검정
- 전체 분석을 수동으로 다시 수행

</td>
<td>

**당신:** "`statistical-analysis` 스킬로 분석해 주세요"

**AI:**
- 먼저 데이터 분포 확인
- 올바른 검정 선택 (모수적 vs 비모수적)
- 효과 크기와 신뢰 구간 보고
- 출판 수준의 그림 생성
- APA 형식의 결과 섹션 출력

</td>
</tr>
</table>

---

### 🚀 빠른 시작

스킬은 AI 어시스턴트에게 어떻게 행동할지 알려주는 **지시 파일**일 뿐입니다. 프로젝트에 넣으면 AI가 자동으로 지시를 따릅니다.

#### Cursor (.cursorrules)

```bash
# 스킬을 프로젝트 루트에 복사
cp skills/latex-paper.md .cursorrules

# 또는 기존 규칙에 추가
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# 스킬을 프로젝트 루트에 복사
cp skills/latex-paper.md CLAUDE.md

# 또는 기존 지시에 추가
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# 스킬을 프로젝트 루트에 복사
cp skills/latex-paper.md AGENTS.md

# 또는 기존 지시에 추가
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **프로 팁:** 여러 스킬을 하나의 파일로 연결하여 결합할 수 있습니다!

---

<a name="skills-table"></a>

### 📚 스킬 카탈로그

#### 📝 학술 글쓰기

| 스킬 | 설명 | 사용 시점 |
|-------|-------------|----------|
| [`latex-paper`](skills/latex-paper.md) | 저널별 포맷팅이 적용된 LaTeX 논문 작성 | 저널 또는 학회 논문 작성 |
| [`research-proposal`](skills/research-proposal.md) | 연구비 및 학위 연구 제안서 작성 | 연구비 신청 또는 학위 제안서 작성 |
| [`literature-review`](skills/literature-review.md) | 체계적 문헌 검토 및 종합 | 연구 분야 검토 또는 관련 연구 작성 |
| [`academic-english`](skills/academic-english.md) | 학술 영어 교정 및 문법 | 비원어민 영어 논문 교정 |

#### 📊 데이터 분석

| 스킬 | 설명 | 사용 시점 |
|-------|-------------|----------|
| [`statistical-analysis`](skills/statistical-analysis.md) | 적절한 가정 검정을 포함한 통계 검정 | 실험 데이터 분석 |
| [`data-visualization`](skills/data-visualization.md) | 출판 수준의 그림 (matplotlib/seaborn/plotly) | 논문용 그림 제작 |
| [`ml-experiment`](skills/ml-experiment.md) | 적절한 베이스라인을 포함한 ML 실험 추적 | 머신러닝 실험 수행 |

#### 📖 문헌 관리

| 스킬 | 설명 | 사용 시점 |
|-------|-------------|----------|
| [`zotero-integration`](skills/zotero-integration.md) | Zotero 참고문헌 통합 | Zotero로 참고문헌 관리 |
| [`citation-management`](skills/citation-management.md) | 다양한 스타일의 인용 포맷팅 | 다른 저널용 참고문헌 포맷팅 |

#### 🔬 실험 도구

| 스킬 | 설명 | 사용 시점 |
|-------|-------------|----------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | 깔끔한 Jupyter 노트북 워크플로 | 노트북 실행 및 정리 |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | 재현 가능한 연구 환경 | 재현 가능한 실험 설정 |

#### 📬 논문 제출

| 스킬 | 설명 | 사용 시점 |
|-------|-------------|----------|
| [`conference-submission`](skills/conference-submission.md) | 학회 제출 체크리스트 및 포맷팅 | NeurIPS, ICML, CVPR 등에 제출 |

---

### 🎬 사용 예시

#### 예시 1: 전체 논문 작성

```bash
# 1. latex-paper 스킬 로드
cp skills/latex-paper.md CLAUDE.md

# 2. AI 어시스턴트에게 요청
"Write a LaTeX paper for IEEE TPAMI on my transformer attention mechanism.
Include: abstract, introduction, related work, method, experiments, conclusion.
Use IEEE citation format. Reference figures as Fig. 1, Fig. 2, etc."
```

#### 예시 2: 실험 데이터 분석

```bash
# 1. statistical-analysis 스킬 로드
cp skills/statistical-analysis.md .cursorrules

# 2. AI 어시스턴트에게 요청
"Analyze the data in results.csv. Compare model A vs model B performance.
Check normality, run appropriate tests, report effect sizes and CIs.
Generate a box plot for Figure 1."
```

#### 예시 3: 완전한 연구 워크플로

여러 스킬을 결합한 전체 워크플로는 [`examples/research-workflow.md`](examples/research-workflow.md)를 참조하세요.

---

### ❓ FAQ

<details>
<summary><b>Q: 이 스킬들은 어떤 AI 어시스턴트와 함께 작동하나요?</b></summary>

이 스킬들은 사용자 정의 지시를 지원하는 모든 AI 코딩 어시스턴트에서 작동합니다:
- [Cursor](https://cursor.sh) — `.cursorrules`를 통해
- [Claude Code](https://claude.ai/code) — `CLAUDE.md`를 통해
- [Kimi Code](https://kimi.ai) — `AGENTS.md`를 통해
- [Windsurf](https://windsurf.ai) — `.windsurfrules`를 통해
- [Cline](https://github.com/cline/cline) — `.clinerules`를 통해
- [Aider](https://aider.chat) — `.aider.conf.yml`를 통해
- 지시 파일을 읽는 모든 어시스턴트

</details>

<details>
<summary><b>Q: 여러 스킬을 결합할 수 있나요?</b></summary>

네! 스킬 파일을 연결하기만 하면 됩니다:

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

또는 현재 작업에 따라 선택적으로 사용하세요.

</details>

<details>
<summary><b>Q: 프롬프트를 직접 쓰는 것과 어떻게 다른가요?</b></summary>

스킬은:
- **영구적** — 프로젝트에 저장되어 세션 간에 유지됨
- **버전 관리** — git으로 변경 사항 추적
- **재사용 가능** — 팀과 공유 가능
- **조합 가능** — 여러 스킬 결합 가능
- **검증됨** — 실제 연구 워크플로를 통해 개선됨

</details>

<details>
<summary><b>Q: 분야에 맞게 스킬을 수정할 수 있나요?</b></summary>

물론입니다! 스킬은 마크다운 파일일 뿐입니다. 이 저장소를 포크하고 연구 분야, 저널 요구사항, 실험실 규약에 맞게 커스터마이즈하세요.

</details>

<details>
<summary><b>Q: 비영어 논문에도 작동하나요?</b></summary>

네! `latex-paper`와 `academic-english` 같은 스킬은 중국어 (中文), 일본어 (日本語) 및 기타 언어로 구성할 수 있습니다. 각 스킬의 문서에서 언어 옵션을 확인하세요.

</details>

---

### 🔗 함께 보기

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — AI 코딩 어시스턴트 규칙 및 설정 큐레이션
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — AI 어시스턴트 출력 품질 검증
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai) (commit-ai) — AI 기반 컨벤션 커밋 메시지
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Model Context Protocol 서버 컬렉션

---

### 🤝 기여

기여를 환영합니다! [CONTRIBUTING.md](CONTRIBUTING.md)를 참조하세요.

**기여 방법:**
- 🆕 연구 분야에 맞는 새 스킬 추가
- 🐛 버그 수정 또는 기존 스킬 개선
- 📖 문서 개선
- 💡 [Issues](https://github.com/liangzhengtao/awesome-skills/issues)를 통해 새 스킬 아이디어 제안

---

### 📄 라이선스

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ 맨 위로 돌아가기](#-awesome-skills)**

---
