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
np.random.seed(0)

x2 = np.random.randint(10, size=(3, 4))

print(x2[:2, :3]) # first 2 row and 3 columns
print(x2[:, ::2]) # every row with column's step=2
print(x2[::-1, ::-1]) # mirror every axis
print(x2[:, 2]) # second column
print(x2[0, :]) # first row
```

Зрізи масиву повертають views, а не копії, тому якщо ми змінемо зрізаний підмасив, то батьківський масив також зміниться.

### Копії масивів
```python
np.random.seed(0)

x2 = np.random.randint(10, size=(3, 4))
x2[0] = 0

x2_sub_copy = x2[:2, :2].copy()
x2_sub_copy[0][0] = 1

print(x2_sub_copy)
print(x2)
```

### Зміна форми масивів
```python
x2 = np.arange(1, 10)
x = np.array([1, 2, 3])

print(x2.reshape((3, 3)))
print(x[np.newaxis, :]) # add new axis to make row-vector
print(x[:, np.newaxis]) # add new axis to make column-vector
```

### Злиття масивів 
```python
x = np.array([1, 2, 3])
y = np.array([3, 2, 1])
z = np.array([[99],
              [99]])

grid = np.array([[1, 2, 3],
                 [4, 5, 6]])
                 
print(np.concatenate([x, y]))
print(np.concatenate([grid, grid]))
print(np.concatenate([grid, grid], axis=1)) # конкатенація за колонками
print(np.vstack([x, grid]))
print(np.hstack([z, grid]))

# np.dstack for 3-dimensional array
```

### Розбиття масивів
```python
x = np.arange(10)
grid = np.arange(32).reshape((8, 4))
grid2 = np.arange(16).reshape((4, 4))

x1, x2, x3 = np.split(x, [3, 5])
upper, mid, lower = np.vsplit(grid, [2, 6])
left, right = np.hsplit(grid2, [2])

print(x1, x2, x3, '\n')
print(upper, '\n', mid, '\n', lower)
print('\n', left, '\n', right)

#np.dsplit for 3-rd dimension
```

### Висновок:
Я навчився створювати масиви, дізнався про одновиміну і багатовимірну індексацію, вияснив різницю між python типами даних і 