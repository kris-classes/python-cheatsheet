Python Cheatsheet 
<sup>[Fork this on GitHub](https://github.com/BisratYalew/python-cheatsheet)
</sup>
=================



## About
I have created this cheatsheet with intention of collecting python code snippets that I used on my projects/programs and from the internet for reducing coding hours and making other developers life easier.


# Basic

## [String](#String)

- [strip](#strip())
- [lstrip](#lstrip())
- [rstrip](#rstrip())
- [upper](#the-upper(),-lower(),-isupper(),-islower()-string-methods)
- [isupper](#the-upper(),-lower(),-isupper(),-islower()-string-methods)
- [lower](#the-upper(),-lower(),-isupper(),-islower()-string-methods)
- [islower](#the-upper(),-lower(),-isupper(),-islower()-string-methods)
- [in](#the-upper(),-lower(),-isupper(),-islower()-string-methods)
- [not in](#the-upper(),-lower(),-isupper(),-islower()-string-methods)

- [ord](#ord())
- [Template Strings](#template-strings)
- [Pyperclip module](#pyperclip)

<br><br>

# Intermediate


## [File](#file)


- [Read File](#read-a-file)
- [Write a File](#write-a-file)
- [Copy File](#copy-a-file)
- [Move File](#move-a-file)
- [Readline](#readline)

<br><br>



# Advanced

- [Regular Expressions](#regular-expressions)
- [Socket](#socket)




<br><br><br><br>




String
------
### strip()

```python
>>> check = '    Python is great!     '  # removes characters from both left and right based on the argument
>>> check.strip()
'Python is great'
```

### lstrip()
```python
>>> check.lstrip()
'Python is great!     ' ## removes characters from left based on the argument
```

### rstrip()
```python
>>> check.rstrip() ## removes characters from left based on the argument
'     Python is great!'
```



### ord()
```python
>>> ord('A'), ord('Z')
(65, 90)
>>> ord('0'), ord('9')
(48, 57)
>>> ord('a'), ord('z')
(97, 122)
>>> ord('B'), ord('Y')
(66, 89)
```


#### The in and not in Operators with string
```python 
>>> 'Python' in 'Python is great!'
True
>>> 'python' in 'Python'
True
>>> 'PYTHON' in 'Python is great!'
False
>>> '' in 'python'
True
>>> 'Python' not in 'python and javascript' ## Matches case
False
```

#### The in and not in Operators with list
```python 
>>> a = ['P', 'y', 't', 'h', 'o', 'n']
>>> 'p' in a
False
>>> 'P' in a
True
>>> 'o' in a
True

## On Integers List
>>> a = [1, 2, 3, 5]
>>> 5 in a
True
>>> 4 in a
False
>>> 1 in a
True
```


### The upper(), lower(), isupper(), islower() string methods

```python
>>> check = 'Hello world!'
>>> check = check.lower() ## converts check to lower
>>> check
'hello world!'
>>> check = check.isupper() ## checks whether check variable is upper or not. 
False
>>> check = check.islower() ## checks whether check variable is upper or not. 
True
>>> check = check.upper() ## converts check to upper
>>> check
'HELLO WORLD!'
>>> check = check.isupper() ## checks whether check variable is upper or not. 
True
>>> check = check.islower() ## checks whether check variable is upper or not. 
False
```


### Template Strings
##### <i>Template strings are a simpler mechanism which are used to handle format strings generated by users</i>

```python
>>> from string import Template
>>> language = 'Python'
>>> t = Template('$name is great!')
>>> t.substitute(name=language) ## Substitutes name with language variable
'Python is great!'
```

### Pyperclip
##### <i>Pyperclip is python library that help us easily copy and paste string</i>

##### First Install it using pip

```
pip install pyperclip
```

```python
>>> import pyperclip
>>> pyperclip.copy('Hello World') ## Copy Hello World
>>> pyperclip.paste()
'Hello World'
```

<br><br>


# Intermediate

## File

### Read a file
### In Python 3, If files do not open in binary mode, the encoding will be determined by ```locale.getpreferredencoding(False)``` or user's input.
```python
>>> with open("/etc/hosts", encoding="utf-8") as f:
...     content = f.read()
...
>>> print(type(content))
<class 'str'>

```
#### In python3 binary mode
``` python
>>> with open("/etc/hosts", "rb") as f:
...     content = f.read()
...
>>> print(type(content))
<class 'bytes'>
```


#### In python2
```python
## The content of the file is a byte string, not a Unicode string.
>>> with open("/etc/passwd") as f:
...    content = f.read()
>>> print(type(content))
<type 'str'>
>>> print(type(content.decode("utf-8")))
<type 'unicode'>
```


### Write a File
```python
>>> file_content = "Python is great!"
>>> with open("check.txt", "w") as file:
...     file.write(file_content)
```


### Copy a file
```python
>>> from distutils.file_util import copy_file
>>> copy_file("a", "b")
('b', 1)
```
### Move a File
```python
>>> from distutils.file_util import move_file
>>> move_file("./a", "./b")
'./b'
```

### Readline
```python
## If you are not using linux machine try to change the file path to read
>>> with open("/etc/hosts") as f:
...     for line in f:
...         print(line, end='')
...
127.0.0.1       localhost
255.255.255.255     broadcasthost
::1             localhost
```


<br><br>



# Advanced

## Regular Expressions
Non-special chars match themselves. Exceptions are special characters:

```
\       Escape special char or start a sequence.
```

```
.       Match any char except newline, see re.DOTALL
```
```
^       Match start of the string, see 
re.MULTILINE
```
```
$       Match end of the string, see re.MULTILINE
```
```
[]      Enclose a set of matchable chars
```
```
R|S     Match either regex R or regex S.
```
```
()      Create capture group, & indicate precedence
After '[', enclose a set, the only special chars are:
```
```
]   End the set, if not the first char
```
```
-   A range, eg. a-c matches a, b or c
```
```
^   Negate the set only if it is the 1st char
```
## Regular Expression Examples
### re.findall()
```python
# split all string from a sentence
>>> import re
>>> source = "Python is great!"
>>> re.findall('[\w]+', source)
['Python', 'is', 'great!']
```

### Match hex color value
```python 
>>> re.match('^#?([a-f0-9]{6}|[a-f0-9]{3})$', '#ffffff')
<_sre.SRE_Match object at 0x0000000002F04120>
>>> re.match('^#?([a-f0-9]{6}|[a-f0-9]{3})$', '#cdcdcd')
<_sre.SRE_Match object at 0x0000000002EA3160>
```


### Match username doesn't have any special characters
```python
>>> re.match('^[a-zA-Z0-9-_]{3,16}$', 'Check') is not None
True
>>> re.match('^\w|[-_]{3,16}$', 'che%ck') is not None
False
```


### Match email address format
```python
re.match('^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$',
...          'check@example.com')
<_sre.SRE_Match object at 0x0000000002EA3180>
```

<br>
<br>

## Contributing

Feel free to contribute and send pull requests

## Author

* [BisratYalew](https://bisratyalew.github.io)

