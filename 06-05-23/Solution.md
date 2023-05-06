
Here are the descriptions of this group of friends:
1) John can run 10 m/s for 6 seconds, but then must rest for 20 seconds
2) James can run 8 m/s for 8 seconds, but then must rest for 25 seconds
3) Jenna can run 12 m/s for 5 seconds, but then must rest for 16 seconds
4) Josh can run 7 m/s for 7 seconds, but then must rest for 23 seconds
5) Jacob can run 9 m/s for 4 seconds, but then must rest for 32 seconds
6) Jerry can run 5 m/s for 9 seconds, but then must rest for 18 seconds

After 1234 seconds, what is the distance of the winning runner?

Time Complexity for this algo is **O(n)**

### Code 

```python
def distance_covered(speed, run_time, rest_time, total_time):
    distance = 0
    while total_time > 0:
        if total_time >= run_time:
            distance += speed * run_time
            total_time -= run_time
        else:
            distance += speed * total_time
            total_time = 0
        total_time -= rest_time
    return distance

runners = [
    {'name': 'John', 'speed': 10, 'run_time': 6, 'rest_time': 20},
    {'name': 'James', 'speed': 8, 'run_time': 8, 'rest_time': 25},
    {'name': 'Jenna', 'speed': 12, 'run_time': 5, 'rest_time': 16},
    {'name': 'Josh', 'speed': 7, 'run_time': 7, 'rest_time': 23},
    {'name': 'Jacob', 'speed': 9, 'run_time': 4, 'rest_time': 32},
    {'name': 'Jerry', 'speed': 5, 'run_time': 9, 'rest_time': 18}
]

distances = {runner['name']: distance_covered(runner['speed'], runner['run_time'], runner['rest_time'], 1234) for runner in runners}

winner = max(distances, key=distances.get)

print(f"The winner is {winner} with a distance of {distances[winner]} meters.")

```

### Output

```
The winner is Jenna with a distance of 3540 meters.

```
