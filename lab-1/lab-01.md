# Lab 1

This assessment contains materials that may be subject to copyright and other intellectual property rights. 

Modification, distribution or reposting of this document is strictly prohibited. Learners found reposting this document or its solution anywhere will be subject to the college’s Academic Integrity policy.

## Due: 

## Objectives:

- Learn how to analysis
- Learn to write recursive functions
- Make connections between analytical run times and actual performance

## Setup


All files needed for this lab were created by doing the first task in [lab 0](lab-00.md).  If you didn't do lab 0, do the first task to create your lab repository.

Unless otherwise stated, all writing goes into the file lab2.md


## Part A: Code and Discuss

Step 1: Form a group 4 to 6 members


Step 2: Individually write the following function (by hand so we can trade it)

```python
def sum_to_goal(numbers_list, goal)
```

This function is passed a list of unique numbers.  It will find the two numbers in the list that sum up to the goal value. Function returns the product of the two numbers(the product is the result of multiplying the two numbers together) .  If there are no two numbers that when summed results in the goal state, function returns 0.

Step 3: Estimate your own function's run time.  You do not need to do a full analysis but make a guess.

Step 4: Trade your functions within your group so that each person is looking at someone else's code and perform a full analysis of the function with respect to the size of the list.


Step 5: Discuss your results.  Was there any version that had a different run time?  Which version looks like it would run the fastest?

Step 6:  Repeat the above steps with the following function:

```python
def fibonacci(n)
```
this function is passed a non-negative integer, that we will call n in this description.  function returns the nth fibonacci number in the fibonacci sequence.  

let $F_n$ represent the nth fibonacci number.

* $F_0 = 0$
* $F_1 = 1$
* $F_2 = 1$
* $F_3 = 2$
* $F_4 = 3$
...
* $F_n = F_{n-1} + F_{n-2}$

the nth fibonacci number is the sum of the 2 previous fibonacci numbers.


### Part A Write UP:

1. Did your teammate's analysis match what you thought your function's runtime was?

2. Rewrite the two functions for part A in lab1.md file.  You can write exactly what you wrote on paper or you can alter it based on your discussions with your teammates.  If you made a change (outside of correcting syntax), why did you do it? if you did not alter it why not?

3. How would you test whether or not your analysis was correct?  Write a small python program to test your functions and demonstrate that the function behaves according to the expected runtime. 



## Part B Analysis


Follow this guide on how to perform an analysis:

https://seneca-ictoer.github.io/data-structures-and-algorithms/B-Algorithms-Analysis/how-to-do-an-analysis

Perform an analysis of the following functions.  

### function 1:

Analyze the following function with respect to number

```python
def function1(number):
	total = 0

	for i in range(number):
		x = i + 1
		total += x * x

	return total
```

# Function 1 Answer

## Code under analysis

```python
def function1(number):
    total = 0

    for i in range(number):
        x = i + 1
        total += x * x

    return total
```

* Let **n** be the input size, where **n = number**.
* Let **T(n)** be the total number of operations executed by `function1` on input **n**.

## Counting operations

```python
def function1(number):
    total = 0                      # 1

    for i in range(number):        # n iterations
                                  # +1 to create the range (constant)
        x = i + 1                  # 2·n   (1 add + 1 assign per iteration)
        total += x * x             # 3·n   (1 mult + 1 add + 1 assign per iteration)

    return total                   # 1
```

Operation Counts:

* `total = 0` → **1**
* loop iterations → **n**
* range creation (constant) → **1**
* `x = i + 1` inside loop → **2n**
* `total += x * x` inside loop → **3n**
* `return total` → **1**

$$
T(n) = 1 + n + 1 + 2n + 3n + 1
$$

## Simplifying

$$
T(n) = (1+1+1) + (n + 2n + 3n) = 3 + 6n = 6n + 3
$$

## Big-O conclusion

The dominating term is linear in $n$.
**Therefore, $T(n) \in O(n)$.**




### function 2:

Analyze the following function with respect to number

```python
def function2(number):
	return (number * (number + 1) * (2 * number + 1)) // 6
```

# Function 2 Answer

