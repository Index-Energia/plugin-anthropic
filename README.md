# Index Energia

Dados e análises do setor elétrico brasileiro direto no Claude. O plugin conecta o Claude ao servidor MCP da Index Energia e adiciona as skills DEX, que orientam análises verificáveis e a configuração de alertas e relatórios recorrentes.

## O que faz

- **Consultas:** PLD, CMO, mercado, operação do sistema, geração, carga, hidrologia, reservatórios, curtailment, dados da CCEE e do ONS, documentos regulatórios e Diário Oficial da União.
- **Skill `dex-analise`:** compara períodos equivalentes, separa dados de hipóteses e cita a data de referência e a fonte de cada número.
- **Skill `dex-rotinas`:** prepara tarefas da Index por agenda ou por evento de publicação de dados (por exemplo, "me avise por e-mail quando o PLD sair"). A tarefa só é ativada depois que você revisa e autoriza a definição.

## Como usar

1. Instale o plugin e, na aba **Connectors**, conecte o conector **Index Energia** com a sua conta Index (OAuth).
2. Pergunte em linguagem natural, por exemplo: "Analise o PLD desta semana por submercado" ou "Prepare um alerta por e-mail quando o PLD horário for publicado".

É preciso uma conta Index Energia com acesso ao Index IA e ao MCP no plano da empresa.

## Dados e privacidade

As perguntas viram chamadas às ferramentas do servidor `https://mcp.indexenergia.com.br/mcp`, autenticadas com a sua conta. A Index registra a ferramenta chamada, usuário, empresa e duração, sem guardar o conteúdo por padrão. Tarefas criadas ficam na sua conta Index e podem ser pausadas ou excluídas a qualquer momento. Política de privacidade: https://indexenergia.com.br/privacy-policy · Termos: https://indexenergia.com.br/terms · Suporte: https://indexenergia.com.br/contact
