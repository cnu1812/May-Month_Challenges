
Given instructions for john are "<<<<<<><><><><<<<><><><><><<<<><><><><><>>>><<><><><><><><><><>>>><<<<<><><><><><<<<<><><><><><><<<<><><><><><><><><><><><<<<<<><><<><><>>><<>><<><<>><><<><><><><><><><<<<<<<<<>><<><><<<><><><><<<<<<>>>>>>>>>>><>><><><>><<<><><><><<><><<><><><><><><><<<<><><><>><<>>>>><><><>><<<><><><><><><>><><><><><><><><><><><><><><><><><<<><><><><><><><><><><><><><><><><><>>>><><><><><><><><><>><<<<<<<<<<>>>>><<<<<>>>><<<<>><<><<><><><><><><><><><><<<<<<<><><<><<><<><<><><><><><<>><><>><><><><><<><<<<<>><<<<><><<<><>>><<><>>>>><>>><<><<><><><><<>><><><><><><><><><><><><><><><><<<<><><<<<><<<>>>>>>>>><<><<<>>>>><<<<<<<<<>>>><<><>><><<><<>><<>><<>><"

- The value of "<" is +1
- The value of ">" is -1

Counting the frequency of both the chars we can achieve the answer.

The time complexity taken by the algo is **O(1)**


### Code 

```
instruction ="<<<<<<><><><><<<<><><><><><<<<><><><><><>>>><<><><><><><><><><>>>><<<<<><><><><><<<<<><><><><><><<<<><><><><><><><><><><><<<<<<><><<><><>>><<>><<><<>><><<><><><><><><><<<<<<<<<>><<><><<<><><><><<<<<<>>>>>>>>>>><>><><><>><<<><><><><<><><<><><><><><><><<<<><><><>><<>>>>><><><>><<<><><><><><><>><><><><><><><><><><><><><><><><><<<><><><><><><><><><><><><><><><><><>>>><><><><><><><><><>><<<<<<<<<<>>>>><<<<<>>>><<<<>><<><<><><><><><><><><><><<<<<<<><><<><<><<><<><><><><><<>><><>><><><><><<><<<<<>><<<<><><<<><>>><<><>>>>><>>><<><<><><><><<>><><><><><><><><><><><><><><><><<<<><><<<<><<<>>>>>>>>><<><<<>>>>><<<<<<<<<>>>><<><>><><<><<>><<>><<>><"

num_lt = instruction.count("<")
num_gt = instruction.count(">")
floor = num_lt - num_gt

print(f"John ended up on floor {floor}.")

```

### Output

```
John ended up on floor 56.

```