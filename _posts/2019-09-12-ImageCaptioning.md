---
title: "Batch Vs Mini Batch Gradient Descend"
date: 2019-09-12
tags: [Gradient Descend]
excerpt: "Difference between Batch and mini-batch gradient descend and their advantages and disadvantages."
---
Deep leaning works best in the regime of Big data . Algorithms tends to work slow on large data sets. that’s why we need fast optimization algorithms to cope well with the large data sets. One little example of optimization is when we use vectorization instead of loops . So whenever we find a loop that can be implemented using vectorization we do it without giving it a second thought.

### Batch vs Mini batch gradient descend :
Mini batch gradient descend is also used to get an optimized algorithm.

**We want our gradient descend(backward propagation ) to not sit idle until we have gone through whole training data (forward propagation).**

Unlike batch descend , mini batch descend use mini batches of training data . when we use whole training data to get the output from forward propagation .Gradient descend step will be at rest during this whole time . If we could somehow manage to get this gradient descend working before going through whole training data we could get a better optimized algorithm. So we divide training data into mini batches and we do our forward and back propagation for each mini batch .

**Batch gradient descend :** If batch size is equal to # of training examples(m)

**Disadvantage:** It takes very long time per iteration if training set is very large. Gradient descend sits idle.

**Stochastic gradient descend:** If batch size is 1 then we will do forward and backward propagation for 1 training example at a time.

**Disadvantage :** We lose speed up from the vectorization because we are using only a single training example at a time.

**What should be the batch size ?**
We want to keep vectorization and at the same time we want to make progress without going through entire training set. so we have to use batch size between 1 and m . typical mini batch size are 64,128,256 . These sizes are usually written as power of 2.

**Note:** If training set is small ( m < 2000) then we can use batch gradient descend because in case of small training set gradient decent will not have to wait long enough.