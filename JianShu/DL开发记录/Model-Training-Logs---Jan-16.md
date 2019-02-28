LSTM with trained word2vec - Jan 16
```
[cyang@bej-song smt-deeplearning]$ python3 train_model_lstm.py
Using TensorFlow backend.
Loading data...
Loading train  22
Loading test  23
Shape of data set before padding (45,)  data length [8097, 8320, 13400, 8473, 7889, 5196, 7875, 4782                     , 8042, 2363, 4273, 9451, 9514, 9211, 8486, 3716, 7996, 2107, 12033, 15555, 3003, 4159, 7534, 8255,                      2026, 2976, 1979, 4660, 4244, 4413, 3851, 4070, 2967, 5203, 8271, 4538, 3102, 2044, 3912, 4861, 8064                     , 2067, 18359, 5097, 2026]
Shape of data set after padding [(8097, 25), (8320, 25), (13400, 25), (8473, 25), (7889, 25), (5196,                      25), (7875, 25), (4782, 25), (8042, 25), (2363, 25), (4273, 25), (9451, 25), (9514, 25), (9211, 25)                     , (8486, 25), (3716, 25), (7996, 25), (2107, 25), (12033, 25), (15555, 25), (3003, 25), (4159, 25),                      (7534, 25), (8255, 25), (2026, 25), (2976, 25), (1979, 25), (4660, 25), (4244, 25), (4413, 25), (385                     1, 25), (4070, 25), (2967, 25), (5203, 25), (8271, 25), (4538, 25), (3102, 25), (2044, 25), (3912, 2                     5), (4861, 25), (8064, 25), (2067, 25), (18359, 25), (5097, 25), (2026, 25)]  data length [8097, 832                     0, 13400, 8473, 7889, 5196, 7875, 4782, 8042, 2363, 4273, 9451, 9514, 9211, 8486, 3716, 7996, 2107,                      12033, 15555, 3003, 4159, 7534, 8255, 2026, 2976, 1979, 4660, 4244, 4413, 3851, 4070, 2967, 5203, 82                     71, 4538, 3102, 2044, 3912, 4861, 8064, 2067, 18359, 5097, 2026]
Shape of Labels Matrix (45, 10)  data length [10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10                     , 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10                     , 10, 10, 10, 10, 10, 10]
num_sample =  45
maxlen =  25
maxstep =  4000
num_words =  5312
Shape of dataset after reshape (45, 4000, 25)
start_char =  None
oov_char =  2
22 train sequences
23 test sequences
Number of features -  100000
Number of Labels -  10
Number of Word -  5312
Found 23724 word vectors.
Found 5208 of 5312 in word dict
Embedding matrix -  (5312, 100)
2019-01-17 17:32:55.197680: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports i                     nstructions that this TensorFlow binary was not compiled to use: AVX2 FMA
_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
embedding_1 (Embedding)      (None, 100000, 100)       531200
_________________________________________________________________
lstm_1 (LSTM)                (None, 100)               80400
_________________________________________________________________
dense_1 (Dense)              (None, 10)                1010
=================================================================
Total params: 612,610
Trainable params: 612,610
Non-trainable params: 0
_________________________________________________________________
None
Train on 31 samples, validate on 14 samples
Epoch 1/10
31/31 [==============================] - 97s 3s/step - loss: 2.2595 - acc: 0.1935 - val_loss: 1.6882                      - val_acc: 0.5000
Epoch 2/10
31/31 [==============================] - 93s 3s/step - loss: 1.7055 - acc: 0.6129 - val_loss: 1.6135                      - val_acc: 0.4286
Epoch 3/10
31/31 [==============================] - 93s 3s/step - loss: 1.3889 - acc: 0.8065 - val_loss: 1.5774                      - val_acc: 0.5000
Epoch 4/10
31/31 [==============================] - 93s 3s/step - loss: 1.1508 - acc: 0.8387 - val_loss: 1.5771 - val_acc: 0.5000
Epoch 5/10
31/31 [==============================] - 94s 3s/step - loss: 0.9651 - acc: 0.8710 - val_loss: 1.5887 - val_acc: 0.4286
Epoch 6/10
31/31 [==============================] - 94s 3s/step - loss: 0.8192 - acc: 0.8710 - val_loss: 1.6200 - val_acc: 0.4286
Epoch 7/10
31/31 [==============================] - 92s 3s/step - loss: 0.7044 - acc: 0.8710 - val_loss: 1.6489 - val_acc: 0.4286
Epoch 8/10
31/31 [==============================] - 92s 3s/step - loss: 0.6139 - acc: 0.8710 - val_loss: 1.7035 - val_acc: 0.4286
Epoch 9/10
31/31 [==============================] - 91s 3s/step - loss: 0.5431 - acc: 0.8710 - val_loss: 1.7072 - val_acc: 0.5000
Epoch 10/10
31/31 [==============================] - 92s 3s/step - loss: 0.4886 - acc: 0.9032 - val_loss: 1.8228 - val_acc: 0.4286
[cyang@bej-song smt-deeplearning]$
```
Conv1D & LSTM with trained word2vec - Jan 16
```
[cyang@bej-song smt-deeplearning]$ python3 train_model_lstm.py
Using TensorFlow backend.
Loading data...
Loading train  22
Loading test  23
Shape of data set before padding (45,)  data length [8097, 8320, 13400, 8473, 7889, 5196, 7875, 4782, 8042, 2363, 4273, 9451, 9514, 9211, 8486, 3716, 7996, 2107, 12033, 15555, 3003, 4159, 7534, 8255, 2026, 2976, 1979, 4660, 4244, 4413, 3851, 4070, 2967, 5203, 8271, 4538, 3102, 2044, 3912, 4861, 8064, 2067, 18359, 5097, 2026]
Shape of data set after padding [(8097, 25), (8320, 25), (13400, 25), (8473, 25), (7889, 25), (5196, 25), (7875, 25), (4782, 25), (8042, 25), (2363, 25), (4273, 25), (9451, 25), (9514, 25), (9211, 25), (8486, 25), (3716, 25), (7996, 25), (2107, 25), (12033, 25), (15555, 25), (3003, 25), (4159, 25), (7534, 25), (8255, 25), (2026, 25), (2976, 25), (1979, 25), (4660, 25), (4244, 25), (4413, 25), (3851, 25), (4070, 25), (2967, 25), (5203, 25), (8271, 25), (4538, 25), (3102, 25), (2044, 25), (3912, 25), (4861, 25), (8064, 25), (2067, 25), (18359, 25), (5097, 25), (2026, 25)]  data length [8097, 8320, 13400, 8473, 7889, 5196, 7875, 4782, 8042, 2363, 4273, 9451, 9514, 9211, 8486, 3716, 7996, 2107, 12033, 15555, 3003, 4159, 7534, 8255, 2026, 2976, 1979, 4660, 4244, 4413, 3851, 4070, 2967, 5203, 8271, 4538, 3102, 2044, 3912, 4861, 8064, 2067, 18359, 5097, 2026]
Shape of Labels Matrix (45, 10)  data length [10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10]
num_sample =  45
maxlen =  25
maxstep =  4000
num_words =  5312
Shape of dataset after reshape (45, 4000, 25)
start_char =  None
oov_char =  2
22 train sequences
23 test sequences
Number of features -  100000
Number of Labels -  10
Number of Word -  5312
Found 23724 word vectors.
Found 5208 of 5312 in word dict
Embedding matrix -  (5312, 100)
2019-01-17 17:51:30.526812: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA
_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
embedding_1 (Embedding)      (None, 100000, 100)       531200
_________________________________________________________________
conv1d_1 (Conv1D)            (None, 4000, 100)         250100
_________________________________________________________________
lstm_1 (LSTM)                (None, 100)               80400
_________________________________________________________________
dense_1 (Dense)              (None, 10)                1010
=================================================================
Total params: 862,710
Trainable params: 862,710
Non-trainable params: 0
_________________________________________________________________
None
Train on 31 samples, validate on 14 samples
Epoch 1/10
31/31 [==============================] - 6s 190ms/step - loss: 2.3340 - acc: 0.1290 - val_loss: 1.6172 - val_acc: 0.0714
Epoch 2/10
31/31 [==============================] - 6s 193ms/step - loss: 1.6487 - acc: 0.5484 - val_loss: 1.8559 - val_acc: 0.2857
Epoch 3/10
31/31 [==============================] - 5s 171ms/step - loss: 1.3445 - acc: 0.5806 - val_loss: 1.9479 - val_acc: 0.0000e+00
Epoch 4/10
31/31 [==============================] - 5s 158ms/step - loss: 1.3836 - acc: 0.4839 - val_loss: 1.5358 - val_acc: 0.4286
Epoch 5/10
31/31 [==============================] - 5s 167ms/step - loss: 1.1370 - acc: 0.7097 - val_loss: 1.7416 - val_acc: 0.2857
Epoch 6/10
31/31 [==============================] - 5s 170ms/step - loss: 0.8560 - acc: 0.7097 - val_loss: 1.7194 - val_acc: 0.4286
Epoch 7/10
31/31 [==============================] - 5s 169ms/step - loss: 0.8596 - acc: 0.8065 - val_loss: 1.9075 - val_acc: 0.2857
Epoch 8/10
31/31 [==============================] - 5s 165ms/step - loss: 0.7522 - acc: 0.7742 - val_loss: 1.9631 - val_acc: 0.3571
Epoch 9/10
31/31 [==============================] - 5s 161ms/step - loss: 0.6625 - acc: 0.8710 - val_loss: 1.8800 - val_acc: 0.2857
Epoch 10/10
31/31 [==============================] - 5s 163ms/step - loss: 0.5867 - acc: 0.8065 - val_loss: 1.8342 - val_acc: 0.3571
[cyang@bej-song smt-deeplearning]$
```
Conv1D & LSTM with pre-trained doc2vec word vecs - Jan 23
```
D:\Dev\gitlab\smt-deeplearning>python3 train_model_lstm.py
Using TensorFlow backend.
Loading data...
Loading train  22
Loading test  23
Shape of data set before padding (45,)  data length [8097, 8320, 13400, 8473, 7889, 5196, 7875, 4782, 8042, 2363, 4273, 9451, 9514, 9211, 8486, 3716, 7996, 2107, 12033, 15555, 3003, 4159, 7534, 8255, 2026, 2976, 1979, 4660, 4244, 4413, 3851, 4070, 2967, 5203, 8271, 4538, 3102, 2044, 3912, 4861, 8064, 2067, 18359, 5097, 2026]
Shape of data set after padding [(8097, 25), (8320, 25), (13400, 25), (8473, 25), (7889, 25), (5196, 25), (7875, 25), (4782, 25), (8042, 25), (2363, 25), (4273, 25), (9451, 25), (9514, 25), (9211, 25), (8486, 25), (3716, 25), (7996, 25), (2107, 25), (12033, 25), (15555, 25), (3003, 25), (4159, 25), (7534, 25), (8255, 25), (2026, 25), (2976, 25), (1979, 25), (4660, 25), (4244, 25), (4413, 25), (3851, 25), (4070, 25), (2967, 25), (5203, 25), (8271, 25), (4538, 25), (3102, 25), (2044, 25), (3912, 25), (4861, 25), (8064, 25), (2067, 25), (18359, 25), (5097, 25), (2026, 25)]  data length [8097, 8320, 13400, 8473, 7889, 5196, 7875, 4782, 8042, 2363, 4273, 9451, 9514, 9211, 8486, 3716, 7996, 2107, 12033, 15555, 3003, 4159, 7534, 8255, 2026, 2976, 1979, 4660, 4244, 4413, 3851, 4070, 2967, 5203, 8271, 4538, 3102, 2044, 3912, 4861, 8064, 2067, 18359, 5097, 2026]
Shape of Labels Matrix (45, 10)  data length [10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10]
num_sample =  45
maxlen =  25
maxstep =  4000
num_words =  5312
Shape of dataset after reshape (45, 4000, 25)
start_char =  None
oov_char =  2
22 train sequences
23 test sequences
Number of features -  100000
Number of Labels -  10
Number of Word -  5312
Found 24750 word vectors.
Found 5210 of 5312 in word dict
Embedding matrix -  (5312, 100)
2019-01-23 09:49:36.012404: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2
_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
embedding_1 (Embedding)      (None, 100000, 100)       531200
_________________________________________________________________
conv1d_1 (Conv1D)            (None, 4000, 100)         250100
_________________________________________________________________
lstm_1 (LSTM)                (None, 100)               80400
_________________________________________________________________
dense_1 (Dense)              (None, 10)                1010
=================================================================
Total params: 862,710
Trainable params: 862,710
Non-trainable params: 0
_________________________________________________________________
None
Train on 31 samples, validate on 14 samples
Epoch 1/10
2019-01-23 09:49:37.558740: W tensorflow/core/framework/allocator.cc:122] Allocation of 1240000000 exceeds 10% of system memory.
2019-01-23 09:49:40.516357: W tensorflow/core/framework/allocator.cc:122] Allocation of 1240000000 exceeds 10% of system memory.
31/31 [==============================] - 6s 196ms/step - loss: 2.4096 - acc: 0.0968 - val_loss: 1.8701 - val_acc: 0.2143
Epoch 2/10
2019-01-23 09:49:42.951427: W tensorflow/core/framework/allocator.cc:122] Allocation of 1240000000 exceeds 10% of system memory.
2019-01-23 09:49:45.614624: W tensorflow/core/framework/allocator.cc:122] Allocation of 1240000000 exceeds 10% of system memory.
31/31 [==============================] - 5s 163ms/step - loss: 2.1164 - acc: 0.2903 - val_loss: 1.8610 - val_acc: 0.2143
Epoch 3/10
2019-01-23 09:49:47.988562: W tensorflow/core/framework/allocator.cc:122] Allocation of 1240000000 exceeds 10% of system memory.
31/31 [==============================] - 5s 161ms/step - loss: 1.9532 - acc: 0.2581 - val_loss: 2.1804 - val_acc: 0.0000e+00
Epoch 4/10
31/31 [==============================] - 5s 167ms/step - loss: 1.7863 - acc: 0.3548 - val_loss: 1.7692 - val_acc: 0.3571
Epoch 5/10
31/31 [==============================] - 5s 160ms/step - loss: 1.7045 - acc: 0.4839 - val_loss: 1.8800 - val_acc: 0.0000e+00
Epoch 6/10
31/31 [==============================] - 5s 162ms/step - loss: 1.5472 - acc: 0.4194 - val_loss: 1.6998 - val_acc: 0.2143
Epoch 7/10
31/31 [==============================] - 5s 164ms/step - loss: 1.8960 - acc: 0.2903 - val_loss: 1.8228 - val_acc: 0.1429
Epoch 8/10
31/31 [==============================] - 5s 160ms/step - loss: 1.4885 - acc: 0.5484 - val_loss: 1.5737 - val_acc: 0.3571
Epoch 9/10
31/31 [==============================] - 5s 165ms/step - loss: 1.3357 - acc: 0.6129 - val_loss: 1.7388 - val_acc: 0.1429
Epoch 10/10
31/31 [==============================] - 5s 160ms/step - loss: 1.2687 - acc: 0.6452 - val_loss: 1.9803 - val_acc: 0.0714
```
