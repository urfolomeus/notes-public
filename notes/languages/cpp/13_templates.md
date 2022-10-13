# Templates

## Template Types

A **template type** is a special type that can take on different types when the type is initialized. For example, `std::vector` uses a template type:

```c++
std::vector<char>         // a vector that holds items of primitive type char
std::vector<int>          // a vector that holds items of primitive type int
std::vector<uiuic::Cube>  // a vector that holds items of user-defined type uiuc::Cube
```

Key ideas:

Defined in: `#include <vector>`
Initialization: `std::vector<T> v`
Add to (back) of vector: `::push_back(T)`
Access specific element: `::operator[](unsigned pos)`
Number of elements: `::size()`

When initializing a "templated" type, the template type goes inside of `< >` at the end of the type name:

```c++
std::vector<char> vChars;
std::vector<int> vInt;
std::vector<uiuc::Cube> vCubes;
```

See the [example code](../../example_code/cpp-vector/) for more details.

## Creating Template Types

C++ allows us to use the power of templates in building our own classes.

```c++
template <typename T>
class List {
  ...
  private:
    T data_;
}
```

Or when building functions:

```c++
template <typename T>
int max(T a, T b) {
  if (a > b) { return a; }
  return b;
}
```

## Compile-Time Binding

Templated variables are checked at compile time, which allows for errors to be caught before running the program:

```c++
template <typename T>
T max(T a, T b) {
  if (a > b) { return a; }
  return b;
}

// max(4, 7); => OK
// max(Cube(3), Cube(6)); => !! Error (unless we've overridden operator::> in our Cube class)
```

See the [example code](../../example_code/cpp-templates/) for more details.
