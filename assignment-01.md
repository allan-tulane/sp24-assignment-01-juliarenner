

# CMPS 2200 Assignment 1

**Name: Julia Renner**


In this assignment, you will learn more about asymptotic notation, parallelism, functional languages, and algorithmic cost models. As in the recitation, some of your answer will go here and some will go in `main.py`. You are welcome to edit this `assignment-01.md` file directly, or print and fill in by hand. If you do the latter, please scan to a file `assignment-01.pdf` and push to your github repository. 
  
  

1. (2 pts ea) **Asymptotic notation** (12 pts)

  - 1a. Is $2^{n+1} \in O(2^n)$? Why or why not? 
.  
.  Yes, 2^(n+1) is in O(2^n). This is because 2^(n+1) is equal to 2(2^n) which will be smaller than or equal to c(2^n)
.  by a constant factor. 2^(n+1) is bounded above by 2^n, and therefore is in O(2^n) and grows no faster than 2^n.
.  
. 
  - 1b. Is $2^{2^n} \in O(2^n)$? Why or why not?     
.  
.  No, 2^2^n is not in O(2^n). This is because there is no constant c that can satisfy the inequality 2^2^n <= c(2^n)
.  since 2^2^n grows at a double-exponential rate while 2^n grows at a single-exponential rate. 2^2^n grows much faster, and
.  is not bounded above by O(2^n).
.  
  - 1c. Is $n^{1.01} \in O(\mathrm{log}^2 n)$?    
.  
.  No, n^1.01 is not in O(log^2(n)). This is because n^1.01 is a polynomial function and will grow faster than any 
.  logarithmic function squared so it cannot be bounded above by O(log^2(n)).
.  

  - 1d. Is $n^{1.01} \in \Omega(\mathrm{log}^2 n)$?  
.  
.  Yes, n^1.01 is in Omega((log)^2 n). n^1.01 is a polynomial function and will grow faster than
.  any logarithmic function squared.
.
.
  - 1e. Is $\sqrt{n} \in O((\mathrm{log} n)^3)$?  
.  
.  No, sqrt(n) is not in O((logn)^3). This is because sqrt(n) will grow faster than the constant multiple of logn,
.  especially considering that it is cubed meaning it will go even slower. sqrt(n) is not bounded above by O((logn)^3).
.
.
  - 1f. Is $\sqrt{n} \in \Omega((\mathrm{log} n)^3)$?  
.
.  Yes, sqrt(n) is in Omega((logn)^3). This is because sqrt(n) will grow much faster than the constant multiple of logn^3.
.
.

2. **SPARC to Python** (12 pts)

Consider the following SPARC code of the Fibonacci sequence, which is the series of numbers where each number is the sum of the two preceding numbers. For example, 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610 ... 
$$
\begin{array}{l}
\mathit{foo}~x =   \\
~~~~\texttt{if}{}~~x \le 1~~\texttt{then}{}\\
~~~~~~~~x\\   
~~~~\texttt{else}\\
~~~~~~~~\texttt{let}{}~~(ra, rb) = (\mathit{foo}~(x-1))~~,~~(\mathit{foo}~(x-2))~~\texttt{in}{}\\  
~~~~~~~~~~~~ra + rb\\  
~~~~~~~~\texttt{end}{}.\\
\end{array}
$$ 

  - 2a. (6 pts) Translate this to Python code -- fill in the `def foo` method in `main.py`  

  - 2b. (6 pts) What does this function do, in your own words?  
.  
. This function calculates a number in the Fibonacci Sequence. The function foo takes 'x' as an
. argument, and returns the xth Fibonacci number. If x is 0 or 1, the function returns 0 or 1.
. For other values, it recursively calls itself to compute the two previous Fibonacci numbers, 
. and sums them to find the current number. 
.  
  

3. **Parallelism and recursion** (26 pts)

Consider the following function:  

```python
def longest_run(myarray, key)
   """
    Input:
      `myarray`: a list of ints
      `key`: an int
    Return:
      the longest continuous sequence of `key` in `myarray`
   """
```
E.g., `longest_run([2,12,12,8,12,12,12,0,12,1], 12) == 3`  
 
  - 3a. (7 pts) First, implement an iterative, sequential version of `longest_run` in `main.py`.

  - 3b. (4 pts) What is the Work and Span of this implementation?  
.  
.  The Work of this implementation is O(n) where n is the length of mylist. 
.  This is because the function longest_run employs a loop where the number of 
.  iterations is proportional to the length of the list. 
.  The Span of this implementation is O(n) where n is the length of mylist.
.  This is because the loop iterations must execute sequentially due to the
.  dependencies, so the span is proportional to the total time taken for 
.  the number of iterations. 
.  
  - 3c. (7 pts) Next, implement a `longest_run_recursive`, a recursive, divide and conquer implementation. This is analogous to our implementation of `sum_list_recursive`. To do so, you will need to think about how to combine partial solutions from each recursive call. Make use of the provided class `Result`.   

  - 3d. (4 pts) What is the Work and Span of this sequential algorithm?  
.  
. The Work of this algorithm is O(nlogn), where n is the length of the input list.
. This is because the algorithm recursively processes each element of the input list, dividing it in half at each recursion level.
. This allows for the work done at each level of recursion to be proportional to the number of elements being processed at 
. that level, and the total work done by the algorithm can be represented as the sum of work done at each level. 
. The Span of this algorithm is O(logn), where n is the length of the input list.
. This is because each recursive call depends on the results of previous recursive calls. The number of recursive
. calls made by the algorithm is logarithmic in the size of the input list. 
.  


  - 3e. (4 pts) Assume that we parallelize in a similar way we did with `sum_list_recursive`. That is, each recursive call spawns a new thread. What is the Work and Span of this algorithm?  

.  
. The Work of this algorithm will be the same as it was before (O(nlogn)) because the amount of 
. computation does not change when parallelized.
. The Span of this algorithm will be the same as it was before (O(logn)) because each recursive call
. is still inherently sequential as it depends on the results of previous calls.
.  
.  
.  
.  
.  

