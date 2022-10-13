# Inheritance

**Inheritance** allows a class to inherit all member functions and data from a _base class_ into a _derived class_.

## Initialization

When a derived class is initialized, the derived class _must_ construct the base class:

- `Cube` must construct `Shape`
- uses default constructor if custom one not provided
- custon constructor can be provided with an **initialization list**

## Access Control

When a _base class_ is inherited, the _derived class_:

- **Can access** all _public_ members of the base class
- **Can not access** any _private_ members of the base class

## Initializer List

The syntax to initialize the base class is called the _initializer list_ and can be used for several different purposes:

- Initializing a base class
- Initializing the derived class using another constructor
- Initializing the default values of member variables

## Example

See the [example code](../../example_code/cpp-inheritance/) for more details.

```c++
// Shape.cpp
# include "Shape.h"

Shape::Shape() : Shape(1) {
  // Nothing
}

Shape::Shape(double width) : width_(width) {
  // Nothing
}

double Shape::getWidth() const {
  return width_;
}

// Cube.h
#include "Shape.h"
#include "HSLAPixel.h"

namespace uiuc {
  class Cube : public Shape {
    public:
      Cube(double width, uiuc::HSLAPixel color);
      double getVolume() const;

    private:
      uiuc::HSLAPixel color_;
  }
}

// Cube.cpp
#include "Cube.h"
#include "Shape.h"

namespace uiuc {
  Cube::Cube(double width, uiuc::HSLAPixel color) : Shape(width) {
    color_ = color;
  }

  double Cube::getVolume() const {
    // Cannot access Shape::width_ due to it being "private"
    // ...instead we use the public Shape::getWidth() function

    return getWidth() * getWidth() * getWidth();
  }
}
```
