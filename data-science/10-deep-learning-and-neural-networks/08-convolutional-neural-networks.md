# Convolutional neural networks

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/34-keras-convolutional-networks.ipynb

## CNN's: what are they for?

- When you have data that doesn't neatly align into columns
    - Images that you want to find features within
    - Machine translation
    - Sentence classification
    - Sentiment analysis
- They can find features that aren't in specific spot
    - Like a stop sign in a picture
    - Or words within a sentence
- They are "feature-location invariant"

## How do they work?

- Inspired by the biology of the visual cortex
    - Local receptive fields are groups of neurons that only respond to a part of what your eyes see (subsampling)
    - They overlap each other to cover the entire field (convolutions)
    - They feed into a higher layers that identify increasingly complex images
        - Some receptive fields identify horizontal lines, lines at different angles, etc. (filters)
        - These would feed into a layer that identifies shapes
        - Which might feed into a layer that identifies objects
        - For color images, extra layers for red and blue

## How do we know that's a stop sign?

- Individual local receptive fields scan the image looking for edges, and pick up the edges of the stop sign in a layer
- Those edges in turn get picked up by a higher level convolution that identifies the stop sign's shape (and letters too)
- This shape then gets matched against your pattern of what a stop sign looks like, also using the strong red signal coming from your red layers
- That information keeps getting processed upward until your foot hits the brake
- A CNN works the same way

## CNNs with keras

- Source data must be of appropriate dimensions
    - ie with x length x colors channels
- Conv2D layer type does the actual convolution on a 2D image
    - Conv1D and Conv3D also available - doesn't have to be image data.
- MaxPooling2D layers can be used to reduce a 2d layer down by taking the minimum value in a given block
- Flatten layers will convert the 2D layer to a 1D layer for passing into a flat hidden layer of neurons
- Typical usage:
    Conv2D -> MaxPooling2D -> Dropout -> Flatten -> Dense -> Dropout -> Softmax

## CNNs are hard

- Very resource-intensive (CPU, GPU and RAM)
- Lots of hyperparameters
    - Kernel sizes, many layers with different numbers of units, amount of pooling... in addition to the usual stuff like number of layers, choice of optimizer
- Getting the training data is often the hardest part. As well as storing and accessing it.

## Specialized CNN architectures

- Defines specific arrangement of layers, padding, and hyperparameters
- LeNet-5
    - Good for handwriting recognition
- AlexNet
    - Image classification, deeper than LeNet
- GoogLeNet
    - Even deeper, buty with better performance
    - Introduces inception modules (groups of convolution layers)
- ResNet (Residual Network)
    - Even deeper - maintains performance via skip connections.
