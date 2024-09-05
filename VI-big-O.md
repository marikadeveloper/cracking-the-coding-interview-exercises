### VI.1 The following code computes the product of a and b. What is its runtime?

```c
int product(int a, int b) {
  int sum = 0;
  for (int i = 0; i < b; i++) {
    sum += a;
  }
  return sum;
}
```

#### Solution

O(b) because the loop iterates from i = 0 to i = b so b times.

### VI.2 The following code computes a^b. What is its runtime?

```c
int power(int a, int b) {
  if (b < 0) return 0;
  else if (b == 0) return 1;
  else return a * power(a, b - 1);
}
```

#### Solution

O(b) because the recursion happens b times, since b keeps being decremented by 1.

### VI.3 The following code computes a % b. What is its runtime?

```c
int mod(int a, int b) {
  if (b <= 0) return -1;
  int div = a / b;
  return a - div * b;
}
```

#### Solution

O(1) since we're doing constant work, no loops no recursive calls.

### VI.4 The following code performs integer division. What is its runtime (assuming a and b are positive)?

```c
int div(int a, int b) {
  int count = 0;
  int sum = b;
  while (sum <= a) {
    sum += b;
    count++;
  }
  return count;
}
```

#### Solution

O( a/b ), for example if we do 10/2, the while loop will go on 5 times.
If we do 9/3 it will run 3 times instead.

### VI.5 The following code computes the integer square root of a number. If the nr is not a perfect square (no integer square root), it returns -1. It does this by successive guessing. If n is 100, it first guesses 50. Too high? Try something lower - halfway between 1 and 50. What is its runtime?

```c
int sqrt(int n) {
  return sqrt_helper(n, 1, n);
}

int sqrt_helper(int n, int min, int max) {
  if (max < min) return -1; // no square root

  int guess = (min + max) / 2;
  if (guess * guess == n) { // found it!
    return guess;
  } else if (guess * guess < n) { // too low
    return sqrt_helper(n, guess + 1, max); // try higher
  } else { // too high
    return sqrt_helper(n, min, guess - 1); // try lower
  }
}
```

#### Solution

// n = 100 (10)
// 100, 1, 100 guess = 50
// 100, 1, 49 guess = 25
// 100, 1, 24 guess = 13
// 100, 1, 12 guess = 7
// 100, 8, 12 guess = 14
// 100, 8, 11 guess = 9
// 100, 10, 11 guess = 10

The recursion happens log(n) times. So O(log n).
Note from the book solution: this is binary search.

### VI.6 The following code computes the integer square root of a number. If the number is not a perfect square then it returns -1. It does this by trying increasingly large numbers until it finds the right value (or is too high). What is its runtime?

```c
int sqrt(int n) {
  for (int guess = 1; guess * guess <= n; guess++) {
    if (guess * guess == n) {
      return guess;
    }
  }
  return -1;
}
```

#### Solution

guess \* guess = n is saying that guess goes up to the square root of n.
Therefore this is O(sqrt(n)).

### VI.7 If a binary search tree is not balanced, how long might it take (worst case) to find an element in it?

O(N). We might have only one branch and have to find the leaf deep down and visit each node once.

### VI.8 You are looking for a specific value in a binary tree, but the tree is not a binary search tree. What is the time complexity of this?

O(N) we might be in the situation of a tree having only one branch. Without any order anyways we might have to visit every node before finding the right one. Like having a library catalogue not in alphabetical order.

### VI.9 The appendToNew method appends a value to an array by creating a new, longer array and returning this longer array. You've used the appendToNew method to create a copyArray function that repeatedly calls appendToNew. How long does copying an array take?

```c++
int[] copyArray(int[] array) {
  int[] copy = new int[0];
  for (int value : array) {
    copy = appendToNew(copy, value);
  }
  return copy;
}

int[] appendToNew(int[] array, int value) {
  // copy all elements over to new array
  int[] bigger = new int[array.length + 1];
  for (int i = 0; i < array.length; i++) {
    bigger[i] = array[i];
  }

  // add new element
  bigger[bigger.length - 1] = value;
  return bigger;
}
```

### Solution

We are creating a new array of size value+1 for each value of the input array. This is O(N^2).
