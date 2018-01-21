---
layout:     post
title:      "Deep_Learning_with_Python_Keras"
subtitle:
date:       2018-01-21 11:00:00
author:     "随机漫步的傻瓜"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    -  机器学习
---
- You can think of a deep network as a multi-stage information distillation operation, where information goes through successive filters and comes out increasingly "purified" (i.e. useful with regard to some task).
- These are the two essential characteristics of how deep learning learns from data: the
incremental, layer-by-layer way in which increasingly complex representations are developed, and the fact these intermediate incremental representations are learned jointly, each layer being updated both to follow the representational needs of the layer above and the needs of the layer below. Together, these two properties have made deep learning vastly more successful than previous approaches to machine learning.
- Here our network consists of a sequence of two Dense layers, which are densely-connected (also called "fully-connected") neural layers
-  The term "stochastic" refers to the fact that each batch of data is drawn at random
-  Momentum addresses two issues with SGD: convergence speed, and local minima.
- There are two key architecture decisions to be made about such stack of dense layers:How many layers to use.How many "hidden units" to chose for each layer.
- crossentropy is usually the best choice when you are dealing with models that output probabilities. Crossentropy is a quantity from the field of Information Theory, that measures the "distance" between probability distributions, or in our case, between the ground-truth distribution and our predictions.
- Note that the call to model.fit() returns a History object. This object has a member history, which is a dictionary containing data about everything that happened during training
- Our previous loss, categorical_crossentropy, expects the labels to follow a categorical encoding. With integer labels, we should use sparse_categorical_crossentropy
- If you are trying to classify data points between N classes, your network should end with
a Dense layer of size N.
- Note that the quantities that we use for normalizing the test data have been computed using the training data. We should never use in our workflow any quantity computed on the test data, even for something as simple as data normalization.
- Our network ends with a single unit, and no activation (i.e. it will be linear layer). This is a typical setup for scalar regression (i.e. regression where we are trying to predict a single continuous value).
- When features in the input data have values in different ranges, each feature should be scaled independently as a preprocessing step.
- When little training data is available, it is preferable to use a small network with very few hidden layers (typically only one or two), in order to avoid severe overfitting.
- When training, a mini-batch is used to compute a single gradient descent update applied to the weights of the model.
- The arrow of time. If you are trying to predict the future given the past (e.g. the weather tomorrow, stock movements, and so on), you should not randomly shuffle your data before splitting it, because that would create a "temporal leak": you model would effectively be trained on data from the future. In such situations you should always make sure that all data in your test set is posterior to the data in the training set.
- In general, with neural networks, it is safe to input missing values as 0, under the condition that 0 is not already a meaningful value. The network will learn from exposure to the data that the value 0 simply means "missing data" and will start ignoring the value. However, note that if you are expecting missing values in the test data but the network was trained on data without any missing values, then the network will not have learned to ignore missing values! In this situation, then you should artificially generate training samples with missing entries: simply copy some training samples several times and drop some of the features that you expect are susceptible to go missing in the test data.
- Always keep this in mind: deep learning models tend to be good at fitting to the training data, but the real challenge is generalization, not fitting.
- The general workflow to find an appropriate model size is to start with relatively few layers and parameters, and start increasing the size of the layers or adding new layers until you see diminishing returns with regard to the validation loss.
- L2 regularization is also called weight decay in the context of neural networks. Don’t let the different name confuse you: weight decay is mathematically the exact same as L2 regularization.
- Dropout, applied to a layer, consists of randomly "dropping out" (i.e. setting to zero) a number of output features of the layer during training.
- The "dropout rate" is the fraction of the features that are being zeroed-out; it is usually set between 0.2 and 0.5. At test time, no units are dropped out, and instead the layer’s output values are scaled down by a factor equal to the dropout rate, so as to balance for the fact that more units are active than at training time.
- Note that this process can be implemented by doing both operations at training time and leaving the output unchanged at test time, which is often the way it is implemented in practice:
- The core idea is that introducing noise in the output values of a layer can break up happenstance patterns that are not significant (what Hinton refers to as "conspiracies"), which the network would start memorizing if no noise was present.
- To recap: here the most common ways to prevent overfitting in neural networks:Getting more training data.
Reducing the capacity of the network. Adding weight regularization. Adding dropout.
- Keep it in mind: machine learning can only be used to memorize patterns which are present in your training data. You can only recognize what you have seen before. Using machine learning trained on past data to predict the future is making the assumption that the future will behave like the past. That is often not the case.
- For balanced classification problems, where every class is equally likely, accuracy and ROC-AUC are common metrics. For class-imbalanced problems, one may use Precision-Recall. For ranking problems or multi-label classification, one may use Mean Average Precision.
- Always monitor the training loss and validation loss, as well as the training and validation values for any metrics you care about. When you see that the performance of the model on the validation data starts degrading, you have achieved overfitting.
-  Its depth can be arbitrary, since the output depth is a parameter of the layer, and the different channels in that depth axis no longer stand for specific colors like in an RGB input, rather they stand for what we call filters.
- In Conv2D layers, padding is configurable via the padding argument, which takes two values: "valid", which means no padding (only "valid" window locations will be used), and "same", which means "pad in such a way as to have an output with the same width and height as the input". The padding argument defaults to "valid".
- Strided convolutions are rarely used in practice, although they can come in handy for some types of models, and it is generally good to be familiar with the concept.
- On the other hand, convolution is most typically done with 3x3 windows and no stride (stride 1).
- Note that the depth of the feature maps is progressively increasing in the network (from 32 to 128), while the size of the feature maps is decreasing (from 148x148 to 7x7). This is a pattern that you will see in almost all convnets.
- A Python generator is an object that acts as an iterator, i.e. an object you can use with the for/in operator. Generators are built using the yield operator.
- A common and highly effective approach to deep learning on small image datasets is to leverage a pre-trained network
- Feature extraction consists of using the representations learned by a previous network to extract interesting features from new samples. These features are then run through a new classifier, which is trained from scratch.
- As we saw previously, convnets used for image classification comprise two parts: they start with a series of pooling and convolution layers, and they end with a densely-connected classifier. The first part is called the "convolutional base" of the model. In the case of convnets, "feature extraction" will simply consist of taking the convolutional base of a previously-trained network, running the new data through it, and training a new classifier on top of the output.
- Why only reuse the convolutional base? Could we reuse the densely-connected classifier as well? In general, it should be avoided. The reason is simply that the representations learned by the convolutional base are likely to be more generic and therefore more reusable: the feature maps of a convnet are presence maps of generic concepts over a picture, which is likely to be useful regardless of the computer vision problem at hand. On the other end, the representations learned by the classifier will necessarily be very specific to the set of classes that the model was trained on—they will only contain information about the presence probability of this or that class in the entire picture. Additionally, representations found in densely-connected layers no longer contain any information about where objects are located in the input image: these layers get rid of the notion of space, whereas the object location is still described by convolutional feature maps. For problems where object location matters, densely-connected features would be largely useless.
- Note that the level of generality (and therefore reusability) of the representations extracted by specific convolution layers depends on the depth of the layer in the model. Layers that come earlier in the model extract local, highly generic feature maps (such as visual edges, colors, and textures), while layers higher-up extract more abstract concepts (such as "cat ear" or "dog eye"). So if your new dataset differs a lot from the dataset that the original model was trained on, you may be better off using only the first few layers of the model to do feature extraction, rather than using the entire convolutional base.
- In Keras, freezing a network is done by setting its trainable attribute to False
- Note that in order for these changes to take effect, we must first compile the model. If you ever modify weight trainability after compilation, you should then re-compile the model, or these changes would be ignored.
- Another widely used technique for model reuse, complementary to feature extraction, is fine-tuning. Fine-tuning consists in unfreezing a few of the top layers of a frozen model base used for feature extraction, and jointly training both the newly added part of the model (in our case, the fully-connected classifier) and these top layers. This is called "fine-tuning" because it slightly adjusts the more abstract representations of the model being reused, in order to make them more relevant for the problem at hand.
- Thus the steps for fine-tuning a network are as follow:1) Add your custom network on top of an already trained base network. 2) Freeze the base network.3) Train the part you added.4) Unfreeze some layers in the base network.5) Jointly train both these layers and the part you added.
- Remember: if global order matters in your sequence data, then it is preferable to use a recurrent network to process it. This is typically the case for timeseries, where the recent past is likely to be more informative than the distant past. But if global ordering isn’t fundamentally meaningful, then 1D convnets will turn out to work at least as well, while being cheaper. This is often the case for text data, where a keyword found at the beginning of a sentence is just as meaningful as a keyword found at the end.
- "N-grams" are overlapping groups of multiple consecutive words or characters.
- Collectively, the different units into which you can break down text (words, characters or N-grams) are called "tokens", and breaking down text into such tokens is called "tokenization".
-  In this section we will present two major ones: one-hot encoding of tokens, and token embeddings (typically used exclusively for words, and called "word embeddings").
- Word N-grams are groups of N (or fewer) consecutive words that you can extract from a sentence. The same concept may also be applied to characters instead of words.
- The term "bag" here refers to the fact that we are dealing with a set of tokens rather than a list or sequence: the tokens have no specific order. This family of tokenization method is called "bag-of-words."
- Because bag-of-words are not an order-preserving tokenization method (the tokens generated are understood as a set, not a sequence, and the general structure of the sentences is lost), bag-of-words tend to be used in shallow language processing models rather than in deep learning models. Extracting N-grams is a form of feature engineering, and deep learning does away with this kind of rigid and brittle feature engineering, replacing it with hierarchical feature learning. One-dimensional convnets and recurrent neural networks, introduced later in this chapter, are capable of learning representations for groups of words and characters without being explicitly told about the existence of such groups, simply by looking at continuous word or character sequences. For this reason, we will not be covering N-grams any further in this book. But do keep in mind that they are a powerful, unavoidable feature engineering tool when using lightweight shallow text processing models such as logistic regression and random forests.
- One-hot encoding is the most common, most basic way to turn a token into a vector.
- Unlike word vectors obtained via one-hot encoding, word embeddings are learned from data. It is common to see word embeddings that are 256-dimensional, 512-dimensional, or 1024-dimensional when dealing with very large vocabularies. So, word embeddings pack more information into far fewer dimensions.
- There are two ways to obtain word embeddings:
Learn word embeddings jointly with the main task you care about (e.g. document classification or sentiment prediction). In this setup, you would start with random word vectors, then learn your word vectors in the same way that you learn the weights of a neural network.
Load into your model word embeddings that were pre-computed using a different machine learning task than the one you are trying to solve. These are called "pre-trained word embeddings".
- To get a bit more abstract: the geometric relationships between word vectors should reflect the semantic relationships between these words. Word embeddings are meant to map human language into a geometric space.
- It is thus reasonable to learn a new embedding space with every new task
- The Embedding layer takes as input a 2D tensor of integers, of shape (samples, sequence_length), where each entry is a sequence of integers. It can embed sequences of variable lengths, so for instance we could feed into our embedding layer above batches that could have shapes (32, 10) (batch of 32 sequences of length 10) or (64, 15) (batch of 64 sequences of length 15). All sequences in a batch must have the same length, though (since we need to pack them into a single tensor), so sequences that are shorter than others should be padded with zeros, and sequences that are longer should be truncated.
- This layer returns a 3D floating point tensor, of shape (samples, sequence_length, embedding_dimensionality). Such a 3D tensor can then be processed by a RNN layer or a 1D convolution layer (both will be introduced in the next sections).
- Instead of learning word embeddings jointly with the problem you want to solve, you could be loading embedding vectors from a pre-computed embedding space known to be highly structured and to exhibit useful properties—that captures generic aspects of language structure. The rationale behind using pre-trained word embeddings in natural language processing is very much the same as for using pre-trained convnets in image classification: we don’t have enough data available to learn truly powerful features on our own, but we expect the features that we need to be fairly generic, i.e. common visual features or semantic features. In this case it makes sense to reuse features learned on a different problem.
- Like all recurrent layers in Keras, SimpleRNN can be run in two different modes: it can return either the full sequences of successive outputs for each timestep (a 3D tensor of shape (batch_size, timesteps, output_features)), or it can return only the last output for each input sequence (a 2D tensor of shape (batch_size, output_features)). These two modes are controlled by the return_sequences constructor argument.
- It is sometimes useful to stack several recurrent layers one after the other in order to increase the representational power of a network. In such a setup, you have to get all intermediate layers to return full sequences:
-  This is essentially what LSTM does: it saves information for later, thus preventing older signals to gradually vanish during processing.
- Just keep in mind what the LSTM cell is meant to do: allowing past information to be reinjected at a later time, thus fighting the vanishing gradient problem.
- So we will normalize each timeseries independently so that they all take small values on a similar scale.
- In the same way that it is useful to establish a common sense baseline before trying machine learning approaches, it is useful to try simple and cheap machine learning models (such as small densely-connected networks) before looking into complicated and computationally expensive models such as RNNs. This is the best way to make sure that any further complexity we throw at the problem later on is legitimate and delivers real benefits.
- the proper way to use dropout with a recurrent network: the same dropout mask (the same pattern of dropped units) should be applied at every timestep, instead of a dropout mask that would vary randomly from timestep to timestep. What’s more: in order to regularize the representations formed by the recurrent gates of layers such as GRU and LSTM, a temporally constant dropout mask should be applied to the inner recurrent activations of the layer (a "recurrent" dropout mask). Using the same dropout mask at every timestep allows the network to properly propagate its learning error through time; a temporally random dropout mask would instead disrupt this error signal and be harmful to the learning process.
- Every recurrent layer in Keras has two dropout-related arguments: dropout, a float specifying the dropout rate for input units of the layer, and recurrent_dropout, specifying the dropout rate of the recurrent units.
- Recurrent layer stacking is a classic way to build more powerful recurrent networks
- To stack recurrent layers on top of each other in Keras, all intermediate layers should return their full sequence of outputs (a 3D tensor) rather than their output at the last timestep. This is done by specifying return_sequences=True
-  A bidirectional RNN is common RNN variant which can offer higher performance than a regular RNN on certain tasks. It is frequently used in natural language processing—you could call it the Swiss army knife of deep learning for NLP.
- A bidirectional RNN exploits this idea to improve upon the performance of chronological-order RNNs: it looks at its inputs sequence both ways, obtaining potentially richer representations and capturing patterns that may have been missed by the chronological-order version alone.
- To instantiate a bidirectional RNN in Keras, one would use the Bidirectional layer, which takes as first argument a recurrent layer instance. Bidirectional will create a second, separate instance of this recurrent layer, and will use one instance for processing the input sequences in chronological order and the other instance for processing the input sequences in reversed order
- Stacked RNNs provide more representational power than a single RNN layer. They are also much more expensive, and thus not always worth it. While they offer clear gains on complex problems (e.g. machine translation), they might not always be relevant to smaller, simpler problems.
- Bidirectional RNNs, which look at a sequence both ways, are very useful on natural language processing problems. However, they will not be strong performers on sequence data where the recent past is much more informative than the beginning of the sequence.
- The same properties that make convnets excel at computer vision also make them highly relevant to sequence processing. Indeed, time can be treated as a spatial dimension, like the height or the width of a 2D image.
- Such 1D convnets can be competitive with RNNs on certain sequence processing problems, usually at a considerably cheaper computational cost.
- How 1D convolution works: each output timestep is obtained from a temporal patch in the input sequence.
- Because 1D convnets process input patches independently, they are not sensitive to the order of the timesteps (beyond a local scale, the size of the convolution windows), unlike RNNs
- One strategy to combine the speed and lightness of convnets with the order-sensitivity of RNNs is to use a 1D convnet as a preprocessing step before a RNN. This is especially beneficial when dealing with sequences that are so long that they couldn’t realistically be processed with RNNs, e.g. sequences with thousands of steps. The convnet will turn the long input sequence into much shorter (downsampled) sequences of higher-level features. This sequence of extracted features then becomes the input to the RNN part of the network.
- In the same way that 2D convnets perform well for processing visual patterns in 2D space, 1D convnets perform well for processing temporal patterns. They offer a faster alternative to RNNs on some problems, in particular NLP tasks.
- Because RNNs are extremely expensive for processing very long sequences, but 1D convnets are cheap, it can be a good idea to use a 1D convnet as a preprocessing step before a RNN, shortening the sequence and extracting useful representations for the RNN to process.
-  An Inception module: a subgraph of layers with several parallel convolutional branches.
- A residual connection: reinjection of prior information downstream via feature map addition.
- In the functional API, you are directly manipulating tensors, and you use layers as functions that take tensors and return tensors (hence the name "functional API").
- The only part that may seem a bit magical at this point is instantiating a Model object using only an input tensor and output tensor. Behind the scenes, Keras will retrieve every layer that was involved in going from input_tensor to output_tensor, bringing them together into a graph-like data structure—a Model.
- The functional API can be used to build models that have multiple inputs. Typically, such models will at some point "merge" their different input branches using a layer that can combine several tensors, i.e. by adding them, concatenating them, etc. This is usually done via a Keras "merge operation" such as keras.layers.add, keras.layers.concatenate, etc.
- Several common neural network components are implemented as graphs. Two notable ones are Inception modules, and residual connections.
- INCEPTION MODULES ：It consists of a stack of modules which themselves look like small independent networks, split into several parallel branches. The most basic form of an inception module has three to four branches starting with a 1x1 convolution, following up with a 3x3 convolution, and ending with the concatenation of the resulting features. This setup helps the network separately learn spatial features and channel-wise features, which is more efficient than learning them jointly
- They tackle two common problems that plague any large-scale deep learning model: vanishing gradients, and representational bottlenecks. In general, adding residual connections to any model that has over ten layers is likely to be beneficial.
- A residual connection simply consist of making the output of an earlier layer available as input to a later layer, effectively creating a shortcut in a sequential network. Rather than being concatenated to the later activation, the earlier output is summed with the later activation, which assumes that both activations have the same size. In case of differing sizes, one may use a linear transformation to reshape the earlier activation into the target shape (e.g. a Dense layer without an activation, or for convolutional feature maps, a 1x1 convolution without an activation).
- This problem occurs both with very deep networks and with recurrent networks over very long sequences—in both cases, a feedback signal must be propagated through a long series of operations. You are already familiar with the solution that the LSTM layer uses to address this problem in recurrent networks: it introduces a "carry track" that propagates information in parallel to the main processing track. Residual connections work in a very similar way in feedforward deep networks, but they are even simpler: they introduce a purely linear information carry track parallel to the main layer stack, thus helping to propagate gradients through arbitrarily deep stacks of layers.
- One more important feature of the functional API is the ability to reuse a layer instance several time. When you call a layer instance twice, instance of instantiating a new layer for each call, you are reusing the same weights with every call. This allows you to build models that have shared branches—several branches that all share the same knowledge and perform the same operations, i.e. that share the same representations, and learn these representations simultaneously for different sets of inputs.
- Importantly, in the functional API, models can be used as you would use layers—effectively, you may think of a model as a "bigger layer". This is true of both the Sequential and Model classes. This means that you can call a model on an input tensor, and retrieve an output tensor
- How to reuse the weights of a layer or model across different processing branches, by calling a same layer or model instance several times.
- A callback is an object (a class instance implementing specific methods) that is passed to the model in the call to fit and that is called by the model at various points during training. It has access to all the data available about the state of the model and its performance, and it is capable to take action, for instance interrupting training, saving a model, loading a different weight set, or otherwise altering the state of the model.
- You can use the EarlyStopping callback to interrupt training once a target metric being
monitored has stopped improving for a fixed number of epochs
- This callback is typically used in combination with ModelCheckpoint, which allows to continually save the model during training (and optionally, to save only the current best model so far, i.e. the version of the model that achieved the best performance at the end of an epoch).
- You can use this callback to reduce the learning rate when the validation loss has stopped improving. Reducing or increasing the learning rate in case of a "loss plateau" is is an effective strategy to get out of local minima during training.
-  TensorBoard gives you access to several neat features, all inside your browser:Visually monitoring your metrics during training. Visualizing your model architecture.Visualizing histograms of activations and gradients. Exploring embeddings in 3D.
- Since the embedding space is actually 128-dimensional, TensorBoard automatically reduces it 2D or 3D using a dimensionality reduction algorithm of your choice: either PCA or T-SNE.
- In previous examples, we were only normalizing data before feeding it into our models. However, data normalization should still be a concern after every transformation operated by the network: even if the data coming in a Dense or Conv2D network has 0-mean and unit variance, there are no reasons to expect a priori that this will still be the case for the data coming out.
- Batch normalization is a type of layer (BatchNormalization in Keras) introduced in 2015 by Ioffe and Szegedy, capable of adaptively normalizing data even as its mean and variance change over time during training. It works by internally maintaining an exponential moving average of the batch-wise mean and variance of the data seen during training. The main effect of batch normalization is that it helps with gradient propagation—much like residual connections—and thus it allows for deeper networks. Some very deep networks can only be trained if they include multiple BatchNormalization layers.
- The BatchNormalization layer is typically used after a convolutional or densely-connected layer:
- The BatchNormalization layer takes an axis argument, which specifies the
features axis which should be normalized. This argument defaults to -1, the last axis in
the input tensor. This is the correct value when using Dense layers, Conv1D layers, RNN layers, as well as Conv2D layers with data_format set to "channels_last". However, in the niche use case of Conv2D layers with data_format set to "channels_first", the features axis is axis number 1, and the axis argument in BatchNormalization should then be set to 1 accordingly.
- Often, it turns out that random search (picking the hyperparameters to evaluate at random, repeatedly) is the best solution, despite being the most naive one. However, one tool that I have found reliably better than random search is Hyperopt, a Python library for hyperparameter optimization which internally uses trees of Parzen estimators to predict sets of hyperparameters that are likely to work well. Another library called Hyperas integrates Hyperopt for use with Keras models. Do check it out.
- One thing that I have found to work well in practice—but which does not generalize to every problem domain—is the use of an ensemble of tree-based methods (such as random forests or gradient boosted trees) and deep neural networks.
- That’s precisely the point of ensembling. It’s not so much about how good your best model is, it is about the diversity of your set of candidate models.
- In recent times, one style of basic ensemble that has been very successful in practice is the "wide and deep" category of models, blending deep learning with shallow learning, consisting in jointly training a deep neural net with a large linear model. The joint training of a family of diverse models is yet another option to achieve model ensembling.
- Remember that you should manage to get your model to overfit (thus identifying a model capacity level that is above that you need), and only then start adding regularization or start downsizing your model.
- Convnets are often ended with either a Flatten operation or a global pooling layer, turning spatial feature maps into vectors, followed by Dense layers to achieve classification or regression.
- Note that it is highly likely that regular convolutions will soon be mostly (or completely) replaced by an equivalent but faster and even representationally efficient alternative, the depthwise separable convolution (SeparableConv2D layer). This is true for 3D, 2D or 1D inputs. When building a new network from scratch, using depthwise separable convolutions is definitely the way to go. The SeparableConv2D layer can be used as a drop-in replacement for Conv2D, resulting in a smaller and faster network that will also perform better on its task.
- In order to stack multiple RNN layers on top of each other, each layer prior to the last one should return the full sequence of its outputs (to each input timestep will correspond an output timestep); if you are not stacking any further RNN layers, then it is common to only return the last output, which contains information about the entire sequence.