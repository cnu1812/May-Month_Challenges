Given an integer string, create all integer permutations of its digits. Determine if there is a
permutation whose integer value is evenly divisible by 7, i.e. (permutation value) mod 7 = 0.

For example, the possible permutations of 789 are p = {789, 798, 879, 897, 978, 987}. Of
these values, p[2] and p[6] are divisible by 7 because 798 mod 7 = 0 and 987 mod 7 = 0.
Their average is (798 + 987) / 2 = 892.5

What we need to do is determine if any of the permutations of 1867 are divisible by 7, and
if so, what is the average between the smallest and largest permutation? Decimals are
allowed.

### Complexity

In the worst case, where there are no divisible permutations, the time complexity of this code is O(n!). In the best case, where the first permutation is divisible by 7, the time complexity is O(n). In practice, the time complexity will typically be somewhere in between these two extremes, depending on the input integer string.

Therefore, the time complexity of this code can be expressed as O(n!) in the worst case and O(n*k) in the best case, where k is the number of divisible permutations.

### Code

```python
from itertools import permutations

num_str = '1867'

divisible_perms = list(filter(lambda x: int(''.join(x)) % 7 == 0, permutations(num_str)))
if divisible_perms:
    avg = (int(''.join(min(divisible_perms))) + int(''.join(max(divisible_perms)))) / 2
    print(f"The average of the smallest and largest permutations is {avg:.2f}.")
else:
    print("There are no permutations that are divisible by 7.")
```

### Output

```
The average of the smallest and largest permutations is 5152.00.
```

