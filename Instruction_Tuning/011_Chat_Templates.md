# 💬 Chat Templates per Language Models

📚 Modulo: Chat Templates
🎯 Obiettivo: Strutturare in modo coerente le conversazioni tra utenti e modelli LLM tramite formati standardizzati come ChatML.

---

## 📌 Cos’è un Chat Template?

* Un **chat template** è una struttura formale per organizzare il dialogo tra utente e modello.
* Serve a:

  * Garantire **coerenza** nelle interazioni
  * Mantenere il **contesto conversazionale**
  * Facilitare la comprensione del **ruolo** di ogni messaggio (utente, sistema, assistente)

---

## 🧱 Base Model vs Instruct Model

| Tipo di modello    | Caratteristiche                                                               |
| ------------------ | ----------------------------------------------------------------------------- |
| **Base Model**     | Addestrato su dati grezzi per il completamento (es. SmolLM2-135M)             |
| **Instruct Model** | Fine-tuned per seguire istruzioni e conversazioni (es. SmolLM2-135M-Instruct) |

📌 Per usare un *base model* come se fosse un *instruct model*, è essenziale formattare correttamente i prompt tramite un **chat template** (es. ChatML).

---

## 🧭 Struttura del ChatML

Esempio base:

```
<|im_start|>user
Hi there!<|im_end|>
<|im_start|>assistant
Nice to meet you!<|im_end|>
```

Esempio Python:

```python
messages = [
    {"role": "system", "content": "You are a helpful assistant focused on technical topics."},
    {"role": "user", "content": "Can you explain what a chat template is?"},
    {"role": "assistant", "content": "A chat template structures conversations between users and AI models..."}
]
```

---

## 🧩 Ruoli nei messaggi

* **system**: istruzioni globali su come il modello deve comportarsi.
* **user**: input da parte dell’utente.
* **assistant**: risposte generate dal modello.

Esempio:

```python
system_message = {
    "role": "system",
    "content": "You are a professional customer service agent. Always be polite, clear, and helpful."
}
```

---

## 🔁 Multi-turn Conversations

I chat template supportano **storico conversazionale**:

```python
conversation = [
    {"role": "user", "content": "I need help with my order"},
    {"role": "assistant", "content": "I'd be happy to help. Could you provide your order number?"},
    {"role": "user", "content": "It's ORDER-123"},
]
```

---

## ⚙️ Integrazione con Transformers

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("HuggingFaceTB/SmolLM2-135M-Instruct")

messages = [
    {"role": "system", "content": "You are a helpful coding assistant."},
    {"role": "user", "content": "Write a Python function to sort a list"},
]

formatted_chat = tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True
)
```

---

## 🎨 Personalizzazione Template

```python
template = '''
<|system|>{system_message}
<|user|>{user_message}
<|assistant|>{assistant_message}
'''.lstrip()
```

---

## 🔁 Multi-turn con contesto

```python
messages = [
    {"role": "system", "content": "You are a math tutor."},
    {"role": "user", "content": "What is calculus?"},
    {"role": "assistant", "content": "Calculus is a branch of mathematics..."},
    {"role": "user", "content": "Can you give me an example?"},
]
```

---

## 📚 Risorse utili

* [Hugging Face Chat Templating Guide](https://huggingface.co/docs/transformers/chat_templating)
* [Transformers Documentation](https://huggingface.co/docs/transformers/index)
* [Chat Templates Examples Repo](https://github.com/huggingface/transformers/tree/main/templates)

---

✅ *I chat templates sono fondamentali per portare i modelli base a comportarsi come modelli conversazionali istruiti. Offrono coerenza, chiarezza e compatibilità con strumenti come Hugging Face Transformers.*

