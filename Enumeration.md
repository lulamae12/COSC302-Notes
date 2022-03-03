# Enumeration

lecture notes link: https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Enumeration/

Four main ones to study:
- Div/Mod Enumeration
- Power Set Enumeration
- N choose K combonations
- Permutations

---

# Div Mod Enumerations

Often numbers/strings or you have a set of objects with size 'l' and they can all have one of 'n' values.

Examples of Div Mod:

| Example | 'l' value | 'n' value |
| ----------- | ----------- | ----------- |
|Enumerate all 5-character strings containing the letters 'a', 'b' and 'c'|l = 5 | n = 3, {'a','b','c'}|
|Enumerate all 4-digit numbers in base 6|l = 4| n = 6|
|Suppose you have an infinite number of balls, which can have five colors. If two balls have the same color, they are indistinguishable. And suppose you have 7 numbered boxes. Enumerate the distinguishable ways that you put balls into the boxes.|l = 7| n = 5|

To do a div mod enumeration you need to generate all possible combinations of the array. There are n^l ways to do this.

## Do this by using DIV and MOD:

1. take the current number and  % by the n value
2. then divide that number by n

code example:
```/* Calculate n^l.  This is inefficient, but since l is small, it's ok. */

  top = 1;
  for (i = 0; i < l; i++) top *= n;

  /* Enumerate the numbers from 0 to n^l-1, and for each of these
     numbers extract each digit when the number is considered in 
     base n.  We do that by taking the number mod n, and then 
     dividing the number by n. */

  for (i = 0; i < top; i++) {
    j = i;
    for (k = 0; k < l; k++) {

      modulo by n
      digit = j % n;

      divide by n
      j /= n; 
      printf("%c", 'a'+digit);
    }
    printf("\n");
  }
  return 0;
}

```


the general formula is: 
- (i/n) % n

or

- v[i] = (j/(ni))%n.

# Power Set Enumeration

Power set Enumeration is used when you want to enumerate all subsets of an item.

The Power Set of a set is the set of all subsets of the set.


Power Set size = 2 ^ l , where 'l' is the items in the set.


## Process

1. 2^l may be calculated with bit arithmetic as (1 << l). 
2. if you want to see if the j-th digit of the bit string s is one, test whether (s & (1 << j)) is non-zero.
3. if it is 1, than its part of the subset


Code Example:

```
int main()
{
  vector <string> people;
  string s;
  int i, j;

  while (cin >> s) people.push_back(s);
  if (s.size() > 30) {
    cerr << "Sorry, not generating more than 2^30 teams\n";
    exit(1);
  }

  for (i = 1; i < (1 << people.size()); i++) {
    for (j = 0; j < people.size(); j++) {   // Print the bit strings
      printf("%c", (i & (1 << j)) ? '1' : '0');
    }
    for (j = 0; j < people.size(); j++) {   // Print the teams
      if (i & (1 << j)) printf(" %s", people[j].c_str());
    }
    printf("\n");
  }
  exit(0);
}
```


# "n choose k" Enumeration Using Recursion

Example:

Suppose I want to generate all three-person teams from a collection of n people. 

This is an "n choose k" enumeration, where k is equal to 3 and n is the size of the people.

recursive code to solve this Example:
```
// index is an index into people. GenTeams() is initially called with index = 0, and every time it is called recursively, index is incremented.
 
// npeople is the number of people left to put on teams. You could omit it and simply use (3 - teams.size()), but I think it's clearer to have npeople be a parameter.


void People::GenTeams(int index, int npeople)
{
  int i;

  /* Base case -- if there are no more people to add, 
     print out the team and return */

  if (npeople == 0) {
    cout << team[0];
    for (i = 1; i < team.size(); i++) cout << " " << team[i];
    cout << endl;
    return;
  }

  /* This is a second base case -- if there are fewer people left to add
     than there are places left on the team, then it's impossible to finish,
     so simply return.  Ask yourself why this is better than testing whether
     index is equal to people.size(), and returning if so. */

  if (npeople > people.size() - index) return;

  /* Now, put the person in people[index] onto the team, and call GenTeams()
     recursively.  Afterwards, take the person off of the team. */
  
  team.push_back(people[index]);
  GenTeams(index+1, npeople-1);
  team.pop_back();

  /* Finally, call GenTeams() recursively without putting
     people[index] on the team. */

  GenTeams(index+1, npeople);
}

```

# Permutations

Permutations are easy, espically with the next_permutation function, but doing it on your own is simple as well


Basically you do this.

1. make a temporary variable to store item to swap
2. Write a for loop that goes throught the vector
3. store people at i into the temp var
4. set people[i] to people [index]
5. set people[index] to the temp var


```
 for (i = index; i < people.size(); i++) {

    tmp = people[i];         /* Swap people[index] with people[i] */
    people[i] = people[index];
    people[index] = tmp;
}
```


Code example of this:

```
class People {
  public:
    vector <string> people;
    void GenPermutations(int index);
};

void People::GenPermutations(int index)
{
  int i;
  string tmp;

  /* Base case -- we're done - print out the vector */

  if (index == people.size()) {
    cout << people[0];
    for (i = 1; i < people.size(); i++) cout << " " << people[i];
    cout << endl;
    return;
  }

  /* Otherwise, for each element of the vector, swap it with the element
     in index, call GenPermutations() recursively on the remainder of the
     vector, and then swap it back. */
     
  for (i = index; i < people.size(); i++) {

    tmp = people[i];         /* Swap people[index] with people[i] */
    people[i] = people[index];
    people[index] = tmp;

    GenPermutations(index+1);  

    tmp = people[i];          /* Swap back */
    people[i] = people[index];
    people[index] = tmp;
  }
}
```

