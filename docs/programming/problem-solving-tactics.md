# Problem-Solving Tactics

## Loop invariants

Loop invariants is an important problem-solving tactic. Large classes of problems consist of a number of smaller _subproblems_. Such problems are solved by loops designed for solving them.

The loop has to be designed in such a way that after each iteration of the loop, the problem is _partially solved_ up to that point. Given the partial solution, the loop body has to find the solution for the subproblem larger by 1. That way, after the loop completes, the whole problem is solved.

The loop body differs from problem to problem. It is the programmer's job to recognize the subproblem structure and write a loop body that maintains the loop invariant.

### Example

Let's assume that a problem asks to sort an array $a$ consisting of $n$ elements. A loop designed for solving that problem assumes that the problem is solved for subproblem $[a_0 ... a_{i - 1}]$, that is, elements $[a_0 ... a_{i - 1}]$ has been sorted. Given that elements $[a_0 ... a_{i - 1}]$ has been sorted and a new element $a_i$, the loop body has to sort elements $[a_0 ... a_i]$. As the loop body ensures that elements $[a_0 ... a_i]$ is sorted, when the loop terminates, the whole array is sorted.
