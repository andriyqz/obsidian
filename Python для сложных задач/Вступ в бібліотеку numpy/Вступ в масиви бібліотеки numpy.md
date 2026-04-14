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
print(x1.itemsize) # size of every element in bytes
print(x2.nbytes) # x2.itemsize * x2.size
```

### Індексація
```python
np.random.seed(0)

x2 = np.random.randint(10, size=(3, 4))

print(x2)
print(x2[1, 2])

x2[0][0] = 3.14 # will be just 3!
print(x2)
```

### Зрізи
```python
np.random.seed(0)

x = np.arange(10)

print(x[4:-1:2]) # from 4 to end with step = 2
print(x[::2]) # from start to end with step = 2
print(x[1::2]) # from 1 to end with step = 2
print(x[5::-2]) # from 5 to start with step = 2
```

### Багатовимірні зрізи
```python

```