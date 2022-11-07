# Other keras examples

## Example: multi-class classification

MNIST is an example of multi-class classification.

```python
model = Sequential()
model.add(Dense(64, activation='relu', input_dim=20)
model.add(Dropout(0.5))
model.add(Dense(64, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(10, activation='softmax'))
sgd = SGD(lr=0.01, decay=1e-6, momentum=0.9, nesterov=True)
model.compile(loss='categorical_crossentropy', optimizer=sgd, metrics=['accuracy'])
```

## Example: binary classification

```python
model = Sequential()
model.add(Dense(64, input_dim=20, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(64, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(1, activation='sigmoid'))
model.compile(loss='binary_crossentropy', optimizer='rmsprop', metrics=['accuracy'])
```


## Integratin Keras with scikit_learn

```python
from tesorflow.keras.wrappers.scikit_learn import KerasClassifier

def create_model():
    model = Sequential()
    model.add(Dense(64, input_dim=20, activation='relu'))
    model.add(Dropout(0.5))
    model.add(Dense(64, activation='relu'))
    model.add(Dropout(0.5))
    model.add(Dense(1, activation='sigmoid'))
    model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])

    return model

estimator = KerasClassifier(build_fn=create_model, epochs, verbose=0)

cv_scores = cross_val_score(estimator, labels, cv=10)
print(cv_scores.mean())
```

## Trying to predict political parties with Keras

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/33-using-keras-to-predict-political-parties.ipynb
