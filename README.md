# CSV Data Agent with DeepSeek-R1 

## Overview

This project demonstrates how to interact with CSV data using a DeepSeek-R1-Distill-Qwen-32B. It integrates a streaming LLM from Hugging Face to process natural language queries on a pandas DataFrame. The project leverages `langchain`, `pandas`, and `huggingface_hub` to enable seamless data interaction.

## Features
- Uses a Hugging Face-hosted LLM `(deepseek-ai/DeepSeek-R1-Distill-Qwen-32B)` for processing queries.
- Parses structured output from the LLM.
- Integrates `langchain` to create a pandas DataFrame agent.
- Allows querying CSV data using natural language prompts.
- Supports structured parsing for responses.

## Installation

1. Clone this repository:
```
git clone https://github.com/DataByteSun/CSV-Data-Agent-with-DeepSeek-R1.git
```
2. Create and activate a virtual environment (optional but recommended):
```
python -m venv venv
source venv/bin/activate   # On Windows use: venv\Scripts\activate
```
3. Install dependencies:
```
pip install -r requirements.txt
```
4. Set up your environment variables:
- Create a .env file in the project directory and add your Hugging Face API key(Get Free key from <a href="https://huggingface.co/" target="_blank">Huggung Face</a>):
  ```
  HUGGINGFACE_API_KEY=your_huggingface_api_key
  ```
- Load environment variables:
  ```
  from dotenv import load_dotenv
  load_dotenv()
  ```

## Usage
1. Load and preprocess your CSV data:
```
import pandas as pd
df = pd.read_csv("your_data.csv")
```
2. Instantiate the LLM and create an agent:
```
from huggingface_hub import InferenceClient

client = InferenceClient(api_key="your_huggingface_api_key")
agent = create_pandas_dataframe_agent(llm=client, df=df, verbose=True)
```
3. Query the agent using natural language:
```
result = agent.invoke("how many rows are there?")
```

## Expected Output (Screenshots)

- Running `agent.invoke("how many rows are there?")` may yield an output like:
![image](https://github.com/user-attachments/assets/9a072d14-e302-49f4-b350-2afa212cde53)


- With a Prompt Engineering
    Question: `How may patients were hospitalized during Mar 2021 in Alaska use column hospitalizedCumulative?`
  ![image](https://github.com/user-attachments/assets/9918b54b-8a2f-460c-a364-0de30bf40b2c)
  ![image](https://github.com/user-attachments/assets/ad531f61-9d31-45b5-bc49-3db0a5b358f2)




> ⚠️ **Warning:**
> This code includes experimental components that may pose risks. Ensure thorough testing in a sandboxed environment to avoid potential vulnerabilities or data loss.
## Customization

Modify `model_name` in the Hugging Face API request to experiment with different LLMs.

Adjust parameters such as `temperature`, `max_tokens`, and `top_p` for fine-tuning responses.


## Contributions

Feel free to contribute by opening an issue or submitting a pull request.

## Contact

For questions or feedback, reach out to `surajpawar.in@gmail.com`.

