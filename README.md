Sah.Fin — Assistente Financeira Virtual 💸

Desafio: Agente Financeiro Inteligente com IA Generativa

Agente de educação financeira desenvolvido para mulheres, especialmente mães solo e mães atípicas. A Sah.Fin oferece orientação financeira empática, acessível e prática — sem julgamentos e sem termos complicados.

Problema que resolve
Mulheres com alta carga mental enfrentam dificuldades para organizar as finanças: falta de educação financeira prática, medo de investir e ausência de ferramentas que falem sua linguagem.
Como funciona
A Sah.Fin atua como uma assistente empática que:

Explica finanças em linguagem simples, sem termos técnicos
Simula cenários reais ("se eu guardar R$50 por mês…")
Ajuda na organização de gastos, metas e prioridades
Mantém contexto da conversa para acompanhar a evolução da usuária
Não faz recomendações sem antes entender o perfil da usuária


Stack
ComponenteTecnologiaInterfaceStreamlitLLMOllama (phi3, local)Base de conhecimentoJSON + CSV mockados

Estrutura do Repositório
📁 lab-agente-financeiro/
│
├── 📄 README.md
│
├── 📁 data/
│   ├── historico_atendimento.csv
│   ├── perfil_investidor.json
│   ├── produtos_financeiros.json
│   └── transacoes.csv
│
├── 📁 docs/
│   ├── 01-documentacao-agente.md     # Caso de uso e arquitetura
│   ├── 02-base-conhecimento.md       # Estratégia de dados
│   └── 03-prompts.md                 # Engenharia de prompts
│
└── 📁 src/
    └── app.py

Como rodar
bash# Instale as dependências
pip install streamlit pandas requests

# Certifique-se que o Ollama está rodando localmente
ollama run phi3

# Rode a aplicação
streamlit run src/app.py

Arquivos de dados
ArquivoDescriçãoperfil_investidor.jsonPerfil, metas e comportamento financeiro da usuáriaprodutos_financeiros.jsonProdutos disponíveis com explicações simplestransacoes.csvHistórico de gastos para análise de padrõeshistorico_atendimento.csvInterações anteriores para manter contexto

Segurança e Anti-Alucinação

Respostas baseadas apenas nos dados fornecidos
Sem recomendações de investimento sem perfil definido
Dados sensíveis nunca são solicitados nem compartilhados
Quando não sabe, admite e redireciona


Limitações declaradas

Não fornece aconselhamento financeiro profissional
Não acessa dados bancários reais
Não realiza investimentos automáticos
Não substitui um consultor financeiro


Persona
Nome: Sah.Fin
Tom: Acolhedor, direto, conversacional e levemente motivador
Público-alvo: Mulheres de 25 a 45 anos, renda baixa a média, com alta carga mental e pouco conhecimento financeiro
