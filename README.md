# 🧾 Multimodal RAG Tax Filing Assistant

### **AI-Powered Document Understanding System for Tax Analysis (PDF + CSV/Excel + Images)**

This project is a **Multimodal Retrieval-Augmented Generation (RAG)** system designed to help users analyze tax-related documents such as:

* Salary Slips
* Form 16
* Investment Proofs
* Expense Reports
* PF/ELSS/LIC Receipts (Images)
* CSV/Excel financial tables

The assistant uses **PDF extraction, Table processing, Image embeddings, FAISS vector search, and rule-based answer generation**, all wrapped inside a **Gradio conversational interface**.

---

# 🌟 Key Features

### ✔️ **1. Multimodal RAG Pipeline**

The system supports all three major modalities:

| Modality       | Supported Formats | Techniques Used                           |
| -------------- | ----------------- | ----------------------------------------- |
| **PDF (text)** | .pdf              | PyPDF2 extraction + Sentence Embeddings   |
| **Tables**     | .csv, .xlsx       | Row-wise text transformation + Embeddings |
| **Images**     | .jpg/.jpeg/.png   | CLIP-based image embeddings               |

All processed chunks are indexed using **FAISS L2 vector search** to enable similarity-based retrieval.

---

### ✔️ **2. Automatic Sample Tax Document Generator**

The project ships with a built-in generator that produces realistic documents:

#### Generates:

* **Salary Slip (PDF)**
* **Form 16 (PDF)**
* **Investment Summary (CSV)**
* **Monthly Expense Report (Excel)**
* **Investment Proof Receipts (Images)**

Uses:

* **ReportLab** for PDF creation
* **Pillow (PIL)** for image generation
* **Pandas** for tables

This is ideal for testing the RAG system without needing real financial documents.

---

### ✔️ **3. RAG System with FAISS Vector Indexing**

Supports individual indices for:

* **PDF Chunks**
* **Table Rows**
* **Image Descriptions**

Models used:

* **SentenceTransformer (MiniLM-L6-v2)** for PDF & table text
* **CLIP (ViT-B/32)** for images

Retrieval returns:

* Relevant PDF sentences
* Matching rows from CSV/Excel
* Contextually relevant images

---

### ✔️ **4. Intelligent Answer Generation**

Rule-based reasoning engine handles tax-specific queries like:

* “What is my taxable income?”
* “List all Section 80C deductions.”
* “Show PF contribution details.”
* “How much TDS was deducted?”

Answers combine:

* Retrieved context
* Summaries extracted from documents
* Image previews (when relevant)

---

### ✔️ **5. Gradio Chat Application**

UI contains two tabs:

#### **📤 Upload Documents**

Upload:

* PDFs
* CSV/Excel
* Image proofs

#### **💬 Chat with Assistant**

Ask tax questions directly.

System workflow:

1. User types query
2. Embeddings generated
3. Top-k relevant chunks retrieved
4. Rule-based answer crafted
5. Response shown (with images if applicable)

---

# 🧠 Tech Stack

| Component          | Technology                                  |
| ------------------ | ------------------------------------------- |
| Embeddings (text)  | SentenceTransformer (MiniLM-L6-v2)          |
| Embeddings (image) | CLIP ViT-B/32                               |
| Vector DB          | FAISS L2 Index                              |
| Processing         | PyPDF2, Pandas, Pillow                      |
| UI                 | Gradio Blocks & ChatInterface               |
| Sample Docs        | ReportLab, Faker-style synthetic generation |
| Language           | Python                                      |

---

# 📂 Project Structure

```
Multimodal-RAG-Tax-Assistant/
│
├── sample_tax_docs/                 # Auto-generated test docs
│   ├── salary_slip_apr2024.pdf
│   ├── form16_fy2023-24.pdf
│   ├── investments_fy2023-24.csv
│   ├── monthly_expenses_2023.xlsx
│   ├── pf_receipt.jpg
│   ├── elss_certificate.jpg
│   └── lic_premium.jpg
│
├── multimodal_rag_tax_filing_assistant.py   # Main RAG application
├── README.md
└── requirements.txt
```

---

# 🚀 How to Run the Project

### **1. Install Dependencies**

```
pip install -q sentence-transformers faiss-cpu pypdf2 pandas pillow gradio openai python-dotenv transformers torch torchvision openpyxl tabulate reportlab
```

---

### **2. Generate Sample Documents**

This will create all PDF/CSV/Excel/Image samples:

```
python multimodal_rag_tax_filing_assistant.py
```

or inside the script:

```
generate_all_documents()
```

---

### **3. Launch the Gradio App**

```
demo.launch(share=True)
```

Output will show:

```
Running on: https://xxxx.gradio.live
```

Open in your browser.

---

# 📝 Example Queries

Try asking:

* **“What is my total taxable income?”**
* **“List all 80C deductions I can claim.”**
* **“Show TDS from salary slip.”**
* **“Where is PF contribution mentioned?”**
* **“Summarize investments from the CSV file.”**

The assistant retrieves relevant PDF/table/image chunks and constructs a natural answer.

---

# 🔐 Security Notice

Unlike earlier projects, **this script DOES NOT use Gemini API keys or LLM keys**.
It uses embedding models only (MiniLM + CLIP).
No API risk.

---

# 🎯 Future Enhancements

* Upgrade to full LLM-based answer generation
* Add OCR to support scanned documents
* Full tax computation engine (New vs Old Regime)
* API deployment using FastAPI
* User login + encrypted document vault

---

# 👨‍💻 Author

**Ravi Sankkaran I**
