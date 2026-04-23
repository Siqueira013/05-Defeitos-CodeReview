# 📦 Relatório Final

> **Atividade:** Bug Report Profissional + Code Review Guiado
> **Curso:** Qualidade de Software
> **Professor:** Prof. Claudio Nunes

---

## 👥 Identificação da dupla

| Nome completo | RA | GitHub |
|---|---|---|
| [Guilherme Siqueira] | [227421] | [@Siqueira013] |
| [Patrick Santos] | [225469] | [@PatrickBucanero] |

**Ambiente de testes:** Chrome 121 no Windows 11, GitHub Pages do fork e edição via Codespaces (VS Code online)

---

## 📋 Sumário

- [📦 Relatório Final](#-relatório-final)
  - [👥 Identificação da dupla](#-identificação-da-dupla)
  - [📋 Sumário](#-sumário)
  - [Parte A — Bug Reports](#parte-a--bug-reports)
    - [BUG-001 — Sistema permite criar tarefa sem título](#bug-001--sistema-permite-criar-tarefa-sem-título)
    - [BUG-002 — Contagem de tarefas pendentes incorreta](#bug-002--contagem-de-tarefas-pendentes-incorreta)
    - [BUG-003 — Formulário não é limpo após envio](#bug-003--formulário-não-é-limpo-após-envio)
  - [Parte B — Code Review](#parte-b--code-review)
    - [Resumo](#resumo)
    - [Findings detalhadas](#findings-detalhadas)
    - [Finding #1](#finding-1)
    - [Finding #2](#finding-2)
    - [Finding #3](#finding-3)
    - [Finding #4](#finding-4)
    - [Finding #5](#finding-5)
    - [Finding #6](#finding-6)
  - [💭 Reflexão final](#-reflexão-final)
  - [📣 Declarações](#-declarações)
    - [Uso de IA como parceiro de trabalho](#uso-de-ia-como-parceiro-de-trabalho)
    - [Declaração de autoria](#declaração-de-autoria)

---

## Parte A — Bug Reports

(Conteúdo resumido dos principais defeitos identificados)

### BUG-001 — Sistema permite criar tarefa sem título
Problema de validação: o sistema aceita tarefas com campo obrigatório vazio.

### BUG-002 — Contagem de tarefas pendentes incorreta
Erro lógico: tarefas urgentes são contabilizadas duas vezes.

### BUG-003 — Formulário não é limpo após envio
Problema de UX: campos permanecem preenchidos após criação da tarefa.

---

## Parte B — Code Review

### Resumo

| # | Linha | Dimensão | Rótulo | Severidade |
|---|-------|----------|--------|------------|
| 1 | 10–13 | Segurança | blocker | Crítica |
| 2 | 5 | Padrões | nit | Baixa |
| 3 | 15–28 | Erros | major | Média |
| 4 | 38–97 | Complexidade | major | Alta |
| 5 | 38–136 | Padrões | major | Média |
| 6 | 30–36 | Legibilidade | nit | Baixa |

---

### Findings detalhadas

### Finding #1
SQL Injection por concatenação de string na query.

### Finding #2
Constante `TIPOS_VALIDOS` não utilizada para validação.

### Finding #3
Ausência de tratamento de erros em funções assíncronas.

### Finding #4
Alta complexidade ciclomática na função de cálculo de limite.

### Finding #5
Duplicação de lógica entre funções similares.

### Finding #6
Variáveis com nomes pouco descritivos (ex: `u`).

---

## 💭 Reflexão final

A atividade permitiu compreender, na prática, a importância de identificar defeitos tanto na execução quanto na análise estática do código. A elaboração dos bug reports reforçou a necessidade de clareza, reprodutibilidade e justificativa técnica, enquanto o code review evidenciou como problemas críticos — como falhas de segurança, ausência de tratamento de erros e alta complexidade — podem passar despercebidos sem uma análise estruturada.

Além disso, ficou evidente que boas práticas, como validação de dados, uso de padrões e escrita de código legível, são essenciais para garantir qualidade e manutenção do sistema. O exercício também mostrou como o trabalho em dupla e a revisão sistemática contribuem para uma visão mais completa do código, aproximando a atividade de um cenário real de desenvolvimento profissional.

---

## 📣 Declarações

### Uso de IA como parceiro de trabalho

- [ ] Não usamos IA nesta atividade.
- [x] Usamos IA para esclarecer conceitos teóricos.
- [x] Usamos IA para revisar a redação dos bug reports.
- [x] Usamos IA para discutir se um achado era ou não um defeito.
- [x] Uso específico: apoio na estruturação dos bug reports e code review

---

### Declaração de autoria

Declaramos que este relatório é de autoria da dupla, que exploramos pessoalmente a aplicação da Parte A e lemos o código da Parte B. As findings aqui registradas representam nosso próprio julgamento técnico.