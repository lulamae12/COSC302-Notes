# Sorting Algorithims

lecture notes link: https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Sorting/


---

# Bubble Sort

Running time: O(n^2)

Bubble sort is "an awful sorting algorithim"

bubble sort works like this:

- run through the elements from the smallest index to the largest
- if the current element is greater than the next element, swap them
- after each iteration of the loop, the largest element will always be at the end
- loop again for the size - 1


code example:

```
void sort_doubles(vector <double> &v, bool print)
{
  int i, j, n;
  double tmp;

  n = v.size();
  for (i = 0; i < n-1; i++) {

    /* This is the inner loop. Each time you perform it, you can stop
       one step closer to the beginning of the vector, because the previous
       iteration has placed the element where it belongs. */

    for (j = 0; j < n-i-1; j++) {   
      if (v[j] > v[j+1]) {
        
        //swap
        tmp = v[j];
        v[j] = v[j+1];
        v[j+1] = tmp;
      }
    }
    // The vector is printed here, but I've omitted the code. 
  }
}
```

```
                 | UNIX> bin/bubble_sort 8 1 14 yes yes
Before the loop: | 3.62 6.14 4.35 3.88 4.12 8.09 6.28 0.72
i = 0            | 3.62 4.35 3.88 4.12 6.14 6.28 0.72 8.09 
i = 1            | 3.62 3.88 4.12 4.35 6.14 0.72 6.28 8.09 
i = 2            | 3.62 3.88 4.12 4.35 0.72 6.14 6.28 8.09 
i = 3            | 3.62 3.88 4.12 0.72 4.35 6.14 6.28 8.09 
i = 4            | 3.62 3.88 0.72 4.12 4.35 6.14 6.28 8.09 
i = 5            | 3.62 0.72 3.88 4.12 4.35 6.14 6.28 8.09 
i = 6            | 0.72 3.62 3.88 4.12 4.35 6.14 6.28 8.09 
```

# Selection Sort
Running time: O(n^2)

selection sort is "an awful sorting algorithim" but can sometimes be useful

best for sorting shuffled cards


selection sort works like this:

- Iteration 0: find the smallest element in the vector, and you swap it with element 0.

- Iteration 1: find the second smallest element in the vector, and you swap it with element 1.

- Iteration 2: find the second smallest element in the vector, and you swap it with element 1.

- Iteration n: find the nth smallest element in the vector, and you swap it with element at n.

You'll note that at iteration i you don't have to look at any of the elements before index i, because they are the smallest elements up to element i. So, at iteration i, you simply look for the smallest element from index i to the end of the vector, and swap that with element i.

Example:
```
                 | UNIX> bin/selection_sort 8 1 13 yes yes
Before the loop: | 4.91 9.10 6.96 9.22 4.24 5.93 1.32 4.50
i = 0            | 1.32 9.10 6.96 9.22 4.24 5.93 4.91 4.50 
i = 1            | 1.32 4.24 6.96 9.22 9.10 5.93 4.91 4.50 
i = 2            | 1.32 4.24 4.50 9.22 9.10 5.93 4.91 6.96 
i = 3            | 1.32 4.24 4.50 4.91 9.10 5.93 9.22 6.96 
i = 4            | 1.32 4.24 4.50 4.91 5.93 9.10 9.22 6.96 
i = 5            | 1.32 4.24 4.50 4.91 5.93 6.96 9.22 9.10 
i = 6            | 1.32 4.24 4.50 4.91 5.93 6.96 9.10 9.22 
```

Example Code:
```
void sort_doubles(vector <double> &v, bool print)
{
  int i, j, k, n;
  double tmp;
  int minindex;

  n = v.size();

  /* Outer loop.  At each of these iterations, we
     are going to find the smallest element from
     index i to the end, and swap it with the
     element in index i.  */
  for (i = 0; i < n-1; i++) {
    
    /* Put the index of the smallest element 
       starting at index i in minindex. */

    minindex = i;
    for (j = i+1; j < n; j++) {
      if (v[j] < v[minindex]) {
        minindex = j;
      }
    }

    /* Now swap v[minindex] with v[i] */

    tmp = v[i];
    v[i] = v[minindex];
    v[minindex] = tmp;
      
    /* Optionally print the vector. */

    if (print) {
      for (k = 0; k < n; k++) printf("%4.2lf ", v[k]);
      cout << endl;
    }
  }
}
```


# Insertion Sort
Running time: O(n^2)

most important of O(n^2) sorting algorithms 

How it works: In iteration i, make sure that the first i+2 values in the vector are sorted.

Example Output
```
                                                | UNIX> bin/insertion_1_sort 8 1 4 yes yes
Before the loop. The first element is sorted.   | 6.54 5.68 0.50 7.33 5.30 6.50 6.74 8.55 
Iteration 0: The first 2 elements are sorted.   | 5.68 6.54 0.50 7.33 5.30 6.50 6.74 8.55 
Iteration 1: The first 3 elements are sorted.   | 0.50 5.68 6.54 7.33 5.30 6.50 6.74 8.55 
Iteration 2: The first 4 elements are sorted.   | 0.50 5.68 6.54 7.33 5.30 6.50 6.74 8.55 
Iteration 3: The first 5 elements are sorted.   | 0.50 5.30 5.68 6.54 7.33 6.50 6.74 8.55 
Iteration 4: The first 6 elements are sorted.   | 0.50 5.30 5.68 6.50 6.54 7.33 6.74 8.55 
Iteration 5: The first 7 elements are sorted.   | 0.50 5.30 5.68 6.50 6.54 6.74 7.33 8.55 
Iteration 6:       All 8 elements are sorted.   | 0.50 5.30 5.68 6.50 6.54 6.74 7.33 8.55 

```

Code Example: 
```
void sort_doubles(vector <double> &v, bool print)
{
  size_t i, j;
  double tmp;

  /* Optionally print the vector */

  if (print) {
    for (j = 0; j < v.size(); j++) printf("%.2lf ", v[j]);
    cout << endl;
  }

  for (i = 1; i < v.size(); i++) {
    /* Inner loop -- while element i is out of place,  
       swap it with the element in front of it. */

    for (j = i; j >= 1 && v[j] < v[j-1]; j--) {
      tmp = v[j-1];
      v[j-1] = v[j];
      v[j] = tmp;
    }

    /* Optionally print the vector */

    if (print) {
      for (j = 0; j < v.size(); j++) printf("%.2lf ", v[j]);
      cout << endl;
    }
  }
}
```




---
# Heap Sort, Merge Sort and Quicksort

Heap sort, Merge sort and Quicksort are three O(n log(n)) algorithms for sorting. 

---

# Heap Sort
Running time: 


# Merge Sort
Running time: 


# Quicksort Implementation #1
Running time: 


# Quicksort Implementation #2
Running time: 


# Quicksort Implementation #3
Running time: 


# Bucket Sort - Linear Time Sorting
Running time: 