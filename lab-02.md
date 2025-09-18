# Lab 2

This assessment contains materials that may be subject to copyright and other intellectual property rights. 

Modification, distribution or reposting of this document is strictly prohibited. Learners found reposting this document or its solution anywhere will be subject to the college’s Academic Integrity policy.


## Due: Sunday  May 25 - Note: in-lab component is to be done in the lab in week of May 19

## Objectives:

-   Practice performing a full analysis
-   Practice writing recursive functions
-   Understanding the difference between wall-clock time and runtime

## Setup


All files needed for this lab were created by doing the first task in [lab 0](lab-00.md).  If you didn't do lab 0, do the first task to create your lab repository.

Unless otherwise stated, all writing goes into the file lab2.md

## Part A Analysis


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

Analyze the following function with respect to number

```python
def function4(number):
	total = 1
	for i in range(1, number):
		total *= i + 1
	return total
```

## Part B - Programming:

- Write the following python functions **recursively**.
- A non-recursive solution that works will not be given credit (even if it passes testing)

### function 1:

This function is passed a number and returns(number)! = (number)(number-1)(number-2)...(3)(2)(1). By definition, 0! = 1

Only a recursive solution will be accepted!

```python
def factorial(number)
```

### function 2:

Write the **RECURSIVE** function linear_search. linear_search() is passed a list of values and a key. If a matching key is found in the list, function returns index of where the key was found. If the key is not found, function returns -1.

NOTE: you are not allowed to use any of the built in list functions for this problem. The only function you are allowed to use is len()

```python
def linear_search(list, key)
```

HINT: you may need to write the actual recursive function with a different set of arguments to accomplish this task.

### function 3:

Write the **RECURSIVE** function binary_search. binary_search() is passed a sorted list of values and a key. If a matching key is found in the list, function returns index of where the key was found. If the key is not found, function returns -1.

NOTE: you are not allowed to use any of the built in list functions for this problem. The only function you are allowed to use is len()

```python
def binary_search(list, key)
```

HINT: you may need to write the actual recursive function with a different set of arguments to accomplish this task.


## Part C In-Class Discussion


Get together into a small group 2 to 3 students for this part the lab.  To be done in class

The following are 3 functions that will all return the same thing given the same list for mylist and the same key.  They are 3 very different approaches to exactly the same problem.  Answer these on your handout

This may be useful: https://wiki.python.org/moin/TimeComplexity

1. **WITHOUT DOING AN ANALYSIS** (so by gut feeling alone), rank the 3 functions.  Discuss this with your group and explain why you say what you say.
2. Determine what these functions do, state it in English.  This does not mean "it has this loop, then it compares.." thats not what is being asked for.  State it like "this function is passed and array and a key value, it will...and return ....".  Include an example for a given list/key, what the return value is.
3. Run lab2timing.py in your repo.  Does the timing validate your ranking?  Any surprises?
4. Analyze the 3 functions. (this can be split amoungst your group members).  You need to do at least one each.  Share the results.
5. Run lab2timing.py with increasing values of the amount of data (increase by 1000 each time).  Is there a pattern? (Note: ensure that you are using the same "machine" as you change the data size.  Ideally a local computer to avoid inconsistencies).  Does the timing reflect what you expect based on your analysis?


```python

def one(mylist, key):
	total = 0
	for i in range(len(mylist)):
		for j in range(i+1,len(mylist)):
			if i != j:
				if mylist[i] + mylist[j] == key:
					total += 1
	return total

def two(mylist, key):
	total = 0
	mylist.sort()
	i = 0
	j = len(mylist)-1
	while (i < j):
		if(mylist[i] + mylist[j] < key):
			i+=1
		elif(mylist[i] + mylist[j] > key):
			j-=1
		else:
			total += 1
			i+=1
			j-=1
	return total

def three(mylist, key):
	items={}
	total = 0
	for number in mylist:
		items[number]=1
	for number in mylist:
		other = key-number
		if(other in items):
			total+=1
	return total//2
```



  
### Based on the work above, do the following/answer the questions:


## Submitting your lab

* push an updated version of lab2.md and any other relevant files into the lab2 folder of your lab repository

## Lab Rubric:

* For part A and B to be completed, a complete analysis (full 5 steps) for every function must be completed as well as working recursive functions.  (your code must pass testing)

* For part C to be completed, you must arrive in class within 15 minutes of the start of your lab period and participate in the class discussion and all 5 of tasks/answers are added to lab2.md


| Criteria       | Poor - 0 mark     | Fair - 1 marks                                                                                                                     | Good - 2 marks                                                              |
| -------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------- |
| Lab Completion | All parts incomplete | (part A and B)  or (part C) is incomplete | All parts completed |



