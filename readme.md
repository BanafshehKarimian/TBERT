# tBERT

In this project we implement TBERT: Topic models and BERT joining forces for semantic similarity detectio. 
Semantic similarity detection problem has applications ranging from question answering to plagiarism detection.
![image](https://user-images.githubusercontent.com/19387425/190729974-305d67f1-d58c-4926-b406-76d577fbd1bf.png)
The idea is adding topic information to pre trained bert
## What is BERT:
Bert has only the encoder part of the transformer and has the following features:
- Can be fine-tuned with just one additional output layer
- Applications such as question answering and language inferencet
- Adds [CLS] at beginning
- Adds [SEP] between sentences
- Position, Segment, Token embedding
- Two tasks:
  - masking some percentage of the input
  - predict if second sentence is next one


### • GSDMM

- Similar to LDA, is specifically aimed at detecting topics in smaller documents
- assumes **only one topic per document.**
- LDA
- A Bayesian unsupervised learning
- Generates topic based on word frequency
- Mixtures of topics in a document
- Starts from randomly assigning topics to each word of a document
- Counts frequency of topics in a document c(Tj,Di)
- Counts frequency of assigning each word to a topic c(wq,Tj)
- Removes a words topic from document and updates counts
- Multiplies c(Tj,Di) and c(wq,Tj) for each topic j
- Assigns topic with max{c(Tj,Di)*c(wq,Tj)} to word wq
- Repeats for all words in each pass

# Topic models:


- MSRP The Microsoft Research Paraphrase dataset (MSRP):
    - news websites sentences
    - Label 1 : same context, 0 : O.W.
- The SemEval CQA dataset :
    - An initial post as well as 10 possibly relevant posts
    - ranking
- The Quora duplicate questions dataset
    - two questions
    - label 1 : If paraphrases, 0 : O.W.

# Datasets:


# tBert Architecture:


# tBert Architecture:

- Input: Tokenized and combined two sentences
- Output: only CLS part


# tBert Architecture:

- Input: Tokenized sentence 1 and sentence 2
- Two methods for topic modeling:
    - document and word topics
- Uses LDA and GSDMM Topic modeling methods


```
T 1 ... TN
```
```
document
```
```
Probability
of topic 1
```
```
... Probability
of topic Z
```
# Document vs word topics:


```
T 1 ... TN
```
```
word
```
```
Probability
of topic 1
```
```
... Probability
of topic Z
```
```
... word
```
```
Probability
of topic 1
```
```
... Probability
of topic Z
```
..
   .

```
Mean Probability
of topic 1
```
```
... Mean Probability
of topic Z
```
# Document vs word topics:


# tBert Architecture:

- Input: combined topic vectors and C vector
- Pass from two layer MLP
- Softmax


- Topic baselines
    - calculate the JensenShannondivergence (JSD) between the topic distributions
       of the two sentences.
    - The model predicts a negative label if JSD is larger than a threshold
- Siamese BiLSTM
    - with pretrainedGloVeembeddings
- Previous systems:
    - Compared against three highest performing system of earlier work based on
       F 1 score.
- Bert
    - C vector (as in tBERT) followed by a softmaxlayer

# Baselines:


# Results:

```
Topics improve performance
```

# Results:

```
They evaluate systems based on F 1 scores
The early stopping is used during fine tuning
```

# Results:


# Our Results:

```
Document converges faster
```

# Our Results:

```
Reached 75.2 and 75.
```

# Compare:

```
Test f 1 : 90 Test f 1 : 74 Test f 1 : 79
```

