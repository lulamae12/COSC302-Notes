# Running Times - Big O - O(n)
lecture notes link: http://web.eecs.utk.edu/~jplank/plank/classes/cs202/Notes/BigO/index.html


## Terminology

| Operation | Name |
| ----------- | ----------- |
|O(1)          |  "Constant Time" |
|O(n)          |  "Linear Time"|
|O(n^2)        |  "Quadratic Time"|
|O(log(n))     |  "log time"|
|O(n*log(n))   |  "N log N"|
|O(α(n))       |  "Inverse Ackerman, (basically constant time)"|

## Running Times Table

## O(1) - Constant Time
| Operation | Running time in O(n) | Time |
| ----------- | ----------- | ----------- |
|Appending to a list, vector or deqeue|O(1)          |  "Constant Time" |
|Pushing to a list or deqeue|O(1)          |  "Constant Time" |
|Accessing an element of a list|O(1)          |  "Constant Time" |
|Accessing an element of a vector|O(1)          |  "Constant Time" |
|Accessing an element of a deqeue|O(1)          |  "Constant Time" |
## O(n) - Linear Time:
| Operation | Running time in O(n) | Time |
| ----------- | ----------- | ----------- |
|Single for loop|O(n)          |  "Linear Time"|
|Disjoint Set Union()|O(n)          |  "Linear Time"|
|Creating a vectorof n elements|O(n)          |  "Linear Time"|
|Creating a list of n elements|O(n)          |  "Linear Time"|
|Creating a deque of n elements|O(n)          |  "Linear Time"|
|Traversing a set or map|O(n)          |  "Linear Time"|
|Inserting an element into a vector |O(n)          |  "Linear Time"|
|Deleting an element in a vector |O(n)          |  "Linear Time"|
## O(n^2) - Quadratic Time:
| Operation | Running time in O(n) | Time |
| ----------- | ----------- | ----------- |
|Double nested for loop|O(n^2)        |  "Quadratic Time"|
## O(log(n)) - Log Time:
| Operation | Running time in O(n) | Time |
| ----------- | ----------- | ----------- |
|Inserting elements into a set|O(log(n))     |  "log time"|
|Finding elements in a set|O(log(n))     |  "log time"|
|Deleting elements in a set|O(log(n))     |  "log time"|
|Inserting elements into a map|O(log(n))     |  "log time"|
|Finding elements in a map|O(log(n))     |  "log time"|
|Deleting elements in a map|O(log(n))     |  "log time"|
|Disjoint Sets Find() in union by size|O(log(n))     |  "log time"|
|Disjoint Sets Find() in union by height|O(log(n))     |  "log time"|
## O(n * log(n)) - n * log(n) Time:
| Operation | Running time in O(n) | Time |
| ----------- | ----------- | ----------- |
|Creating a set with n elements|O(n*log(n))   |  "N log N"|
|Creating a map with n elements|O(n*log(n))   |  "N log N"|
|Sorting a vector of n elements|O(n*log(n))   |  "N log N"|
## O(α(n)) - Inverse Ackerman, (basically constant time):
| Operation | Running time in O(n) | Time |
| ----------- | ----------- | ----------- |
|Find() in Union by rank with path compression|O(α(n))       |  "Inverse Ackerman, (basically constant time)"|