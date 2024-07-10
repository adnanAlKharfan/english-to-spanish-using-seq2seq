# English to Spanish using seq2seq

This Repository contains my attempt to create AI translation Model. I used sequence to sequence architecture with attention(force learning) to be able to obtain more semantic meaning therefore getting better result exceeding not only the regular translation which is word-to-word but also the regular AI Model.


## Introduction

English-to-Spanish model is model that takes english sentence and translate it to spanish sentence using sequence to sequence and attention(force learning). 

### Sequence-To-Sequence

Sequence-To-Sequence or in other words encoder-decoder architecture is consist of two part encoder and decoder. The encoder will take the input and try to find the context using previous words, the context of a sentence will be represented as a vector. The decoder will take context vector and use it in every prediction keeping in mind the previouses predicted words to establish a correct sentence as its output.

### Attention

Attention as the name suggest is a layer or architecture that tries to compute where the model should keep its attention on, the attention layer compute similarity between words so it takes the first input word both cell and hidden state, and the output of the first decoder lstm cell states then calculate the similarity between the words been feeded to the both of them using dot product then softmax is applied to the output. the output will be multiply with the original encode state. so the output from the soft max of how much should the model concetrate on.

### Teacher Learning

Teacher Learning is one method that is used in Attention, it way to provide the correct word to next lstm decoder cell rather on it depend on the previous prediction.


## Methodology 

After loading the data and tranfer them into sequence and padding them, I loaded word2vec glove weights as my embedding english layer. the model is consist of english embedded layer, bidirectional lstm layer, spanish embedded layer, repeate vector layer, concatenation layer on the last axis, Dense layer with 10 neurons, Dense layer with 1 neuron using softmax as activation function, Dot layer, decoder lstm layer, initial hidden state as input layer, initial cell state as input layer and finally a lamda layer that stack all the prediction of the decoder lstm and change the dimension. after the embedding layer changes the words to vectors, the bidirectional layer takes the embedding output then in parallel the decoder embedding layer finishes it's output to pass it with initial hidden state to attention layer that first repeat the embedding vector to match the input sentance, concate them after then pass them the two dense layers to get alpha as scale the output of the embedding layer, it will keep that until all the output sentence is finished and finally stack the outputs of all of loop to create a final sentence.

## Experiment

- batch size: `64`
- epochs: `50`
- validation split: `0.2`

### Example of the model prediction

```
orginal: cuff him.
espósale.
```

## Contribution 

feel free to make a pull request to update or fix any discovered issue 
 

  
