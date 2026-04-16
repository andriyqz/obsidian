### Функції агрегування
```python
x = np.arange(16).reshape(4, 4)

  

print(x, '\n')

print(x.sum(axis=0)) # x.nansum

print(x.sum(axis=1))

print(x.prod(axis=1)) # x.nanprod

print(x.min(axis=1)) # x.nanmin, x.nanmax exists too

print(x.std(axis=0)) # x.nanstd

print(x.mean(axis=0)) # x.nanmean

print(x.var(axis=0)) # x.nanvar

print(np.argmin(x, axis=1)) # returns index of minimum, np.nanargmin exists too

print(np.argmax(x, axis=1)) # returns index of maximum, np.nanargmax exists too

print(np.median(x)) # return median for whole array, np.nanmedian exists too

print(np.percentile(x, 25)) # np.nanpercentile exists too, значення нижче якого лежать 25% всіх даних

print(np.any(x)) # checks whether true elements exist or not

print(np.all(x)) # checks whether all elements are true or not
```