# Class constructors

## Automatic Default Constructor

If we do not explicitly provide a class constructor, C++ will implicitly call the default constructor, which just initializes all variables to their default values. If _any_ custom constructors exist then an automatic default constructor is _not_ defined.

## Custom Default Constructor

Defined as a member function with the same name as the class.

- Takes no parameters
- Does not return
- Provides custom default values for member variables

```c++
// Cube.h
class Cube {
  public:
    Cube(); // Custom default constructor
    double getVolume();

  private:
    double length_;
};

// Cube.cpp
#include "Cube.h"

Cube::Cube() {
  length_ = 1;
}

double Cube::getVolume() {
  return length_ * length_ * length_;
}

// main.cpp
#include <iostream>
#include "Cube.h"

int main() {
  Cube c;
  std::cout << "Volume: " << c.getVolume() << std::endl;
  return 0;
}
```

## Custom Constructor

Defined as a member function with the same name as the class. Unlike the custom _default_ constructor, the custom constructor allows us to pass in parameters that we can then use when initializing the variables.

We can include both a default constructor and a constructor.

```c++
// Cube.h
class Cube {
  public:
    Cube();               // custom default constructor
    Cube(double length);  // custom single argument constructor
    double getVolume();

  private:
    double length_;
};

// Cube.cpp
#include "Cube.h"

Cube::Cube() {
  length_ = 1;
}

Cube::Cube(double length) {
  length_ = length;
}

double Cube::getVolume() {
  return length_ + length_ + length_;
}

// main.cpp
#include <iostream>
#include "Cube.h"

int main() {
  Cube c(2);
  std::cout << "Volume: " << c.getVolume() << std::endl;
  return 0;
}
```

## If A Matching Constructor Cannot Be Found

If we try to instantiate an object using a constructor that does not exist, the compiler will throw an error. It is important to note that, if we provide a constructor, the default constructor will not exist and therefor we will have to use the constructor(s) that we provided.

For example, the following will throw a compiler error:

```c++
// Cube.h
class Cube {
  public:
    Cube(double length);  // custom single argument constructor
    // ...

  private:
    double length_;
};

// Cube.cpp
#include "Cube.h"

Cube::Cube(double length) {
  length_ = length;
}

// main.cpp
#include <iostream>
#include "Cube.h"

int main() {
  Cube c();  // this will error as the only constructor that we have requires a single argument
  // ...
  return 0;
}
```
