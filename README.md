# Projet RAG (Retrieval-Augmented Generation) : Optimisation du Chunking

Ce dépôt contient une implémentation de **Retrieval-Augmented Generation (RAG)** conçue pour démontrer l'importance cruciale de la stratégie de découpage du texte (**chunking**) sur la qualité des réponses d'une IA.



## 📋 Description du Projet
L'objectif est de construire un système capable de répondre à des questions complexes sur un document technique (ici, un livre de thermodynamique de 39 Mo) en utilisant une base de données vectorielle. Le projet compare trois approches de traitement des données pour optimiser la pertinence sémantique.

## 🛠️ Stack Technique
* **Base de données vectorielle :** ChromaDB.
* **Modèle d'Embeddings :** `all-MiniLM-L6-v2` via `sentence-transformers`.
* **LLM :** Modèles via l'API OpenRouter (ex: GPT-4o).
* **Traitement de texte :** NLTK et LangChain.

## 📂 Stratégies de Chunking Comparées

### 1. Chunking Basique (Taille fixe)
Découpage simple en blocs de 500 caractères avec un chevauchement de 100 caractères.
* **Inconvénient :** Risque élevé de couper des phrases ou des idées au milieu, nuisant à la cohérence sémantique.

### 2. Solution 1 : NLTK (Basé sur les phrases)
Utilisation de la tokenisation par phrases pour s'assurer qu'un bloc ne s'arrête jamais en plein milieu d'une idée.
* **Outil :** `sent_tokenize` de la bibliothèque NLTK.

### 3. Solution 2 : LangChain (RecursiveCharacter)
Découpage hiérarchique intelligent utilisant des séparateurs logiques (`\n\n`, `\n`, `.`, ` `).
* **Avantage :** Préserve au maximum la structure logique et sémantique du texte.



## 🚀 Installation et Utilisation

### Prérequis
```bash
pip install chromadb openai pypdf2 python-docx sentence-transformers nltk langchain langchain-text-splitters

## Configuration
Placez vos documents (PDF, DOCX, TXT) dans le dossier du projet.


Configurez votre clé API OpenRouter dans le code:


Python
OPEN_ROUTER_API_KEY = "VOTRE_CLE_API"
Lancez le notebook pour indexer les documents et interroger le système.

