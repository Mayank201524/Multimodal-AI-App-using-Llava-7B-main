# Multimodal Retrieval-Augmented Generation (RAG) Pipeline
This project implements a **Multimodal Retrieval-Augmented Generation (RAG)** system that can retrieve and reason over both textual and image data. The pipeline leverages **OpenAI** for language and embedding models (text), **CLIP** (via `open_clip`) for image embeddings, and **FAISS** for efficient similarity search. It is designed to answer natural language queries over a mixed corpus of text and images.

## 🚀 Features
- **Multimodal retrieval:** Seamlessly search over both text and image datasets.
- **Text understanding:** Uses OpenAI embeddings for semantic text search.
- **Image understanding:** Uses CLIP for encoding and retrieving images based on their relevance to a text query.
- **Efficient retrieval:** FAISS for fast vector similarity search.
- **Generative QA:** (Optional) Use OpenAI GPT to generate final answers from retrieved context.

## 📁 Project Structure
- `multimodal_rag.py` — Main pipeline script
- `texts/` — Directory containing text documents (.txt)
- `images/` — Directory containing image documents (.jpg/.png)

## 🛠️ Requirements
- Python 3.8+
- `openai`
- `faiss-cpu`
- `open_clip_torch`
- `Pillow`
- `tqdm`
- `torch`
- `numpy`
**Install all dependencies:**  
`pip install openai faiss-cpu open_clip_torch Pillow tqdm torch numpy`

## 📦 Usage
1. **Prepare your data:** Place text files in the `texts/` directory and image files in the `images/` directory.
2. **Set your OpenAI API key:** Export your key as an environment variable:  
`export OPENAI_API_KEY=sk-...`
3. **Run the script:**  
`python multimodal_rag.py --query "your question here"`
**Available arguments:**  
- `--query` : Your natural language query.
- `--k` : Number of top text and image results to retrieve (default: 3).
- `--texts_path` : Path to text docs folder (default: `texts/`).
- `--images_path` : Path to images folder (default: `images/`).

## ⚙️ How It Works
1. **Embedding:** Text docs are split and embedded using OpenAI’s model. Images are embedded using CLIP.
2. **Indexing:** FAISS indexes are built for both text and image embeddings.
3. **Retrieval:** For a user query, the system retrieves top matching text chunks and top matching images (using CLIP’s text encoder).
4. **(Optional) Answer Generation:** Retrieved contexts (text + image info) are combined and, optionally, passed to GPT to generate a final answer.

## 💡 Example
`python multimodal_rag.py --query "Describe the Mona Lisa and show similar images."`  
The system retrieves relevant text and images, then (optionally) generates an answer.

## 🛠️ Customization
Adjust chunk size, number of top results, model names, or other parameters by editing `multimodal_rag.py`. Swap out embedding or generation models as desired.

## 🙏 Credits
**Text embeddings:** [OpenAI](https://openai.com/)  
**Image embeddings:** [CLIP (open_clip)](https://github.com/mlfoundations/open_clip)  
**Vector search:** [FAISS](https://github.com/facebookresearch/faiss)

## 📜 License
MIT License
