# Dataset: CoNLL 2003 (English)
The English dataset was obtained from <a href="https://paperswithcode.com/dataset/conll-2003">PapersWithCode</a> which was introduced by Sang and Meulder in their paper in 2013, <a href="https://paperswithcode.com/paper/introduction-to-the-conll-2003-shared-task">Introduction to the CoNLL-2003 Shared Task: Language-Independent Named Entity Recognition</a>. At the time of writing, the dataset consists of the following:

| English Data           | Articles | Sentences | Tokens  | LOC  | MISC | ORG  | PER  |
| ---------------------- | -------- | --------- | ------- | ---- | ---- | ---- | ---- |
| [Training set](train)  | 946      | 14,987    | 203,621 | 7140 | 3438 | 6321 | 6600 |
| [Development set](dev) | 216      | 3,466     | 51,362  | 1837 | 922  | 1341 | 1842 |
| [Test set](test)       | 231      | 3,684     | 46,435  | 1668 | 702  | 1661 | 1617 |

Moreover, the leaderboard for Named Entity Recognition (NER) with this dataset can be found <a href="https://paperswithcode.com/sota/named-entity-recognition-ner-on-conll-2003">here</a>. The state of the art currently is an F1 score of **94.6** using ACE + document-context model, which is described in more detail in their <a href="https://paperswithcode.com/paper/automated-concatenation-of-embeddings-for-1">paper</a>.