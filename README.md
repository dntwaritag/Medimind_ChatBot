#  Medimind: A Domain-Specific Medical Chatbot

---

## 1. Introduction

**Medimind** is a smart, domain-specific chatbot designed to deliver accurate and informative responses about medications, side effects, and related medical conditions. Powered by a fine-tuned **Transformer model** and an advanced **Retrieval-Augmented Generation (RAG)** framework, it merges generative AI with medical data retrieval to provide **fact-based and context-aware answers**.

---

## 2. Key Features

* **Domain-Specific Intelligence**: Focused on medications, adverse effects, and health-related questions.
* **RAG Architecture**: Combines context retrieval with generative modeling for grounded responses.
* **Smart Query Handling**: Identifies and rejects non-medical questions politely.
* **Gradio Interface**: Offers a clean, web-based UI for seamless user interaction.
* **Optional LLM Integration**: Supports Groq’s LLaMA 3.1 model for enhanced generation when API access is available.

---

## 3. Domain Focus

Medimind is tailored for the **healthcare domain**, specializing in drug-related queries. It ensures safe, specific, and relevant responses for users seeking guidance on side effects or medication use.

---

## 4. Dataset

The chatbot is trained on the `[drugs_side_effects_drugs_com.csv](https://drive.google.com/file/d/1k21j42Wq7YYb_rsB-NGafZkFcAThbzzB/view?usp=drive_link)` dataset, which includes user-submitted reviews detailing drug names, side effects, medical conditions, and ratings.

### Preprocessing Steps:

* Filling or removing missing values
* Generating diverse Q\&A pairs
* Tokenization using Hugging Face’s AutoTokenizer
* Splitting into training, validation, and test sets

---

## 5. Models Used

| Component       | Model                                    |
| --------------- | ---------------------------------------- |
| Core QA Model   | `google/flan-t5-small` (fine-tuned)      |
| Baseline Model  | `google/flan-t5-base`                    |
| Embedding Model | `sentence-transformers/all-MiniLM-L6-v2` |
| Vector Database | ChromaDB                                 |
| Optional LLM    | `llama-3.1-70b-versatile` via Groq API   |

The system retrieves top-k documents, then generates a response grounded in that context using a Transformer-based model.

---

## 6. Performance Overview

The fine-tuned Flan-T5 model outperformed the baseline across all major metrics:

| Metric       | Fine-tuned | Baseline |
| ------------ | ---------- | -------- |
| **ROUGE-1**  |  53.9%     | 39.2%    |
| **BLEU**     |  44.7%     | 31.4%    |
| **METEOR**   |  47.9%     | 36.2%    |
| **Accuracy** |  71.3%     | 52.0%    |

Medimind also excels in **qualitative testing**, generating reliable answers while rejecting irrelevant queries effectively.

---

## 7. User Interface

Medimind features a **modern, responsive web interface** built with **Gradio**. Key components include:

* Question input with optional Groq AI toggle
* Clear response area with drug and condition summaries
* Accordion for retrieved context, sources, and metrics
* Disclaimer reminding users to consult healthcare professionals

---

## 8. Demo Video

Watch a full demonstration of Medimind’s functionality, including setup, training, and live interaction.

 [Watch the Demo Video](https://youtu.be/CtdxsC5Alv0)

---

## 9. Getting Started

###  Clone the Repository

```bash
git clone https://github.com/dntwaritag/Medimind_ChatBot.git
cd Medimind
```


###  Install Dependencies

```bash
pip install -r requirements.txt
```

> Alternatively, dependencies are auto-installed via `medimindbot.py`.

###  API Keys

To enable Groq integration, set your `GROQ_API_KEY` environment variable or use Colab secrets.

Ensure your dataset path (`[drugs_side_effects_drugs_com.csv](https://drive.google.com/file/d/1k21j42Wq7YYb_rsB-NGafZkFcAThbzzB/view?usp=drive_link)`) is correctly configured.

###  Run the Chatbot

```bash
python MedimindBot.py
```

Once launched, access the chatbot via the Gradio-provided local URL.

---

## 10. Sample Queries

Try the following:

* "What are the side effects of **Ibuprofen**?"
* "Tell me about the side effects of **Lisinopril** for **high blood pressure**."
* "Is **Amoxicillin** safe to use?"
* "What is the capital of France?" → *Out-of-domain query*

---

## 11. Future Improvements

* Expand coverage across more medical subdomains
* Improve detection and rejection of out-of-scope queries
* Add conversational memory for follow-up questions
* Support multilingual Q\&A
* Integrate verified external medical APIs

---

