# AI Meal Planner with DALL-E Image Generation

This project uses OpenAI's GPT and DALL-E models to create personalized daily meal plans and generate corresponding images for each meal. You provide a list of ingredients, and the application generates a complete plan for breakfast, lunch, and dinner, including recipes, calorie counts, and visually appealing images.

## Features

-   **Customizable Meal Plans:** Generate plans based on specific ingredients, calorie targets, and dietary preferences.
-   **AI-Powered Recipes:** Leverages GPT-4 or GPT-3.5-turbo for creative and detailed recipe generation.
-   **Dynamic Image Generation:** Uses DALL-E 3 to create high-quality, unique images for each meal.
-   **Flexible Output:** Can generate the meal plan in plain text or styled HTML/CSS.
-   **Easy to Use:** All logic is contained within a single Jupyter Notebook for straightforward execution.

## How It Works

1.  **Meal Plan Generation:** The `create_meals` function constructs a detailed prompt with user-defined ingredients and constraints (e.g., calorie limit, use only provided ingredients). It sends this prompt to the OpenAI Chat Completions API.
2.  **Response Parsing:** The API returns a structured meal plan. The notebook is designed to parse this response, separating the recipes from a list of DALL-E-compatible image prompts (the meal titles).
3.  **Image Creation:** The `create_and_save_image` function iterates through the extracted titles. For each title, it calls the OpenAI Images API (DALL-E) to generate an image.
4.  **Saving Images:** The generated image is downloaded from the URL provided by the API and saved locally to an `images/` directory.

## Setup and Usage

### 1. Prerequisites

-   Python 3.7+
-   Jupyter Notebook or JupyterLab

### 2. Installation

1.  Clone this repository or download the `main.ipynb` file.
2.  Create and activate a virtual environment (recommended):
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```
3.  Install the required Python packages from the first cell of the notebook or by running:
    ```bash
    pip install openai jupyter python-dotenv pillow requests
    ```

### 3. Configuration

1.  Create a file named `.env` in the root directory of the project.
2.  Add your OpenAI API key to the `.env` file:
    ```
    OPENAI_API_KEY="your_openai_api_key_here"
    ```

### 4. Running the Notebook

1.  Start Jupyter:
    ```bash
    jupyter notebook
    ```
2.  Open `main.ipynb`.
3.  Run the cells in order:
    -   The first cells install dependencies and load the API key.
    -   The `create_meals` cell defines the function to generate the meal plan. You can modify the `foods` variable to change the input ingredients.
    -   The `create_and_save_image` cell defines the function for image generation.
    -   The final cells execute the functions, print the results, and display/save the generated images.

## Project Structure

```
.
├── images/               # Directory for saved meal images
├── main.ipynb            # The main Jupyter Notebook
├── .env                  # File for API key (create this yourself)
└── README.md             # Project documentation
```
