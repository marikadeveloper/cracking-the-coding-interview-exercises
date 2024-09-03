### VI.1 The following code computes the product of a and b. What is its runtime?

```c++
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
