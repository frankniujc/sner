# sner
The Python interface to the Stanford NER Server.

[![PyPI version](https://badge.fury.io/py/sner.svg)](https://badge.fury.io/py/sner)
[![PyPI](https://img.shields.io/pypi/pyversions/sner.svg)](https://badge.fury.io/py/sner)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/caihaoyu/sner/master/LICENSE)

# Stanford NER Project

* [Home Page](https://nlp.stanford.edu/software/CRF-NER.shtml)

* [Ner Server](https://nlp.stanford.edu/software/crf-faq.shtml#cc)

# Installation
```bash
pip install sner
```
or

```bash
python setup install
```

# Start

run these commands to start java server

```bash
cd your_stanford_ner_dir
java -Djava.ext.dirs=./lib -cp stanford-ner.jar edu.stanford.nlp.ie.NERServer -port 9199 -loadClassifier ./classifiers/english.all.3class.distsim.crf.ser.gz
```
Then the sner can worked like this

```python
from sner import Ner

test_string = "Alice went to the Museum of Natural History."
tagger = Ner(host='localhost',port=9199)
print(tagger.get_entities(test_string))
```
result is

```python
[('Alice', 'PERSON'),
 ('went', 'O'),
 ('to', 'O'),
 ('the', 'O'),
 ('Museum', 'ORGANIZATION'),
 ('of', 'ORGANIZATION'),
 ('Natural', 'ORGANIZATION'),
 ('History', 'ORGANIZATION'),
 ('.', 'O')]

```
