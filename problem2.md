## Find the largest palindrome made from the product of two 3-digit numbers.

###### The isPalindrome() function part of the solution was written by Danish Raza, found in the article by Abhijit Shankhdhar in the geeksforgeeks.org website (under the following URL: https://www.geeksforgeeks.org/check-number-palindrome-not-without-using-extra-space/).

I have integrated this function into my code to help solve the problem, but I have added my own comments to ensure that I have reviewed the function to understand the logic behind it before implementing it within the rest of my code (below the function). I simply had to solve the problem! :smile:

	def isPalindrome(n): 
	
A variable, (divisor) is set to help determine the first digit of the number (eventually through division). Initially set at a value of 1, the first indefinite (while) loop is used to determine just how large (by factors of ten) this variable needs to be. (ex. __*1,234*__ would need __*1,000*__)

Almost like a counter variable, the while loop will increase the divisor variable by a factor of ten until it reaches the required value. So, since __*1,234 / 100 == 12.34*__, that will be the last iteration bringing the updated divisor value to __*1,000*__ (since the next iteration will surpass the loop condition: __*1,234 / 1,000 > 10*__)

		divisor = 1

		while (n / divisor >= 10): 
			divisor *= 10

		while (n != 0): 

The floor division of any number by the divisor variable would isolate the leading number and the modular division by 10 would yeild the trailing number or last digit. __*Ex: (1,234 // 1,000 == 1) and (1,234 % 10 == 4)*__. These values are temporarily assigned to two new variables, leading and trailing respectively.

			leading = n // divisor
			trailing = n % 10
The IF statement checks if the leading and trailing number determined earlier are equal to each other. If not, then the function returns false, ending the iteration here to prevent further calculation, since this number is already not a palindrome.

			if (leading != trailing):
				return False
Given that the number passes through the IF statement, it is then prepared for the  next iteration by removing the first and last digits that were already checked. The  following iteration would then check the next, inner two digits and this while loop will repeat accordingly until the  function has determined the number to be a palindrome, thus finally returning True.

The variable n, holding the number to be checked is then updated to a new value with all digits excluding the first and last that were already checked. Ex: (__*1234 % 1000 == 234*__, followed by __*234 // 10 == 23*__. Thus the 1 and 4 are removed to reveal __*23*__)

			n = (n % divisor)//10
Right before the next iteration of this while loop is started, since n has been updated, the divisor is also updated to reflect the lenth of the new number. It is divided by 100 since n has been reduced by 2 digits.

			divisor = divisor/100
		return True
An empty list to eventually hold all palindrome numbers
	
	blist = []
A nested definite (for) loop to create an array of all possible products between two 3-digit numbers (*100 to 999*)

	for i in range(100,1000,1):
		for j in range(100,1000,1):
			k = i*j
The IF statements calls the isPalindrome() function here to check if each product is a Palindrome. If k is a  Palindrome, it is appended into the previously empty blist[]. The list is then sorted in descending order with the *list.sort()* built-in function

		if isPalindrome (k):
			blist.append(k)
			blist.sort(reverse=True)
Asking to print the first (index position 0) from blist will yield the final answer of the largest palindrome made from the product of two 3-digit numbers. It is __906,609__.
	
	print ("The largest palindrome made from the product of two 3-digit numbers is: ", blist[0])


##### The full code is shown below:

	def isPalindrome(n): 
		
		divisor = 1
		while (n / divisor >= 10): 
		divisor *= 10
		
		while (n != 0):
			leading = n // divisor
			trailing = n % 10
			
			if (leading != trailing):
				return False
			
			n = (n % divisor)//10
			divisor = divisor/100
		
		return True

	blist = []
	#	
	for i in range(100,1000,1):
		for j in range(100,1000,1):
			k = i*j
	#
		if isPalindrome (k):
			blist.append(k)
			blist.sort(reverse=True)
	#
	print ("The largest palindrome made from the product of two 3-digit numbers is: ", blist[0])

