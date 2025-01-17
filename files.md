# File


- [Read File](#read-a-file)
- [Write a File](#write-a-file)
- [Copy File](#copy-a-file)
- [Move File](#move-a-file)
- [Readline](#readline)

### open a file without using `with` keyword
```python
f = open("passwords.txt")
lines = f.readlines()
f.close()
```
<br><br>
### Read a file
### In Python 3, If files do not open in binary mode, the encoding will be determined by ```locale.getpreferredencoding(False)``` or user's input.
```python
>>> with open("/etc/hosts") as f:
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

### [Back To Top](#file)
