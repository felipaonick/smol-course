# 🧠 Supervised Fine-Tuning (SFT)

## ✅ Cos’è il Supervised Fine-Tuning?

Il **Supervised Fine-Tuning (SFT)** è un processo fondamentale per:

* Raffinare il comportamento di un **modello LLM pre-addestrato** su compiti specifici.
* Adattarlo a **casi d’uso verticali** o contesti aziendali/domains (es. customer service, medicina, legale).

---

## 🧠 Come funziona SFT?

* Mostra al modello esempi di input-output **etichettati** (token supervisionati).
* Il modello **impara pattern** coerenti con il comportamento desiderato.
* Riutilizza la conoscenza generale appresa nel pretraining, ma la **ri-orienta** su uno specifico target.

---

## 🔍 Quando usare SFT?

SFT è consigliato quando:

* Hai bisogno di **risposte consistenti e controllate**
* Il tuo dominio richiede **terminologia specialistica** o **formati rigorosi**
* Vuoi **personalizzare un modello open-source** per scenari professionali (es. normative, compliance)

✳️ **Esempi concreti**:

* Chatbot di supporto tecnico che segue le linee guida aziendali
* Modelli legali o medici con terminologia specialistica certificata

---

## 🛠 Processo di Fine-Tuning

1. **Prepara il dataset**:

   * Dataset etichettato di alta qualità (chat, QA, istruzioni)
   * Coprire **casi d’uso reali** e variabilità del linguaggio

2. **Formattazione con chat template**:

   * Es: `apply_chat_template(tokenize=False, add_generation_prompt=False)`
   * Mantieni coerenza con il pretraining del modello

3. **Fine-Tuning** con framework dedicati:

   * `transformers` (Hugging Face)
   * `trl` (Transformer Reinforcement Learning)

4. **Monitoraggio continuo**:

   * Usa set di validazione per evitare **overfitting**
   * Misura se il modello mantiene capacità generali

---

## 🧩 SFT e Preference Alignment

* SFT è **la base di partenza** per tecniche come:

  * **RLHF** (Reinforcement Learning from Human Feedback)
  * **DPO** (Direct Preference Optimization)

🔎 Il modello viene prima fine-tunato con SFT → poi ulteriormente allineato a preferenze umane tramite reward modeling o policy optimization.

---

## 🧪 TRL (Transformer Reinforcement Learning)

* Toolkit su Hugging Face per addestrare LLMs con reinforcement learning.
* Supporta architetture decoder-only e encoder-decoder.
* Include:

  * ✅ SFT (Supervised Fine-Tuning)
  * ✅ RM (Reward Modeling)
  * ✅ PPO (Proximal Policy Optimization)
  * ✅ DPO (Direct Preference Optimization)

📦 Modulo chiave per SFT + RL nei casi d’uso LLM personalizzati.

---

📘 *Il Supervised Fine-Tuning è il primo passo per ottenere modelli realmente utili nei contesti specialistici: aumenta la precisione, controlla l'output e allinea le risposte a standard professionali.*
