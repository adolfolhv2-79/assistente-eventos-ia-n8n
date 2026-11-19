# Plano de testes sugerido — ambiente fictício

> **Não são resultados de testes já executados.** Estes cenários orientam uma eventual implementação didática com dados inventados.

| Caso | Entrada fictícia | Verificação proposta |
| --- | --- | --- |
| Mensagem de texto | “Quais oficinas acontecem no sábado?” | Consulta à base simulada sem inventar horários |
| Mensagens em sequência | “Olá” e “quero saber a programação” | Agrupamento de mensagens da mesma conversa |
| Áudio | Gravação de teste autorizada | Transcrição seguida de resposta coerente |
| Imagem | Cartaz fictício de um evento inventado | Extração de texto sem suposições indevidas |
| PDF | Programação sintética em PDF | Extração de conteúdo e tratamento de erro |
| Data expirada | Pedido de ingresso para evento fictício passado | Não registrar novo ingresso |
| Registro fictício | Pedido completo com dados sintéticos | Confirmar somente depois do sucesso da ferramenta |
| Falha de planilha | Simulação de erro na API de teste | Informar falha sem afirmar que o registro ocorreu |
| Isolamento de conversas | Duas sessões de teste | Não misturar histórico ou registros das sessões |
| Entrada ambígua | “Quero dois” sem contexto | Solicitar a informação faltante em vez de presumir |

## Evidências futuras

Registrar entradas sintéticas, comportamento esperado, resultado observado, logs sem segredos e data do teste. Sem essas evidências, não marcar cenários como aprovados.
