### Structured array
```python
data = np.zeros(4, dtype={'names': ('name', 'age', 'weight'),
                          'formats': ('U10', 'i4', 'f8')})


name = ['Alice', 'Bob', 'Cathy', 'Doug']
age = [25, 45, 37, 19]
weight = [55, 85.5, 68, 61.5]

data['name'] = name
data['age'] = age
data['weight'] = weight

  

print(data)
print(data['name'])
print(data[0])
print(data[-1]['age'])
print(data[data['age'] < 30]['name'])
```

```python
np.dtype({'names': ('name', 'age', 'weight'),
          'formats': ('U10', 'i4', 'f8')})
          
np.dtype({'names': ('name', 'age', 'weight'),
          'formats': ((np.str_, 10), int, np.float32)})

np.dtype([('f0', 'S10'), ('f1', '<i4'), ('f2', 'f8')])

tp = np.dtype([('id', 'i8'), ('mat', 'f8', (3, 3))])
np.zeros(1, dtype=tp)
```

### np.recarray
```python
person_dtype = np.dtype({'names': ('name', 'age', 'weight'),
                         'formats': ('U10', 'i4', 'f8')})


data = np.zeros(3, dtype=person_dtype)
data_rec = data.view(np.recarray)

data_rec.age # but slower
```