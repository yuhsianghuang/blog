---
layout: post
title: Interpretable Drug Target Prediction Using Deep Neural Representation
---

#### Paper link: [Interpretable Drug Target Prediction Using Deep Neural Representation](https://astro.temple.edu/~tua87106/ijcai_dti.pdf).
### TLDR

### Key Points
- Predict drug-target(Protein) interaction (Binary prediction)
- Protein is in a SMILES string format.
    - Encoding with RNN.
- Drug is in a graph format.
    - Encoding with Graph CNN.
- Attentive Pooling Network is applied to get the final representation of drug and target.
    - Attentive Pooling provides a two-way attention mechanism that enables the input pairs to **be aware of each other**.
    - As the readout function in MPNN framework.
    - Context:
        - Drug: Atom hidden vectors
        - Target: Hidden vectors generated from RNN.
    - A soft alignment matrix is first obtained with the following equation:
        - $$A = tanh(P^TUD)$$
    - Apply Max pooling columnwise and rowwise.
    - Apply Softmax on the resulting value as attention weight.
- Siamese Network is used to inference.
    - Dot product on two input vectors.
    - Activate with sigmoid function to normalize the value into [0, 1] range.
- Loss function: Negative Loglikelihood.
- Dataset:
    - 39,747 positive examples and 31,218 negative examples extracted from BindingDB.
- Interpretability:
    - case study of a top predicted interaction between chemical (PubChem ID: 117793281) and protein (UniProt ID: Q9HBH9)
    - by comparing this interpretation with that obtained by molecular docking, which is currently more biologically interpretable.
