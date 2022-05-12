# Halting Problem
http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Halting/


```
string halt(char *program, char *input);

```


The Halting Problem is a little weird.

- if the program, when compiled and executed never returns, return: "Infinite Loop"
- if the program, when compiled and executed **with an input** never returns, return: "Halt"

- halt() is not allowed to ever go into an infinite loop

The Halt() Program is impossible to write