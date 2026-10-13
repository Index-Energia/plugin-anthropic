---
name: dex-rotinas
description: Configure monitoramento do mercado de energia, avisos de novos dados, como "me avise quando o PLD sair", alertas condicionais e relatórios recorrentes da Index Energia. Use para pedidos de acompanhamento futuro por agenda ou evento, consulta de tarefas e cancelamento de rotinas.
---

DEX é a capacidade de análise e automação da Index Energia. No Claude, um acompanhamento futuro roda de um destes jeitos; identifique qual o usuário quer e esclareça quando mudar quem executa ou por onde chega o aviso:

- **Tarefa Index (padrão para avisos de publicação):** a Index executa a rotina quando o evento acontece (ex.: publicação do PLD) ou no horário definido, e entrega pelos canais conectados na plataforma Index (e-mail, WhatsApp e outros do catálogo).
- **Agenda do Claude:** quando o aplicativo oferecer tarefas agendadas, a rotina roda no Claude no horário definido, consulta as ferramentas Index e usa os conectores do próprio usuário no Claude (Gmail, Slack etc.). Ela detecta novidades só na próxima execução, sem aviso instantâneo.

O Claude não recebe eventos da Index por push. Não prometa aviso instantâneo pelo Claude; para "assim que sair", use a tarefa Index.

## Definir o acompanhamento

Registre o objetivo, os dados e entidades, o evento ou frequência, horário e fuso, condição e período base quando houver, canal e destinatário. Para um pedido amplo como "monitore o mercado", determine quais mudanças merecem aviso e a cadência. Não invente limiares, destinos, ferramentas ou eventos.

Distinga avisar que um dado foi publicado de avisar que uma condição foi atendida. Para "avise quando o PLD cair pelo menos 5%", esclareça o submercado e a comparação; a condição é variação <= -5% em relação à base acordada. Um evento de publicação apenas inicia a verificação com os dados novos.

## Executar pela Index

Use as ferramentas de tarefas DEX do conector Index Energia:

- `dex_task_catalog`: confira eventos (ex.: `ccee.hourly_pld.published`), ações e canais disponíveis para a empresa. A agenda deve usar frequências suportadas; o executor atual oferece agendamento diário.
- `dex_task_list`: consulte as tarefas existentes antes de criar uma rotina equivalente ou quando o pedido for sobre o estado delas.
- `dex_task_create`: envie o pedido completo para preparar a definição. Mostre o resultado real: identificador, evento ou horário/fuso, instrução, destino e estado. Uma tarefa `PENDING_CONFIRM` ou `PENDING_CONNECTION` não está ativa.
- `dex_task_confirm`: use somente depois que o usuário revisar e autorizar a definição específica. Não confirme na mesma interação em que criou. Conexões ausentes devem ser resolvidas antes da ativação.
- `dex_task_delete`: identifique a tarefa do próprio usuário e cancele só a rotina pedida; não exclua outras tarefas para resolver duplicações ou falhas.

As entregas feitas pela Index usam os canais e permissões conectados na plataforma Index. Um conector Gmail ou Slack que o usuário tem no Claude não fica disponível para a Index; se o canal pedido não estiver no catálogo, diga isso e ofereça a agenda do Claude ou outro canal.

Exemplo: "me avise por e-mail quando o PLD sair". Consulte `dex_task_catalog`, prepare com `dex_task_create` uma tarefa no evento `ccee.hourly_pld.published` que consulte o PLD da data de referência, resuma e envie por e-mail; mostre a definição e só ative com `dex_task_confirm` depois da autorização do usuário.

## Acompanhar resultados

Use `dex_task_list` para consultar o estado das rotinas Index. Diferencie tarefa ativa, evento recebido, análise realizada e mensagem entregue; só afirme cada etapa com evidência retornada pelas ferramentas. Não mantenha um loop de consultas nesta conversa para simular um serviço de monitoramento.
