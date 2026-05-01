# vector-db-visualization- 

This project is a high-performance **Vector Database** with a beautiful **AI Visualizer**. It allows you to store, search, and visualize data based on its "meaning" (semantics) rather than just keywords.

## 🚀 What is happening?

Imagine you have thousands of notes. Usually, you'd search for a specific word. In this project, you can search for a **concept**. For example, searching for "sushi" might find results about "ramen" or "Japanese food" even if the word "sushi" isn't there, because the system understands they are related.

### 🧠 The Brain (Backend - C++)
The backend is built in **C++** for extreme speed. It handles the "heavy lifting" of math and data storage.

1.  **Vector Storage**: It stores data as "vectors" (long lists of numbers). These numbers represent the "fingerprint" of the data's meaning.
2.  **Search Algorithms**: It implements three ways to find the closest matches:
    *   **Brute Force**: Checks every single item (slow but 100% accurate).
    *   **KD-Tree**: A smart tree structure that narrows down the search space (faster).
    *   **HNSW (Hierarchical Navigable Small World)**: A cutting-edge "graph" structure. It's like a social network for data—it jumps between related points to find the best match incredibly fast.
3.  **Local AI (Ollama)**: It connects to **Ollama** to use real AI models (like Llama 3.2) to:
    *   Turn your text into vectors (Embedding).
    *   Answer your questions based on your notes (RAG - Retrieval Augmented Generation).

### 🎨 The Face (Frontend - HTML/JS)
The frontend is a futuristic dashboard that lets you see the "semantic space."

1.  **3D/2D Visualizer**: It uses a math trick called **PCA (Principal Component Analysis)** to squash complex AI data into a 2D map. You can actually see clusters of related topics (e.g., all sports notes grouping together).
2.  **Search & Interact**: You can type queries, see the search latency in microseconds, and watch the visualizer highlight the best matches.
3.  **Ask AI Tab**: You can upload documents, and then chat with them. The system finds the most relevant parts of your docs and gives them to the AI to help it answer you accurately.

## 🛠️ How it works (The Flow)

1.  **Input**: You type "What is a binary tree?" in the frontend.
2.  **Embedding**: The backend sends this text to Ollama, which returns a "vector" (e.g., `[0.12, -0.45, ...]`).
3.  **Search**: The C++ engine uses the **HNSW graph** to find the most similar vectors in your database in less than a millisecond.
4.  **Retrieval**: The backend pulls the original text for those matching vectors.
5.  **Generation**: If you're in the "Ask AI" tab, it sends your question + those matching snippets to the AI (Llama 3.2).
6.  **Response**: The AI gives you a natural answer, and the frontend shows you exactly which documents it used as context on the map.

## 📂 Key Files
- [main.cpp](file:///c:/Users/raghav/Your-OWN-AI/main.cpp): The entire C++ engine (Server, Database, Algorithms).
- [index.html](file:///c:/Users/raghav/Your-OWN-AI/index.html): The beautiful, dark-themed dashboard and visualizer logic.
- [httplib.h](file:///c:/Users/raghav/Your-OWN-AI/httplib.h): A library used for the C++ web server.
