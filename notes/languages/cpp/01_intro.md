# Introduction

## Types

- C++ is **strongly typed**
- This means that every variable has
  - A **type**
  - A **name**
  - A **value**
  - A **location in memory**
- There are only two kinds of types that a variable can have
  - A **primitive** type defined by the language
  - A **user-defined** type (this can include types made available through the standard library)
- There are 6 commonly used **primitive types**
  - integer
  - character (represents a _single byte_)
  - boolean
  - float (a single-precision float, i.e. float32)
  - double (a double-precision float, i.e. float64)
  - void (denotes the absence of a value)
- This is not an exhaustive list but all that we need to cover for now
- **User-defined types** can be defined by us, by other 3rd party libraries or by the C++ standard library (called STL - Standard Template Library). Essentially any type that is not a primitive.
  - Two common user-defined types:
    - `std::string` a string (sequence of characters)
    - `std::vector` a dynamically-growing array
  - Note that the standard library needs to be implemented by the creators of your operating system and compiler.
  - The **user-defined types** in the standard library are built in the exact same way that we build our own user-defined types.

## Running a C++ program

- Every C++ program uses a main function `int main()` as its starting point. This function returns an integer. By convention, the return value is `0` if the program was successful and non-zero on errors.
