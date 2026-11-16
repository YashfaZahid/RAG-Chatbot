# Origin

Origin is a multi-turn chat workspace. You set the system role, pick a model, set the temperature, and keep threads on disk in `chats.json`.

The repository is named RAG-Chatbot. This build does not retrieve documents. There is no vector store, no file upload, and no citation step. It is a system-prompted assistant with a custom Streamlit UI. SupportPearlz is the retrieval project.

## What it does

- Default persona: a precise technical assistant, editable from the sidebar
- Model name and temperature stored in the session
- Prompt starters for architecture and debugging questions
- Local chat history in `chats.json`
- A charcoal UI drawn in the page, with no image assets

## Run

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Create a `.env` file next to `app.py`:

```text
OPENAI_API_KEY=sk-...
```

```bash
streamlit run app.py
```

Do not commit `.env`. `chats.json` is local history. Treat it as private if you use the app for real notes.

## Layout

```text
app.py              UI, session, and the chat call
requirements.txt    openai, langchain, langchain-openai, streamlit
chats.json          Saved threads
```

## Limits

Answers are the model's, constrained only by the system role you typed. There is no grounding in your files. If you need answers from a knowledge base, use SupportPearlz.
