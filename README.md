# 🌐 Microsoft Graph-RAG Indexing and Quering

## 🕸 GraphRAG 

is a modular graph-based Retrieval-Augmented Generation (RAG) system designed to extract meaningful, structured data from unstructured text using the power of large language models (LLMs). It enhances LLMs’ ability to reason about private data by leveraging knowledge graph memory structures. The system is part of a data pipeline and transformation suite that aims to improve the accuracy and relevance of generated text.

## 🕸 WorkFlow of LLM-generated knowledge graphs
- The LLM processes the entire private dataset, creating references to all entities and relationships within the source data, which are then used to create an LLM-generated knowledge graph. 
- This graph is then used to create a bottom-up clustering that organizes the data hierarchically into semantic clusters (indicated by using color in Figure 3 below). This partitioning allows for pre-summarization of semantic concepts and themes, which aids in holistic understanding of the dataset. 
- At query time, both of these structures are used to provide materials for the LLM context window when answering a question. 

> Notebook : Graph_RAG.ipynb

## 🛠️ How to use :

> Install and Input Directory :
```
pip install graphrag
mkdir -p input`
```
> Populate  `input` Directory with documents to RAG
```
Input File : Financial_Fundamental_Analysis.txt
```

> initialize workspace, run the graphrag.index --init command in . root folder

```
python -m graphrag.index --init --root .
```

> Running the Query Engine - `Global Search`
**Global search to ask a high-level question or holostic question**

```
python -m graphrag.query \
--root . \
--method global \
"What are the top themes in this story?"
```

> Running the Query Engine - `Local Search`
**Local search to ask a more specific question about a particular character**

```
python -m graphrag.query \
--root ./ragtest \
--method local \
"Who is Scrooge, and what are his main relationships?"
```

---

## 📰 Key Features of GraphRAG:

### 🌐  https://microsoft.github.io/graphrag/posts/get_started/

### Knowledge Graph Creation:
GraphRAG uses LLMs to create a knowledge graph from an input corpus. This graph represents the relationships and entities within the data, providing a structured way to understand complex information12.

### Prompt Augmentation:
At query time, GraphRAG uses the knowledge graph to augment prompts. This means that when a user asks a question, the system can provide more accurate and contextually relevant answers by leveraging the structured data in the graph13.

### Improved Retrieval:
Traditional Retrieval-Augmented Generation (RAG) techniques often rely on vector similarity for searching information. GraphRAG enhances this by using graph-based methods, which can better connect disparate pieces of information and provide synthesized insights12.

### Application to Private Data:
One of the significant advantages of GraphRAG is its ability to work with private datasets that the LLM has never seen before. This includes proprietary research, business documents, and other sensitive information12.

### Enhanced Document Analysis:
GraphRAG shows substantial improvements in question-and-answer performance, especially when dealing with complex documents or large data collections. It can identify themes, semantic concepts, and provide holistic understanding.

### Example Use Case:
Imagine you have a large collection of business reports and you want to extract key insights. Using GraphRAG, you can create a knowledge graph from these reports and then query the system to get detailed, contextually relevant answers about trends, key themes, and other insights.

For more detailed information, you can check out the GraphRAG repository and the Microsoft Research Blog Post.



