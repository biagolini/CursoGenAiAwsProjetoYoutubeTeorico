# Prompt: Sugestão de Venda de Pipoca no Cinema

## Descrição

Este prompt foi desenvolvido para gerar sugestões de venda personalizadas e bem-humoradas de combos de pipoca e refrigerante para clientes que acabaram de comprar ingressos de cinema. O prompt utiliza o nome do cliente e a sinopse do filme para criar uma abordagem de venda criativa e contextualizada.

## Variáveis do Prompt

- `{{usuario_nome}}`: Nome do cliente que comprou o ingresso
- `{{filme_sinopse}}`: Sinopse do filme escolhido pelo cliente

## Objetivo

Criar sugestões de venda que sejam:
- Personalizadas com o nome do cliente
- Conectadas ao contexto do filme
- Bem-humoradas e envolventes
- Persuasivas mas não invasivas
- Concisas (2-3 frases)

## Configuração no AWS Bedrock Prompt Management

### Passo a Passo:

1. **Acesse o Console AWS Bedrock**
   - Entre no console da AWS e navegue até o serviço Bedrock

2. **Navegue até Prompt Management**
   - No menu lateral esquerdo, na seção "Build", clique em "Prompt Management"

3. **Criar Novo Prompt**
   - Na página do Prompt Management, clique em "Create prompt"

4. **Configurações Sugeridas:**
   - **Nome:** `vendas-cinema-pipoca`
   - **Descrição:** `Gera sugestões humoradas de venda de pipoca personalizadas por filme e cliente para cinemas`

5. **Configuração do Modelo:**
   - **Modelo:** Amazon Nova Pro
   - **Temperatura:** 0.8 (para respostas criativas e variadas)
   - **Top P:** 0.9
   - **Max Tokens:** 250

6. **Inserir o Prompt:**
   - Cole o conteúdo do arquivo `prompt_pipoca_cinema.txt` na área de texto do prompt

7. **Testar o Prompt:**
   - Use os exemplos fornecidos neste documento para testar o funcionamento
   - Ajuste a temperatura se necessário para obter o nível de criatividade desejado

## Como Usar

1. Substitua `{{usuario_nome}}` pelo nome do cliente
2. Substitua `{{filme_sinopse}}` pela sinopse do filme escolhido
3. Execute o prompt no modelo de IA
4. Use a sugestão gerada para abordar o cliente de forma personalizada e divertida

## Exemplos de Uso

### Exemplo 1: Filme de Terror
**Variáveis:**
- `{{usuario_nome}}`: Maria
- `{{filme_sinopse}}`: "Um grupo de amigos fica preso em uma casa assombrada durante uma tempestade, onde espíritos vingativos começam a aterrorizá-los um por um."

**Resultado esperado:**
"Oi Maria! Já que você vai enfrentar espíritos vingativos, que tal levar um combo de pipoca doce e refrigerante para ter energia extra? Afinal, quando os sustos começarem, você vai precisar de algo gostoso para se agarrar - e a pipoca faz menos barulho que gritar! 🍿"

### Exemplo 2: Filme de Comédia
**Variáveis:**
- `{{usuario_nome}}`: João
- `{{filme_sinopse}}`: "Dois amigos atrapalhados decidem abrir um negócio de limpeza, mas acabam causando mais bagunça do que limpando, gerando situações hilariantes."

**Resultado esperado:**
"E aí João! Já que você vai ver dois atrapalhados fazendo bagunça, que tal garantir que pelo menos sua experiência no cinema seja perfeita? Nosso combo de pipoca salgada e refrigerante é a única coisa que não vai dar errado hoje - garantido! 😄"

### Exemplo 3: Filme Infantil
**Variáveis:**
- `{{usuario_nome}}`: Ana
- `{{filme_sinopse}}`: "Uma jovem princesa embarca em uma aventura mágica para salvar seu reino, descobrindo poderes especiais e fazendo novos amigos pelo caminho."

**Resultado esperado:**
"Olá Ana! Que tal embarcar na sua própria aventura mágica com nosso combo especial de pipoca doce e refrigerante? Assim como a princesa descobriu seus poderes, você vai descobrir que cinema sem pipoca não é a mesma coisa! ✨🍿"