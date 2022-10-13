# C++ Classes

C++ classes encapsulate data and associated functionality into an object

```c++
class Cube {
  public:
    double getVolume();
    // ...

  private:
    double length_;
};
```

## Encapsulation

**Encapsulation** encloses data and functionality into a single unit (called a class).

Data: `length_` (`_` suffix denotes private)
Functionality: `getVolume()`

There are two axes to consider in a C++ class: data vs functionality and public vs private. The later is referred to as the protection layer.

Public == anyone can access
Private == can only be accessed by the class itself

In C++ there is another layer to consider. The **interface** to the class (i.e. the description of how things can be accessed by client code) is defined separately from the **implementation** of the class (i.e. the code that defines how the class works). The interface is written in a `.h` header file and the implementation is written in a `.cpp` file.

### Header file

Defines the interface to the class, which includes:

- declaration of _all_ member variables
- declaration of _all_ member functions

but does not contain the implementation.

Example:

```c++
// always include the next line in a header file
// instructs the compiler to only compile this file once
// even if multiple people use our class we'll only want
// the definition of the class to be defined exactly once
#pragma once

class Cube {
  // public protection layer
  public:
    double getVolume();
    double getSurfaceArea();
    void setLength(double length);

  // private protection layer
  private:
    double length_;
};
```
