# Visão técnica da arquitetura

Esta visão foi elaborada a partir da leitura de um export do n8n de 2026, com 28 nós. O material é retrospectivo e não documenta um serviço público em funcionamento.

## Entrada e classificação

Um webhook recebe o evento de mensagem. Nós de preparação extraem os campos necessários e um **Switch** separa os formatos texto, imagem, áudio e PDF.

## Normalização multimodal

- **Texto:** segue para o buffer.
- **Imagem:** um HTTP Request obtém o arquivo e um componente do Gemini analisa seu conteúdo para produzir texto utilizável pelo fluxo.
- **Áudio:** o arquivo é obtido por HTTP e transcrito por um componente do Gemini.
- **PDF:** o conteúdo é obtido por HTTP e encaminhado a um nó de extração de arquivo.

## Buffer e processamento

Nós **Data Table**, **Wait** e **Code** registram mensagens, aguardam um intervalo, recuperam mensagens da mesma conversa, preparam um lote e limpam registros já processados. A finalidade é reduzir respostas separadas para mensagens enviadas em sequência.

**Observação do export:** o nó de espera possui um nome que menciona 15 segundos, mas o parâmetro numérico `amount` estava configurado em `30`. É um ponto de revisão no ambiente original, e não uma promessa de latência da aplicação.

## Agente, memória e ferramentas

O agente usa um modelo Google Gemini e memória Redis. Há também conexões de ferramenta com uma calculadora e operações de inclusão de linhas em Google Sheets. O documento não apresenta os identificadores de planilhas, os campos reais de registro, os prompts internos ou as credenciais.

## Saída

A resposta principal é enviada em texto por integração WhatsApp. O objetivo da arquitetura é manter o ciclo de recebimento, entendimento e encaminhamento numa única orquestração.

## O que o arquivo não comprova

- Resultados quantitativos ou economia de tempo atribuíveis a este fluxo.
- Cobertura ou aprovação de testes automatizados.
- Disponibilidade contínua do serviço.
- Que todos os nós presentes no export sejam utilizados em cada execução.

Toda implementação futura publicada deve utilizar dados e identidades fictícias e autorização adequada.
