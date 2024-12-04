# Problem-Solving Tactics

## Loop invariants

Loop invariants is an important problem-solving tactic. A certain class of problems consist of a number of smaller _subproblems_. Such problems are solved by loops designed for solving them. Starting from the smallest subproblem, the loop proceeds to bigger subproblems in each iteration, and eventually solves the whole problem.

The loop has to be designed in such a way that after each iteration of the loop, the problem is _partially solved_ up to that point. Given the partial solution of smaller subproblems, the loop body has to find the solution for the subproblem larger in size by 1. That way, after the loop terminates, the whole problem is solved.

Notice that after each iteration, the loop ensures that the condition _the subproblem has been solved_ holds true. The condition is called the _loop invariant._

It is the programmer's job to recognize how the problem can be divided into subproblems and write a loop body that maintains the loop invariant. The loop body differs from problem to problem.

### Example

Let's assume that a problem asks to sort an array $a$ consisting of $n$ elements. A loop designed for solving that problem assumes that the problem is solved for subproblem $[a_0 ... a_{i - 1}]$, that is, elements $[a_0 ... a_{i - 1}]$ has been sorted. Given that elements $[a_0 ... a_{i - 1}]$ has been sorted and a new element $a_i$, the loop body has to sort elements $[a_0 ... a_i]$. As the loop body ensures that elements $[a_0 ... a_i]$ is sorted, when the loop terminates, the whole array is sorted. The loop invariant in this case is _the array $[a_0…a_i]$ is sorted._

## Backtracking

Backtracking is an important problem solving technique.

### Backtracking problems

Backtracking problems consist of a number of _steps_ with each step having a few _possibilities_. Backtracking requires _traversing all the possibilities_ consisting of all the steps. For example, printing all possible $n$ digit numbers can be viewed as a problem consisting of $n$ steps. For each step, there are 10 possibilities, that is the 10 decimal digits. Printing all possible $n$-digit numbers means trying all the possibilities for each of the $n$ steps.

The number of steps and the possibilities for each step may vary problem to problem. For the all possible $n$-digit numbers problem, for each step, the possibilities are the same, all the 10 decimal digits. For the all possible subsets of a set of size $n$ problem, for each step there are two possibilities, whether the element is included in the subset or not. For some problems, the possibilities may not be independent like the earlier. For example, in finding all possible permutations, an element chosen at a step cannot be chosen in later steps; the function has to keep track of it.

### Backtracking algorithms

Backtracking algorithms employ recursion to solve a backtracking problem. Each function call takes care of a step where the step is identified by a function parameter. After choosing a possibility for its step, the function lets exploring all the possibilities for the rest of the steps by calling the function itself with a smaller parameter.

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

In the preceding example of a backtracking function for printing all possible $n$-digit numbers, the step is identified by the parameter `n`. For any step `n`, the `for` loop tries a possibility, that is a digit `i`, and calls the function itself with parameter `n-1` to find the all possible $n-1$-digit numbers after it. Once the function returns after trying all the $n-1$-digit numbers, the loop tries the next possibility, that is the next digit `i`, and again calls the function itself to find the all possible $n-1$-digit numbers after it. This process continues until all the possibilities of the current step, that is all the 10 decimal digits, are tried.
