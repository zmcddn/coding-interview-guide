# Dynamic Programming (DP)

**Dynamic Programming (DP)** is an algorithm technique which is usually based on a recurrent formula and one (or some) starting states.

- It is used to solve problems that have the following two characteristics:

    1. The problem can be broken down into **overlapping subproblems** - smaller versions of the original problem that are re-used multiple times.
    2. The problem has an **optimal substructure** - an optimal solution can be formed from optimal solutions to the overlapping subproblems of the original problem.

- There are two ways to implement a DP algorithm:

    1. Bottom-up, also known as tabulation.
        - Iterative implementation
        - Derive the final state from known base case, i.e. Fibonacci Sequence
    2. Top-down, also known as memoization (pay attention to the spell!).
        - Recursive implementation
        - **memoizing** a result means to store the result of a function call, usually in a hashmap or an array, so that we can re-use the result instead of recalculation

- When to use DP (the two characteristics):
    - Usually used to find the extreme cases (optimum value) of something: maximum/minimum, shortest/longest, etc
    - When deciding to do something at one step may affect the ability to do something in a later step

## Template

1. **Find the state variables**
    - In a DP problem, a state is a set of variables (state variables) that can sufficiently describe a scenario.
    - Constants should never be state variables.

2. **Find the base case**
    - Base case is used to stop the iteration so it doesn't go on infinitely
    - From the base case we can observe and derive the state transition function

3. **Find the state transition function**
    - State transition function is a recurrence relation to transition between states
    - This is the most difficult thing to discover in a DP problem, ***DRAWING*** helps a lot, especially from the base case
    - Optimization could also be discovered from the drawing
    - Make sure to watch the attached [youtube reference](https://www.youtube.com/watch?v=oBt53YbR9Kk) 

4. **Optimization**
    - **State Reduction**: we could derive the information for some of the state variables based on the other state variables, thus reduce space and/or time complexity


**Summary**:

- Essentially, Dynamic Programming solves problems in a mathematical way. 
- Suppose the DP problem can be described by a math formula (i.e. the Fabonacci Number), think of the state variables as the variables of the function, and the base case is the initial values of the function. To solve a DP problem, we need to follow the template step by step. Once we found the state transition function, the problem is solved.

## Tips:

- Again unless you can see the solution immediately, always draw the recursion tree and look into the base case, its very helpful to find the state transition function 
- Usually a top-down algorithm is easier to implement than the equivalent bottom-up algorithm
- Usually bottom-up is more efficient than top-down in terms of runtime.
- Sometime instead of choosing from a static number of options, we usually add a for-loop to iterate through a dynamic number of options and choose the best one.
- The order of DP matrix traversal (i.e. from top to bottom, from bottom to top, upper half, lower half, etc) is determined by the base condition, remember that the nature of state transfer function is to solve the current state from the **known** previous state

## Reference

- [Dynamic Programming - Learn to Solve Algorithmic Problems & Coding Challenges](https://www.youtube.com/watch?v=oBt53YbR9Kk)
- [Leetcode Dynamic Programming Study Card](https://leetcode.com/explore/learn/card/dynamic-programming/)

## Practice:

- [Leetcode Dynamic Programming Study Plan](https://leetcode.com/study-plan/dynamic-programming)
- [Leetcode Dynamic Programming Study Card](https://leetcode.com/explore/learn/card/dynamic-programming/)

