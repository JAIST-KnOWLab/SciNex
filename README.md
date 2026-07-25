# SciNex: Train-Test Ontology and Knowledge Graphs
 
This release contains the knowledge graphs and refined ontology used in the paper
**"SciNex: Scientific Literature Ontology Construction Using Iterative Schema-Guided Extraction"**
(ISWC 2026 Companion Volume, Bari, Italy).
 
Due to file size, the data is distributed as two zip archives:
 
| Archive | Contents | Period | Role |
|---|---|---|---|
| `scinex_train.zip` | Training knowledge graph + ontology | 2019–2023 | Used to refine the ontology and train KG embedding models |
| `scinex_test.zip` | Test knowledge graph | 2024 | Held out for inductive temporal citation prediction |
 
## Temporal Split
 
The corpus consists of 1,001 ACL Anthology papers, collected by snowball
sampling from the most-cited ACL Anthology paper published in 2019. Papers are
split chronologically by publication year to prevent temporal leakage:
 
- **Train (2019–2023):** 902 papers, 10,629 citation edges. The ontology (T-Box)
  is refined exclusively on this split, and all KG embeddings are trained on it.
- **Test (2024):** 99 papers, 1,570 citation edges. These edges are the gold
  prediction targets. All citation edges from training papers to 2024 papers are
  removed from the training graph. Test papers connect to the graph only through
  `mentions` edges to their extracted entities; graph embeddings remain frozen
  at inference time (inductive setting).
