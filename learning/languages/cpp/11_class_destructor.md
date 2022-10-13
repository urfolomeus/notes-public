# Class Destructor

When an instance of a class is cleaned up, the _class destructor_ is the last call in a class's lifecycle.

## Automatic Default Destructor

An _automatic default destructor_ is added to your class if no other destructor is defined. The only action of the automatic default destructor is to call the default destructor of all member objects.

The compiler will add automatic default destructors anywhere that there are no custom destructors defined.

Destructors **should never** be called directly. Instead they are called automatically when an object's memory is being reclaimed by the system:

- If the object is on the _stack_, this happens when the function that owns the variable's scope returns
- If the object is on the _heap_, this happens when `delete` is used

## Custom Default Destructor

To add custom behaviour to the end-of-life of the object, a custom destructor can be defined as:

- A member function
- With the name of the class preceded by a tilde `~`
- With zero arguments and no return type

```c++
Cube::~Cube();
```

See [example code](../../example_code/cpp-dtor/) for example of this.

## Using custom destructors

A custom destructor is **essential** when an object allocates an external resource that must be closed or freed when the object is destroyed. For example:

- Heap memory
- Open files
- Shared memory
