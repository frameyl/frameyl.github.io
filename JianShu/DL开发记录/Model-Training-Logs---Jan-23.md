LSTM with pre-trained doc2vec sentences vectors - Jan 23
  - param for doc2vec model `vector_size=100, window=3, dm=0, min_count=1, workers=4, epochs=50`
```shell
D:\Dev\gitlab\smt-deeplearning>python3 train_model_lstm.py
Using TensorFlow backend.
C:\Users\CYang\AppData\Local\Programs\Python\Python36\lib\site-packages\gensim\utils.py:1212: UserWarning: detected Windows; aliasing chunkize to chunkize_serial
  warnings.warn("detected Windows; aliasing chunkize to chunkize_serial")
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
Loading train  22
Loading test  23
Shape of data set (45,)  data length [8097, 8320, 13400, 8473, 7889, 5196, 7875, 4782, 8042, 2363, 4273, 9451, 9514, 9211, 8486, 3716, 7996, 2107, 12033, 15555, 3003, 4159, 7534, 8255, 2026, 2976, 1979, 4660, 4244, 4413, 3851, 4070, 2967, 5203, 8271, 4538, 3102, 2044, 3912, 4861, 8064, 2067, 18359, 5097, 2026]
Shape of processed data set 45  data length [4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000]
Loaded tokenizer with 5312 tokens
Shape of raw data set 45  data length [4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000]
num_sample =  45
maxlen =  25
maxstep =  4000
Get Vectors for training data, length =  22
Get Vectors for testing data, length =  23

Shape of input -  (45, 4000, 100)
Train on 31 samples, validate on 14 samples
2019-01-23 22:23:00.518199: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2
Epoch 1/10
31/31 [==============================] - 2s 78ms/step - loss: 2.2412 - acc: 0.1290 - val_loss: 2.2591 - val_acc: 0.0000e+00
Epoch 2/10
31/31 [==============================] - 2s 64ms/step - loss: 2.0534 - acc: 0.2581 - val_loss: 2.3965 - val_acc: 0.0000e+00
Epoch 3/10
31/31 [==============================] - 2s 65ms/step - loss: 1.9351 - acc: 0.2581 - val_loss: 2.5779 - val_acc: 0.0000e+00
Epoch 4/10
31/31 [==============================] - 2s 64ms/step - loss: 1.8656 - acc: 0.2903 - val_loss: 2.7408 - val_acc: 0.3571
Epoch 5/10
31/31 [==============================] - 2s 64ms/step - loss: 1.8191 - acc: 0.3871 - val_loss: 2.7464 - val_acc: 0.3571
Epoch 6/10
31/31 [==============================] - 2s 66ms/step - loss: 1.8201 - acc: 0.3548 - val_loss: 2.8829 - val_acc: 0.3571
Epoch 7/10
31/31 [==============================] - 2s 71ms/step - loss: 1.7900 - acc: 0.4516 - val_loss: 2.8553 - val_acc: 0.4286
Epoch 8/10
31/31 [==============================] - 2s 70ms/step - loss: 1.7457 - acc: 0.3548 - val_loss: 3.0203 - val_acc: 0.3571
Epoch 9/10
31/31 [==============================] - 2s 70ms/step - loss: 1.7072 - acc: 0.4516 - val_loss: 2.9344 - val_acc: 0.3571
Epoch 10/10
31/31 [==============================] - 2s 72ms/step - loss: 1.6797 - acc: 0.4516 - val_loss: 2.9974 - val_acc: 0.3571
```
