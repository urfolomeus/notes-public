# Copy Constructors

A copy constructor is used whenever we have to instantiate a new instance of a class that is a copy of an existing instance. There are several scenarios where this is required including:

- passing an object as a value into a function as a param (this means that the object needs to be copied as it will be being used in a new scope)
- returning an object as a value from a function (again this means that the object will be used in a new scope and so needs to be copied)

## Automatic Copy Constructor

Just like the _automatic default constructor_, which is used when instantiating an object of the class, the _automatic copy constructor_ is used by the class when copying an object if a _custom copy constructor_ has not been provided. This will copy the values of all member variables from the existing object to the copy.

## Custom Copy Constructor

To create a _custom copy constructor_ the following two things must be true:

1. It must obey all the rules of a normal constructor
2. It must take a single parameter, which must be a constant reference of the same type as the class

```c++
Cube::Cube(const Cube & obj)
```

See [the copy constructor example code](../../example_code/cpp-cctor/) for an example.
