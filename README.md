# Treinamento AWS GenAI

Este repositório contém exemplos práticos e testes de chamadas para serviços de IA da AWS utilizando o SDK boto3, desenvolvido para apoiar o curso online de desenvolvimento de aplicações com GenAI na AWS.

## Estrutura do Repositório

Cada serviço da AWS apresentado no curso possui sua própria pasta, onde os exemplos são organizados em subpastas de acordo com o material apresentado nas aulas. Esta estrutura facilita a navegação e o acompanhamento do conteúdo do curso.

```
├── servico-aws-1/
│   ├── aula-01/
│   ├── aula-02/
│   └── ...
├── servico-aws-2/
│   ├── aula-01/
│   ├── aula-02/
│   └── ...
└── ...
```

## Pré-requisitos

Para executar os códigos apresentados neste repositório, você precisa ter:

- **AWS CLI instalado e configurado** com suas credenciais
- Python 3.x instalado
- SDK boto3 instalado (`pip install boto3`)

### Configuração do AWS CLI

Se você precisa de ajuda para instalar e configurar o AWS CLI, assista à playlist completa no YouTube com passo-a-passo detalhado:

🎥 **[Como Configurar AWS CLI - Playlist Completa](https://youtube.com/playlist?list=PL-5Xgq4rqhTymYdKwWAwvd2keY_FFlLTl&si=iuT7obUW2SOFeCkt)**

## Padrão de Código

Este projeto busca seguir o **[PEP 8](https://peps.python.org/pep-0008/)**, o guia oficial de estilo para código Python, sempre que possível. Essa convenção é adotada para:

- Manter consistência em todo o código
- Facilitar a identificação de dependências
- Melhorar a legibilidade e manutenção
- Seguir as melhores práticas da comunidade Python

## Como Usar

1. Clone este repositório
2. Navegue até a pasta do serviço desejado
3. Acesse a subpasta correspondente à aula
4. Execute os exemplos seguindo as instruções específicas de cada código

## Importante

Certifique-se de que suas credenciais AWS estão configuradas corretamente antes de executar qualquer código. Os exemplos utilizam serviços da AWS que podem gerar custos, então monitore seu uso através do AWS Console.


## Instalação e Configuração do Ambiente

Siga estes passos para configurar o projeto em um ambiente limpo e isolado utilizando virtual environments do Python:

### 1. Clone o Repositório

```bash
git clone https://github.com/biagolini/TreinamentoAwsGenAi.git
cd TreinamentoAwsGenAi
```

### 2. Crie e Ative um Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate  # No Windows: .venv\Scripts\activate
```

### 3. Instale as Dependências do Projeto

```bash
pip3 install -r requirements.txt
```

### 4. Registre o Virtual Environment no Jupyter

Para tornar o virtual environment disponível como um kernel no Jupyter:

```bash
python3 -m ipykernel install --user --name=treinamento-aws-genai --display-name "Treinamento AWS GenAI"
```

### 5. Abra o Jupyter

Para iniciar o Jupyter Notebook ou JupyterLab:

```bash
# Para JupyterLab
jupyter lab

# Para Jupyter Notebook
jupyter notebook
```

### 6. Gerenciar Kernels do Jupyter

Para listar todos os kernels disponíveis:

```bash
jupyter kernelspec list
```

Para desregistrar o kernel do virtual environment:

```bash
jupyter kernelspec uninstall treinamento-aws-genai
```

## Conversão entre Jupyter Notebooks e Scripts Python

Você pode converter arquivos entre os formatos `.ipynb` (Jupyter Notebook) e `.py` (script Python) usando o `jupyter nbconvert`:

### Converter Notebook para Script Python

```bash
jupyter nbconvert --to script arquivo-origem.ipynb --output arquivo-destino
```

Isso criará um arquivo `arquivo-destino.py` no mesmo diretório.

### Converter Script Python para Notebook

```bash
jupyter nbconvert --to notebook arquivo-origem.py --output arquivo-destino
```

Isso criará um arquivo `arquivo-destino.ipynb` no mesmo diretório.

