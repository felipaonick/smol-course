# 🧠 Instruction Tuning di Language Models

📚 Modulo: Instruction Tuning
🎯 Obiettivo: Adattare modelli linguistici pre-addestrati a task specifici tramite dati supervisionati e strutture conversazionali (chat templates).

---

## 📌 Cos’è l’Instruction Tuning?

* È il processo di **adattamento di un modello LLM pre-addestrato** a specifici compiti.
* Si realizza tramite:

  1. **Chat Templates** – strutturazione dell’interazione AI-utente
  2. **Supervised Fine-Tuning (SFT)** – addestramento supervisionato con dataset etichettati

---

## 1️⃣ Chat Templates

### 📋 Definizione

* Template che strutturano il dialogo tra utenti e modelli AI.
* Utili per:

  * Assicurare **consistenza** e **contestualità** nelle risposte
  * Allineare l’output a **formati strutturati** come `chatml`

### 🧱 Componenti tipici

* **System prompt**: definisce il comportamento del modello
* **Role-based messages**: suddivisione dei messaggi tra `user`, `assistant`, `system`

### 🧪 Esercizi pratici (notebook)

| Esercizio                                       | Obiettivo |
| ----------------------------------------------- | --------- |
| 🐢 Converti `HuggingFaceTB/smoltalk` → `chatml` |           |
| 🐕 Converti `openai/gsm8k` → `chatml`           |           |

🔗 **Notebook**: chat_templates.ipynb

---

## 2️⃣ Supervised Fine-Tuning (SFT)

### ⚙️ Definizione

* Addestramento supervisionato di un LLM su **dataset etichettati per un task specifico**.
* Obiettivo: migliorare la performance del modello sul task target.

### 🪜 Fasi principali

1. Scelta del dataset (es. `smoltalk`, `the-stack-smol`)
2. Conversione in formato `chatml` (se necessario)
3. Utilizzo di `SFTTrainer` (es. da `trl`) per eseguire il fine-tuning
4. Valutazione delle performance e iterazione

### 🧪 Esercizi pratici (notebook)

| Esercizio                                    | Obiettivo |
| -------------------------------------------- | --------- |
| 🐢 SFT su `HuggingFaceTB/smoltalk`           |           |
| 🐕 SFT su `bigcode/the-stack-smol`           |           |
| 🦁 Scegli un dataset per un caso d’uso reale |           |

🔗 **Notebook**: sft_finetuning.ipynb

---

## 🔗 Risorse e riferimenti

* 📘 [Transformers documentation on chat templates](https://huggingface.co/docs/transformers/chat_templating)
* 🧪 [Script per SFT in TRL](https://github.com/huggingface/trl)
* 🧠 [`SFTTrainer` in TRL](https://huggingface.co/docs/trl/main/en/sft_trainer)
* 📄 [Paper su Direct Preference Optimization](https://arxiv.org/abs/2305.18290)
* 📝 [Guida SFT con TRL](https://huggingface.co/blog/fine-tune-trl)
* 🤖 [Fine-tune Google Gemma con ChatML e TRL](https://huggingface.co/blog/fine-tune-gemma)
* 🌍 [Fine-tuning LLM per cataloghi JSON in persiano](https://huggingface.co/blog/fine-tune-llm-json-persian)

---

✅ *Instruction tuning è una componente fondamentale per costruire applicazioni LLM specializzate, affidabili e allineate agli obiettivi utente. Chat templates + SFT = pipeline robusta.*

