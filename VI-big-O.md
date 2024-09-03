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

// n = 40 (6)
// 40, 1, 40 guess = 20
// 40, 1, 19 guess = 10
// 40, 1, 9 guess = 5
// 40, 6, 9 guess = 7
// 40, 6, 6 guess = 6

The recursion happens log(n) times. So O(log n).
Note from the book solution: this is binary search.
