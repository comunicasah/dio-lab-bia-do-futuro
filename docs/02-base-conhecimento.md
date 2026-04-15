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

[Os dados foram adaptados para refletir a realidade do público-alvo, com foco em educação financeira acessível e aplicável ao dia a dia.

Principais ajustes realizados:

- Simplificação do perfil financeiro (ex: “em organização” ao invés de “moderado”)
- Inclusão de comportamentos e desafios financeiros reais
- Adaptação da linguagem dos produtos financeiros para explicações simples
- Classificação de gastos como essenciais e não essenciais
- Inclusão de contexto emocional nas interações anteriores

Essas adaptações permitem que o agente vá além de respostas técnicas, oferecendo orientações práticas e humanizadas.]

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

[ex: Os JSON/CSV são carregados no início da sessão e incluídos no contexto do prompt]

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

[Sua descrição aqui]

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
