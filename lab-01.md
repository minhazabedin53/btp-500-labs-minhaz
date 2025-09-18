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

### function 2:

Analyze the following function with respect to number

```python
def function2(number):
	return (number * (number + 1) * (2 * number + 1)) // 6
```

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
