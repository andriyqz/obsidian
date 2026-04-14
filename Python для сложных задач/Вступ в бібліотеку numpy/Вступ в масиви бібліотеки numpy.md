### Створення масивів
```python
np.zeros(10, dtype=int)
np.ones((3, 5), dtype='float32')
np.full((3, 5), 3.14)
np.arange(0, 20, 2)
np.linspace(0, 1, 5)
np.random.random((3, 3)) # random values between 0 and 1
np.random.normal(0, 10, (3, 3)) # normal distribution width sigma = 10 around 0
np.eye(3, 5) # E matrix 3x5
np.empty((3, 5)) # empty matrix
```

### Атрибути масивів
```python
x1 = np.random.randint(10, size=6)
x2 = np.random.randint(10, size=(3, 4))
x3 = np.random.randint(10, size=(3, 4, 5))

print(x1.ndim, x1.shape, x1.size)
print(x2.ndim, x2.shape, x2.size)
print(x3.ndim, x3.shape, x3.size)
print(x1.dtype)
```
