# GRAFT
## GRAFT: A Graph-aware Fusion Transformer for Cancer Driver Gene Prediction

GRAFT (Graph-Aware Fusion Transformer) is a deep learning framework for cancer driver gene prediction that integrates multi-omics data and multiple biological networks.

### 🔹 Key Features
Multi-view Graph Encoding: Learns network-specific embeddings from
Protein–Protein Interaction Network (PPI)
Gene Semantic Similarity Network (GO)
Pathway Co-occurrence Network (KEGG)
using separate Graph Convolutional Networks (GCNs), then fuses them via attention.


Functional Embedding Module: Generates functional annotations by learning the importance of curated gene sets from biological pathways and ontologies.


Graph Structural Encoding: Captures global importance (PageRank) and local neighborhood context (Random Walk Positional Encoding) within the PPI network.


Graph-aware Transformer: Combines all features and incorporates an edge-attention bias in a Transformer encoder to model both local and global dependencies.


### 📊 Model Framework
<img width="5589" height="2715" alt="model_framework_figure2" src="https://github.com/user-attachments/assets/5daa1c4b-9fa1-4f3c-90fa-dd1999ce98b7" />


1) Multi-omics features are derived from gene expression, somatic mutation, and DNA methylation data, forming a 48-dimensional vector per gene.


2) Three biological networks—PPI, gene semantic similarity, and pathway co-occurrence—are constructed from STRING/CPDB, GO, and KEGG, respectively.


3) Four main modules:
(A) Multi-view graph encoding
(B) Functional embedding
(C) Graph structural encoding
(D) Graph-aware Transformer for prediction


### 📌 Summary
GRAFT effectively integrates heterogeneous biological data and explicitly incorporates graph topology into the Transformer attention mechanism, achieving state-of-the-art performance in cancer driver gene prediction across multiple cancer types. Functional enrichment analysis of novel predictions further demonstrates its biological validity.


## 🚀 Implementation


To run GRAFT, specify:


PPI network source:
- STRING (STRING v11)
- CPDB (ConsensusPathDB)


Cancer type:
- pan-cancer
- or a specific cancer type code (e.g., KIRC, BRCA, LUAD)


#### Example Usage
```
# Run GRAFT using STRING network for pan-cancer prediction
python run_model.py STRING pan-cancer

# Run GRAFT using CPDB network for KIRC cancer type
python run_model.py CPDB KIRC
```

The script will:
Load the selected PPI network and preprocess it.
Integrate multi-omics features and auxiliary biological networks.
Train and evaluate the GRAFT model for the specified cancer type.
Output performance metrics and prediction scores.



