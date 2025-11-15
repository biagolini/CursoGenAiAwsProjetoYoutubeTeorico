# Prompt: Extração de Dados Turísticos Estruturados

## Descrição

Este prompt foi desenvolvido para extrair dados turísticos estruturados de documentos anexados, com a capacidade de filtrar informações por continente específico. O prompt utiliza Tool Use para garantir que a saída seja um JSON válido e estruturado, com tipos de dados precisos (população como número inteiro absoluto).

## Variáveis do Prompt

- `{{continent}}`: Nome do continente para filtrar os dados (ex: "South America", "Europe", "Asia", "Africa", "Oceania")

## Recursos Utilizados

Este prompt demonstra três recursos avançados do AWS Bedrock:
1. **Prompt Manager**: Centralização e versionamento do prompt
2. **Document Attachment**: Anexação de documentos para análise
3. **Prompt Variables**: Parametrização dinâmica do comportamento

## Objetivo

Extrair informações estruturadas de documentos turísticos, incluindo:
- Nome do país
- População (como número inteiro absoluto)
- Capital
- Principais atrações turísticas

Com a capacidade de filtrar apenas países de um continente específico.

## Configuração no AWS Bedrock Prompt Management

### Passo a Passo:

1. **Acesse o Console AWS Bedrock**
   - Entre no console da AWS e navegue até o serviço Bedrock

2. **Navegue até Prompt Management**
   - No menu lateral esquerdo, na seção "Build", clique em "Prompt Management"

3. **Criar Novo Prompt**
   - Na página do Prompt Management, clique em "Create prompt"

4. **Configurações Sugeridas:**
   - **Nome:** `extracao-dados-turisticos-por-continente`
   - **Descrição:** `Extrai JSON estruturado com informacoes turisticas filtradas por continente de documentos anexados`

5. **Configuração do Modelo:**
   - **Modelo:** Amazon Nova Lite
   - **Temperatura:** 0
   - **Top P:** 1
   - **Max Tokens:** 1000

6. **Inserir o Prompt:**
   - Cole o conteúdo do arquivo `prompt_tourism_extraction.txt` na área de texto do prompt

7. **Configurar Tool (JSON Schema):**
   - Na seção "Tools", clique em "Add tool"
   - Cole o schema JSON fornecido abaixo

8. **Testar o Prompt:**
   - Anexe um documento de teste
   - Defina a variável `continent` (ex: "South America")
   - Execute e verifique se o JSON retornado contém apenas países do continente especificado

## Schema da Tool (JSON)

```json
{
  "tools": [{
    "toolSpec": {
      "name": "extract_tourism_data",
      "description": "Extracts structured tourism data from documents filtered by continent",
      "inputSchema": {
        "json": {
          "type": "object",
          "properties": {
            "countries": {
              "type": "array",
              "description": "List of countries with tourism information from the specified continent",
              "items": {
                "type": "object",
                "properties": {
                  "name": {
                    "type": "string",
                    "description": "Country name"
                  },
                  "population": {
                    "type": "integer",
                    "description": "Country population as absolute number (e.g., 67000000 for 67 million)"
                  },
                  "capital": {
                    "type": "string",
                    "description": "Capital city name"
                  },
                  "tourist_attractions": {
                    "type": "array",
                    "description": "List of main tourist attractions",
                    "items": {"type": "string"}
                  }
                },
                "required": ["name", "population", "capital", "tourist_attractions"]
              }
            }
          },
          "required": ["countries"]
        }
      }
    }
  }],
  "toolChoice": {"tool": {"name": "extract_tourism_data"}}
}
```

## Como Usar

1. **Anexe o documento**: Adicione o documento com informações turísticas à mensagem
2. **Defina o continente**: Substitua `{{continent}}` pelo continente desejado
3. **Execute o prompt**: O modelo retornará apenas dados dos países do continente especificado
4. **Receba JSON estruturado**: A saída será um JSON válido seguindo o schema definido

## Exemplos de Uso

### Exemplo 1: Filtrar América do Sul
**Variável:**
- `{{continent}}`: "South America"

**Resultado esperado:**
```json
{
  "countries": [
    {
      "name": "Brazil",
      "population": 215000000,
      "capital": "Brasília",
      "tourist_attractions": [
        "Christ the Redeemer",
        "Copacabana Beach",
        "Amazon Rainforest",
        "Iguazu Falls"
      ]
    },
    {
      "name": "Argentina",
      "population": 46000000,
      "capital": "Buenos Aires",
      "tourist_attractions": [
        "Obelisco",
        "Teatro Colón",
        "Iguazu Falls",
        "Perito Moreno Glacier"
      ]
    },
    {
      "name": "Peru",
      "population": 34000000,
      "capital": "Lima",
      "tourist_attractions": [
        "Machu Picchu",
        "Sacred Valley",
        "Lake Titicaca"
      ]
    }
  ]
}
```

### Exemplo 2: Filtrar Europa
**Variável:**
- `{{continent}}`: "Europe"

**Resultado esperado:**
```json
{
  "countries": [
    {
      "name": "France",
      "population": 67000000,
      "capital": "Paris",
      "tourist_attractions": [
        "Eiffel Tower",
        "Louvre Museum",
        "Palace of Versailles"
      ]
    },
    {
      "name": "Italy",
      "population": 60000000,
      "capital": "Rome",
      "tourist_attractions": [
        "Colosseum",
        "Vatican City",
        "St. Peter's Basilica",
        "Sistine Chapel",
        "Florence"
      ]
    },
    {
      "name": "Spain",
      "population": 47000000,
      "capital": "Madrid",
      "tourist_attractions": [
        "Prado Museum",
        "Sagrada Familia"
      ]
    }
  ]
}
```

## Vantagens desta Abordagem

1. **Três Recursos em Uma Chamada**: Demonstra Prompt Manager + Document Attachment + Variables
2. **Filtragem Dinâmica**: Mesma configuração serve para qualquer continente
3. **Estrutura Garantida**: Tool Use garante JSON válido sempre
4. **Precisão Numérica**: População como inteiro absoluto elimina ambiguidade
5. **Reutilização**: Um prompt para múltiplos casos de uso
6. **Manutenção Centralizada**: Atualizar no console, sem deploy de código

## Notas Importantes

- **População**: Sempre retornada como número inteiro absoluto (ex: 215000000, não "215 milhões")
- **Continente**: Deve corresponder exatamente ao nome usado no documento
- **Documento**: Deve estar em formato suportado (txt, pdf, docx, html, md)
- **Limite de Tokens**: Configure maxTokens adequado para documentos grandes (recomendado: 1000+)
