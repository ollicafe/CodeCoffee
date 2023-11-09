---
tags:
  - Python
  - Basics
---
A quick reference guide to the basics of [[Python]] 

# Quick Reference
I got nothing here yet

# If/Else Statements
```Python
if <logic_statement>:
	#code goes here
elif <logic_statement>: #else if
	#code goes here
else:
	#code goes here

#shorthand examples
if <logic_statement>: #code goes here

<code1> if <logic1> else <code2> #else if

<code1> if <logic1> else <code2> if <logic2> else <code3> #else, if, elif
#^same as
if <logic1>:
	<code1>
elif <logic2>:
	<code2>
else:
	<code3>

#Example
if 1 < 2:
	pass #does nothing, can't have an empty if statment so use pass instead
```


# Lists
```Python
#Empty List
<variable_name> = []

#Example
myList = ["Item1", "Item2", "Item3"]

#Adding to the list
myList.append("Item4")

#Length of the array
print(len(myList)) #output will now be 4

#Remove element
myList.pop(1) #removes the second item
myList.remove("Item3")

#Combining two lists
myListJr = ["Item5", "Item6"]
myList.extend(myListJr) #adds the second list to the first
```

# Lambda
A small anonymous function
```Python
lambda <arguments> : <expression>

#Example
add = lambda a,b : a+b
print(add(1,2)) #output is 3
```
A more technical example of using lambda is using them in other functions:
```Python
def myFunction(n):
	return lambda a : a * n

myDoubler = myFunction(2)
myTripler = myFunction(3)

print(myDoubler(11)) #output is 22
print(myTripler(11)) #output is 33
```
