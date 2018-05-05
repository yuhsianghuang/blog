---
layout: post
title: Attentional Multilabel Learning over Graphs
---

#### Paper link: [Attentional Multilabel Learning over Graphs: A Message Passing Approach](https://arxiv.org/abs/1804.00293).
### TLDR
[To be filled.]

### Key Points
- It is very common to test a drug on multiple diseases.
- Treat classes as nodes (termed as **label node**) and include them in to the message passing framework.
    - Four kinds of Message Passing:
        - input-input
        - input-label
        - label-input
        - label-label
    - Therefore, classes also have an associated embedding.
    - Class nodes are connected to all the graph nodes.
    - To learn the label-label and label-substructure relationship.
    - Attention pooling is applied on the messages between class nodes and the input nodes.
        - input to class attention and class to input attention.
        - Average pooling is applied on the messages bewteen input nodes.
        - Two labels can indirectly interact with each other after two step of updates.
        - The initial hidden vector of a class node is the same among different instances (Simply an embedding lookup).
            - Class node actually works a pseudo node to short the distance between inputs nodes to facilitate the message exchange process.
                - Correlate with a class by using the class node vector for classification.
                    - Good for to have insight on the difference between classes.
                    - Alleviate the information compression into a single graph vector.
                    - Also provide a class correlated encoded vector.

    - Using the final class node vector for each binary classification.
        - The classifier is shared among all classes.
- Hierarchical attention is proposed to deal with large number of classes and huge graph.
    - K (K ≪ min{|V|, C}) intermediate attentional factors are introduced.
- In order to perform well on this task, two correlation structures must be captured
- Experiments:
    - Datasets:
        - 9cancers:
            - Drug activity against nine types of cancer.
            - Binary indicating whether there is a response, i.e., the drug reduces or prevents tumor growth.
            - Collect from 9 different datasets in PubChem.
            - 22 thousand molecules in total.
            - 3,356 molecules active for at least one type of cancer. 
            - Formed with **all** the active molecules and 10,000 fully inactive molecules.

        - 50proteins:
            - Drug-protein binding prediction.
            - Proteins are labels.
            - Top 50 proteins that are bound by most ligands are selected.
            - 36,349 ligands in total 
                - The average number of proteins to which one ligand binds is 1.35.

    - train/valid/test = 0.6/0.2/0.2
    - Assay ID in 9cancer dataset:

        |Assay ID |Cancer Type |Positive Percentage|
        | ------------- |:-------------:| -----:|
        |1 |Lung |12.28|
        |33 |Melanoma |9.97|
        |41 |Prostate |11.77|
        |47 |Central Nervous System |12.22|
        |81 |Colon |14.50|
        |83 |Breast |16.22|
        |109 |Ovarian |12.76|
        |123 |Leukemia |18.91|
        |145 |Renal |12.03|

    - When the number of propagation layer larger than 6, the improvement rate becomes steady and the model is more likely to overfit.
        - 2 Hypothesis from author:
            - (i) the structure information from distant nodes is much less important than that from close neighbors;
            - (ii) the structure information at every node becomes more global and indistinguishable, causing difficulty for the model to detect meaningful substructures during prediction.
        - Since there are label nodes for shorting the distance, there is no need to propagate for too many times.

### Thoughts
- The label node design is intuitive and helps easing the message passing and alleviate the compression.

