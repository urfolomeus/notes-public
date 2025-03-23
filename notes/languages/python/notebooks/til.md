# Today I learned

These are some interesting things that I've picked up about Python.

## Tuples

Tuples are data structures that can contain one or more values of any type. They are defined by surrounding a comma separated list of values with round brackets, a.k.a parentheses.
The only difference between tuples and lists are that tuples are immutable. You cannot append, change or remove individual members within a tuple.

```jupyter
# we'll use pytest to help us to catch and reason about exceptions
import pytest

my_list = [1, 'a', True]

my_list[0] += 1
my_list[1] = 'b'

print(f"My list is now: {my_list}")

my_tuple = (1, 'a', True)

with pytest.raises(TypeError) as exc_info:
    my_tuple[0] += 1

print(f"Threw exception: \"{exc_info.type.__name__}: {exc_info.value}\"")
```

