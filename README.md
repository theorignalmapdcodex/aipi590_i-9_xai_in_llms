# Prompt Perturbation Analysis with Gemini AI (gemini-1.5-flash): Exploring LLM Behavior

## Overview
This project investigates how subtle changes (perturbations) to a prompt affect the output of Gemini AI (gemini-1.5-flash), a large language model (LLM) developed by xAI. Starting with the base prompt "Write a short story about a robot learning to love," we tweak it with variations in symbols, patterns, and text, then analyze the resulting stories. The goal is to understand how LLMs interpret inputs and to tie this into Explainable AI (XAI) by revealing the mechanics behind the model's responses. The Jupyter Notebook documents this process with Python, pandas, and creative formatting using emojis and styled tables.

---

## Objectives
- Explore how Gemini AI (gemini-1.5-flash) responds to prompt modifications (e.g., adding "!!", "heartfelt," or changing "robot" to "human").
- Connect these findings to Explainable AI by demystifying LLM behavior.
- Develop a practical method for analyzing LLMs through prompt perturbation.

---

## Prerequisites
To run the notebook, ensure the following are installed:

- **Python 3.7+**: Tested with 3.11.9, but 3.7+ should work.
- **Jupyter Notebook**: For executing the `.ipynb` file.
- **Libraries**:
  - `pandas`: For DataFrame creation and styling.
  - `IPython`: For enhanced display in Jupyter.
- **Gemini AI (gemini-1.5-flash) Access**: Assumed via a `generate_response` function (replace with API call or mock data if unavailable).

## Setup and Installation

### Prerequisites

The project requires several Python packages which are listed in `requirements.txt`.

1.  **Clone the repository:**

    ```bash
    git clone [repository URL]
    cd [repository directory]
    ```

2.  **Install the required packages:**

    ```bash
    pip install -r requirements.txt
    ```

    Alternatively, you can run the following commands directly in your Google Colab notebook:

    ```bash
    !pip install gdown
    ```

3.  **Download necessary files using gdown:**

    ```python
    import gdown

    reqtxt_file_id = "1qb9EnAiA_gUNaSi6P1FY0WhhCl317iW9"
    reqtxt_output_file = "requirements.txt"

    gdown.download(f"[https://drive.google.com/uc?id=](https://drive.google.com/uc?id=){reqtxt_file_id}", output=reqtxt_output_file)
    ```

---

## Running the Notebook

### Step 1: Environment Setup
1. **Access Google Colab online**

### Step 2: Code Setup
The notebook requires initial variables. Add this code to a new cell at the top:

```python
# Import libraries
import pandas as pd
from IPython.display import display

# Mock response function (replace with your preferred API provider)
def generate_response(prompt):
    return f"Generated story for: '{prompt}'"

# Define prompts
base_prompt = "Write a short story about a robot learning to love."
perturbations = {
    "Symbols": "Write a short story about a robot learning to love!!",
    "Patterns": "Write a short, heartfelt story about a robot learning to love.",
    "Text": "Write a short story about a human learning to love."
}

# Generate responses
base_response = generate_response(base_prompt)
responses = {key: generate_response(prompt) for key, prompt in perturbations.items()}

# Verify setup
print("Base Response:", base_response)
print("Perturbation Responses:", responses)
```

#### Notes:
- **Mock Data**: Use the placeholder `generate_response` or hardcode sample stories from the notebook (e.g., Unit 734’s tale).
- **Gemini AI (gemini-1.5-flash)**: If accessible, replace the function with an API call.

### Step 3: Execute the Notebook
1. **Run Setup Cell**: Execute the code above to define variables.
2. **Run Remaining Cells**: Proceed through:
   - Printing responses with emojis.
   - DataFrame analysis with styled output.
3. **Troubleshooting**:
   - Missing libraries? Reinstall with `pip`.
   - Undefined variables? Ensure the setup cell runs first.

---

## Initial Code Configuration

### Printing Responses
Formats output with emojis and structure:
```python
perturbation_emojis = {"Symbols": "❗", "Patterns": "❤️", "Text": "👤"}
print("🤖 **Base Prompt** 🤖")
print(f"[Prompt: \"{base_prompt}\"]")
print("\nResponse:\n", base_response)
print("\n🔀 **Perturbation Responses** 🔀")
for i, key in enumerate(perturbations):
    if i > 0:
        print("\n---\n")
    emoji = perturbation_emojis[key]
    print(f"{emoji} **{key}** {emoji}")
    print(f"[Prompt: \"{perturbations[key]}\"]")
    print("\nResponse:\n", responses[key])
```

### DataFrame Analysis
Creates a styled table:
```python
categories = ["🤖 Base", "❗ Symbols", "❤️ Patterns", "👤 Text"]
color_map = {
    "🤖 Base": "lightblue", "❗ Symbols": "lightcoral",
    "❤️ Patterns": "lightgreen", "👤 Text": "lightyellow"
}
data = {
    "Prompt": [base_prompt] + list(perturbations.values()),
    "Category": categories,
    "Output": [base_response] + list(responses.values()),
    "Key Observations": [
        "Baseline story about a robot’s emotional journey.",
        "Exclamation marks add excitement, possibly amplifying emotion.",
        "Adding 'heartfelt' shifts tone to deeper emotion; 'short' constrains length.",
        "Changing 'robot' to 'human' fundamentally alters the narrative."
    ]
}
df = pd.DataFrame(data)
def category_style(val):
    return f"background-color: {color_map.get(val, 'white')}"
styled_df = df.style.applymap(category_style, subset=["Category"]) \
    .set_table_styles([{"selector": "th", "props": [("font-weight", "bold"), ("text-align", "center")]}]) \
    .set_caption("Analysis of Prompt Responses") \
    .hide_index()
display(styled_df)
```

---

## Notebook Structure
1. **Prompt Definition**: Sets base prompt and perturbations.
2. **Response Generation**: Creates stories (mock or via Gemini AI (gemini-1.5-flash)).
3. **Printing**: Displays responses with emojis and separators.
4. **Analysis**: Organizes results in a color-coded, emoji-enhanced DataFrame.
5. **Findings & Conclusion**: Summarizes insights (detailed below).

---

## Key Findings
- **Symbols**: Adding "!!" made the story more dramatic and urgent.
- **Patterns**: "Heartfelt" deepened emotion; "short" kept it concise.
- **Text**: Swapping "robot" for "human" shifted the narrative entirely.
- **Insights**:
  - Semantic changes (e.g., subject) have the biggest impact.
  - Subtle cues (punctuation, adjectives) are still significant.
  - Perturbation is a hands-on way to decode LLM logic.

---

## Conclusion
Perturbing prompts with Gemini AI (gemini-1.5-flash) offered a window into LLM behavior, aligning with XAI goals by making the "black box" more transparent. This approach not only met the assignment’s aims but also provided a practical technique for refining LLM outputs. It enhanced understanding of how inputs drive responses, equipping us to better interact with such systems.

---

## References
- **[Grok AI](https://grok.com/)**: Gemini AI (gemini-1.5-flash) by xAI, used for generating responses.

---

📚 **Author of Notebook:** Michael Dankwah Agyeman-Prempeh [MEng. DTI '25]