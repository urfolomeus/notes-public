# Copy Assignment Operator

In C++, a _copy assignment operator_ defines the behaviour when an object is copied using the _assignment operator_ `=`. Whilst a _copy constructor_ creates a new ojbect that is a copy of an existing object, an _assignment operator_ assigns a value to an existing object. As such a constructor is not needed. In fact, the assignment operator can _only be called_ on an existing object.

## Automatic copy assignment operator

If we do not define a copy assignment operator for a class, C++ will create a _default assignment operator_ for us. This will copy the values of all member variables.

## Custom copy assignment operator

We can create a custom copy assignment operator as long as it has the following properties:

- is a public member function of the class
- has the _exact_ function name `operator=`
- has a return value of a reference to the class' type
- has exactly one argument, which must be a const reference of the class' type

```c++
Cube & Cube::operator=(const Cube & obj)
```

See [the example code](../../example_code/cpp-assignmentOp/) for some examples.
