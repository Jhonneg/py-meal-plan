# Planejador de Refeições com IA e Geração de Imagens DALL-E (Português)

Este projeto utiliza os modelos GPT e DALL-E da OpenAI para criar planos de refeições diários personalizados e gerar imagens correspondentes para cada refeição. Você fornece uma lista de ingredientes, e a aplicação gera um plano completo para café da manhã, almoço e jantar, incluindo receitas, contagem de calorias e imagens visualmente atraentes.

## Funcionalidades

-   **Planos de Refeições Personalizáveis:** Gere planos com base em ingredientes específicos, metas de calorias e preferências alimentares.
-   **Receitas Geradas por IA:** Utiliza o GPT-4 ou GPT-3.5-turbo para a geração de receitas criativas e detalhadas.
-   **Geração Dinâmica de Imagens:** Usa o DALL-E 3 para criar imagens únicas e de alta qualidade para cada refeição.
-   **Saída Flexível:** Pode gerar o plano de refeições em texto simples ou em HTML/CSS estilizado.
-   **Fácil de Usar:** Toda a lógica está contida em um único Jupyter Notebook para uma execução simples.

## Como Funciona

1.  **Geração do Plano de Refeições:** A função `create_meals` constrói um prompt detalhado com os ingredientes e restrições definidos pelo usuário (ex: limite de calorias, usar apenas os ingredientes fornecidos). Ela envia este prompt para a API de Chat Completions da OpenAI.
2.  **Análise da Resposta:** A API retorna um plano de refeições estruturado. O notebook é projetado para analisar essa resposta, separando as receitas de uma lista de prompts de imagem compatíveis com o DALL-E (os títulos das refeições).
3.  **Criação de Imagens:** A função `create_and_save_image` itera sobre os títulos extraídos. Para cada título, ela chama a API de Imagens da OpenAI (DALL-E) para gerar uma imagem.
4.  **Salvando Imagens:** A imagem gerada é baixada da URL fornecida pela API e salva localmente em um diretório `images/`.

## Configuração e Uso

### 1. Pré-requisitos

-   Python 3.7+
-   Jupyter Notebook ou JupyterLab

### 2. Instalação

1.  Clone este repositório ou baixe o arquivo `main.ipynb`.
2.  Crie e ative um ambiente virtual (recomendado):
    ```bash
    python -m venv venv
    source venv/bin/activate  # No Windows, use `venv\Scripts\activate`
    ```
3.  Instale os pacotes Python necessários a partir da primeira célula do notebook ou executando:
    ```bash
    pip install openai jupyter python-dotenv pillow requests
    ```

### 3. Configuração

1.  Crie um arquivo chamado `.env` no diretório raiz do projeto.
2.  Adicione sua chave de API da OpenAI ao arquivo `.env`:
    ```
    OPENAI_API_KEY="sua_chave_de_api_da_openai_aqui"
    ```

### 4. Executando o Notebook

1.  Inicie o Jupyter:
    ```bash
    jupyter notebook
    ```
2.  Abra o `main.ipynb`.
3.  Execute as células em ordem:
    -   As primeiras células instalam as dependências e carregam a chave da API.
    -   A célula `create_meals` define a função para gerar o plano de refeições. Você pode modificar a variável `foods` para alterar os ingredientes de entrada.
    -   A célula `create_and_save_image` define a função para a geração de imagens.
    -   As células finais executam as funções, imprimem os resultados e exibem/salvam as imagens geradas.

## Estrutura do Projeto

```
.
├── images/               # Diretório para imagens de refeições salvas
├── main.ipynb            # O Jupyter Notebook principal
├── .env                  # Arquivo para a chave da API (crie você mesmo)
└── README.md             # Documentação do projeto