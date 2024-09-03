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
