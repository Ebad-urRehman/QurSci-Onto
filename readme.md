# QurSci-Onto: Resources for Computational Scientific Exegesis (Tafsir Ilmi)

This repository contains the supplementary resources for research on process-aware ontology and dataset for Scientific Exegesis (Tafsir Ilmi).

## 📁 Repository Structure
```bash
├── .gitignore                     # Git ignore rules
├── readme.md                      # This file
├── requirements.txt               # Python dependencies
├── data/                          # Core datasets
│   ├── ayah_ontology.csv         # Annotated Quranic verses (194 records)
│   ├── exegesis_rows.csv         # Tafsir exegesis records
│   └── scientific_ontology.csv   # Scientific nodes and relations (74 nodes)
└── evaluation/                    # Evaluation scripts
    ├── ir_evaluation_kg.py        # KG-enhanced IR evaluation
    ├── SETUP_SUMMARY.md           # Setup guide for running evaluation
    └── results/                   # Output directory (generated after running)
        ├── ir_evaluation_summary.csv
        ├── ir_evaluation_category_summary.csv
        └── ir_evaluation_results.json
```


## 📊 Dataset Overview

### 1. Ayah Ontology (`ayah_ontology.csv`)
**Size:** 194 annotated Quranic verses  
**Contents:**
- Verse citations (Surah:Ayah) in Uthmani script
- English translations
- Scientific domains (Biological, Cosmological, Geological)
- Scientific topics (Embryology, Water Cycle, etc.)
- Thematic contexts (Eschatology, History, etc.)
- Links to Tafsir sources and scientific ontology nodes

### 2. Exegesis Data (`exegesis_rows.csv`)
**Contents:** Exegetical records  
**Features:**
- Citations and references
- Arabic and English summaries of scientific topics
- Cross-references to Quranic verses

### 3. Scientific Ontology (`scientific_ontology.csv`)
**Size:** 74 scientific nodes across 8 topics  
**Structure:**
- Hierarchical decomposition of scientific phenomena
- Process vs. Entity categorization
- Sequential ordering (hasLogicalOrder)
- Causal relationships (transforms_into, causes, analogy_to, etc.)
- Quranic terminology with modern scientific interpretations

## 🔬 Evaluation Resources

### Running the Evaluation
The `evaluation/` directory contains scripts to reproduce the retrieval experiments:

```bash
# Install dependencies
pip install -r requirements.txt

# Set your OpenAI API key
export OPENAI_API_KEY='your-key-here'

# Run evaluation
cd evaluation
python ir_evaluation_kg.py
```

Key Features:
- Baseline (keyword-only) vs. Enhanced (ontology-guided) retrieval
- Implementation of P@k, R@k, NDCG@k, MRR metrics
- FAISS-based vector search with text-embedding-3-small
- Semantic enrichment through ontology grounding

### 📋 Data Schema

#### Ayah Ontology Schema

| Column | Type | Description |
|--------|------|-------------|
| surah_ayah | String | Quranic verse reference (e.g., "23:14") |
| hasText | String | Arabic text in Uthmani script |
| hasTranslation | String | English translation |
| hasBroadCategories | List | Scientific domains (Biological, Cosmological, etc.) |
| hasScientificTopics | List | Specific scientific phenomena |
| hasThemes | List | Contextual themes |
| hasScientificConceptID | String | Foreign key to scientific process |
| hasScientificNodes | List | Foreign keys to granular scientific nodes |
| hasTafsirID | String | Foreign key to Tafsir index |

#### Scientific Ontology Schema

| Column | Type | Description |
|--------|------|-------------|
| hasTopicID | String | Scientific topic identifier (e.g., "TOPIC_EMBRYO") |
| hasNodeID | String | Atomic node identifier (e.g., "NODE_EMBRYO_01") |
| hasType | String | "Process" (sequential) or "Entity" (static) |
| hasQuranicTermArabic | String | Original Quranic terminology |
| hasScientificKeywords | String | Modern scientific interpretation |
| hasLogicalOrder | Integer | Sequential position in process |
| hasRelation | String | Causal relationship type |
| hasParentNode | String | Reference to parent node |

### 🔒 Ethical & Usage Guidelines

#### Copyright Notice

#### Copyright Notice

The dataset contains:

- Quranic text: In the public domain
- Translations: Used under fair use for academic research
- Tafsir summaries: Expert-derived abstracts with page citations
- Scientific annotations: Original scholarly work

Important: The original Tafsir books are copyrighted. This dataset provides only page-referenced summaries, not full text.

#### Intended Use

- Academic research in Quranic NLP
- Computational analysis of scientific exegesis
- Development of retrieval-augmented generation systems
- Comparative studies of religious and scientific discourse

#### Restrictions

- Not for commercial use
- Not for theological debate or fatwa issuance
- Requires attribution in publications
- Subject to CC-BY-NC 4.0 license terms

### 📈 Statistics Summary

| Metric | Count |
|--------|-------|
| Total annotated verses | 194 |
| Tafsir exegesis records | 260 |
| Scientific ontology nodes | 74 |
| Major scientific topics | 8 |
| Verses mapped to topics | 36 |
| Verses with node-level mapping | 24 |
| Evaluation queries | 24 |

### 📝 Citation

If you use this resource, please cite our paper (bibtex will be added upon acceptance).

### 🤝 Contributing & Feedback

For questions, issues, or contributions, please use the repository's issue tracker or contact methods provided below.


### ❓ Questions Answers for Clarity

Q: Why only 36 out of 194 verses have scientific topic mappings?
A: Our annotation follows a phased approach: all 194 verses are linked to Tafsir, 36 are mapped to specific scientific topics, and 24 have granular node-level annotations. This reflects the progressive depth of annotation.

Q: Can I get the full Tafsir texts?
A: No, due to copyright restrictions. We provide precise page citations for verification in the original published volumes.

Q: How were the scientific nodes validated?
A: Through a two-stage process: (1) extraction from Tafsir using LLMs with strict provenance tracking, (2) validation by domain experts from Islamic studies faculties.

Q: What embedding model was used?
A: OpenAI's text-embedding-3-small (as specified in config.yaml). All experiments are reproducible with this model.



**If you use this resource in your research, please cite our paper:**



## License
This dataset and ontology are licensed under the **Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)**. 

You are free to:
- **Share** — copy and redistribute the material in any medium or format.
- **Adapt** — remix, transform, and build upon the material.

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made.
- **Non-Commercial** — You may not use the material for commercial purposes.

View the full license: [https://creativecommons.org/licenses/by-nc/4.0/](https://creativecommons.org/licenses/by-nc/4.0/)