## Code under analysis

```python
def function2(number):
    return (number * (number + 1) * (2 * number + 1)) // 6
```

* Let **n** be the input size, where **n = number**.
* Let **T(n)** be the total number of operations executed by `function2` on input **n**.

## Counting operations

```text
a = number + 1        # 1 add
b = 2 * number        # 1 mult
c = b + 1             # 1 add
d = number * a        # 1 mult
e = d * c             # 1 mult
f = e // 6            # 1 integer division
return f              # 1
```

$$
T(n) = 1+1+1+1+1+1+1 = 7 \quad (\text{a constant})
$$

## Simplifying

$$
T(n) = x \quad \text{for some constant } x
$$

## Big-O conclusion

No loops or recursion; work doesn’t scale with **n**.
**Therefore, $T(n) \in O(1)$** (constant time).





### function 3:

Analyze the following with respect to the length of the list.  Note that the function call len() which returns the length of the list is constant (O(1)) with respect to the length of the list.
```python
def function3(list):
	n = len(list)
	for i in range(n - 1):
		for j in range(n - 1 - i):
			if list[j] > list[j+1]:
				tmp = list[j]
				list[j] = list[j+1]
				list[j + 1] = tmp
```

# Function 3 Answer

## Code under analysis

```python
def function3(lst):
    n = len(lst)
    for i in range(n - 1):
        for j in range(n - 1 - i):
            if lst[j] > lst[j + 1]:
                tmp = lst[j]
                lst[j] = lst[j + 1]
                lst[j + 1] = tmp
```

## Variables & functions

* Let **n = len(lst)** be the input size.
* Let **T(n)** be the number of primitive operations executed by `function3` on an input of length **n**.

## Count operations

```python
n = len(lst)                       # 1

for i in range(n - 1):             # outer loop: (n - 1) iterations
    for j in range(n - 1 - i):     # inner loop: (n - 1 - i) per i
        if lst[j] > lst[j + 1]:    # 1 comparison each inner iteration
            tmp = lst[j]           # 1
            lst[j] = lst[j + 1]    # 1
            lst[j + 1] = tmp       # 1
```

Totals across all iterations:
* **Comparisons:** $\sum_{i=0}^{n-2} (n-1-i) = \frac{n(n-1)}{2}$.
* **Swaps:** happen only when the `if` is true. Let **S** be the number of swaps.
  * Each swap has **3** operations so **$3S$**

$$
T(n) \approx \underbrace{\frac{n(n-1)}{2}} \;+\; \underbrace{3S} \;+\; O(1).
$$

## Simplifying

* **Worst case** : every comparison does a swap, so $S = \frac{n(n-1)}{2}$.

  $$
  T_{\text{worst}}(n) \approx \frac{n(n-1)}{2} + 3\cdot\frac{n(n-1)}{2}
  = 2\,n(n-1) = 2n^2 - 2n \in O(n^2).
  $$
* **Best case** : $S = 0$.

  $$
  T_{\text{best}}(n) \approx \frac{n(n-1)}{2} \in O(n^2).
  $$
* **Average case**: expected change $\approx \frac{n(n-1)}{4}$, and bubble sort does one swap per change ⇒ $S \approx \frac{n(n-1)}{4}$.

  $$
  T_{\text{avg}}(n) \approx \frac{n(n-1)}{2} + 3\cdot\frac{n(n-1)}{4}
  = \frac{5}{4}\,n(n-1) \in O(n^2).
  $$

## Big-O conclusion

* **Time complexity:** $O(n^2)$ 




### function 4:


Analyze function4 with respect to the length of the mystring.  Hint, you will need to set up two mathematical functions for operator counting.  one for function2 and the other for recursive_function2

```python

def recursive_function4(mystring,a, b):
	if(a >= b ):
		return True
	else:
		if(mystring[a] != mystring[b]):
			return False
		else:
			return recursive_function4(mystring,a+1,b-1)

def function2(mystring):
	return recursive_function4(mystring, 0,len(mystring)-1)

```

# Function 4 Answer

