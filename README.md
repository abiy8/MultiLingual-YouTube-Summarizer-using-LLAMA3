# Multilingual YouTube Summarizer

A Gradio application that retrieves YouTube captions, summarizes them with a locally hosted Llama 3 model, and optionally translates the result.

**Stack:** Python · Gradio · LangChain · Ollama / Llama 3 · deep-translator

## Features

- Retrieve a video's title, description, and available transcript.
- Split transcripts into configurable chunks.
- Produce a map-reduce summary with adjustable temperature.
- Translate the summary using GoogleTranslator.

## Architecture

`YouTube captions → LangChain loader → text chunks → Ollama Llama 3 → combined summary → optional translation → Gradio UI`

## Run locally

```bash
git clone https://github.com/abiy8/MultiLingual-YouTube-Summarizer-using-LLAMA3.git
cd MultiLingual-YouTube-Summarizer-using-LLAMA3
python -m venv .venv
# Activate .venv for your operating system.
pip install -r requirements.txt
ollama pull llama3
ollama serve
# In another terminal, with the environment active:
python main.py
```

Open `http://localhost:7860`. If Ollama is already running, skip `ollama serve`. No OpenAI API key is required by this implementation: `tiktoken` uses a GPT-4 tokenizer only to estimate token counts.

## Limitations

The application retrieves existing captions; it does not perform speech recognition on videos without captions. YouTube availability, scraping changes, translation limits, and model resources affect results. Summaries may omit or misstate information. Dependencies are unpinned and use older LangChain APIs, so a compatible environment may be needed. `demo.launch(share=True)` requests a public Gradio share link; set `share=False` for local-only use.

## Provenance

The previous README referenced [motolomygolda's repository](https://github.com/motolomygolda/MultiLingual-YouTube-Summarizer-using-LLAMA3). That reference is retained here for transparency; this page documents the code in `abiy8`'s repository and does not claim sole original authorship. No license file is included in this checkout, so the previous unverified MIT license claim has been removed.
