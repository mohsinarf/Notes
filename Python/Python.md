## Strings in Python
```
# String concatination
print("This is a sample \" string." + phrase)

# Convert string into upper case
print(phrase.upper())

# Print True if string is upper case
print(phrase.isupper())

# Get a specific characte from a string 
print(phrase[3]);

# Get the position of a substring in the main string
print(phrase.index("another"))

# Replace the part of a string with another string
print(phrase.replace("is", "was"))
```
## Number in Python
```
from math import *

num = 10
num2 = -20

# int to string  conversion
print("my favourite number:" + str(num))

# absolute value
print(abs(num2))

# exponent
print(pow(3,2))

 # return the largest number
print(max(1, 2, 0, 23))

# Roundoff a number
print(round(3.7))

# Squre root of number
print(sqrt(25))
```
## Geting inputs from the user
```
num1 = input("Enter first number :")
num2 = input("Enter second number :")

result = float(num1) + float(num2)

print("Summation of both number is ", result)
```
## Comments
```
# This is a single line comment.

'''
This is a multi line 
comment.
'''
```
## List
```
friends = ["Mike", "Jim", "Harry", "Kim"]
relatives = ["Bob", "Tom"]
# Print whole list
print(friends)
# Print elements between 0  ~ 2
print(friends[0:2])
# Print elements from 3 to list end
print(friends[3:])
# Print last element
print(friends[-1])

friends.extend(relatives)

friends.append("Mindy")

friends.insert(1, "Nancy")

friends.remove("Harry")

# Remove the last elements from the list 
friends.pop()

print(friends.index("Bob"))

print(friends.count("Jim"))

friends.sort()
print(friends)

friends.reverse()
print(friends)

friends.clear()
```
## Tuples
A tuple is a sequence of immutable Python objects. Tuples are sequences, just like lists. The differences between tuples and lists are, the tuples cannot be changed unlike lists
```
# Elements in tuples are immutable
coordinates = (2, 3, 8)
print(coordinates[1])
```

## Functions
```
def cube(num):
    return pow(num, 3)

number = input("Enter your number :")
result = cube(int(number))
print("Cube of "+str(number) + " is equal to " + str(result))
```

## Conditional statements
```
is_male = False
is_tall = True

if is_male and is_tall:
    print("You are male and tall. ")
    
elif is_male or is_tall:
    print("You are either male or tall. ")

else:
    print("You are neither male nor tall.")

def max_num(num1, num2, num3):
    if num1 >= num2 and num1 >= num3:
        print(num1)
    elif num2 >= num1 and num2 >= num3:
        print(num2)
    else:
        print(num3)

max_num(40,14,20)
```

## For loops
```
name = "Mohsin Ali"
for letter in name:
    print(letter)

friends = ["Jim", "Mark", "Tom", "Cindy"]
for friend in friends:
    print(friend)

for num in range(10):
    print(num)

for num in range(12, 19):
    print(num)
```
```
if letter in "AEIOUaeiou":
    print("Vowel detected.")
```

## Iterating nested loops
```
number_grid = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

for row in number_grid:
    for col in row:
        print(col)
```

## Try/ Except
```
try:
    result = 10/0
    number = int(input("Enter your number: "))
    print(number)
except ValueError as err:
    print(err)
except ZeroDivisionError as err:
    print(err)
```

## Dictionaries
```
calender = {
    1:"January",
    2:"Februray",
    3:"March",
    4:"April",
    5:"May",
    6:"June",
    7:"July",
    8:"August",
    9:"September",
    10:"October",
    11:"November",
    12:"December"
}   
print(calender[6])
print(calender.get(13, "Not a valid key."))
```
## Guessing game
```
secret_word = "Ali"
input_word  = ""
guess_limit = 5
out_of_guesses = False
count = 0

while secret_word != input_word and not(out_of_guesses):
    input_word = input("Guess the name : ")
    count +=1
    if guess_limit == count:
        out_of_guesses = True
    
if out_of_guesses:
    print("You lost. Out of guesses.")
else:
    print("You won!")
```

## Class
```
class student:
    def __init__(self, name, age, gpa, is_on_probation):
        self.name = name
        self.age  = age
        self.gpa  = gpa
        self.is_on_probation = is_on_probation

    def is_on_honor(self):
        if self.gpa <= 3.5:
            return True
        else:
            return False

```

```
from student import student

student1 = student("Jim", 25, 2.6, False)
student2 = student("Mark", 23, 3.7, True)

print(student1.is_on_probation)
print(student2.is_on_probation)
```
