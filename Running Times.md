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

| Operation | Running time in O(n) | Time |
| ----------- | ----------- | ----------- |
|Appendiung to a list, vector or deqeue|O(1)          |  "Constant Time" |
|Pushing to a list or deqeue|O(1)          |  "Constant Time" |
|acceseeing and element of a list, vector or deqeue|O(1)          |  "Constant Time" |
||||
||||
||||
|single for loop|O(n)          |  "Linear Time"|
|Disjoint Set Union()|O(n)          |  "Linear Time"|
|creating a vector or list or deque of n elements|O(n)          |  "Linear Time"|
|traversing a set or map|O(n)          |  "Linear Time"|
|deleting or inseting an element into a vector |O(n)          |  "Linear Time"|
||||
||||
||||
|Double nested for loop|O(n^2)        |  "Quadratic Time"|
||||
||||
||||
|Inserting, finding and deleting elements in sets and maps|O(log(n))     |  "log time"|
|Disjoint Sets Find() in union by size or height|O(log(n))     |  "log time"|
||||
||||
||||
|creating sets and maps with n elements|O(n*log(n))   |  "N log N"|
|sorting a vector of n elements|O(n*log(n))   |  "N log N"|
||||
||||
||||
|Find() in Union by rank with path compression|O(α(n))       |  "Inverse Ackerman, (basically constant time)"|