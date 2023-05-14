**Given:** “kjslaqpwoereeeeewwwefifjdksjdfhjdksdjfkdfdlddkjdjfjfjfjjjjfjffnefhkjgefkgjefkjgkefjekihutrieruhi
gtefhgbjkkkknbmssdsdsfdvneurghiueor”

**Prove:** The minimum number of steps required to delete this series


## Time Complexity

- The simplify_series function iterates over each character in the alphabet, which has a constant length of 26. Within the loop, it performs a regular expression substitution using re.sub, which has a time complexity of O(n), where n is the length of the series string. Therefore, the time complexity of this function can be approximated as O(26 * n) = O(n).

- The find_character_with_least_appearances function calls simplify_series, which has a time complexity of O(n). It then iterates over each character in the alphabet, performing a count operation on the simplified string, which has a time complexity of O(n). Therefore, the overall time complexity of this function is O(26 * n) = O(n).

- The disconnect_nodes function repeatedly calls the find_character_with_least_appearances function within a while loop until the series string becomes empty. In the worst case, each call to find_character_with_least_appearances may process the entire length of the series string. Therefore, the time complexity of this function can be approximated as O(n^2).

Overall, the time complexity of the provided code is **O(n^2)**, where n is the length of the series string.

## Code

```
import re

def simplify_series(series):
    for char in 'abcdefghijklmnopqrstuvwxyz':
        series = re.sub(f'{char}+', char, series)
    return series

def find_character_with_least_appearances(series):
    
    simplified = simplify_series(series)
    lowest_count = 0
    character = ''
    for char in 'abcdefghijklmnopqrstuvwxyz':
        count = simplified.count(char)
        if count > 0 and (lowest_count == 0 or count < lowest_count):
            lowest_count = count
            character = char
    return lowest_count, simplified.replace(character, '')

def disconnect_nodes(series):
    total_steps = 0
    while series:
        steps, series = find_character_with_least_appearances(series)
        total_steps += steps
    return total_steps

series = "kjslaqpwoereeeeewwwefifjdksjdfhjdksdjfkdfdlddkjdjfjfjfjjjjfjffnefhkjgefkgjefkjgkefjekihutrieruhigtefhgbjkkkknbmssdsdsfdvneurghiueor"
print(disconnect_nodes(series))
```

## Output

`92`