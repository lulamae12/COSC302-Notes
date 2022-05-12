# NP Completeness
http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/NP/

P, NP, NP-Complete and NP-Hard are sets of problems, defined as follows:
- **P** are Problems solvable in Polynomial time
- **NP**: Verifyable in polynomial time
- **NP-Hard**: The problem is at least as hard as a NP-Complete problem but is not nessicarily NP
- **NP-Complete**: Are NP-Hard and NP. 

only one NP-Complete problem has been defined: 3-Sat

No One is able to prove that NP == P or NP != P


# Traits of NP-Completeness:

- If G is an NP Complete problem, then G may be solved in exponential time with enumeration.
- If G is an NP Complete problem, then G must be framed as a "yes/no" question, and a "yes" answer must be verifiable in polynomial time.
- Let G be an NP Complete problem. If you can solve G in time O(T), then you can solve 3-SAT in time O(Tp), where p is a polynomial of the input size of G and 3-SAT.
- NP complete problems may or may not be solvable in Polynomial time, we dont know.