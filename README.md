# Conversation Management & Classification using Groq API

![Python](https://img.shields.io/badge/Python-3.13%2B-blue.svg)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![LLMs](https://img.shields.io/badge/LLMs-412991?style=flat&logo=openai&logoColor=white)
## Overview

This project implements core conversational AI functionalities leveraging the Groq API with OpenAI SDK compatibility. The main focus is on managing conversational history with summarization and extracting structured user information from chat conversations via JSON schema classification.

This solution is fully implemented in Python within a Google Colab notebook and uses only standard libraries plus the Groq OpenAI-compatible API—no external frameworks.

---

## Features

### Task 1: Conversation History Management with Summarization

- Maintains a running history of user-assistant interactions.
- Provides customizable truncation of conversation history by:
  - Number of conversation turns (messages).
  - Total character or word length.
- Implements **periodic summarization** after every K-th conversation turn to keep history concise.
- Summaries are composed by prompting the model with conversation context.
- Demonstrates the functionality with multiple chat examples and truncation settings.

### Task 2: JSON Schema Classification & Information Extraction

- Defines a JSON schema (`UserInformationModel`) to extract:
  - Name
  - Email
  - Phone number
  - Location
  - Age
  - Technology stack (as a list of strings)
- Uses Groq API’s OpenAI-compatible function calling capability to extract structured data.
- Validates extracted data against the schema using Pydantic.
- Processes multiple sample chats demonstrating full extraction and validation.

---

## Structure and Usage

### Setup Instructions

1. **API Key:**  
   Replace the placeholder API key in the notebook (if not given) with your actual Groq API key.  
```

client = OpenAI(
base_url="https://api.groq.com/openai/v1",
api_key="YOUR_GROQ_API_KEY"
)

```

2. **Dependencies:**  
Install required packages in the Colab environment:  
```

!pip install --quiet requests openai jsonschema pydantic[email]

```

3. **Run Cells Sequentially:**  
Execute notebook cells in order to initialize models, define conversation management logic, and perform extraction demos.

### Key Components

- **Conversation Management:**  
Functions: `add_message()`, `generate_summary()`, `periodic_summarization()`, truncation helpers.  
Variables: `MESSAGE_HISTORY`, `SUMMARY`, `turn_count`, `summarization_interval`.

- **Information Extraction:**  
Pydantic model `UserInformationModel` for structured data validation.  
Extraction via `extract_information()` function using the Groq API with function calling.

- **Sample Conversations:**  
Various test samples including customer support, registration, surveys, and onboarding with tech stack mentions.

---

## Running Demonstrations

- **Conversation Management Testing:**  
Populates conversation history, runs summaries every 8 turns, and shows truncation behavior.

- **Information Extraction Testing:**  
Loops through multiple sample chats, invoking the extraction function, validating results, and printing structured output.

---

## Security Notes

- **API Keys should never be hard-coded in shared notebooks or repos.**  
Use environment variables or input prompts for secure handling.

- **`google.colab.userdata` entries are never shared upon exporting notebooks.**

---

## Repository Contents

- `ConversationManager.ipynb` (this notebook): Full implementation of both tasks.
- Sample conversation data embedded in the notebook.
- Full documentation within notebook markdown cells.
- Comments and print statements for clarity in every step.

---


## Contact

For any questions or help with the code, please open an issue or contact the author.

---

This project demonstrates solid practical skills in advanced conversational AI tasks, combining summarization, context management, and structured information extraction.

Happy coding! 🚀

