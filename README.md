# ass1

# Q1.Considerfollowingtwolists: a=[1,2,2,3,5,8,13,21,34,55,89] b=[1,2,3,4,5,6,7,8,9,10,11,12,13] Write a python program that returns a list that contains only the elements that are common 

a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]

b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]

c=[]

for i in range(len(a)):

    if a[i] in b:
    
        c.append(a[i])
c=set(c)

print(c)


# Q2. Write a python program to create a list of ‘n’ integers . Find all prime numbers from the above created list and store them in a separate list. Display both list.(Using Recursion) 

lst = []

n =int(input("enter no of elements :")) 

for i in range(0,n):  

ele = int(input())   

lst.append(ele)   

print(lst)  

primes = [num for num in lst if num > 1 and num % 2!=0 and num % 3!=0]

print("prime numbers are : ",primes)   

# Q3.Write a program to create a list of ‘n’ integers and find their median.  

import numpy as np 

lst = [] 

n =int(input("enter no of elements :")) 

for i in range(0,n): 

ele = int(input()) 

lst.append(ele)

print(lst) 


# Q4.Write a python program to accept the strings which contain all vowels.


def check(string) :

 string = string.lower()
 
vowels = set("aeiou"	

 s = set({})
 
	for char in string :

		if char in vowels :

   s.add(char)
		
  else:
	
   pass
	
 if len(s) == len(vowels) :

  print("Accepted")
	
 else :

  print("Not Accepted")

if

__name__ == "__main__" :	

 string = "SEEquoiaL"

 check(string)


 #  Q6.Write a python function to find all duplicates in the list 

  def find_duplicates(lst):

    seen = set()
    
    duplicates = set()
    
    for items in lst:
    
        if item in seen:
        
            duplicates.add(item)
        
        else:
        
            seen.add(item)
    
    return list(duplicates)

user_input = input("Enter the inputs",list)

duplicates = find_duplicates(user_input)

print("Duplicates in the list:",duplicates)


# Q7. largest number

def find_largest_number(numbers):

    if not numbers:

        return None  

    largest = numbers[0]

    for num in numbers:
        
        if num > largest:
        
            largest = num

    return largest

my_numbers = [10, 5, 8, 20, 15, 25, 18]

largest_number = find_largest_number(my_numbers)

if largest_number is not None:
 
    print("The largest number in the list is:", largest_number)

else:

    print("The list is empty.")

# Q8. unique ele

import numpy as np

def unique(list1):
	
 x = np.array(list1)

 print(np.unique(x))

list1 = [10, 20, 10, 30, 40, 40]

print("the unique values from 1st list is")

unique(list1)


list2 = [1, 2, 1, 1, 3, 4, 3, 3, 5]

print("\nthe unique values from 2nd list is")

unique(list2)

# Q9 square of all ele

def square_num(n):

    return n * n

nums = [4, 5, 2, 9]

print("Original List: ", nums)

result = map(square_num, nums)

print("Square the elements of the said list using map():")

print(list(result))

# Q10. gcd lcd

import math

def find_gcd(x, y):

    return math.gcd(x, y)

def find_lcm(x, y):
   
    return abs(x * y) // find_gcd(x, y)

try:
    
    input_numbers = input("Enter a list of numbers separated by spaces: ")
    
    numbers = [int(num) for num in input_numbers.split()]

except ValueError:

    print("Invalid input. Please enter valid numbers.")
    
    exit()

if len(numbers) < 2:
    
    print("Please provide at least two numbers.")
    
    exit()

gcd_result = numbers[0]

lcm_result = numbers[0]

for num in numbers[1:]:

    gcd_result = find_gcd(gcd_result, num)
    
    lcm_result = find_lcm(lcm_result, num)

print("Input numbers:", numbers)

print("GCD of the numbers:", gcd_result)

print("LCM of the numbers:", lcm_result)

# Q11 shape area triangle rect circle cone

import math

class Shape:

    def calculate_triangle_area(self, base, height):
    
        return 0.5 * base * height

    def calculate_rectangle_area(self, length, width):
        
        return length * width

    def calculate_circle_area(self, radius):
        
        return math.pi * radius**2

    def calculate_cone_area( , radius, height):
        
        slant_height = math.sqrt(radius**2 + height**2)
        
        return math.pi * radius * (radius + slant_height)

if __name__ == "__main__":
    
    my_shape = Shape()

    triangle_area = my_shape.calculate_triangle_area(5, 8)
    
    rectangle_area = my_shape.calculate_rectangle_area(4, 6)
    
    circle_area = my_shape.calculate_circle_area(3)
    
    cone_area = my_shape.calculate_cone_area(2, 4)

    print("Area of Triangle:", triangle_area)
    
    print("Area of Rectangle:", rectangle_area)
    
    print("Area of Circle:", circle_area)
    
    print("Area of Cone:", cone_area)

    


# ass2

# Q1 lambda for add 2 num

# a
add_numbers = lambda x, y: x + y

num1 = 1

num2 = 2

result = add_numbers(num1, num2)

print("The sum of", num1, "and", num2, "is", result)

# b lambda for even or not

numbers = input("Enter a list of numbers separated by spaces: ").split()

numbers = [int(num) for num in numbers]

results = list(map(lambda num: "even" if num % 2 == 0 else "odd", numbers))

for num, result in zip(numbers, results):

    print("Number {} is {}".format(num, result))

    
# c factorial

x = lambda num : 1 if num <= 1 else num*x(num-1)

number = int(input('Enter number: '))

print('%d != %d' %(number, x(number)))

# d maximum ele

lst = [20, 10, 20, 4, 100]

print(max(lst, key=lambda value: int(value)) )

# Q2 
# a palindrome

def isPalindrome(string): 
    
    if (string == string[::-1]) : 
        
        return "The string is a palindrome." 
    else: 

        return "The string is not a palindrome." 
 
string = input ("Enter string: ") 
 
print(isPalindrome(string))


# b sort a list of string alphabetically

my_dict = {

"L1": ["Red", "Green", "Yellow", "Blue"],

 "L2": ["Violet", "Dark green", "Pink", "White"],

 "L3": ["Black", "Aqua", "Beige", "Aqua"],

 "L4": ["Alice Blue", "Cyan", "Gold", "Silver"]

}


print("Before Sorting:")


for key, value in my_dict.items():

 print(key + ": " + str(value))

sorted_dict = {key: sorted(value, key=lambda x: x.lower())

   for key, value in my_dict.items()}

print("\nAfter Sorting:")

for key, value in sorted_dict.items():

 print(key + ": " + str(value))

 # c area of triangle


calculate_area = lambda base, height: 0.5 * base * height

base = float(input("Enter the base length of the triangle: "))

height = float(input("Enter the height of the triangle: "))

area = calculate_area(base, height)

print("The area of the triangle is:", area)

# d list is sublist

from functools import reduce

from operator import and_ 

def contains(superset, subset) -> bool:
	
	return reduce(and_, [i in superset for i in subset])

superset = [3, 4, 5, 6]

subset = [4, 5]

not_subset = [4, 5, 7]


print(f"{subset} is in {superset}: {contains(superset,subset)}")

print(f"{not_subset} is in {superset}: {contains(superset,not_subset)}")

# q3 curried func power of num

def power(base):
  
  def inner(exponent):
   
    if exponent == 0:
    
      return 1
    
    else:
    
      return base * inner(exponent - 1)
  
  return inner


square = power(2)  

cube = power(3)  

result = square(5)  

another_result = cube(4)  

print(result)
print(another_result)

# Q4 palindrome 

def is_palindrome(check_type=str):
 
  def inner(text):
   
   processed_text = check_type(text).lower().replace(" ", "")
   
    return processed_text == processed_text[::-1]

  return inner

# Q5 hypotenuse 




