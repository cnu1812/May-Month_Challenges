**Given:** “kjslaqpwoereeeeewwwefifjdksjdfhjdksdjfkdfdlddkjdjfjfjfjjjjfjffnefhkjgefkgjefkjgkefjekihutrieruhi
gtefhgbjkkkknbmssdsdsfdvneurghiueor”

**Prove:** The minimum number of steps required to delete this series


## Time Complexity

**Time Complexity:** O(N*N), as we are using a loop to traverse N times and in each traversal we are recursively calling the function which will cost O(N) time. Where N is the length of the string.

Overall, the time complexity of the provided code is **O(n^2)**, where n is the length of the series string.

## Code

```

def findMinimumDeletion(l, r, dp, s):
 
    if l > r:
        return 0
    if l == r:
        return 1
    if dp[l][r] != -1:
        return dp[l][r]
 
    
    res = 1 + findMinimumDeletion(l + 1, r,
                                     dp, s)
 
    for i in range(l + 1, r + 1):
 
        if s[l] == s[i]:
            res = min(res, findMinimumDeletion(l + 1, i - 1, dp, s) +
                           findMinimumDeletion(i, r, dp, s))
     
    # Memoize
    dp[l][r] = res
    return res
 
if __name__ == "__main__":
 
    s = "kjslaqpwoereeeeewwwefifjdksjdfhjdksdjfkdfdlddkjdjfjfjfjjjjfjffnefhkjgefkgjefkjgkefjekihutrieruhigtefhgbjkkkknbmssdsdsfdvneurghiueor"
    n = len(s)
    N = 131
    dp = [[-1 for i in range(N)]
              for j in range(N)]
    print(findMinimumDeletion(0, n - 1, dp, s))
```

## Output

`78`
