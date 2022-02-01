# Named-Entity-Recognition
A DL model to predict named entity recognition using BLSTM and GloVe word embeddings using PyTorch. Two models have been trained using the CoNLL-2003 corpus. The difficulty in correctly predicting the NER tag comes from encountering unknown words. If a word in not in the corpus, the model cannot be expected to correctly classify the NER tag for that word. However, strategies in handling unknown words can be utilized to lessen the severity of this issue. For example, adding <code>\<UNK\></code> tags, and other variants such as <code>\<UNK-UPPERCASE\></code> and <code>\<UNK-NUMBER\></code>, assists the model in learning how to handle unknown words.

For more details on the dataset, click [here](data/README.md).

## First Model: BLSTM with random embeddings
This model was a typical one-layer bidirectional LSTM with dropout. However, the embeddings used were randomly intialized. The model architecture is shown below:

<p align="center">
  Embedding (100-dim) > BLSTM (size 256) > Linear (size 512) > ELU > Linear (size 10)
</p>

## Second Model: BLSTM with GloVe embeddings
This model is similar to the previous model. However, the embedding layer is replaced with a pretrained GloVe embedding layer. Moreover, spelling features on the words were concatenated to the embedding layer, yielding a richer word representation. Examples of spelling features include <code>ALL_UPPER</code> (e.g. IBM), <code>ALL_LOWER</code> (e.g. cat), <code>NUMBER</code>, <code>FIRST_UPPER</code> (i.e. John), and <code>OTHERS</code>. This improvement can be clearly seen by the F1 score jump between this model and the previous (80.33 to 93.23). The model architecture is shown below:

<p align="center">
  GloVe Embedding + Spelling Embedding (120-dim) > BLSTM (size 256) > Linear (size 512) > ELU > Linear (size 10)
</p>

## Results
| Model                              | Precision | Recall | Accuracy | F1 score |
| ---------------------------------- | --------- | ------ | -------- | -------- |
| BLSTM + Random Embeddings          | 84.22%    | 76.79% | 96.03%   | 80.33    |
| BLSTM + GloVe + Spelling Embedding | 92.54%    | 93.92% | 98.83%   | 93.23    |

While these results look very promising, keep in mind that the average sentence length in English is 14 words. Thus, for the sentence, the accuracy becomes (98.83%)^14, which is approximately 85%. The current state of the art has an F1 score of 94.6. Hence there is still room for improvement in this task. One future work idea that could enhance this method is adding an additional embedding layer to capture not only the spelling features, but also the character-level features, perhaps by utilizing a CNN.