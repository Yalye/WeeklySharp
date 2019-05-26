
[Dynamic Progamming is just a fancy way to say 'remembering stuff to save time later'](https://www.quora.com/How-should-I-explain-dynamic-programming-to-a-4-year-old/answer/Jonathan-Paulson) is an excellent explantion of **Dynamic Programming**. The `remembered stuffs ` is often known as subproblem results, and **Dynamic Programming** is a problem-solving method which combines the solutions of subproblems. Dynamic Programming is often shorted as **DP**.

To be more specific. We use DP to break a problem into simpler sub-problems recursively. Firstly, we need to confirm whether DP is applicable for the problem, there're two key checkpoints: does the problem have **optimal substructure** and are the problem's sub-problems **overlapping**. Secondly, we solve the problem by **top-down recursion** or **bottom-up approach**. 

Before we go deep, we should understand the above terms.  
 * Optimal substructure: it means that the solution to a given optimization problem can be obtained by the combination of optimal solutions to its sub-problems.  
 * Overlapping sub-problems: it means recursive solving algorithm should solve the same sub-problems over and over, rather than generating new sub-problems.   
 * top-down recursion: it's recursive version of dp solution, and solutions to sub-problems are stored so each sub-problem is solved once.  
 * bottom-up approach: solve all sub-problems first, then use these solutions to solve bigger sub-problems. 

#### References
[top-50-dynamic-programming-practice-problems](https://blog.usejournal.com/top-50-dynamic-programming-practice-problems-4208fed71aa3)