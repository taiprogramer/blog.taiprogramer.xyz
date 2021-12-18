
[//]: <> (SPDX-License-Identifier: CC0-1.0)
[//]: <> (Author: Huynh Van Tai aka taiprogramer)
[//]: <> (Website: https://www.taiprogramer.xyz)
[//]: <> (Because Windows uses CRLF as line-break, Linux is using only LF. So,
to make Windows users happy [that's you, my little world, the first person who
receives this document], I convert LF to CRLF. The world is a mess. We need to
talk to work together to build a better world for our new generation, peace.)
[//]: <> (Compile:)
[//]: <> (pandoc -V papersize:a4 -f gfm -o python3_thebasis.pdf python3_thebasis.md)
[//]: <> (Date created: Dec 15 2021)
[//]: <> (Last modified: Dec 18 2021)

# Python3 Cheatsheet: The Basis

**Disclaimer:**
The document author has published this document with the hope that it may be
helpful to others. However, the author does not guarantee that all information
contained in this document is correct or accurate. There is no warranty,
expressed or implied, of merchantability or fitness for any purpose. The author
does not assume any liability or responsibility for using the information
contained in this document.

**Date created**: Dec 15 2021

**Last modified:** Dec 18 2021


## Things to remember

- Thank Guido van Rossum for creating a beautiful programming language.
- Python is a dynamic typing language. (You don’t need to specify the type of
  the variable. The variable can be anything. If you want to denote the data
  type for your big project, from Python3.6 you can)
- Space is important.
- Use .editorconfig to make your codebase consistent and your partners happy.

## If-else

```py
name = "Guido van Rossum"

if name == "Le Dao": # part 1 (can standalone)
    print("My little world!.")
elif name == "Guido van Rossum": # part 2 (can be multiple)
    print("He is the creator of Python programming language.")
else: # part 3 (must be only one)
    print("Just a person exists on this planet.")
```

## Loop

- while

```py
x = 1
while x <= 10:
    print("Guido van Rossum.")
    x += 1

# infinity loop
while True:
    # do something.
    break # to break this loop if needed
```

- for

```py
# print "I love you" 10 times.
for i in range(10):
    print("I love you.")

# loop through a list.
my_num = [5, 7]
for num in my_num:
    # do everything with every single num.
```

## Logical operators

Python logical operators: **and**, **or**, **not**. You can use them to combine
conditional statements.

```py
gpa = 3.99

if gpa > 3.2 and gpa <= 4:
    print("You have a high GPA. Ya. That's it.",
            "A high score doesn't mean anything.",
            "If you can't solve problems or help others, you suck.")
```

## Function

Function in Python can return anything. There is no need to specify the return
type of function.

- Without argument

```py
def say_hello():
    print("Hello, World!")
```

- With argument

```py
def say_hello(name):
    print("Hello,", name)

say_hello("Donald J Trump") # output: Hello, Donald J Trump
```

- Return something

```py
def sum(a, b):
    return a + b

# call
print(sum(5, 7)) # output: 12
print(sum("7", "9")) # output: "79", funny, right?
```

## Class

Examples say a thousand words.

```py
class Person:
    # constructor
    def __init__(self, name, dob, sex):
        # the first argument ("self") represents the current object.
        # The name of the first argument can be anything. But use "self" to make
        # others happy.
        self.name = name
        self.dob = dob
        self.sex = sex

    # Define methods (A method is a function that an instance of a class calls
    # it (obj.method_name))
    # It is humanity. Don't be shy.
    def eat(self, food):
        print(f"{self.name} is eating {food}.")
    def sleep(self, hour):
        print(f"{self.name} is sleeping about {hour} hour(s).")
    def make_love(self, person, duration):
        print(f"{self.name} is making love with {person.name} in {duration}",
        "minutes.")
    def shit(self):
        print(f"{self.name} is shitting.")
    def __str__(self): # define a string to print when print(obj) called.
        return f"My name is {self.name}. My birthday is {self.dob}."
# use of the class Person
tai = Person(name="Tai", dob="05/05/2000", sex="Male")
dao = Person(name="Dao", dob="05/05/2000", sex="Female")

print(tai) # print the value that returned from __str__
# output: My name is Tai. My birthday is 05/05/2000.

tai.eat("Apple") # output: Tai is eating Apple.
dao.eat("Banh trang tron") # output: Dao is eating Banh trang tron.
tai.make_love(dao, 90) # output: Tai is making love with Dao in 90 minutes.
```

Now, your turn.

---

What chapters do you need to include in future documents?

- [ ] Built-in data structures.
- [ ] Type annotation.

---

This document is licensed under the Creative Commons Zero v1.0 Universal.

Examples, recipes, and other code in this document are additionally licensed
under the Unlicense.
