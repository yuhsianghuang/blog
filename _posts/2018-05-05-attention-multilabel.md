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

    - Using the final class node vector for each binary classification.
        - The classifier is shared among all classes.
- Hierarchical attention is proposed to deal with large number of classes and huge graph.
    - K (K ≪ min{|V|, C}) intermediate attentional factors are introduced.
- In order to perform well on this task, two correlation structures must be captured


### Thoughts
- The label node design is intuitive and helps easing the message passing and alleviate the compression.

