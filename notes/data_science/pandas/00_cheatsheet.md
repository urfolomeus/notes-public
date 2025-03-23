# Creating a DataFrame

```python
import pandas as pd

# from a numpy array
data = np.random.random(size=(5, 3))
df = pd.DataFrame(data_np, columns=["A", "B", "C"])

# from a dictionary - option 1
data = {"A": [1, 2, 3], "B": ["Sam", "Alex", "John"]}
df = pd.DataFrame(data)

# from a dictionary - option 2
data = [{"A": 1, "B": "Sam"}, {"A": 2, "B": "Alex"}, {"A": 3, "B": "John"}]
df = pd.DataFrame(data)

# Or a list of rows (ie tuples) with a dtype
dtype = [("A", int), ("B", (str, 20))]
data = np.array([(1, "Sam"), (2, "Alex"), (3, "John")], dtype=dtype)
df = pd.DataFrame(data)
```

# Importing data into a DataFrame

```python
import pandas as pd

# csv
df = pd.read_csv("example.csv")
df.head()

# json
df = pd.read_json("example.json")
df.head()

# from a python data structure
data = [
	{"a": 1, "b": 2},
	{"a": 4, "b": 5},
]
df = pd.DataFrame(data)
```

# Converting data

See [[00_pro_tips#Immutable vs. mutable]] to find out why I'm using `copy()` with `to_numpy()`.

```python
import pandas as pd

df = pd.read_csv("example.csv")

# to numpy
df.to_numpy().copy()
```

# Inspecting data

```python
import pandas as pd

df = pd.read_csv("astronauts.csv")

# get first 5 rows
df.head()
# get first 2 rows
df.head(2)

# get last 5 rows
df.tail()
# get last row
df.tail(1)

# get a random sample containing 3 rows
df.sample(3)

# get some information about the dataframe including things like column info and the number of non-null values in each column
df.info()

# get statistical information about the dataframe
df.describe()

# get the number of rows and columns
df.shape()

# get the correlation between numeric columns
df.corr(numeric_only=True)

# The number of each occurrence for a series
df["Year"].value_counts()

# There are also a whole host of math/stats functions, such as
df.max(numeric_only=True)
```