# Named-Entity-Recognition
A DL model to predict named entity recognition using BLSTM and GloVe word embeddings using PyTorch. Two models have been trained using the CoNLL-2003 corpus. The difficulty in correctly predicting the NER tag comes from encountering unknown words. If a word in not in the corpus, the model cannot be expected to correctly classify the NER tag for that word. However, strategies in handling unknown words can be utilized to lessen the severity of this issue. For example, adding <code>\<UNK\></code> tags, and other variants such as <code>\<UNK-UPPERCASE\></code> and <code>\<UNK-NUMBER\></code>, assists the model in learning how to handle unknown words.

## First Model: BLSTM with random embeddings
This model was a typical one-layer bidirectional LSTM with dropout. However, the embeddings used were randomly intialized. The model architecture is shown below:

<p align="center">
  Embedding (100-dim) > BLSTM (size 256) > Linear (size 512) > ELU > Linear (size 10)
</p>

## Second Model: BLSTM with GloVe embeddings
This model is similar to the previous model. However, the embedding layer is replaced with a pretrained GloVe embedding layer. Moreover, character-level and spelling-level features on the words were concatenated to the embedding layer, yielding a richer word representation. This improvement can be clearly seen by the F1 score jump between this model and the previous (81 to 94). The model architecture is shown below:

<p align="center">
  GloVe Embedding + Character-Embedding (120-dim) > BLSTM (size 256) > Linear (size 512) > ELU > Linear (size 10)
</p>

## Results
| Model | Accuracy | F1 score |
| ----- | -------- | -------- |
| BLSTM + Random Embeddings | 96% | 81 |
| BLSTM + GloVe + Character-Level Embedding | 99% | 94 |
