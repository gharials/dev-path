# Problem-Solving Tactics

## Loop invariants

Loop invariants is an important problem-solving tactic. A certain class of problems consist of a number of smaller _subproblems_. Such problems are solved by loops designed for solving them. Starting from the smallest subproblem, the loop proceeds to bigger subproblems in each iteration, and eventually solves the whole problem.

The loop has to be designed in such a way that after each iteration of the loop, the problem is _partially solved_ up to that point. Given the partial solution of smaller subproblems, the loop body has to find the solution for the subproblem larger in size by 1. That way, after the loop terminates, the whole problem is solved.

Notice that after each iteration, the loop ensures that the condition _the subproblem has been solved_ holds true. The condition is called the _loop invariant._

It is the programmer's job to recognize how the problem can be divided into subproblems and write a loop body that maintains the loop invariant. The loop body differs from problem to problem.

### Example

Let's assume that a problem asks to sort an array $a$ consisting of $n$ elements. A loop designed for solving that problem assumes that the problem is solved for subproblem $[a_0 ... a_{i - 1}]$, that is, elements $[a_0 ... a_{i - 1}]$ has been sorted. Given that elements $[a_0 ... a_{i - 1}]$ has been sorted and a new element $a_i$, the loop body has to sort elements $[a_0 ... a_i]$. As the loop body ensures that elements $[a_0 ... a_i]$ is sorted, when the loop terminates, the whole array is sorted. The loop invariant in this case is _the array $[a_0…a_i]$ is sorted._

## Recursion

Recursion is an important problem solving technique. It is useful in problems where solution to the problem has a relationship with the solution to its smaller case.

### Designing recursion

Finding recursive solution to a problem mainly involves the following two steps:

1. Find the relationship between the solution of $n$ and the solution of $n - 1$.
2. Define the result for the base conditions.

### Properties of recursion

Keep the following properties of recursion in mind:

* A _chain of function calls_ is needed to solve a problem.
* Each function call has its _own copy_ of all of its local variables, including its parameters.
* All the calls, however, have access to the _global variables_ of the program.
* The calling function _waits_ for the result to be returned by the function it called with a smaller parameter.

## Backtracking

Backtracking is an important problem solving technique exploiting recursion.

### Backtracking problems

Backtracking problems consist of a number of _levels_ or _steps_ with each level having a few _choices_ or _possibilities_. Backtracking means _traversing all the possibilities_ consisting of all the levels. For example, printing all possible $n$-digit numbers can be viewed as a problem consisting of $n$ levels. For each level, there are 10 choices, that is the 10 decimal digits. Printing all possible $n$-digit numbers means trying all the choices for each of the $n$ levels.

The number of levels and the choices for each level may vary problem to problem. For the all possible $n$-digit numbers problem, for each level, the choices are the same, all the 10 decimal digits. For the all possible subsets of a set of size $n$ problem, for each level there are two choices, whether the element is included in the subset or not. For some problems, the choices may not be independent like the earlier. For example, in finding all possible permutations, an element chosen at a level cannot be chosen in later levels; the function has to keep track of it.

### Backtracking algorithms

Backtracking algorithms employ recursion to solve a backtracking problem. Each function call takes care of a level where the level is identified by a function parameter. After making a choice for its level, the function lets exploring all the possibilities for the rest of the levels by calling the function itself with a smaller parameter.

```js
let printAllNumbers = (n, p) => {
    
    if (n == 0) {
        console.log(p);
        return;
    }

    for (let i = 0; i < 10; i++) {
        printAllNumbers(n - 1, p + i);
    }
}
```

In the preceding example of a backtracking function for printing all possible $n$-digit numbers, the level is identified by the parameter `n`. For any level `n`, the `for` loop tries a possibility, that is a digit `i`, and calls the function itself with parameter `n-1` to find the all possible $n-1$-digit numbers after it. Once the function returns after trying all the $n-1$-digit numbers, the loop tries the next possibility, that is the next digit `i`, and again calls the function itself to find the all possible $n-1$-digit numbers after it. This process continues until all the possibilities of the current level, that is all the 10 decimal digits, are tried.

Passing result and keeping track of choices in levels vary problem to problem.