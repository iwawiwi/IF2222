# Python main program

```Python
# Python program to execute
# main directly
print ("Always executed")
 
if __name__ == "__main__":
    print ("Executed when invoked directly")
else:
    print ("Executed when imported")
```

Reference from [geeksforgeeks.org](https://www.geeksforgeeks.org/what-does-the-if-__name__-__main__-do/)

Python does not support explicit multiple constructors, yet there are some ways using which the multiple constructors can be achieved. If multiple `__init__` methods are written for the same class, then the latest one overwrites all the previous constructors. Look at the example below.

```Python
class example:
  
    def __init__(self):
        print("One")
  
    def __init__(self):
        print("Two")

    # this definition will be executed when 
    # an object is instantiated 
    def __init__(self):
        print("Three")
```

Reference from [geeksforgeeks.org](https://www.geeksforgeeks.org/what-is-a-clean-pythonic-way-to-have-multiple-constructors-in-python/)