```python
def recursive_function4(mystring,a,b):
    if (a >= b):
        return True
    else:
        if (mystring[a] != mystring[b]):
            return False
        else:
            return recursive_function4(mystring, a+1, b-1)

def function2(mystring):
    return recursive_function4(mystring, 0, len(mystring)-1)
```

---

## Variables & functions

* Let **n = len(mystring)**.
* Let **T(n)** = number of operations for `function2(mystring)` (the wrapper).
* Let **R(n)** = number of operations for `recursive_function4(mystring, a, b)` on a string of length **n** (worst case, when recursion continues to the middle).

---

## Counting operations

### For `function2(mystring)`:

```python
return recursive_function4(mystring, 0, len(mystring)-1)
```

* `len(mystring)` → 1
* subtraction `-1` → 1
* function call overhead → 1

So:

$$
T(n) = 3 + R(n)
$$

---

### For `recursive_function4(mystring,a,b)`:

Case 1 — Base case (`a >= b`):

* comparison → 1
* return True → 1

So:
$$
R(1) = R(0) = 2
$$

Case 2 — Recursive case (`a < b`):

* comparison `a >= b` → 1
* comparison `mystring[a] != mystring[b]` → 1
* if equal, recursive call:
  * preparing arguments (`a+1`, `b-1`) → 2
  * recursive call itself → R(n-2)

Total:

$$
1 + 1 + 2 = 4 + R(n-2)
$$

---

## Build Recurrence

For recursive case:

$$
R(n) = 4 + R(n-2)
$$

Base cases:

$$
R(0) = 2, \quad R(1) = 2
$$

---

## Solve Recurrence

Expand:

$$
\begin{aligned}
R(n) &= 4 + R(n-2) \\
     &= 4 + (4 + R(n-4)) \\
     &= 4 + 4 + R(n-4) \\
     &= 4k + R(n-2k)
\end{aligned}
$$

So:

$$
R(n) = 4 \cdot \frac{n}{2} + 2 = 2n + 2
$$

---


* For `recursive_function4`:

  $$
  R(n) = 2n + 2 \in O(n)
  $$

* For `function2`:

  $$
  T(n) = 3 + R(n) = 3 + (2n + 2) = 2n + 5 \in O(n)
  $$

* **Final:** Both `function2` and `recursive_function4` run in **O(n)** time


### function 5:

Analyze the following function with respect to number


```python
def function5(value, number):
	if (number == 0):
		return 1
	elif (number == 1):
		return value
	else:
		half = number // 2
		result = function5(value, half)
		if (number % 2 == 0):
			return result * result
		else:
			return value * result * result

```
# Function 5 Answer

```python
def function5(value, number):
    if number == 0: return 1
    elif number == 1: return value
    else:
        half = number // 2
        result = function5(value, half)
        if number % 2 == 0:
            return result * result
        else:
            return value * result * result
```


* Let **n = number** (the exponent).
* Let **T(n)** be the time to compute `function5(value, n)`.

* Base cases `n ∈ {0,1}` do **O(1)** work.
* Otherwise we:

  * Recursively call once on **⌊n/2⌋**,
  * Do a **constant** amount of local work (a few ops and at most **two multiplications**).


$$
T(n) = T(\lfloor n/2 \rfloor) + O(1), \quad T(0)=T(1)=O(1).
$$

Each call halves **n**, so we have about **log₂ n** levels. Constant work per level ⇒ total is **O(log n)**.


* **Time:** $O(\log n)$


## Submitting your lab

In order to get a mark for this lab, you must submit:

- a complete analysis of every function in part B.
- Place all your work for this lab into the file lab1.md unless otherwise indicated


When you are happy with the state of your files, submit a link to your repo's lab1 folder into blackboard.  

Note: Submission of a link to Blackboard is an indication that your lab is ready for grading in the current state.  Do not submit a link until you are ready to be graded.


## Lab Rubric:

| Criteria       | Poor - 0 mark     | Fair - 0.5 marks                                                                                                                     | Good - 1 marks                                                              |
| -------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------- |
| Lab Completion | Part B is incomplete | Part B but was missing key steps or part B was completed correctly but was more than 15 min late for Part A | Successfully complete Part A, B |
