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

## Topic models:
Two methods of topic modeling are as follows:
- GSDMM
  - Assuming **only one topic per document**, it is Similar to LDA, and is specifically aimed at detecting topics in smaller documents
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
## Datasets:
- MSRP The Microsoft Research Paraphrase dataset (MSRP):
    - news websites sentences
    - Label 1 : same context, 0 : O.W.
- The SemEval CQA dataset :
    - An initial post as well as 10 possibly relevant posts
    - ranking
- The Quora duplicate questions dataset
    - two questions
    - label 1 : If paraphrases, 0 : O.W.

## tBert Architecture:
![image](https://user-images.githubusercontent.com/19387425/190730771-5d9cc45d-4203-414e-9429-57138f2a74b2.png)
The Bert part has:
- Input: Tokenized and combined two sentences
- Output: only CLS part
![image](https://user-images.githubusercontent.com/19387425/190730882-e49d162c-9a86-4ccc-93d3-be32d2e83ff2.png)
The topic model part has:
- Input: Tokenized sentence 1 and sentence 2
- Two methods for topic modeling:
    - document and word topics
- Uses LDA and GSDMM Topic modeling methods
![image](https://user-images.githubusercontent.com/19387425/190731090-27142cf8-e29c-44f2-843a-313e32a3985d.png)

The top layer combins topic vectors and C vector and Passes from two layer of MLP and Softmax.
![image](https://user-images.githubusercontent.com/19387425/190732970-401f4d2d-7304-42cc-b7a4-c3c206c304b8.png)

## Results:
The following figure compares our results with that of the paper.
![image](https://user-images.githubusercontent.com/19387425/190735021-0aa5f387-5ed9-4a92-b9aa-722f5a00696d.png)
