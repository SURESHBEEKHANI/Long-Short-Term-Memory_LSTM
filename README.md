# Sequence Modeling with LSTM

This project demonstrates how to build and train a sequence model using an LSTM (Long Short-Term Memory) network for sequence prediction tasks. The model architecture includes an embedding layer, an LSTM layer, and a dense output layer.

## Model Architecture

1. **Embedding Layer**: 
   - Converts input sequences of integers into dense vectors of fixed size.
   - Parameters:
     - `total_words`: The size of the vocabulary.
     - `10`: Dimension of the dense embedding vectors.
     - `input_length`: Length of input sequences (`max_sequence_len - 1`).

2. **LSTM Layer**:
   - Processes the sequence data and retains temporal information.
   - Parameters:
     - `100`: Number of units in the LSTM layer.

3. **Dense Layer**:
   - Outputs the probability distribution over the vocabulary.
   - Parameters:
     - `total_words`: Size of the output layer (same as vocabulary size).
     - `activation='softmax'`: Softmax activation function to produce a probability distribution.

## Model Compilation

- **Optimizer**: Adam
- **Loss Function**: Categorical Crossentropy (suitable for multi-class classification tasks)
- **Metrics**: Accuracy

## Training the Model

The model is trained using the `fit` method with the following parameters:

- **Epochs**: 50
- **Batch Size**: 32
- **Verbose**: 1 (Displays the progress bar)

## Code Example

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Embedding, LSTM, Dense

# Define the model
model = Sequential([
    Embedding(total_words, 10, input_length=max_sequence_len-1),
    LSTM(100),
    Dense(total_words, activation='softmax')
])

# Compile the model
model.compile(
    optimizer='adam',
    loss='categorical_crossentropy',
    metrics=['accuracy']
)

# Train the model
model.fit(
    x_train,
    y_train,
    epochs=50,
    batch_size=32,
    verbose=1
)
