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
