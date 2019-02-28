```python
from gensim.test.utils import common_texts, get_tmpfile
from gensim.models import Word2Vec

path = get_tmpfile("word2vec.model")

print(common_texts)
model = Word2Vec(common_texts, size=100, window=5, min_count=1, workers=4)
model.save("word2vec.model")

model = Word2Vec.load("word2vec.model")

model.build_vocab([["hello", "world"]])
model.train([["hello", "world"]], total_examples=1, epochs=1)

model.train([['chair', 'dog']], total_examples=1, total_words=2, epochs=1)

model.wv.save_word2vec_format('word2vec.txt')

vector = model.wv['world']
print(vector.shape, vector)

vector = model.wv['fuck']
print(vector.shape, vector)

from gensim.models import KeyedVectors

path = get_tmpfile("wordvectors.kv")
model.wv.save("wordvectors.kv")
```
