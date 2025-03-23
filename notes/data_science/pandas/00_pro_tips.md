# Pro Tips

## NumPy vs. Pandas

### Immutable vs. mutable

> TL;DR always call `copy()` explicitly after calling `to_numpy()` so that changes to the NumPy data structure are not reflected in the Pandas dataframe.

If you convert a Pandas dataframe to a NumPy array and then subsequently change values in the NumPy array, those changes may or may not be reflected in the dataframe, depending on some implicit circumstances.

It is, therefore, always best to explicitly copy the resulting NumPy array to ensure that it will never affect the parent Pandas dataframe.

For example:

```python
import pandas as pd

df = pd.DataFrame([{"foo": 1, "bar": 2.3}])
df.head()
#=> | foo | bar |
#   |  1  | 2.3 |

data = df.to_numpy()
data[0,0] = 100
print(data)
#=> [100., 2.3]
df.head()
#=> | foo | bar |
#   |  1  | 2.3 |
```

This happens because the type for `foo` is Int, and the type for `bar` is Float. This causes NumPy to perform a conversion to treat all values as floats.

However, if all types are Int, no implicit conversion is done by `to_numpy()`, and so the implicit copy does not happen.

```python
import pandas as pd

df = pd.DataFrame([{"foo": 1, "bar": 2}])
df.head()
#=> | foo | bar |
#   |  1  |  2  |

data = df.to_numpy()
data[0,0] = 100
print(data)
#=> [100, 2]
df.head()
#=> | foo | bar |
#   | 100 |  2  |
```

To make this more explicit, we can explicitly call `copy()` and break the link between the dataframe and the NumPy structure.

```python
import pandas as pd

df = pd.DataFrame([{"foo": 1, "bar": 2}])
df.head()
#=> | foo | bar |
#   |  1  |  2  |

data = df.to_numpy().copy()
data[0,0] = 100
print(data)
#=> [100, 2]
df.head()
#=> | foo | bar |
#   |  1  |  2  |
```

### When to use NumPy over Pandas

> TL;DR prefer Pandas over NumPy unless there is a piece of functionality that is not available in Pandas (even then it probably is available but just achieved in a different way).

For the most part, Pandas acts as a superset of NumPy. If it's available in NumPy, it's probably available in NumPy. In these situations, we should just use the method that makes the most sense. If we're working with a Pandas object, use Pandas. If we're working with a NumPy object, use NumPy direct.

```python
# imagine we have a DataFrame that contains a column of integers titled `age`
print(df['age'].mean(), df['age'].to_numpy().mean())
#=> 54.48844884488449 54.48844884488449
```

There are some exceptions to this rule:

```python
# some functions are only available in Pandas
print(df['age'].quantile(0.5))

# some functions are only available in NumPy
print(df['age'].to_numpy().reshape((3, -1)))
```

## Saving and loading data state

As we work with dataframes in Pandas it can be handy to save out our state at certain points so that we can reload that data later. There are many formats that Pandas can work with, but most often we'll just use CSV because it's human readable, easy to work with and easy to share with others.

```python
import numpy as np
import pandas as pd

df = pd.DataFrame(np.random.random(size=(100000, 4)), columns=["A", "B", "C", "D"])

df.to_csv("my_data.csv")

# or if we would prefer not to include the index column and only want 4 significant digits...
df.to_csv("my_data.csv", index=False, float_format="%0.4f")

# we can bring that saved state back in with
df = pd.read_csv("my_data.csv")
```