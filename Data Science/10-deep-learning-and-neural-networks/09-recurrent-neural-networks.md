# Recurrent neural networks

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/35-rnn-sentiment-analysis.ipynb

### RNNs: what are they for?

- Time series data
    - When you want to predict future behavior based on past behavior
    - Web logs, sensor logs, stock trades
    - Where to drive your self-driving car based on past trajectories
- Data that consists of sequences of arbitrary length
    - Machine translation
    - Image captions
    - Machine generated music

## A Reccurrent neuron

- As we run a training step on a neuron, it will apply a step function.
- Usually we would output the result, but now we will feed it back to the same neuron
- It will influence the next step of the computation.

## RNN Topologies

- Sequence to sequence
    - i.e., predict stock prices based on series of historical data
- Sequence to vector
    - i.e., words in sentence to sentiment
- Vector to sequence
    - i.e., create captions from an image
- Encoder to Decoder
    - Sequence -> vector -> sequence
    - i.e., machine translation

## Training RNNs

- Backpropogation through time
    - Just like backpropogation on MLPs, but applied to each time step
- All those time steps add up fast
    - Ends up looking like a really, really deep neural network.
    - Can limit backpropogation to a limited number of time steps (truncated backpropogation though time)

- State from earlier time steps get dilluted over time
    - This can be a problem for example when learning sentence structures
    - LSTM Cell
        - Long Short-Term Memory Cell
        - Maintains separate short-term and long-term states
    - GRU Cell
        - Gated Recurrent Unit
        - Simplified LSTM cell that performs about as well

- It's really hard
    - Very sensitive to topologies, choice of hyperparameters
    - Very resource intensive
    - A wrong choice can lead to a RNN that doesn't converge at all.
