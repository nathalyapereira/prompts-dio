# 🤖 Agentes de Carreira em Tecnologia — DIO

> Sistema multiagente para descoberta de perfil profissional e planejamento de carreira em tecnologia, desenvolvido com prompts de IA para o bootcamp da [DIO](https://dio.me).

---

## 📋 Visão Geral

Este repositório contém dois agentes de IA que trabalham em conjunto para guiar o usuário desde a **descoberta do seu perfil profissional** até a **criação de um plano de estudos personalizado** em tecnologia.

```
Usuário → [Agent 1: Entrevistador] → [Agent 2: Planejador] → Roadmap Personalizado
```

---

## 🧩 Agentes

### 🟣 Agent 1 — Entrevistador de Carreira

**Objetivo:** Conduzir uma entrevista estruturada para identificar o perfil do usuário e sugerir as melhores carreiras em tecnologia.

**Como funciona:**

O agente realiza **7 perguntas sequenciais** (uma por vez) para mapear:

| # | Tema da Pergunta |
|---|-----------------|
| 1 | O que atrai o usuário em tecnologia |
| 2 | Experiência prévia na área |
| 3 | Disponibilidade de horas por semana |
| 4 | Preferência de trabalho (pessoas, dados ou código) |
| 5 | Objetivo principal (emprego, transição ou crescimento) |
| 6 | Assuntos e tecnologias de interesse |
| 7 | Experiências anteriores aproveitáveis |

Após coletar as respostas, o agente aplica uma **matriz de decisão interna** (pontuação de 0 a 20) e apresenta as **3 carreiras mais compatíveis** com o perfil, ranqueadas e detalhadas com vantagens, desafios e contexto de mercado.

**Handoff:** Quando o usuário escolhe uma carreira, o Agent 1 transfere os dados do perfil para o Agent 2.

**Regras importantes:**
- Faz **apenas 1 pergunta por vez**
- Para após as 7 perguntas — sem perguntas extras
- **Não gera planos de estudo** (responsabilidade do Agent 2)
- **Não cita salários específicos**

---

### 🟢 Agent 2 — Planejador de Roadmap

**Objetivo:** Receber o perfil coletado pelo Agent 1 e gerar um **plano completo e personalizado** de estudos para a carreira escolhida.

**Dados recebidos do Agent 1:**

| Campo | Descrição |
|-------|-----------|
| `CARREIRA_ESCOLHIDA` | Carreira selecionada pelo usuário |
| `HORAS_SEMANA` | Disponibilidade semanal de estudo |
| `EXPERIENCIA` | Nível: zero / iniciante / alguma |
| `OBJETIVO` | Primeiro emprego / transição / crescimento |
| `PREFERENCIA` | Pessoas / dados / código |
| `INTERESSES` | Tecnologias mencionadas |

**O que o agente entrega:**

```
🧩 Visão do Dia a Dia       → Atividades típicas da carreira
🧠 Mapa de Skills           → Core skills + nice-to-have + ferramentas
📅 Roadmap de 90 Dias       → Semana a semana, adaptado às horas disponíveis
🚀 Projeto de Portfólio     → Projeto prático com escopo e entregáveis definidos
💬 Roteiro de Entrevistas   → 5 perguntas comuns júnior com exemplos de resposta
🎓 Trilha DIO Recomendada   → Bootcamp ou trilha específica na plataforma DIO
```

**Personalização automática por perfil:**

| Disponibilidade | Adaptação |
|-----------------|-----------|
| Menos de 5h/semana | Prazos estendidos, foco no essencial |
| 5–10h/semana | Roadmap padrão de 90 dias |
| Mais de 15h/semana | Conteúdo extra e projetos avançados |

| Experiência | Adaptação |
|-------------|-----------|
| Zero | Explicações didáticas, fundamentos reforçados |
| Iniciante | Equilíbrio entre teoria e prática |
| Alguma | Foco em gaps específicos e portfólio |

| Objetivo | Adaptação |
|----------|-----------|
| Primeiro emprego | Ênfase em portfólio e entrevistas |
| Transição | Destaque para transferência de skills |
| Crescimento | Foco em habilidades avançadas |

---

## 🔄 Fluxo Completo

```
                    ┌─────────────────────────────┐
                    │         AGENT 1             │
                    │      Entrevistador          │
                    │                             │
                    │  7 perguntas sequenciais    │
                    │        ↓                    │
                    │  Análise de perfil          │
                    │        ↓                    │
                    │  3 carreiras ranqueadas     │
                    │        ↓                    │
                    │  Usuário escolhe 1          │
                    └────────────┬────────────────┘
                                 │ handoff com dados do perfil
                                 ▼
                    ┌─────────────────────────────┐
                    │         AGENT 2             │
                    │        Planejador           │
                    │                             │
                    │  Recebe perfil completo     │
                    │        ↓                    │
                    │  Gera plano personalizado   │
                    │        ↓                    │
                    │  Roadmap de 90 dias pronto  │
                    └─────────────────────────────┘
```

---

## 🛠️ Como Usar

1. Copie o prompt do **Agent 1** e cole em uma plataforma de IA (ex: ChatGPT, Copilot Studio, Claude)
2. Responda as 7 perguntas da entrevista
3. Escolha uma das 3 carreiras sugeridas
4. Copie o prompt do **Agent 2** em uma nova conversa (ou configure o handoff na plataforma)
5. Informe os dados do seu perfil e receba seu roadmap personalizado

---

## 🎓 Sobre o Projeto

Projeto desenvolvido durante o bootcamp **CI&T — Do Prompt ao Agente** na plataforma [DIO](https://dio.me), com foco em engenharia de prompt e construção de agentes de IA aplicados a casos de uso reais.
