# tangguh-demo

A Streamlit demo dashboard for TANGGUH, a child nutrition and health assistant. It combines a stunting prediction model with a generative-AI chatbot and a feedback form.

## Features

The sidebar of `dashboard.py` exposes three pages:

- **Interaction with TANGGUH** - a chat interface for questions about child nutrition and health, backed by a generative language model (Google PaLM). A GPT-4 option exists in the code but is shown as not yet available.
- **Stunting prediction** - takes a child's sex, age, birth weight and length, current weight and length, and exclusive breastfeeding status, runs a trained scikit-learn model, and asks the language model to explain the result and give advice.
- **Feedback** - a form that sends feedback by email through SMTP.

Texts are translated with `deep_translator`.

## Tech stack

- Python, Streamlit
- scikit-learn, pandas
- Google Generative AI (PaLM) and OpenAI chat clients
- deep_translator

## Structure

| Path | Purpose |
| --- | --- |
| `dashboard.py` | Streamlit entry point and sidebar navigation |
| `homepage/` | Home page and the feedback email form |
| `models/pred_advice.py` | Stunting prediction and advice generation |
| `models/relate_chatbot.py` | Chat interface |
| `models/chatbot/` | PaLM and GPT-4 client wrappers |
| `models/multimodels/` | Notebook and Excel dataset used to build the prediction model |
| `helper/translator.py` | Translation helper |

## Running it

```bash
pip install -r requirements.txt
streamlit run dashboard.py
```

The app also expects local files that are not part of this repository: the trained `model.pkl`, a `secret/getApi.py` module that supplies the API keys, and the `assets/tangguh.png` logo. Note that `smtplib` and `email` listed in `requirements.txt` are part of the Python standard library; remove them from the file if `pip install` fails on them.
