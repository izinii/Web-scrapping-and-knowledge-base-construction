# Web-scrapping-and-knowledge-base-construction
This project is part of the Web datamining &amp; semantics course.

![BBC Website](Documents/bbc_website_image.png)

## Overview

This project is divided into two parts: **Part 1: Web Scraping and Knowledge Base Construction** and **Part 2: Knowledge Graph Embedding**. The goal is to build a knowledge graph from raw text data (such as articles), enrich it using external data sources like DBpedia, and then apply knowledge graph embedding techniques to analyze and visualize the relationships between the entities in the graph.

### **Part 1: Web Scraping and Knowledge Base Construction**

In **Part 1**, we focus on building a knowledge graph by scraping web content, cleaning the data, and performing several Natural Language Processing (NLP) tasks. The tasks in this part include:

1. **Text Cleaning & Preprocessing**: 
   - We clean and normalize the text dataset by removing unwanted characters and applying tokenization, stemming, and lemmatization.
   
2. **Named Entity Recognition (NER)**: 
   - Using CRF models and spaCy’s pre-trained models (such as `en_ner_conll03`), we extract named entities from the text, such as persons, organizations, and locations.
   
3. **Relation Extraction (RE)**: 
   - We use spaCy to extract relationships between the identified entities. This includes applying dependency parsing to identify subject-predicate-object triples.

4. **Knowledge Graph Construction**: 
   - The extracted entities and relations are transformed into RDF triples and loaded into an RDF graph.
   
5. **Web Scraping**: 
   - We fetch and process web content from specific websites (such as BBC) to enrich the knowledge graph with relevant data.

**Tools & Libraries Used**: 
- Python (for programming)
- spaCy (for NLP tasks)
- BeautifulSoup, NLTK (for text preprocessing)
- rdflib (for knowledge graph creation)
- SPARQLWrapper (for querying external RDF data sources)

---

### **Part 2: Knowledge Graph Embedding**

In **Part 2**, we apply graph embedding techniques to represent the knowledge graph in a continuous vector space. The goal is to capture the relationships between entities and evaluate how well the graph embeddings capture these relationships.

1. **Graph Embedding Models**: 
   - We use PyKEEN to apply embedding models such as **TransE** and **DistMult** to learn low-dimensional representations of the entities and relations in the graph.
   
2. **Data Augmentation**: 
   - We explore the impact of enriching the graph with external data from DBpedia, adding new entities and relationships to the graph, and observing how this affects the performance of the embedding models.

3. **Evaluation**: 
   - The models are evaluated using metrics such as **Mean Rank**, **MRR (Mean Reciprocal Rank)**, and **Hits@10**. We compare the performance of the embedding models before and after data augmentation.

4. **Visualization**: 
   - Using t-SNE and other visualization techniques, we create 2D representations of the graph embeddings to explore the structure of the graph and identify clusters of semantically related entities.

**Tools & Libraries Used**: 
- PyKEEN (for graph embeddings)
- sklearn (for metrics and t-SNE visualization)
- Matplotlib, Plotly (for visualizations)
- SPARQLWrapper (for querying external data sources like DBpedia)
- NumPy, Pandas (for data manipulation)

---

## Key Findings & Results

- **Part 1**: After web scraping and knowledge base construction, we successfully built a knowledge graph with entities and relationships extracted from BBC articles. The graph was enriched with external data from DBpedia, adding valuable context to the entities.

- **Part 2**: After applying graph embedding models, we observed that **TransE** outperformed **DistMult** in terms of Mean Rank and Hits@10 metrics. However, the introduction of data augmentation through DBpedia resulted in a performance drop for both models. The increase in noise and ambiguity in the enriched graph negatively impacted the results.

---

## Project Setup

To run the project, you need to install the required dependencies. You can use the following commands to install them:

```bash
pip install pykeen torch
pip install matplotlib scikit-learn
pip install plotly
pip install SPARQLWrapper
```

### **Usage**

1. **Part 1**:  
   - Run the web scraping script to collect data from the BBC website.
   - Process and clean the text data.
   - Perform Named Entity Recognition (NER) and Relation Extraction (RE).
   - Build the RDF graph using the extracted entities and relationships.
   - Enrich the graph with external data from DBpedia via SPARQL queries.

2. **Part 2**:  
   - Use the PyKEEN pipeline to apply graph embedding models (TransE and DistMult).
   - Perform data augmentation with external DBpedia data.
   - Evaluate the performance of the models using standard metrics (Mean Rank, MRR, Hits@10).
   - Visualize the embeddings using t-SNE and other techniques.

---

## Conclusion

This project demonstrates the process of building and embedding a knowledge graph. By combining web scraping, NLP techniques, and external data enrichment, we were able to construct a graph that represents real-world entities and their relationships. Despite some challenges with data augmentation, the project provides a solid foundation for exploring graph embeddings and their applications in NLP and data science.