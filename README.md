# Tensorflow Speech Recognition
Speech recognition using google's [tensorflow](https://github.com/tensorflow/tensorflow/) deep learning framework, [sequence-to-sequence](https://www.tensorflow.org/versions/master/tutorials/seq2seq/index.html) neural networks.

Replaces [caffe-speech-recognition](https://github.com/pannous/caffe-speech-recognition), see there for training data.

**Extensions** to current tensorflow probably needed:

* [Sliding Window GPU implementation](https://github.com/tensorflow/tensorflow/issues/211)
* Continuous seq2seq adaptation
* Modular graphs/models + persistance
* Incremental collaborative snapshots

**Ultimate goal:**
Create a decent standalone speech recognition for Linux etc.
Some people say we have the models but not enough training data.
We disagree: There is plenty of training data (100GB [here](http://www.openslr.org/12), on Gutenberg, synthetic Text to Speech snippets, Movies with transcripts, YouTube with captions etc etc) we just need a simple yet powerful model. It's only a question of time...


Update: Nervana [showed](https://www.youtube.com/watch?v=NaqZkV_fBIM) that it is possible for 'independents' to build models that are state of the art. Unfortunately they didn't open source the software.
[Sphinx starts using tensorflow LSTMs](http://cmusphinx.sourceforge.net/).

**Collaborators wanted!** We are in the process of tackling this project in seriousness. Make a pull request if you want to join the party, no matter your background.

We are still in the **planning phase**! See [train.py](https://github.com/pannous/tensorflow-speech-recognition/blob/master/train.py) for the suggested general architecture. You can contribute right away by discussing or implementing one of the (easy) train_... methods.

** Getting started **
`./train.sh`
`./record.py`

**Fun tasks for newcomers**
* Data Augmentation :  create on-the-fly modulation for our data: increase the speech frequency, add background noise, alter the pitch etc,...
* Create a matrix auto encoder:  the current autoencoder takes a vector as input. each of the easy to add one dimension to autoencode spectrograph files preserving the axis information.
* Modular persistance: It is important that we have a mechanism to persist and load subsets of the whole model, and to make it extensible on demand. So far the Graph.load and Saver.load mechanisms are insufficient for that. Todo: use keras graph for that?
