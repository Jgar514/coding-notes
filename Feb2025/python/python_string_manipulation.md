# Learn String Manipulation by Buiding a Cipher
source: freeCodeCamp - Scientific Computing with Python

## Variables

Variables are an essential part of Python and any programming language. A variable is a name that references or points to an object. You can declare a variable by writing the variable name on the left side of the assignment operator = and specifying the value to assign to that variable on the right side of the assignment operator:
  - variable_name = value
  - number = 5

## Strings

Variables can store values of different data types. You just assigned an integer value, but if you want to represent some text, you need to assign a string. Strings are sequences of characters enclosed by single or double quotes, but you cannot start a string with a single quote and end it with a double quote or vice versa

```python
string_1 = "I am a string"
string_2 = 'I am also a string'
string_3 = 'This is not valid"
```
## functions

### print()

You can use the built-in function print() to print the output of your code on the terminal.

Functions are reusable code blocks that you can call, or invoke, to run their code when you need them. To call a function, you just need to write a pair of parentheses next to its name. You will learn more about functions very soon.

### argument

An argument is an object or an expression passed to a function — added between the opening and closing parentheses — when it is called:
```python
greet = 'Hello!'
print(greet)
```
The code in the example above would print the string 'Hello!', which is the value of the variable greet passed to print() as the argument.

### numerical index

Each string character can be referenced by a numerical index. The index count starts at zero. So the first character of a string has an index of 0. For example, in the string 'Hello World', 'H' is at index 0, 'e' is at index 1, and so on.

Each character of a string can be accessed by using bracket notation. You need to write the variable name followed by square brackets and add the index of the character between the brackets:

```python
text = 'Hello World'
r = text[8]
```

You can also access string characters starting from the end of the string. The last character has an index of -1, the second to last -2 and so on.

### len() function
You can access the number of characters in a string with the built-in len() function.

```python
text = 'Hello World'
print(len(text))

# output is 11
```

### type()

Another useful built-in function is type(), which returns the data type of a variable. Modify your print() call to print the data type of text.

```python
text = 'Hello World'
print(type(text))

# output = <class 'str'>
```
  - this is telling that our variable is a string

## Variable Naming

Key aspects of variable naming in Python are:

- Some words are reserved keywords (e.g. for, while, True). They have a special meaning in Python, so you cannot use them for variable names.
- Variable names cannot start with a number, and they can only contain alpha-numeric characters or underscores.
- Variable names are case sensitive, i.e. my_var is different from my_Var and MY_VAR.
- Finally, it is a common convention to write variable names using snake_case, where each space is replaced by an underscore character and the words are written in lowercase letters.

## method

### .find()

You are going to use the .find() method to find the position in the alphabet of each letter in your message. A method is similar to a function, but it belongs to an object.

```python
sentence = 'My brain hurts!'
sentence.find('r')
```
Above, the .find() method is called on sentence (the string to search in), and 'r' (the character to locate) is passed as the argument. The sentence.find('r') call will return 4, which is the index of the first occurrence of 'r' in sentence.

```python
alphabet = 'abcdefghijklmnopqrstuvwxyz'
alphabet.find('z')
```
## Caesar cipher

The first kind of cipher you are going to build is called a Caesar cipher. Specifically, you will take each letter in your message, find its position in the alphabet, take the letter located after 3 positions in the alphabet, and replace the original letter with the new letter.

To implement this, you will use the .find() method discussed in the previous step. Modify your existing .find() call passing it text[0] as the argument instead of 'z'.
```python
text = 'Hello World'
shift = 3
alphabet = 'abcdefghijklmnopqrstuvwxyz'
alphabet.find(text[0])
```

The print() function gives you only an output in the console, but functions and methods can have a return value that you can use in your code.

```python
text = 'Hello World'
shift = 3
alphabet = 'abcdefghijklmnopqrstuvwxyz'
index = alphabet.find(text[0])
```
.find() returns the index of the matching character inside the string. If the character is not found, it returns -1. As you can see, the first character in text, uppercase 'H', is not found, since alphabet contains only lowercase letters.

You can transform a string into its lowercase equivalent with the .lower() method. Add another print() call to print text.lower() and see the output.

```python
text = 'Hello World'
shift = 3
alphabet = 'abcdefghijklmnopqrstuvwxyz'
index = alphabet.find(text[0])
print(index)
print(text.lower())

# output = -1
# output = hello world
```
Remove the last print() call. Then, instead of text[0], pass text[0].lower() as the argument to your .find() call and see the output.

```python
text = 'Hello World'
shift = 3
alphabet = 'abcdefghijklmnopqrstuvwxyz'
index = alphabet.find(text[0].lower())
print(index)

# output = 7
```
### operators

As you can see from the output, 'h' is at index 7 in the alphabet string. Now you need to find the letter at index 7 plus the value of shift. For that, you can use the addition operator, +, in the same way you would use it for a mathematical addition.

Modify your shifted variable so that it stores the value of alphabet at index index + shift.

```python
text = 'Hello World'
shift = 3
alphabet = 'abcdefghijklmnopqrstuvwxyz'
index = alphabet.find(text[0].lower())
print(index)
shifted = alphabet[index + shift]
print(shifted)
```

