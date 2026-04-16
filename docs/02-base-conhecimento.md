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

```python
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
```

Os dados ficam disponíveis em memória para consultas durante toda a interação.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?
Para simplificar, podemos simplesmente injetar os dados em nosso prompt, garantindo que o Agente tenha o melhor contexto possível. Lembrand que em soluções mais robustas, o ideal é que essas informações carregadas dinamicamente para que possamos ganhar flexibilidade.

Os dados são utilizados de forma dinâmica, conforme a necessidade da interação:

- Perfil do usuário → incluído no contexto base (system prompt)
- Transações → analisadas para gerar insights personalizados
- Produtos financeiros → consultados para explicações educativas
- Histórico → utilizado para manter continuidade da conversa

O agente não recebe todos os dados de uma vez, mas sim apenas o contexto relevante para cada pergunta, evitando excesso de informação e melhorando a precisão das respostas.

---

## Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.
```text
Dados e Perfil do Cliente (perfil_investidor.json):
{
  "nome": "Maria Soares",
  "idade": 34,
  "profissao": "Auxiliar Administrativo",
  "renda_mensal": 2200.00,
  "perfil_investidor": "em construção",
  "objetivo_principal": "Construir reserva de emergência",
  "patrimonio_total": 2000.00,
  "reserva_emergencia_atual": 500.00,
  "aceita_risco": false,
 "desafios": [
    "Dificuldade em guardar dinheiro",
    "Gastos frequentes com alimentação fora de casa",
    "Falta de planejamento mensal"
  ],
  "comportamento_financeiro": {
    "controle_gastos": false,
    "costuma_parcelar": true,
    "tem_reserva": false
  },
  "metas": [
    {
      "meta": "Montar reserva de emergência",
      "valor_necessario": 6000.00,
      "prazo": "2026-12"
    },
    {
      "meta": "Quitar dívidas",
      "valor_necessario": 1500.00,
      "prazo": "2026-08"
    }
  ]
}
```


Transações (transacoes.csv):
```
data,descricao,categoria,valor,tipo,essencial
2025-10-01,Salário,receita,5000.00,entrada,sim
2025-10-02,Aluguel,moradia,1200.00,saida,sim
2025-10-03,Supermercado,alimentacao,450.00,saida,sim
2025-10-05,Netflix,lazer,55.90,saida,nao
2025-10-07,Farmácia,saude,89.00,saida,sim
2025-10-10,Restaurante,alimentacao,120.00,saida,nao
2025-10-12,Uber,transporte,45.00,saida,sim
2025-10-15,Conta de Luz,moradia,180.00,saida,sim
2025-10-20,Academia,saude,99.00,saida,nao
2025-10-25,Combustível,transporte,250.00,saida,sim
```

Histórico de Atendimento (historico_atendimento.csv):
```data,canal,tema,resumo,resolvido,emocao,proximo_passo
2025-09-15,chat,CDB,Cliente quis entender como o dinheiro rende,sim,duvida,Explicar com exemplo simples
2025-09-22,telefone,Problema no app,Erro ao acessar extrato resolvido,sim,frustracao,Verificar se voltou a usar normalmente
2025-10-01,chat,Tesouro Selic,Cliente pediu explicação básica,sim,curiosidade,Sugerir como iniciar com valor baixo
2025-10-12,chat,Metas financeiras,Cliente acompanhou reserva de emergência,sim,motivacao,Incentivar continuidade
2025-10-25,email,Atualização cadastral,Atualizou dados pessoais,sim,neutro,Sem ação necessária
```

Produtos Financeiros (produtos_financeiros.json) :
```
[
  {
    "nome": "Tesouro Selic",
    "categoria": "seguranca",
    "nivel_risco": "baixo",
    "explicacao_simples": "É como guardar dinheiro com segurança e ver ele crescer aos poucos, podendo retirar quando precisar.",
    "aporte_minimo": 30.00,
    "indicado_para": "Quem quer começar uma reserva de emergência",
    "ideal_para_perfil": ["iniciante", "em organização"]
  },
  {
    "nome": "CDB com liquidez diária",
    "categoria": "seguranca",
    "nivel_risco": "baixo",
    "explicacao_simples": "Funciona como um dinheiro guardado que rende um pouquinho todos os dias e pode ser retirado a qualquer momento.",
    "aporte_minimo": 100.00,
    "indicado_para": "Quem quer segurança e acesso rápido ao dinheiro",
    "ideal_para_perfil": ["iniciante", "em organização"]
  },
  {
    "nome": "LCI/LCA",
    "categoria": "planejamento",
    "nivel_risco": "baixo",
    "explicacao_simples": "Um tipo de investimento que rende sem desconto de imposto, mas precisa deixar o dinheiro parado por um tempo.",
    "aporte_minimo": 1000.00,
    "indicado_para": "Quem consegue guardar dinheiro sem mexer por alguns meses",
    "ideal_para_perfil": ["organizado"]
  },
  {
    "nome": "Fundo Multimercado",
    "categoria": "crescimento",
    "nivel_risco": "medio",
    "explicacao_simples": "Um investimento que mistura várias estratégias, podendo render mais, mas com algumas oscilações.",
    "aporte_minimo": 500.00,
    "indicado_para": "Quem já tem uma reserva e quer diversificar",
    "ideal_para_perfil": ["organizado", "em evolução"]
  },
  {
    "nome": "Fundo de Ações",
    "categoria": "crescimento",
    "nivel_risco": "alto",
    "explicacao_simples": "Investimento com maior chance de ganho, mas que também pode variar bastante ao longo do tempo.",
    "aporte_minimo": 100.00,
    "indicado_para": "Quem pensa no longo prazo e aceita oscilações",
    "ideal_para_perfil": ["avancado"]
  }
]
```

Instrução para o agente:
Responder de forma simples, sem termos técnicos, priorizando sugestões práticas e acessíveis. Evitar recomendações complexas e focar em pequenas ações que ajudem na organização financeira.

## Exemplo de Contexto Montado

Contexto do Cliente

- Nome: Maria Soares
- Perfil: em construção
- Objetivo: Construir reserva de emergência
- Reserva atual: R$ 500 (meta: R$ 6.000)

Resumo de Gastos
- Moradia: R$ 1.380
- Alimentação: R$ 570
- Transporte: R$ 295
- Saúde: R$ 188
- Lazer: R$ 154,90
- Total: R$ 2.488,90

Produtos Disponíveis
- Tesouro Selic (baixo risco)
- CDB com liquidez diária (baixo risco)
- LCI/LCA (baixo risco)
- Fundo Multimercado (médio risco)
- Fundo de Ações (alto risco)
