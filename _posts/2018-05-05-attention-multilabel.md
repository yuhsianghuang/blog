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
    - Using the final class node vector for each binary classification.
        - The classifier is shared among all classes.
- Hierarchical attention is proposed to deal with large number of classes and huge graph.
- In order to perform well on this task, two correlation structures must be captured


### Thoughts

