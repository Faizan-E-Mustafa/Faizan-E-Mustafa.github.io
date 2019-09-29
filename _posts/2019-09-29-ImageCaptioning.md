---
title: "Keras Implementation of Image Captioning Model"
date: 2019-09-29
tags: [Image Captioning , Projects]
excerpt: "Image captioning is a task that involves computer vision as well as Natural language processing. It takes an image and is able to describe whats going on in the image in English. It uses InceptionV3 to extract features from images and LSTM to generate captions for images.This implementation uses Keras with Tensorflow back end."
---
Image captioning is a task that involves computer vision and natural language processing. It takes an image and can describe what's going on in the image in plain English. A CNN architect is used to extract features from the images. Then the encoded image is passed through a decoder. Since RNN is very good with sequential data and we need to describe an image in a sentence so we could use an RNN or its variant as a decoder.

## Data set:

I used flicker8k data set. It contains 8,000 images. Each image has five captions. The model was trained on 6,000 images, and 1,000 images were spared for Dev and Test set each.

## Encoder:

I used InceptionV3 as an encoder. Taking advantage of the transfer learning pre-trained weights of inception V3 was used. The second last layer of the inception model was the new output of the model, as we want to encode an image into a vector.

## Decoder:

I used LSTM as a decoder. The model summary is as below.

- This is the image model as it takes the encoded image from the inception model and uses a fully connected layer to scale it down from 2048 dimensions to 300 dimensions.
{% include figure image_path="/images/posts/ImageCaptioning/ImageModel.png" alt="this is a placeholder image" caption="Image Model" %}

- This is the language model; It receives one hot vector that is first converted into the embedding vector and then passed through bidirectional LSTM.
{% include figure image_path="/images/posts/ImageCaptioning/LangModel.png" alt="this is a placeholder image" caption="Language Model" %}

- The image model and language model are then merged and passed through another bidirectional LSTM to output a vector of vocabulary size. The highest probability value of the vocabulary vector is the next predicted word.
{% include figure image_path="/images/posts/ImageCaptioning/Final.png" alt="this is a placeholder image" caption="Final Model" %}

These were the values of different variables.
Embedding size = 300
Vocabulary size= 8256
Dropout = 0.5
Optimizer = Adam
Batch Size = 128

## Training:

I trained the model for 13 epochs. The following are loss values for some epochs.

11 epochs : 2108s 703ms/step - loss: 1.3744 - acc: 0.605812 epochs : 2106s 703ms/step - loss: 1.2529 - acc: 0.6332
13 epochs : 2097s 700ms/step - loss: 1.1560 - acc: 0.6571

It gave decent results at the 12th epoch. But the results deteriorated a bit at the 13th epoch, so I did not train it further.

**Note: I trained my model for 10 epochs and the model was working fine. But the next day model was giving results of an untrained model. Turned out I made a new vocabulary and overwrote the previous one. Every time you tokenize a new vocabulary, it assigns a new index to the same word. So I had to train my model all over again. It will make more sense when you go through the code.**

## Testing:

I used a greedy search and beam search to predict the results. Unlike greedy search where we pick only the highest probability to get the next word prediction, In beam search, we pick as many words as we like each time it makes a prediction. Suppose we picked three words, then we will take into account the probability of a whole caption by using the first word, second word, and the third word separately. Whichever is giving us the maximum probability for the caption, we pick that one word.

If you want to know more about the beam search, you can find Andrew Ng's video [***Here.***](https://www.coursera.org/lecture/nlp-sequence-models/beam-search-4EtHZ)

## Results:
{% include figure image_path="/images/posts/ImageCaptioning/result.png" alt="this is a placeholder image" %}

Sometimes Beam Search does its trick.

{% include figure image_path="/images/posts/ImageCaptioning/Beam.png" alt="this is a placeholder image" %}

Kindly share your reviews about the project. Thanks
