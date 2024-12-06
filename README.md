# Langchain RAG Setup Guide 
## Please follow the steps to setup the application.

## Ollama
You'll need to run ollama locally before running any of the python commands as this entire project runs locally. Get the setup from the official page : https://ollama.com/. Once setup is completed, run the following commands in a terminal after closing any running instance of ollama.
```ollama
ollama pull llama3.1
ollama pull nomic-embed-text
ollama serve
```
>You are now good to continue with the setup. Feel free to pull any other models other than llama3.1 as per your wish.

## Install dependencies

1. Run this command to install dependenies in the `requirements.txt` file. 

```python
pip install -r requirements.txt
```
If any of the packages do not install correctly, or throws errors or there is a mismatch of dependencies, god be with you. Im sure you will figure it out.

2. Install markdown depenendies with: 

```python
pip install "unstructured[md]"
```

## Create database

Create the Chroma DB.

The command below will ingest the contents of the md or txt file stored in the DATA_PATH = "data/books"
Put in all the data you wish the LLM to have access to in the data/books folder then run the populate database below.

```python
python populate_database.py
```

## Query the database

Query the Chroma DB.

Run the web ui.
```python
python ui.py
```
## USES

Once the web ui is up. Note the three tabs in the ui which are a basic llm chatbot, a RAG chatbot and lastly the agent bot which requires further setup of sqlmap and katana on your machine to let the LLM agent perform commands on your machine. The basic llm chatbot is fairly straight forward. The RAG chatbot fetches results from the data you have populated from the data/books folder for context specific output. The agent runs basic crawling and sqlmap commands on a page if you ask it to and is mostly experimental.
