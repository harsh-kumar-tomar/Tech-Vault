# Heap Methods
``
```python
arr = [5, 3, 8, 1]
heapq.heapify(arr)
print(arr)  # Output: [1, 3, 8, 5] (min-heap structure)

# push
heapq.heappush(arr, 2)
# pop
min_item = heapq.heappop(arr) # 1

result = heapq.heappushpop(arr, 0) # pop item and pushes 0

```

# Binary Search

```python
import bisect
	 0  1  2  3  4
a = [1, 3, 4, 4, 5]

# returns index where it is can be inserted 
# it does not inserts the value

i = bisect.bisect_left(arr, 4) # 2
i = bisect.bisect_right(arr, 4) # 4


# doent return  any index
bisect.insort_left(arr, 4) #  insert left 
bisect.insort_right(a, 4) # insert right

```


# Queue

```python
from queue import Queue

q = Queue()  # Optional maxsize, default is infinite

q.put(10)
q.put(20)

x = q.get() # 10

print(q.qsize())  # 1 (only 20 left)
print(q.empty())  # False

```

# Deque

```python
from collections import deque

dq = deque()
dq.append(10)
dq.append(20)

print(dq)  # deque([10, 20])

dq.appendleft(5)
print(dq)  # deque([5, 10, 20])

val = dq.pop() # 20
val = dq.popleft() # 5

dq.clear() # deque([])
len(dq)

```
# Fast IO

```python
import sys
input = sys.stdin.readline
# reassigning with faster method 

# input
s = input().strip()  # removes \n and whitespace

# output
sys.stdout.write(str(123) + "\n")

# faster output with join()
print(" ".join(map(str, arr)))  # Output: 1 2 3 4

```

# default dict

```python
from collections import defaultdict

# for normal case
count = defaultdict(int)

arr = [1, 2, 1, 3, 2, 1]
for num in arr:
    count[num] += 1

print(count)  # defaultdict(<class 'int'>, {1: 3, 2: 2, 3: 1})


# for graphs 
graph = defaultdict(list)

edges = [(1, 2), (2, 3), (1, 3)]
for u, v in edges:
    graph[u].append(v)
    graph[v].append(u)

print(graph)

# for sets

d = defaultdict(set)
d['a'].add(1)
d['a'].add(2)
d['b'].add(1)
print(d)

```