# Courses & Sections Semantic Search Embedding

This project demonstrates how to build a simple semantic‐search pipeline over a dataset of courses and sections using [SentenceTransformers](https://www.sbert.net/) for embeddings and [Pinecone](https://www.pinecone.io/) as a vector database.

---

## 📖 Overview

- **Data source**: `course_section_descriptions.csv`  
- **Embedding model**: `all‑MiniLM‑L6‑v2` from SentenceTransformers  
- **Vector database**: Pinecone (cloud‐hosted, serverless)  
- **Notebook**: `Courses_&_Sections_Semantic_Search_Embedding.ipynb`

---

## 🚀 Quickstart

### 1. Clone this repo

```bash
git https://github.com/JoseFArvizu/Courses_Sections_Semantic_Search_Embedding/edit/master/README.md
```

### 2. Install dependencies

```bash
pip install \
  pandas \
  python-dotenv \
  pinecone-client \
  sentence-transformers
```

### 3. Prepare your environment

Create a `.env` file in the project root with your Pinecone credentials:

\`\`\`text
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_ENV=your_pinecone_environment  # e.g. us-west1-gcp
\`\`\`

### 4. Add your data

Ensure `course_section_descriptions.csv` is in the repo root. It should contain at least the following columns:

- `course_id`
- `section_id`
- `course_name`
- `course_technology`
- `course_description`
- `section_name`
- `section_description`

### 5. Run the notebook

Launch Jupyter and open the notebook:

```bash
jupyter notebook "Courses_&_Sections_Semantic_Search_Embedding.ipynb"
```

Walk through cells to:

1. Load your CSV into a Pandas DataFrame  
2. Create a unique ID and metadata dict for each row  
3. Generate embeddings with SentenceTransformer  
4. Initialize Pinecone (`my-index`) and upsert vectors  
5. Query the index with a sample prompt (e.g., “regression in Python”)  
6. Print out any matches above your score threshold (default: 0.4)

---

## ⚙️ Configuration

All of these parameters can be tweaked directly in the notebook:

| Variable           | Default         | Description                                  |
| ------------------ | --------------- | -------------------------------------------- |
| `index_name`       | `my-index`      | Name of your Pinecone index                  |
| `dimension`        | `384`           | Embedding dimension of `all‑MiniLM‑L6‑v2`     |
| `metric`           | `cosine`        | Similarity metric for Pinecone               |
| `top_k`            | `12`            | Number of nearest neighbors to return        |
| `score_threshold`  | `0.4`           | Minimum similarity score to consider a hit   |

---

## 📂 Project Structure

\`\`\`
.
├── Courses_&_Sections_Semantic_Search_Embedding.ipynb
├── course_section_descriptions.csv
├── .env
├── README.md
\`\`\`

---

