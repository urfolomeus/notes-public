# Heap Puzzles

This lesson looks at the four puzzle files located in **example_code/cpp-heapPuzzles**.

## puzzle1

> Note that there is no `new` keyword in the following code example so all of these values are going on the stack.

```c++
int main() {
  // initialize 3 integers
  int  i =  2,  j =  4,  k =  8;
  // initialize 3 integer pointers to the above integers
  int *p = &i, *q = &j, *r = &k;

  //  i = 2,  j = 4,  k = 8
  // *p = 2, *q = 4, *r = 8

  k = i;

  //  i = 2,  j = 4,  k = 2
  // *p = 2, *q = 4, *r = 2

  cout << i << j << k << *p << *q << *r << endl;
  // 242242

  p = q;

  //  i = 2,  j = 4,  k = 2
  // *p = 4, *q = 4, *r = 2

  cout << i << j << k << *p << *q << *r << endl;
  // 242442

  *q = *r;

  //  i = 2,  j = 2,  k = 2
  // *p = 2, *q = 2, *r = 2

  cout << i << j << k << *p << *q << *r << endl;
  // 222222

  return 0;
}
```

## puzzle2

> Note that we have a `new` keyword here, so some memory will be on the heap and some will be on the stack.

```c++
int main() {
  // create an integer pointer `*x` on the stack that points to an unassigned integer on the heap
  int *x = new int;
  // alias that unassigned integer on the heap as `y`
  int &y = *x;
  // assign 4 to the integer called `y` on the heap
  y = 4;

  // Stack: *x = &y
  // Heap: y = 4

  cout << &x << endl;
  cout << x << endl;
  cout << *x << endl;

  /**
   * Output
   * 0x77754321 // the memory address of the pointer on the stack
   * 0x12345    // the memory address on the heap that the pointer is pointing to
   * 4          // the dereferenced data stored in the memory address on the heap that `x` is pointing to
   */

  cout << &y << endl;
  cout << y << endl;
  // cout << *y << endl;  // will cause a compiler error because y is not a pointer and so can't be dereferenced

  /**
   * Output
   * 0x12345  // the memory address of `y` on the heap
   * 4        // the value of `y`
   */

  return 0;
}
```

## puzzle3

```c++
int main() {
  // create two pointers on the stack that do not yet point to anything
  int *p, *q;
  // `p` is now set to point to an int on the heap, as yet unassigned
  p = new int;
  // `q` is now set to point to the same memory address as `p`
  q = p;
  // we now assign the value `8` to the int on the heap that both `p` and `q` point to
  *q = 8;
  // prints out the dereferenced value of `p` to the console, will be 8
  cout << *p << endl;

  // `q` is now pointed to a new int on the heap
  q = new int;
  // and the value of that int on the heap is set to 9
  *q = 9;
  // prints out the dereferenced value of `p` to the console, will be 8 as `p` still points to original int on heap
  cout << *p << endl;
  // prints out the dereferenced value of `q` to the console, will now be 9 as points to new int on heap
  cout << *q << endl;

  /**
   * Output
   * 8
   * 8
   * 9
   */

  return 0;
}
```

## puzzle4

The following example shows that we can store an **array** or list of integers on the heap in the same way that we can store a single integer.

```c++
int main() {
  // create a pointer on the stack that does not yet point to anything
  int *x;
  // create an int that will store the size of the array that we want to create
  int size = 3;
  // create an array that can hold 3 integers on the heap and point `x` to it
  x = new int[size];

  // for each "cell" in the array add 3 to the current index and store the value in the cell
  for (int i = 0; i < size; i++) {
    x[i] = i + 3;
  }

  /**
   * Array will look like this in the heap now
   *
   * |...|
   * |---|
   * | 5 |
   * |---|
   * | 4 |
   * |---|
   * | 3 |
   * |---|
   *
   * because the heap is assign from the bottom and grows upwards
   */

  // we need to remember and use the square bracket syntax when deleting `x` from the heap
  // because it is an array, not a single integer
  delete[] x;
}
```
