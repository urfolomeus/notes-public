# Variable Storage

In C++, an instance of a variable can be stored directly in memory, accessed by a pointer, or accessed by a reference.

```c++
Cube c           // directly in memory
Cube *ptr = &c;  // as a pointer `*`
Cube &ref = c;   // as a reference `&`
```

## Direct Storage

By default, variables are stored directly in memory.

- the _type_ of a variable has no modifiers (i.e. no `*` or `&`)
- the object takes up _exactly its size_ in memory

```c++
Cube c;            // stores a Cube in memory
int i;             // stores an integer in memory
uiuc::HSLAPixel p;  // stores a pixel in memory
```

## Storage By Pointer

- The _type_ of a variable is modified with an asterisk `*`
- A pointer takes a "memory address width" of memory (i.e. 64 bits on a 64-bit system)
- The pointer "points" to the allocated space of the object

```c++
Cube *c;             // pointer to a Cube in memory
int *i;              // pointer to an integer in memory
uiuc::HSLAPixel *p;  // pointer to a pixel in memory
```

## Storage By Reference

- A reference is an _alias_ to existing memory
- The _type_ of a variable is modified with an ampersand `&`
- A reference _does not store memory itself_, it is only an alias to another variable
- The alias must be assigned when the variable is initialized

```c++
Cube &c = cube;      // alias to the variable `cube`
int &i = count;      // alias to the variable `i`
uiuc::HSLAPixel &p;  // Illegal! Must alias something when variable is initialized
```

### Example: Cube Currency

1. A cube is worth its volume in currency (i.e. a cube of length 1 == CUR1, a cube of length 5 == CUR125)
2. When we receive money, we want the cube itself - not a copy of the cube (otherwise we're creating inflation)

See [the example code](../../example_code/cpp-memory2/) for the working example.

Some things to look out for:

- In ex2, when we send via reference, we still call the `sendCube()` function passing in the object, however the function signature takes a _reference_ to the object, not the object itself, and so no copying takes place

  ```c++
  bool sendCube(Cube & c) {
    // ...
  }

  int main() {
    //...
    sendCube(c);
    //...
  }
  ```

- In ex2, when we send via pointer, the `sendCube()` function now takes a _pointer_ to the object and so we have to pass in the memory address of the object rather than the object itself

  ```c++
  bool sendCube(Cube * c) {
    // ...
  }

  int main() {
    // ...
    sendCube(&c);
    // ...
  }
  ```

I'm not sure which, if either, is the better approach. My instinct would be to prefer the pointer for the following reasons:

1. `sendCube` would error if we did not send the object's memory address, thus being more explicit about what was going on. If it "silently" converted an object to its reference we may introduce a bug at some point if we were unaware of that behaviour.
2. A pointer is clearly a reference to the memory address of another object. An alias seems to me like it might be easy to confuse as an object in its own right. That might be down to lack of experience or an incorrect understanding of what's going on on my part though.

**UPDATE** In the [assignment README]() for week 4 it states:

> It means that a direct reference to the memory is being passed, which uses the same concept of indirection that pointers offer, but with a simple syntax—you just use the variable as you would normally, not by dereferencing a memory address explicitly with the \* operator as pointers do, and yet you are still able to implicitly manipulate the data located at the original memory location. This convenience feature was one of the benefits of C++ over the older C language.

So this is saying that the two mechanisms are essentially the same but the reference is "simpler" to work with because it implicitly does the right thing. I'm not sure that I agree here having been semi-regularly bitten by "magic" code like this in the past.

## Return by ...

Values can be returned in all three ways as well:

- Return by _value_ (default)
- Return by _pointer_ (modified with `*`)
- Return by _reference_ (modified with `&`, acts as an alias)

**Remember** _never_ return a reference to a stack variable created on the stack of your current function! It will be out of scope, and therefor removed, before you can use it.
