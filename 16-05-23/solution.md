**Given:** The start state

```
XXXX.
X....
X..X.
.X.X.
XX.XX

```
**Find:** The lifeform score for the first layout that appears twice

## Time Complexity

calculate_lifeform_score function:

- It iterates over the layout string once, which has a length of 25 (5x5 grid). Hence, the time complexity is O(25) or O(1).
find_first_duplicate_layout function:

- It uses a while loop that continues until the layout is found in the seen_layouts set. In the worst case, where the duplicate layout is found after iterating through all possible layouts, the number of iterations will be bounded by the total number of possible layouts, which is 2^25. Therefore, the worst-case time complexity is O(2^25) or approximately O(33 million).

Overall, the time complexity of the entire code is dominated by the find_first_duplicate_layout function, resulting in a worst-case time complexity of O(2^n*n).

## Code

```
# Online Python compiler (interpreter) to run Python online.
# Write Python 3 code in this online editor and run it.
def calculate_lifeform_score(layout):
    score = 0
    for i in range(len(layout)):
        if layout[i] == 'X':
            score += 2 ** i
    return score

def find_first_duplicate_layout(layout):
    seen_layouts= set()
    t = 0 
    while layout not in seen_layouts:
        seen_layouts.add(layout)
        
        next_layout = ""
        for i in range(len(layout)):
            num_lifeforms = 0
            for dx, dy in [(0, 1), (0, -1), (1, 0), (-1, 0)]:
                x = i % 5
                y = i // 5
                nx = x + dx
                ny = y + dy
                if 0 <= nx < 5 and 0 <= ny < 5 and layout[ny * 5 + nx] == 'X':
                    num_lifeforms += 1
            if layout[i] == 'X' and num_lifeforms == 1:
                next_layout += 'X'
            elif layout[i] == '.' and (num_lifeforms == 1 or num_lifeforms == 2):
                next_layout += 'X'
            else:
                next_layout += '.'
        layout = next_layout
        
    return layout

start_state = [
"XXXX."
 "X...."
"X..X."
".X.X."
"XX.XX"
]

layout = "".join(start_state)

duplicate_layout = find_first_duplicate_layout(layout)
lifeform_score = calculate_lifeform_score(duplicate_layout)

print("Duplicate layout:")
for i in range(0, len(duplicate_layout), 5):
    print(duplicate_layout[i:i+5])
print("Lifeform score:", lifeform_score)
```
## Output

` Lifeform score: 32509983 `