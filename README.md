# Meal Plan Generator with AI

This project leverages OpenAI's powerful AI models to create personalized meal plans, generate illustrative images for each recipe, and provide audio narration for easy-to-follow cooking instructions. It's designed to be an interactive tool for culinary inspiration and assistance, all within a Jupyter Notebook environment.

## Features

*   **Intelligent Meal Plan Generation**: Utilizes OpenAI's GPT models to generate daily meal plans (breakfast, lunch, dinner) based on provided ingredients, calorie goals, and specific dietary preferences. Recipes include detailed instructions, calorie counts, serving sizes, and preparation times.
*   **Recipe Image Generation**: Automatically creates unique and descriptive images for each recipe title using OpenAI's DALL-E model, enhancing the visual appeal of your meal plan.
*   **Audio Narration of Recipes**: Transforms written recipes into spoken audio using OpenAI's Text-to-Speech (TTS) model, making it convenient to listen to instructions while cooking.

## Technologies Used

*   **Python**: The primary programming language.
*   **Jupyter Notebook**: For an interactive and cell-based development experience.
*   **OpenAI API**:
    *   **GPT-3.5/GPT-4**: For generating meal plans and refining recipes for speech.
    *   **DALL-E 3**: For creating recipe images.
    *   **TTS (Text-to-Speech)**: For narrating recipes.
*   **`python-dotenv`**: To manage environment variables (e.g., OpenAI API key).
*   **`Pillow`**: For basic image handling (though primarily used for displaying generated images in the notebook).
*   **`requests`**: For downloading generated images from DALL-E.

## Setup

To get this project up and running, follow these steps:

1.  **Clone the repository** (if applicable, otherwise ensure you have the `main.ipynb` file).

2.  **Install dependencies**:
    Open your terminal or command prompt and run:
    ```bash
    pip install openai jupyter python-dotenv pillow requests -q
    ```

3.  **Set up your OpenAI API Key**:
    *   Obtain an API key from your [OpenAI dashboard](https://platform.openai.com/account/api-keys).
    *   Create a file named `.env` in the root directory of your project.
    *   Add your API key to the `.env` file in the following format:
        ```
        OPENAI_API_KEY='your_openai_api_key_here'
        ```

## Usage

1.  **Open the Jupyter Notebook**:
    Navigate to the project directory in your terminal and run:
    ```bash
    jupyter notebook
    ```
    This will open a browser window with the Jupyter interface. Click on `main.ipynb` to open the notebook.

2.  **Run the cells sequentially**:
    Execute each cell in the `main.ipynb` notebook from top to bottom.

    *   **Meal Plan Generation**: The `create_meals` function (Cell `VSC-031ddcc1`) is the core for generating meal plans. You can customize ingredients, calorie limits, and other parameters.
    *   **Image Generation**: After generating a meal plan, the notebook extracts recipe titles. The `create_and_save_image` function (Cell `VSC-a01a832c`) uses these titles to prompt DALL-E to create and save images for each recipe.
    *   **Recipe Narration**: You can select a specific meal (breakfast, lunch, or dinner). The notebook then refines the recipe text for better spoken delivery and uses the `speak` function (Cell `VSC-1b8d7888`) to generate an audio file of the recipe instructions.

## Workflow Example

1.  Define your desired `foods` and call `create_meals` to get a personalized daily meal plan.
2.  Extract the recipe titles from the generated meal plan.
3.  Loop through the titles to generate and save an image for each recipe using DALL-E.
4.  Choose a specific meal (e.g., "almoço" for lunch).
5.  The selected recipe is then processed by GPT to make it more suitable for narration.
6.  Finally, the `speak` function converts the refined recipe into an audio file, which can be played directly in the notebook.
