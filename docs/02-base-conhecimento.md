# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para que serve na Sah.fin? |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Manter contexto das interações anteriores e evolução da usuária |
| `perfil_investidor.json` | JSON | Personalizar respostas com base no momento financeiro e desafios reais |
| `produtos_financeiros.json` | JSON | Explicar opções financeiras de forma simples e adequada ao perfil |
| `transacoes.csv` | CSV | Identificar padrões de gastos e sugerir melhorias práticas |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Os dados foram adaptados para refletir a realidade do público-alvo, com foco em educação financeira acessível e aplicável ao dia a dia.

Principais ajustes realizados:

- Simplificação do perfil financeiro (ex: “em organização” ao invés de “moderado”)
- Inclusão de comportamentos e desafios financeiros reais
- Adaptação da linguagem dos produtos financeiros para explicações simples
- Classificação de gastos como essenciais e não essenciais
- Inclusão de contexto emocional nas interações anteriores

Essas adaptações permitem que o agente vá além de respostas técnicas, oferecendo orientações práticas e humanizadas.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Existem duas possibilidades: injetar os dados diretamente no prompt (crtl+c, crtl+v) ou carregar os arquivos via código como no exemplo abaixo:
import pandas as pd
import json

# CSVs
historico = pd.read_csv('data/historico_atendimento.csv')
transacoes = pd.read_csv('data/transacoes.csv')

# JSONs
with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
    perfil = json.load(f)

with open('data/produtos_financeiros.json', 'r', encoding='utf-8') as f:
    produtos = json.load(f)

Os dados ficam disponíveis em memória para consultas durante toda a interação.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Os dados são utilizados de forma dinâmica, conforme a necessidade da interação:

- Perfil do usuário → incluído no contexto base (system prompt)
- Transações → analisadas para gerar insights personalizados
- Produtos financeiros → consultados para explicações educativas
- Histórico → utilizado para manter continuidade da conversa

O agente não recebe todos os dados de uma vez, mas sim apenas o contexto relevante para cada pergunta, evitando excesso de informação e melhorando a precisão das respostas.

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

Dados da Usuária:
- Nome: Maria
- Perfil: Em organização financeira
- Renda mensal: R$ 2.200

Resumo do comportamento:
- Dificuldade em controlar gastos
- Não possui reserva de emergência

Últimas transações:
- 02/10: Supermercado - R$ 320
- 05/10: Delivery - R$ 85
- 10/10: Transporte - R$ 120

Histórico recente:
- Já buscou entender Tesouro Selic
- Demonstrou interesse em criar reserva financeira

Instrução para o agente:
Responder de forma simples, sem termos técnicos, priorizando sugestões práticas e acessíveis. Evitar recomendações complexas e focar em pequenas ações que ajudem na organização financeira.
