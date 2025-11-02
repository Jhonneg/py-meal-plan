# Gerador de Plano de Refeições com IA
Este projeto utiliza os poderosos modelos de IA da OpenAI para criar planos de refeições personalizados, gerar imagens ilustrativas para cada receita e fornecer narração em áudio para instruções de culinária fáceis de seguir. Ele foi projetado para ser uma ferramenta interativa para inspiração e assistência culinária, tudo dentro de um ambiente Jupyter Notebook.

## Funcionalidades

*   **Geração Inteligente de Plano de Refeições**: Utiliza os modelos GPT da OpenAI para gerar planos de refeições diários (café da manhã, almoço, jantar) com base em ingredientes fornecidos, metas de calorias e preferências dietéticas específicas. As receitas incluem instruções detalhadas, contagem de calorias, tamanhos de porção e tempos de preparo.
*   **Geração de Imagens de Receitas**: Cria automaticamente imagens únicas e descritivas para cada título de receita usando o modelo DALL-E da OpenAI, aprimorando o apelo visual do seu plano de refeições.
*   **Narração em Áudio de Receitas**: Transforma receitas escritas em áudio falado usando o modelo Text-to-Speech (TTS) da OpenAI, tornando conveniente ouvir as instruções enquanto cozinha.

## Tecnologias Utilizadas

*   **Python**: A linguagem de programação principal.
*   **Jupyter Notebook**: Para uma experiência de desenvolvimento interativa e baseada em células.
*   **OpenAI API**:
    *   **GPT-3.5/GPT-4**: Para gerar planos de refeições e refinar receitas para fala.
    *   **DALL-E 3**: Para criar imagens de receitas.
    *   **TTS (Text-to-Speech)**: Para narrar receitas.
*   **`python-dotenv`**: Para gerenciar variáveis de ambiente (ex: chave da API OpenAI).
*   **`Pillow`**: Para manipulação básica de imagens (embora usado principalmente para exibir imagens geradas no notebook).
*   **`requests`**: Para baixar imagens geradas pelo DALL-E.

## Configuração

Para colocar este projeto em funcionamento, siga estes passos:

1.  **Clone o repositório** (se aplicável, caso contrário, certifique-se de ter o arquivo `main.ipynb`).

2.  **Instale as dependências**:
    Abra seu terminal ou prompt de comando e execute:
    ```bash
    pip install openai jupyter python-dotenv pillow requests -q
    ```

3.  **Configure sua Chave da API OpenAI**:
    *   Obtenha uma chave da API no seu [painel da OpenAI](https://platform.openai.com/account/api-keys).
    *   Crie um arquivo chamado `.env` no diretório raiz do seu projeto.
    *   Adicione sua chave da API ao arquivo `.env` no seguinte formato:
        ```
        OPENAI_API_KEY='sua_chave_da_api_openai_aqui'
        ```

## Uso

1.  **Abra o Jupyter Notebook**:
    Navegue até o diretório do projeto no seu terminal e execute:
    ```bash
    jupyter notebook
    ```
    Isso abrirá uma janela do navegador com a interface do Jupyter. Clique em `main.ipynb` para abrir o notebook.

2.  **Execute as células sequencialmente**:
    Execute cada célula no notebook `main.ipynb` de cima para baixo.

    *   **Geração de Plano de Refeições**: A função `create_meals` (Célula `VSC-031ddcc1`) é o núcleo para gerar planos de refeições. Você pode personalizar ingredientes, limites de calorias e outros parâmetros.
    *   **Geração de Imagens**: Após gerar um plano de refeições, o notebook extrai os títulos das receitas. A função `create_and_save_image` (Célula `VSC-a01a832c`) usa esses títulos para solicitar ao DALL-E que crie e salve imagens para cada receita.
    *   **Narração de Receitas**: Você pode selecionar uma refeição específica (café da manhã, almoço ou jantar). O notebook então refina o texto da receita para uma melhor entrega falada e usa a função `speak` (Célula `VSC-1b8d7888`) para gerar um arquivo de áudio das instruções da receita.

## Exemplo de Fluxo de Trabalho

1.  Defina seus `foods` desejados e chame `create_meals` para obter um plano de refeições diário personalizado.
2.  Extraia os títulos das receitas do plano de refeições gerado.
3.  Percorra os títulos para gerar e salvar uma imagem para cada receita usando DALL-E.
4.  Escolha uma refeição específica (ex: "almoço").
5.  A receita selecionada é então processada pelo GPT para torná-la mais adequada para narração.
6.  Finalmente, a função `speak` converte a receita refinada em um arquivo de áudio, que pode ser reproduzido diretamente no notebook.

