# Box 1

```python
import numpy as np
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import LSTM, Dense

# 1. Prepare time-series data
X_train = np.array([
    [10, 20, 30],
    [20, 30, 40],
    [30, 40, 50],
    [40, 50, 60]
])
print(X_train)
X_train = X_train.reshape(4, 3, 1)
print(X_train)
y_train = np.array([40, 50, 60, 70])
```

# Box 2

```python
# Define the minimal LSTM network
# 3 timesteps, 1 feature, output 1 single next value
model = Sequential([
    LSTM(20, activation='relu', input_shape=(3, 1)), 
    Dense(1, activation='linear')                                         
])

# Compile and train
model.compile(optimizer='adam', loss='mae')
model.fit(X_train, y_train, epochs=200, verbose=0)
```

# Box 3
```python
# Predict the next value
X_input = np.array([50, 60, 70])
X_input = X_input.reshape((1, 3, 1))
prediction = model.predict(X_input, verbose=1)

print(f"Predicted next value: {prediction[0][0]:.2f}")
```
