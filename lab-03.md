# Lab 3

This assessment contains materials that may be subject to copyright and other intellectual property rights. 

Modification, distribution or reposting of this document is strictly prohibited. Learners found reposting this document or its solution anywhere will be subject to the college’s Academic Integrity policy.

## Due:

## Objectives:

* implement a simple doubly linked list
* explore the use of sentinel nodes

## Starter file:

* [drawing templates for linked lists](blanklldiagrams.pdf)
* lab3.py (in repo)
* test_lab3.py (in repo)


## General linked list function.  Each function exists for both versions of the linked list:

### Node

The Node class is declared within DoublyLinked.  It stores:
* a piece of data
* a reference to the next Node in the DoublyLinked (None if Node is last node)
* a reference to the previous Node in the DoublyLinked (None if Node is first node)
    
When a Node is initialized, it is passed a data value.  Optionally it is also passed a reference to the next node and a reference to the previous node (in that order).  If the data values are not passed in, they are defaulted to None.

The Node function has the following member functions:

---

```python
def get_data(self)
```
function returns data stored in node

---

```python
def get_next(self)
```
function returns reference to next node in the list

---

```python
def get_previous(self)
```
function returns reference to previous node in the list

---

### DoublyLinked and Sentinel

---
```python
def get_front(self)
```
This function returns a reference to the first data node in the list.  If list is empty, function returns None

---

```python
def get_back(self)
```
This function returns a reference to the last data node in the list.  If list is empty, function returns None

---

```python  
def push_front(self, data)
```
This function adds data to the front of the list (before the first data node).  This function returns nothing

---

```python  
def push_back(self,data)
```
This function adds data to the back of the list (after the last data node).  This function returns nothing

---

```python  
def pop_front(self)
```
This function removes the first data node from the list.  Function returns value stored in that node

If the function is called on an empty DList, raise the IndexError with this statement

```python
  raise IndexError('pop_front() used on empty list')
```

---

```python  

def pop_back(self)
```
This function removes the last data node from the list.  Function returns value stored in that node

If the function is called on an empty DList, raise the IndexError with this statement

```python
raise IndexError('pop_back() used on empty list')
```

---


## Part 1: Coding of doubly linked list:

Complete the implementation of the functions for DoublyLinked in lab3.py

## Part 2: Coding of a Sentinel Linked list

Sentinel nodes are two nodes that exists at the front and back of a linked list that stores no data. They always exists even when the list is empty. Their purpose is to simplify implementation. When inserting into a list with sentinel nodes, the data nodes go between the sentinels. Thus the first node with data is actually the second node in the linked list. Due to their existence, functions can be greatly simplified. 

Complete the functions for Sentinel in lab3.py

## Part 3: Reflection

Write a short paragraph on what you learned in this lab.  Did you prefer writing a linked list with or without sentinel nodes.

## Submitting your lab

In order to get a mark for this lab, you must submit:
* a successful run of test_lab3 done through the provided github actions (push your completed lab3.py back into your repo and it will trigger the test run)

Please make sure you follow the steps listed below fully

### Submitting your code on github

* submit lab3.py by pushing it into github

## Lab Rubric:

| Criteria | Poor - 0 mark | Fair - 1 marks | Good - 2 marks| 
|---|---|---|---|
| Lab Completion | No successful run for lab 3 | Successful run of lab 3 but Reflection/analysis is missing/incomplete or lacks detiails | A good attempt at completing all parts of the lab, may have some small flaws | 
