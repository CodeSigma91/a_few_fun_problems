## Find the sum of all numbers below 1000 that are divisible by 3 or 5. 

I start with an empty list to hold the numbers between 1 and 1000 that are divisible by 3 or 5
```python
alist = []
```
I introduce a definite (for) loop with a range() function to generate the same number of iterations as all positive integers below 1000
```python
for i in range(1000):
```
Each iteration is checked with an IF statement for divisibility with 3 or 5 using the modular division operation. If it meets this condition, the number is added to the previously empty list.
```python
	if i%3==0 or i%5==0:
		alist.append(i)
```
Finally, I ask to print the sum of all the integer values in the list using the built-in sum() function. The final answer is: **223,168**.
```python
print("The sum of all numbers below 1000 that are divisible by 3 or 5 is: ", sum(alist))
```
##### Full code without comments shown below:
```python
alist = []

for i in range(1000):
	if i%3==0 or i%5==0:
		alist.append(i)

print("The sum of all numbers below 1000 that are divisible by 3 or 5 is: ", sum(alist))
```
