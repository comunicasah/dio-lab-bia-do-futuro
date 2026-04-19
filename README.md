# Sah.Fin - Assistente Financeira Virtual

> Desafio: Agente Financeiro Inteligente com IA Generativa

Agente de educação financeira desenvolvido para mulheres, especialmente mães solo e mães atípicas. A Sah.Fin oferece orientação financeira empática, acessível e prática, sem julgamentos e sem termos complicados.

---

## Demo

[![Assista ao pitch](https://img.shields.io/badge/▶_Assistir-Pitch-red)](https://youtube.com/shorts/O3ADdzVK4Tc)

---

## Problema que resolve

Mulheres com alta carga mental enfrentam dificuldades para organizar as finanças: falta de educação financeira prática, medo de investir e ausência de ferramentas que falem sua linguagem.

---

## Como funciona

A Sah.Fin atua como uma assistente empática que:

- Explica finanças em linguagem simples, sem termos técnicos
- Simula cenários reais ("se eu guardar R$50 por mês...")
- Ajuda na organização de gastos, metas e prioridades
- Mantém contexto da conversa para acompanhar a evolução da usuária
- Não faz recomendações sem antes entender o perfil da usuária

---

## Stack

| Componente | Tecnologia |
|---|---|
| Interface | Streamlit |
| LLM | Ollama (phi3, local) |
| Base de conhecimento | JSON + CSV mockados |

---

## Estrutura do Repositório

```
lab-agente-financeiro/
|
|-- README.md
|
|-- data/
|   |-- historico_atendimento.csv
|   |-- perfil_investidor.json
|   |-- produtos_financeiros.json
|   `-- transacoes.csv
|
|-- docs/
|   |-- 01-documentacao-agente.md
|   |-- 02-base-conhecimento.md
|   `-- 03-prompts.md
|
`-- src/
    `-- app.py
```

---

## Como rodar

**1. Instale as dependências**

```bash
pip install streamlit pandas requests
```

**2. Certifique-se que o Ollama está rodando localmente**

```bash
ollama run phi3
```

**3. Rode a aplicação**

```bash
streamlit run src/app.py
```

---

## Arquivos de dados

| Arquivo | Descrição |
|---|---|
| `perfil_investidor.json` | Perfil, metas e comportamento financeiro da usuária |
| `produtos_financeiros.json` | Produtos disponíveis com explicações simples |
| `transacoes.csv` | Histórico de gastos para análise de padrões |
| `historico_atendimento.csv` | Interações anteriores para manter contexto |

---

## Segurança e Anti-Alucinação

- Respostas baseadas apenas nos dados fornecidos
- Sem recomendações de investimento sem perfil definido
- Dados sensíveis nunca são solicitados nem compartilhados
- Quando não sabe, admite e redireciona

---

## Limitações declaradas

- Não fornece aconselhamento financeiro profissional
- Não acessa dados bancários reais
- Não realiza investimentos automáticos
- Não substitui um consultor financeiro

---

## Persona

**Nome:** Sah.Fin

**Tom:** Acolhedor, direto, conversacional e levemente motivador

**Público-alvo:** Mulheres de 25 a 45 anos, renda baixa a média, com alta carga mental e pouco conhecimento financeiro
