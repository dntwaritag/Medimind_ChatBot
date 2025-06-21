# Medimind_ChatBot:  A Domain-Specific Medical Chatbot

1. Introduction
Medimind is an intelligent chatbot designed to provide accurate information about medications, their side effects, and related medical conditions. It uses advanced NLP techniques, including a fine-tuned Transformer model and a Retrieval-Augmented Generation (RAG) system, to deliver precise and relevant responses within the healthcare domain.

2. Features
Domain-Specific Answers: Provides information focused on drugs, side effects, and medical conditions.

Intelligent Query Handling: Understands user questions and retrieves relevant information.

Retrieval-Augmented Generation (RAG): Combines information retrieval with generative AI for factually grounded responses.

Out-of-Domain Rejection: Gracefully declines to answer non-medical questions.

User-Friendly Interface: An intuitive web interface built with Gradio.

Configurable AI: Option to use an advanced LLM (Groq) if an API key is provided.

3. Domain Focus
Medimind is specifically aligned with the healthcare domain, focusing on drug information and side effects to ensure accuracy and relevance.

4. Dataset
The chatbot's knowledge base is built using the drugs_side_effects_drugs_com.csv dataset, which contains structured information on drug names, medical conditions, and reported side effects.

Key Preprocessing Steps:
Handling missing values.

Creating diverse question-answer pairs for fine-tuning.

Tokenization using Hugging Face's AutoTokenizer.

Splitting data into training, validation, and test sets.

5. Model Used
Core Model: google/flan-t5-small, fine-tuned on the medical dataset.

Embedding Model: sentence-transformers/all-MiniLM-L6-v2 for the vector database.

Vector Database: ChromaDB for efficient information retrieval.

Optional LLM: llama-3.1-70b-versatile (via Groq API) for advanced response generation.

The system uses a RAG framework: it retrieves relevant context from the database first, then generates an answer based on that context.

6. Performance Highlights
The fine-tuned flan-t5-small model showed significant improvements over the flan-t5-base baseline across various NLP metrics like ROUGE, BLEU, METEOR, and Exact Match Accuracy, demonstrating effective domain adaptation. Qualitatively, Medimind provides meaningful responses and effectively rejects out-of-domain queries.

7. User Interface
The chatbot features a user-friendly web interface built with Gradio, providing clear input/output areas, an option to use advanced AI, and sections for retrieved context and sources. A prominent disclaimer reminds users about the informational nature of the chatbot.

8. Demo Video
A demonstration video showcasing Medimind's functionality, user interactions, and key features will be added here.

Watch the Demo Video on YouTube

9. Setup and Run
Clone the repository:

git clone https://github.com/your-username/Medimind.git
cd Medimind

(Replace with your actual repository URL)

Install dependencies:

pip install -r requirements.txt

(Or rely on the pip install commands within medimindbot.py).

API Keys: If using Groq, set your GROQ_API_KEY as an environment variable or in Colab secrets. Ensure your data path is correctly configured for drugs_side_effects_drugs_com.csv.

Run the script:

python medimindbot.py

Access UI: Open the local URL provided by Gradio in your browser.

10. Examples
"What are the side effects of Ibuprofen?"

"Tell me about the side effects of Lisinopril for high blood pressure."

"Is Amoxicillin safe to use?"

"What is the capital of France?" (Out-of-domain query)

11. Future Plans
Expand medical domain coverage.

Improve out-of-domain detection.

Add conversational memory.

Introduce multilingual support.

Integrate with external medical APIs.
