# Heap Memory

**Heap memory** allows us to create memory independent of the lifesycle of a function. In C++, if memory needs to exist for longer than the lifecycle of the function, we _must_ use heap memory. The _only_ way to create heap memory in C++ is with the `new` operator. The `new` operator returns a **pointer** to the memory storing the data, _not_ an instance of the data itself.

The `new` operator will always do three things:

1. Allocate memory on the heap for the data structure
2. Initialize the data structure
3. Return a pointer to the start of the data structure

The memory is _only ever_ reclaimed by the system when the pointer is passed to the `delete` operator.

The code below allocates two chunks of memory:

```c++
int * numPtr = new int;
```

- `int * numPtr` creates a variable named _numPtr_ on **the stack** (because we don't use the `new` operator on the left-hand side)
- `new int` creates a pointer to a memory address on **the heap** that's large enough to store an integer

Heap memory **starts at a low number and grows up** as opposed to stack memory which **starts at a high number and grows down**.

## `nullptr`

The C++ keyword `nullptr` is a pointer that points to the memory address `0x0`

- represents a pointer to nowhere
- address `0x0` is reserved and never used by the system
- address `0x0` will always generate a _segmentation fault_ when accessed
- calls to _delete_ `0x0` are ignored

Consider the following code:

```c++
int main() {
  int *p = new int;
  Cube *c = new Cube;

  *p = 42;
  (*c).setLength(4);

  delete c;
  delete p;
  return 0;
}
```

When we call `delete c` we relinquish the heap memory that `c` was pointing to. However, we _do not_ get rid of the pointer to that memory address. `c` still contains that memory address even though the data no longer exists there. **This is dangerous**. In order to properly deal with this we need use a `nullptr` like so:

```c++
int main() {
  int *p = new int;
  Cube *c = new Cube;

  *p = 42;
  (*c).setLength(4);

  delete c;  c = nullptr;
  delete p;  p = nullptr;
  return 0;
}
```

> Note that it looks as though this might be redundant in the above example as this is the `main()` function and it returns immediately after we delete `c` and `p`. However, not handling this properly just invites heisenbugs further down the line. Also, classes have their destructors silently called when we delete them, which might be the cause of hard to find bugs if we do not use the `nullptr`.

## Arrow operator `->`

When an object is stored via a pointer, access can be made to member functions using the `->` operator.

You'll notice in the above code example the line `(*c).setLength(4);`. This is done so that we first resolve `*c` to get the `Cube` instance and then call the `setLength()` function on it. The parentheses in this scenario are purely to ensure precendence. We should never write code like this normally. We should instead use the **arrow operator** `->` like so:

```c++
c->setLength(4);
```
