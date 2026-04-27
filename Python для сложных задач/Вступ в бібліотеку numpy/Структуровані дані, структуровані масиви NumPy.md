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