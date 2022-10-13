# Stack Memory and Pointers

Every variable in C++ has four things:

1. A type
2. A name
3. A value
4. A location in memory ("memory address")

We covered the first three last week. This week we'll look at the fourth.

The following code snippet uses the `&` operator to print out the memory address of a variable with the _name_ `num` that has the _type_ `int` and the _value_ `7`.

```c++
#include <iostream>

int main() {
  int num = 7;

  std::cout << "Value: " << num << std::endl;
  std::cout << "Address: " << &num << std::endl;

  return 0;
}
```

This gives us output similar to the following:

```bash
Value: 7
Address: 0x7ffee26f7e94
```

The address given to us is for a location on **the stack** and is in hexadecimal. We expect this number to be very high (i.e. there are a lot of hexadecimal digits) because that is an attribute of memory addresses on the stack.

By _default_, every variable in C++ is placed in **stack memory**. Stack memory is **associated with the current function** and the memory's lifecycle is tied to the function, i.e. when the function returns or ends, the stack memory of that function is released.

> Note to self: I wonder if this is the thing that underlies scoping in programming languages? If a variable is local to a function then its memory address is within, or tied to, the area in memory managed by that function. If it is global then perhaps it lies within memory managed by the whole application? Does this then mean that closures are in effect just an area of memory that is managed by the closure at the time of instantiation?

Stack memory always _starts from high addresses and grows down_. In the following code example we initialize `num` as in the first example, but then we call the function `foo()` which creates another variable `x`. We expect the memory address of `x` to be lower than that of `num`.

```c++
#include <iostream>

void foo() {
  int x = 42;
  std::cout << " x in foo(): " << x << std::endl;
  std::cout << "&x in foo(): " << &x << std::endl;
}

int main() {
  int num = 7;
  std::cout << " num in main(): " << num << std::endl;
  std::cout << "&num in main(): " << &num << std::endl;
  return 0;
}
```

This gives us the output:

```bash
 num in main(): 7
&num in main(): 0x7ffc605d9fd4  # 140721925234644 in decimal
 x in foo(): 42
&x in foo(): 0x7ffc605d9fb4     # 140721925234612 in decimal
```

The last two digits are the only difference, which gives us `44` for `num` and `12` for `x`, proving that the first variable that was initialized (`num`) gets the higher memory address.

## Pointers

A **pointer** is a variable that stores the memory address of the data. Simply put, _pointers are a level of indirection from the data_. In C++ a pointer is defined by adding a `*` to the **type** of the variable.

```c++
int * p = &num;  // an integer pointer
```

Given that a pointer stores the _memory location_ of a variable and not the _value_, we need a shorthand way of retrieving the value from the pointer. We can do this using the **dereference operator**, also a `*`. This will follow the pointer to the memory address and retrieve the value.

```c++
int num = 7;
int * p = &num;
int value_in_num = *p;  // 7
p* = 42;                // this reassigns num to be 42 as this is where p* points
```

> Note that the _pointer type_ is `int *` (with a space) and the _dereference operator_ is `*p` (without a space).
