# 📌 Preference Alignment 

## 🎯 Obiettivo del Modulo

Apprendere tecniche per **allineare i modelli linguistici (LLM)** alle **preferenze umane**, in modo che le risposte non siano solo corrette, ma anche **coerenti con valori e aspettative umane**.

> 🔑 **Differenza chiave**:
>
> * **SFT (Supervised Fine-Tuning)** → insegna compiti specifici
> * **Preference Alignment** → affina il comportamento del modello secondo preferenze umane

---

## 🧭 Panoramica dei Metodi di Allineamento

### 🔁 Pipeline Classica di Allineamento

1. **Supervised Fine-Tuning (SFT)**
   Adattamento iniziale a compiti o domini specifici.
2. **Preference Alignment**
   Ulteriore affinamento per migliorare la qualità delle risposte tramite tecniche come:

   * **RLHF** (Reinforcement Learning from Human Feedback)
   * **DPO** (Direct Preference Optimization)
   * **ORPO** (Odds Ratio Preference Optimization)

> ✨ Alcuni approcci moderni, come **ORPO**, **fondono** i due stadi in un unico processo semplificato ed efficiente.

---

## 1️⃣ Direct Preference Optimization (DPO)

### ✅ Descrizione

* Approccio **semplificato** all’allineamento basato su preferenze umane.
* Utilizza direttamente dati di **preferenze** (es: A preferito a B) per **ottimizzare** il modello.
* Evita la necessità di:

  * Modelli di reward
  * Algoritmi di reinforcement learning complessi
* È più **stabile**, più **facile da implementare** e **più efficiente** di RLHF.

### 📚 Risorsa di approfondimento

* [Documentazione DPO (Hugging Face)](https://huggingface.co/blog/dpo)

---

## 2️⃣ Odds Ratio Preference Optimization (ORPO)

### ✅ Descrizione

* Tecnica **unificata** che combina:

  * **Instruction Tuning**
  * **Preference Alignment**
* Obiettivo: modificare la funzione di loss della language modeling combinando:

  * **Negative Log-Likelihood Loss**
  * **Termine Odds Ratio (token-level)**

### ⚙️ Caratteristiche

* **Single-stage training** (un solo processo addestrativo)
* **Senza modello di riferimento (reference-free)**
* **Efficienza computazionale** superiore
* Ottimi risultati su benchmark come **AlpacaEval**

### 📚 Risorsa di approfondimento

* [Documentazione ORPO (Hugging Face)](https://huggingface.co/blog/orpo)

---

## 🧪 Esercizi Pratici (con Notebook)

| Titolo                                 | Descrizione Attività                                       | Link                                                                                                            | Colab |
| -------------------------------------- | ---------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ----- |
| **DPO Training**                       | 🔹 Usa il dataset HH-RLHF di Anthropic                     |                                                                                                                 |       |
| 🔸 Usa un tuo dataset di preferenze    |                                                            |                                                                                                                 |       |
| 🔸 Prova modelli di dimensioni diverse | [Notebook DPO](https://huggingface.co/blog/dpo#training)   | [Apri in Colab](https://colab.research.google.com/github/huggingface/trl/blob/main/examples/dpo_trainer.ipynb)  |       |
| **ORPO Training**                      | 🔹 Allena un modello con dati di istruzione + preferenze   |                                                                                                                 |       |
| 🔸 Varia il peso della loss            |                                                            |                                                                                                                 |       |
| 🔸 Confronta ORPO con DPO              | [Notebook ORPO](https://huggingface.co/blog/orpo#training) | [Apri in Colab](https://colab.research.google.com/github/huggingface/trl/blob/main/examples/orpo_trainer.ipynb) |       |

---

## 📚 Altre Risorse

* 🔗 [Blog di Argilla](https://argilla.io/blog) – panoramica su tecniche di alignment
* 🔗 [Hugging Face TRL Library](https://github.com/huggingface/trl) – implementazioni open-source di DPO e ORPO

---

## ✅ Riepilogo

| Metodo                                         | Vantaggi                                            | Limitazioni |
| ---------------------------------------------- | --------------------------------------------------- | ----------- |
| **DPO**                                        | ➕ Più semplice di RLHF                              |             |
| ➕ Niente reward model                          |                                                     |             |
| ➕ Addestramento diretto su preferenze          | ➖ Richiede preferenze annotate                      |             |
| ➖ Meno flessibile di RLHF in alcuni scenari    |                                                     |             |
| **ORPO**                                       | ➕ Addestramento unificato (istruzioni + preferenze) |             |
| ➕ Architettura reference-free                  |                                                     |             |
| ➕ Alta efficienza                              | ➖ Ancora in fase sperimentale                       |             |
| ➖ Necessità di buona configurazione della loss |                                                     |             |


