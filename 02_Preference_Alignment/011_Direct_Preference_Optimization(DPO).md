# 🧠 Direct Preference Optimization (DPO)

## 📌 Cos'è DPO?
**Direct Preference Optimization (DPO)** è un approccio semplificato all'allineamento dei modelli linguistici (LLM) alle preferenze umane. A differenza di RLHF (Reinforcement Learning from Human Feedback), DPO **non richiede un reward model separato né algoritmi di reinforcement learning complessi** come PPO.

> ✅ Vantaggi principali:
- Nessun reward model richiesto
- Niente RL (es. PPO)
- Approccio più stabile ed efficiente
- Usato in modelli come **LLaMA**

---

## 🔍 Comprendere DPO

### ⚙️ Recasting come problema di classificazione
DPO trasforma l’allineamento alle preferenze in un **problema di classificazione binaria** basato su coppie di risposte:
- Una preferita (chosen)
- Una non preferita (rejected)

### 🧮 Funzione di Loss
Viene usata una **binary cross-entropy loss** per ottimizzare direttamente i pesi del modello rispetto ai dati di preferenza.

---

## 🔧 Processo DPO

1. **Supervised Fine-Tuning (SFT)**  
   - Il modello viene prima adattato al dominio target usando dataset di istruzioni.
   - Costruisce le basi per il preference learning.

2. **Preference Learning**  
   - Si addestra il modello su **coppie di risposte** annotate come `preferred` o `non-preferred`.
   - Il modello impara a distinguere tra risposte migliori e peggiori.

3. **Ottimizzazione diretta**  
   - Il modello viene aggiornato direttamente con i dati di preferenza.
   - Non c'è fase di reward modeling né RL.

---

## 📊 Dataset DPO

### ✅ Struttura Tipica

| Prompt | Chosen | Rejected |
|--------|--------|----------|
| ...    | ...    | ...      |

- `Prompt`: testo input.
- `Chosen`: risposta preferita.
- `Rejected`: risposta meno desiderata.

> 🔁 Varianti: può includere anche `system prompt` o `input` con contesto.  
> 🎭 Supporta dialoghi single-turn (stringhe) o multi-turn (liste di messaggi).

📚 **Dataset DPO disponibili su Hugging Face**:  
👉 [https://huggingface.co/datasets](https://huggingface.co/datasets) (cerca “DPO”)

---

## 🧪 Esempio di Implementazione con `trl`

```python
from trl import DPOConfig, DPOTrainer

# Configurazione
training_args = DPOConfig(
    model_name="your-model-name",
    beta=0.1,
    learning_rate=1e-5,
    ...
)

# Trainer
trainer = DPOTrainer(
    model=model,
    train_dataset=dataset,
    tokenizer=tokenizer,
    args=training_args
)

# Addestramento
trainer.train()
````

> 📘 Maggiori dettagli nel [DPO Tutorial](https://huggingface.co/docs/trl)

---

## ✅ Best Practices

* **Qualità dei dati**: fondamentale.

  * Annotazioni coerenti e chiare.
  * Filtrare esempi di bassa qualità.
  * Preferire dataset adatti allo use-case.

* **Monitoraggio durante il training**:

  * Convergenza della loss
  * Valutazione su dati di validazione
  * Regolare il parametro `beta` se necessario

* **Valutazione**:

  * Confrontare output del modello con quelli del modello di riferimento.
  * Test su prompt diversi (inclusi edge cases).

---

## 🚀 Prossimi Passi

### 📓 DPO Tutorial

👉 Guida pratica per:

* Preparazione dei dati
* Addestramento
* Valutazione

### 🔄 Esplora anche: ORPO

Dopo DPO, esplora **Odds Ratio Preference Optimization**, una tecnica avanzata che unifica SFT e allineamento delle preferenze in un singolo passaggio.

---

> 💡 Con DPO puoi migliorare l’allineamento alle preferenze umane in modo **più semplice, stabile ed efficiente** rispetto a RLHF.

```
