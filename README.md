# Amazon Musical Instruments Review Sentiment Analysis with Ollama LLM

This repo demonstrates how to use an open source LLM via [Ollama](https://ollama.com/) to extract structured information from Amazon product reviews for musical instruments. The workflow leverages the [instructor](https://pypi.org/project/instructor/) library to obtain structured outputs from LLMs, and processes a sample of real Amazon reviews.

It can be used for any dataset that requieres having the information

## What Does This Project Do?

- **Loads a sample of Amazon musical instrument reviews** from `reviews_Musical_Instruments_sample.csv`.
- **Samples one review for each rating (1-5 stars)** to create a balanced dataset.
- **Uses a local LLM (via Ollama) to extract structured information** from each review, including:
  - Sentiment (positive, negative, neutral)
  - Score (1-5)
  - Instrument (or item under review)
  - Review length (short, medium, long)
- **Outputs a DataFrame** with the extracted information for further analysis.

## Main Files

<<<<<<< HEAD
- `ollama_simple_nlp.py`: Main script 
- `reviews_Musical_Instruments_sample.csv`: Sample Amazon reviews for musical instruments.
=======
- `ollama_simple_nlp.py`: Main script that loads data, runs the LLM extraction, and processes results.
- `reviews_Musical_Instruments_sample.csv`: CSV file containing Amazon reviews for musical instruments.
>>>>>>> 69112f6c59aa14b83d408e22f539fc85dfd9b9d0

## Setup Instructions

### 1. Install [uv](https://github.com/astral-sh/uv) (if not already installed)

[uv](https://github.com/astral-sh/uv) is a fast Python package/dependency manager. Install it with:

```bash
pip install uv
```

### 2. Create and Activate a Virtual Environment

```bash
uv venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

Install all required libraries using uv:

```bash
uv pip install pandas openai pydantic instructor
```

### 3. Install and Run Ollama

- Download and install Ollama from [https://ollama.com/download](https://ollama.com/download)
- Start the Ollama server:

```bash
ollama serve
ollama run gemma3:12b
```

> **Note:** The script is configured to use `gemma3:12b` by default. You can use other models that support structured outputs (e.g., Meta Llama). Make sure the model is downloaded and running in Ollama.

### 4. Run the Script

```bash
uv run ollama_simple_nlp.py
```

## How It Works

1. **Data Loading:**
   - Loads the CSV file `reviews_Musical_Instruments_sample.csv`.
   - Samples one review for each star rating (1-5) to create a small, balanced dataset.
2. **LLM Extraction:**
   - For each review, sends the text to the local LLM via the OpenAI-compatible API provided by Ollama.
   - The LLM is prompted to extract sentiment, score, instrument, and review length.
   - The instructor library ensures the output is structured and validated using Pydantic models.
3. **Result Processing:**
   - The script collects the structured results and adds them as columns to the DataFrame.
   - Drops intermediate columns and outputs the final DataFrame.

## Troubleshooting & Tips

<<<<<<< HEAD
- **Ollama "App" vs Terminal:**
  - The script expects Ollama to be running as a background service (not just in a terminal window). If you encounter connection issues, ensure the Ollama app is running and accessible at `http://localhost:11434/v1`.
=======
- **Ollama App vs Terminal:**
  - The script expects Ollama to be running as a background service (not just in a terminal window). If you encounter connection issues, ensure the Ollama app is running and accessible at `http://localhost:11434/v1`.
- **Model Compatibility:**
  - Some models may not support structured outputs or may behave inconsistently. If you encounter issues, try updating Ollama or switching to a different model (e.g., Meta Llama).
- **API Key:**
  - The script uses `api_key="ollama"` as a placeholder. No real OpenAI key is needed for local Ollama usage.
- **Performance:**
  - LLM inference can be slow, especially on large models or limited hardware. The script prints the time taken for each request.
>>>>>>> 69112f6c59aa14b83d408e22f539fc85dfd9b9d0

## Example Output

The script will print the extracted information for each review, such as:

```
Ollama request took 3.21 seconds
Ollama response:  ...
Sentiment: negative
Score: 1
Instrument: guitar amp
Review length: long
```

## References
- [Ollama Documentation](https://ollama.com/docs)
- [Instructor Library](https://python.useinstructor.com/)
- [Pydantic](https://docs.pydantic.dev/)
- [OpenAI Python Library](https://github.com/openai/openai-python)
