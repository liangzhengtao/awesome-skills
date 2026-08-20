[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

# 🧪 Awesome Skills

### Habilidades de asistente de codificación IA para investigadores


<br/>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-12-orange)](#catálogo-de-habilidades)

<br/>

### 🎯 Deja de explicarle tu flujo de investigación a la IA cada vez.<br/>Escribe la habilidad una vez. Obtén resultados perfectos para siempre.

---

### 💡 ¿Qué es esto?

**Awesome Skills** es una colección curada de [habilidades de asistente de codificación IA](https://kimi.ai) — archivos de instrucciones reutilizables que enseñan a tu asistente IA cómo ejecutar tareas de investigación *exactamente* como tú quieres.

En lugar de escribir el mismo prompt una y otra vez, escribes **una habilidad una sola vez** — y tu asistente IA la sigue perfectamente cada vez.

---

### 😤 Antes vs Después

<table>
<tr>
<th width="50%">❌ Sin habilidades</th>
<th width="50%">✅ Con habilidades</th>
</tr>
<tr>
<td>

**Tú:** "Ayúdame a escribir un artículo en LaTeX"

**La IA:**
- Genera una plantilla LaTeX genérica
- Faltan los `\usepackage` de tu campo
- Sin formato específico de la revista
- Citas en formato incorrecto
- Figuras sin referenciar correctamente

*Pasas 30 min corrigiendo todo...*

</td>
<td>

**Tú:** "Escribe mi artículo con la habilidad `latex-paper`"

**La IA:**
- Usa la plantilla exacta de tu revista objetivo
- Formato de cita correcto (APA/IEEE/Nature)
- `\label` y `\ref` correctos para todas las figuras
- Pruebas estadísticas reportadas correctamente
- El código compila sin errores al primer intento

*Listo para enviar en 5 min* ✨

</td>
</tr>
<tr>
<td>

**Tú:** "Analiza estos datos CSV"

**La IA:**
- Ejecuta un `describe()` básico y un gráfico de barras
- Sin prueba de normalidad, sin tamaño del efecto
- Faltan intervalos de confianza
- Prueba estadística incorrecta para tu tipo de datos
- Repites todo el análisis manualmente

</td>
<td>

**Tú:** "Analiza con la habilidad `statistical-analysis`"

**La IA:**
- Primero verifica la distribución de los datos
- Selecciona la prueba correcta (paramétrica vs no paramétrica)
- Reporta tamaños del efecto e ICs
- Genera figuras de calidad publicable
- Produce la sección de resultados en formato APA

</td>
</tr>
</table>

---

### 🚀 Inicio rápido

Las habilidades son simplemente **archivos de instrucciones** que le dicen a tu asistente IA cómo comportarse. Colócalas en tu proyecto y la IA seguirá las instrucciones automáticamente.

#### Cursor (.cursorrules)

```bash
# Copiar habilidad a la raíz del proyecto
cp skills/latex-paper.md .cursorrules

# O agregar a las reglas existentes
cat skills/latex-paper.md >> .cursorrules
```

#### Claude Code (CLAUDE.md)

```bash
# Copiar habilidad a la raíz del proyecto
cp skills/latex-paper.md CLAUDE.md

# O agregar a las instrucciones existentes
cat skills/latex-paper.md >> CLAUDE.md
```

#### Kimi Code (AGENTS.md)

```bash
# Copiar habilidad a la raíz del proyecto
cp skills/latex-paper.md AGENTS.md

# O agregar a las instrucciones existentes
cat skills/latex-paper.md >> AGENTS.md
```

> 💡 **Consejo pro:** ¡Puedes combinar múltiples habilidades concatenándolas en un solo archivo!

---

<a name="catálogo-de-habilidades"></a>

### 📚 Catálogo de habilidades

#### 📝 Escritura académica

| Habilidad | Descripción | Cuándo usarla |
|-----------|-------------|---------------|
| [`latex-paper`](skills/latex-paper.md) | Escritura de artículos LaTeX con formato por revista | Escribir artículos para revistas o conferencias |
| [`research-proposal`](skills/research-proposal.md) | Escritura de propuestas de subvención y tesis | Solicitar financiación o escribir propuestas de tesis |
| [`literature-review`](skills/literature-review.md) | Revisión sistemática de literatura y síntesis | Explorar un campo de investigación o escribir el estado del arte |
| [`academic-english`](skills/academic-english.md) | Pulido del inglés académico y corrección gramatical | Perfeccionar escritos de no nativos |

#### 📊 Análisis de datos

| Habilidad | Descripción | Cuándo usarla |
|-----------|-------------|---------------|
| [`statistical-analysis`](skills/statistical-analysis.md) | Pruebas estadísticas con verificación de supuestos | Analizar datos experimentales |
| [`data-visualization`](skills/data-visualization.md) | Figuras de calidad publicable (matplotlib/seaborn/plotly) | Crear figuras para artículos |
| [`ml-experiment`](skills/ml-experiment.md) | Seguimiento de experimentos ML con baselines apropiados | Ejecutar experimentos de machine learning |

#### 📖 Gestión de literatura

| Habilidad | Descripción | Cuándo usarla |
|-----------|-------------|---------------|
| [`zotero-integration`](skills/zotero-integration.md) | Integración bibliográfica Zotero | Gestionar referencias con Zotero |
| [`citation-management`](skills/citation-management.md) | Formato de citas multi-estilo | Formatear referencias para diferentes revistas |

#### 🔬 Herramientas de experimentación

| Habilidad | Descripción | Cuándo usarla |
|-----------|-------------|---------------|
| [`jupyter-notebook`](skills/jupyter-notebook.md) | Flujos de trabajo limpios con Jupyter Notebook | Ejecutar y organizar notebooks |
| [`docker-reproducibility`](skills/docker-reproducibility.md) | Entornos de investigación reproducibles | Configurar experimentos reproducibles |

#### 📬 Envío de artículos

| Habilidad | Descripción | Cuándo usarla |
|-----------|-------------|---------------|
| [`conference-submission`](skills/conference-submission.md) | Lista de verificación y formato para envío a conferencias | Enviar a NeurIPS, ICML, CVPR, etc. |

---

### 🎬 Ejemplos de uso

#### Ejemplo 1: Escribir un artículo completo

```bash
# 1. Cargar la habilidad latex-paper
cp skills/latex-paper.md CLAUDE.md

# 2. Preguntar a tu asistente IA
"Escribe un artículo LaTeX para IEEE TPAMI sobre mi mecanismo de atención Transformer.
Incluir: resumen, introducción, trabajo relacionado, método, experimentos, conclusión.
Usar formato de cita IEEE. Referenciar figuras como Fig. 1, Fig. 2, etc."
```

#### Ejemplo 2: Analizar datos experimentales

```bash
# 1. Cargar la habilidad statistical-analysis
cp skills/statistical-analysis.md .cursorrules

# 2. Preguntar a tu asistente IA
"Analiza los datos de results.csv. Compara el rendimiento del modelo A vs modelo B.
Verifica normalidad, ejecuta pruebas apropiadas, reporta tamaños del efecto e ICs.
Genera un box plot para la Figura 1."
```

#### Ejemplo 3: Flujo de investigación completo

Consulta [`examples/research-workflow.md`](examples/research-workflow.md) para un flujo de trabajo de extremo a extremo que combina múltiples habilidades.

---

### ❓ FAQ

<details>
<summary><b>¿Con qué asistentes IA funcionan estas habilidades?</b></summary>

Estas habilidades funcionan con cualquier asistente de codificación IA que soporte instrucciones personalizadas:
- [Cursor](https://cursor.sh) vía `.cursorrules`
- [Claude Code](https://claude.ai/code) vía `CLAUDE.md`
- [Kimi Code](https://kimi.ai) vía `AGENTS.md`
- [Windsurf](https://windsurf.ai) vía `.windsurfrules`
- [Cline](https://github.com/cline/cline) vía `.clinerules`
- [Aider](https://aider.chat) vía `.aider.conf.yml`
- Cualquier asistente que lea archivos de instrucciones

</details>

<details>
<summary><b>¿Puedo combinar múltiples habilidades?</b></summary>

¡Sí! Simplemente concatena los archivos de habilidades:

```bash
cat skills/latex-paper.md skills/data-visualization.md > CLAUDE.md
```

O úsalas selectivamente según tu tarea actual.

</details>

<details>
<summary><b>¿En qué se diferencia de simplemente escribir prompts?</b></summary>

Las habilidades son:
- **Persistentes** — guardadas en tu proyecto, no se pierden entre sesiones
- **Versionadas** — seguimiento de cambios con git
- **Reutilizables** — compartibles con tu equipo
- **Componibles** — combinación de múltiples habilidades
- **Probadas** — perfeccionadas a través de flujos de investigación reales

</details>

<details>
<summary><b>¿Puedo modificar las habilidades para mi campo?</b></summary>

¡Por supuesto! Las habilidades son solo archivos markdown. Haz fork de este repositorio y personalízalas para tu área de investigación, requisitos de revista o convenciones de tu laboratorio.

</details>

<details>
<summary><b>¿Estas habilidades funcionan para artículos en otros idiomas?</b></summary>

¡Sí! Habilidades como `latex-paper` y `academic-english` pueden configurarse para chino (中文), japonés (日本語) y otros idiomas. Consulta la documentación de cada habilidad para las opciones de idioma.

</details>

---

### 🔗 Ver también

- 🤖 [awesome-ai-rules](https://github.com/nicekate/awesome-ai-rules) — Colección curada de reglas y configuraciones para asistentes de codificación IA
- ✅ [vibe-check](https://github.com/nicekate/vibe-check) — Valida la calidad de salida de tu asistente IA
- 🔄 [ai-commit](https://github.com/nicekate/commit-ai) (commit-ai) — Mensajes de commit convencionales impulsados por IA
- 🔌 [awesome-mcp-servers](https://github.com/nicekate/awesome-mcp-servers) — Colección de servidores Model Context Protocol

---

### 🤝 Contribuir

¡Las contribuciones son bienvenidas! Consulta [CONTRIBUTING.md](CONTRIBUTING.md) para las directrices.

**Formas de contribuir:**
- 🆕 Agregar una habilidad para tu área de investigación
- 🐛 Corregir bugs o mejorar habilidades existentes
- 📖 Mejorar documentación
- 💡 Sugerir nuevas ideas de habilidades vía [Issues](https://github.com/liangzhengtao/awesome-skills/issues)

---

### 📄 Licencia

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---

<div align="center">

**[⬆ Volver arriba](#-awesome-skills)**

---
