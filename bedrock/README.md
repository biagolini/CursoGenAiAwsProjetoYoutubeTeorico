# Modelos Fundacionais - AWS Bedrock

Este diretório contém exemplos práticos demonstrando duas abordagens diferentes para interagir com modelos de linguagem no AWS Bedrock.

## Arquivos

- `01_invoke_model.ipynb` - Demonstra o uso da API `invoke_model` (método original)
- `02_converse.ipynb` - Demonstra o uso da API `converse` (método moderno)

## Comparação entre os Métodos

### 1. invoke_model: A API Original e Específica

**Legado e Flexibilidade Total**: `invoke_model` é a API original e de mais baixo nível para interagir com os modelos no Bedrock. Ela foi a primeira a ser disponibilizada.

**Corpo da Requisição Específico do Modelo**: A principal característica (e desvantagem) da `invoke_model` é que o body da requisição precisa ser formatado exatamente como o provedor do modelo (Anthropic, Cohere, Meta, etc.) espera. Isso significa que se você criar um código para chamar o Claude da Anthropic e depois quiser testar o Llama da Meta, você precisa reescrever o JSON da requisição, pois eles têm estruturas completamente diferentes.

**Casos de Uso**: É ideal para quando você precisa de controle total sobre parâmetros muito específicos de um modelo que talvez ainda não estejam abstraídos pela API converse. Também é necessária para modelos que não são focados em conversação, como os de geração de imagem ou embeddings.

### 2. converse: A API Moderna e Padronizada

A AWS introduziu a `converse` (e sua versão de streaming, `converse_stream`) para resolver a complexidade da `invoke_model`.

**Interface Unificada**: Este é o ponto principal. A API `converse` oferece uma estrutura de requisição e resposta padronizada que funciona para todos os modelos de texto que suportam conversação. Você escreve o código uma vez, e pode trocar o `modelId` (de um Claude para um Llama, por exemplo) sem alterar a estrutura da sua requisição.

**Foco em Conversação**: Como o nome sugere, ela foi projetada especificamente para casos de uso de conversação (chatbots, assistentes, etc.). Ela gerencia nativamente o histórico da conversa, alternando entre as roles `user` e `assistant`. Com a `invoke_model`, você precisaria gerenciar essa lógica manualmente no corpo da requisição.

**Recursos de Alto Nível**: A API `converse` já vem com funcionalidades mais ricas e fáceis de usar, como:

- **Tool Use (Function Calling)**: A capacidade de o modelo solicitar a execução de ferramentas externas é uma funcionalidade nativa e mais simples de implementar com a `converse`.

- **Multimodalidade Simplificada**: Enviar imagens junto com texto (como no Claude 3) é mais direto na estrutura da `converse`.

- **Integração com Guardrails**: A aplicação de políticas de segurança e filtros de conteúdo é mais integrada.

- **Integração com Prompt Management**: A API `converse` permite integração nativa com o [Amazon Bedrock Prompt Management](https://aws.amazon.com/blogs/machine-learning/amazon-bedrock-prompt-management-is-now-available-in-ga/), facilitando o versionamento, teste e deploy de prompts de forma centralizada. Esta funcionalidade foi [documentada a partir da versão 1.35.56 do boto3](https://boto3.amazonaws.com/v1/documentation/api/1.35.56/reference/services/bedrock-runtime/client/converse.html) em [novembro de 2024](https://pypi.org/project/boto3/#history). Se você quiser criar um prompt manager e não souber como fazer, confira [este tutorial completo](https://builder.aws.com/content/321xnRrCd7ZPRefMbMmIhD6QprR/aws-prompt-manager-tutorial-completo-com-exemplo-pratico-de-sistema-de-agendamento).

## Quando Usar Cada Método

### Use `invoke_model` quando:
- Precisar de controle granular sobre parâmetros específicos do modelo
- Trabalhar com modelos não-conversacionais (imagem, embeddings)
- Integrar com sistemas legados que já usam essa API

### Use `converse` quando:
- Desenvolver aplicações de chat ou assistentes
- Quiser portabilidade entre diferentes modelos
- Precisar de funcionalidades como tool calling ou multimodalidade
- Buscar simplicidade e padronização

## Exemplo de Uso

Ambos os notebooks demonstram:
- Configuração do cliente Bedrock
- Chamadas síncronas e assíncronas (streaming)
- Processamento de respostas
- Salvamento de resultados para análise

Execute os notebooks para ver as diferenças práticas entre as duas abordagens.