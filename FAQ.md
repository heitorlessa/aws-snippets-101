
**Q: How do I store a multiline string in a variable and preserve its format?**

**A:** Use `""" or '''` when defining its value.

```python

multiple_lines = """
    This is a long string that has tabs and spaces
    Including an additional line
         <<THE END>>
"""

print(multiple_lines)
```


**Q: Where can I find all built-in functions for Python?**

**A:** ``docs.python.org`` is a great resource to start with and different ``Python`` versions may have differences in what's available.

For that, here are the links for both of them:

* [Python 2.7](https://docs.python.org/2.7/library/functions.html)
* [Python 3](https://docs.python.org/3/library/functions.html)

**Q: How do I take user's input?**

**A:** You can use ``input`` built-in function

```python
name = input("Hooman, tell my your name: ")
```

**Q: Why do I get ``NameError`` to whatever I input as an answer to above?**

**A:** ``input`` tries to evaluate input data (expression) and an error will be generated if it's unable to evaluate. You can solve this problem in 2 ways:

1. Add your answer between quotes as that will make it as a ``string``
2. Use ``raw_input`` instead as that will be taken care of

> NOTE: ``raw_input`` converts input data as string and doesn't try to evaluate input as an expression. In Python 3 raw_input has been removed and incorporate into input()

**Q: Looking at the docs I see lots of unknown words such as tuple, sequence, iterable, etc. Is there a page for those?**

**A:** Yep! You can find them and much more at [Python Glossary](https://docs.python.org/2.7/glossary.html)

**Q: Is there an easy way to find documentation about a module, function, built-in function, object?**

**A:** Yep! You can use ``help()`` built-in function. Let's say you're looking to understand how to use ``raw_input`` you can use

```python
help(raw_input)

# Once you learned you can put into practice

name = raw_input("Hooman, tell my your name: ")
```

**Q: If everything is an object, how do I find what methods are available within that object?**

**A:** The secret is to use a super helpful built-in function called [``dir``](https://docs.python.org/2/tutorial/modules.html#the-dir-function). You can use it everywhere given the statement _"Everything is an object in Python"_ - Here are some examples

```python
# Create a variable and try to find out what's available to you

a = "Hey!"
dir(a)

# Ignore anything that starts with '_' or '__' at this stage
# Why don't you give a try to any method and find out how to use it

help(a.capitalize)

# Same is true for modules you import, etc.

import os
dir(os)
help(os.environ)

# You got the idea ;)
```

**Q: How do I create a function?**

**A:** You can create using the keyword ``def`` as follows:

```python

def my_function():
    print("Hooman: I'm a function!")

# To confirm your function really is what I'm telling you it is: Asking the interpreter to evaluate it

my_function
<function my_function at 0x....>

# Try call your function by adding `()`

my_function()
```

**Q: How do I document a function and how others can see that?**

**A:** Similarly to the way you'd create a multiline string you can use the same technique right after the function definition - This is called ``docstring``

```python

def my_function(misspelled=True):
    """Hooman function

    This function will return `Human` misspelled just like a cat

    > my_function()

    If you want to help this poor fella and you can call it with the following argument

    > my_function(misspelled=False)
    > my_function(False)

    """

    msg = "Hooman"

    if not misspelled:
        msg = "Human"
    
    return msg

# Try to call help on this function now
help(my_function)

# Print function's docstring -- Useful when you want to explicitly wanna call out how this function should be called in case of an error

print(my_function.__doc__)

```



**Q: How do I pass data into my function?**

**A:** During your function definition you'll need to pass what arguments you're expecting through parameters. Uh oh! I think that's confusing let me break it down:

* ``Parameter`` is what a function takes while it is being called
* ``Arguments`` is what the caller ("the hooman") of that function passes

Let's see an example of that to clarify that:

```python
def my_function(parameter):
    print("Argument received --> ", parameter)

my_function("My argument...")

```
 
**Something you should know**: Regardless of how many parameters you add the user must pass arguments in the same order - Watch out for that.

**Q: How do I allow an user to pass an infinite number of arguments similar to ``ls`` and other UNIX tools?**

**A:** You'll have to use ``*`` and ``**`` respectively - This makes Python to understand [it's an optional/keyword parameter](https://docs.python.org/2/faq/programming.html#how-can-i-pass-optional-or-keyword-parameters-from-one-function-to-another)

```python
def my_function(*params):
    print("Printing my params...")
    
    # all arguments will be contained in a tuple (params) so we iterate that to print what's in it for us
    for arg in params:
        print("Argument --> ", arg)

my_function("Param1", "Param2", "Param3")

# Cool thing is that given this is a optional parameter you can call your function without any arguments at all

my_function()

```

**Something you should know**: If you ever try to mix normal parameter, keywords with a positional argument/keyword you'll have to put them as the last parameters in your function, nothing should come after them

**Q: How do I assign a default parameter value if an user suppressed when calling my function?**

**A:** This is a scenario where you don't want to use `*optional` arguments and instead want to ensure your parameter has a certain value if `None` was given to replace it. 

```python
def my_function(param1, debug=False, region="eu-west-1"):
    if not debug:
        print("Debug hasn't been enabled... let's carry on)
    
    if "eu-west-1" in region:
        print("No region was chosen... defaulting to Ireland")

```




**Q: I'm coming from other languages and I can't seem to find switch/case - Why is that?**

**A:** Python doesn't have ``switch/case`` and you'd have to do a bunch of ``if`` statements to achieve that


```python
if condition:
    return "something"
elif condition 2:
    return "something else"
elif condition 3:
    return "another thing"
else:
    return "other thing"
```

**Q: If I wanted to run something X times I'd use `seq` in shell, how do I do that in Python?**

**A:** You can use `range` that is the equivalent to `seq` - Here's a sample

```python

for sequence in range(1, 5):
    print("Sequence is....", sequence)

```

**Q: How does Python handle string formatting?**

**A:** Python has a number of formatters and the most commonly used is ``format`` - Check this [Unofficial page describing the various forms](https://pyformat.info/)


```python

# Simple formatting

print("{}, who are you?".format("Hooman"))

# It also works for numbers if you need to

print("I have {} EC2 instances named Batman. What happened?".format(1000))

# In case you have many of them, you can name them after whatever makes sense in your code

print("{person}, who are you? I have {amount} EC2 instances named Batman. {question}".format(
    person="Hooman",
    amount=1000,
    question="What's wrong?"
))

# If you prefer numbers you can also use them as long as it's in order

print("{0}, {1}".format(
    "Hooman",
    "Who are you?"
))

```

**Q: Is there a shorter version for simple `if` statement for simple evaluations?**

**A:** Yes - The term you're looking for is often searched as: `one-liner if statement`, `ternary operator`

```python

print("One line" if True else False)

# No else

region = "eu-west-1"

if "eu" in region: print("European region")

```


## Resources

* [Python Bites](https://python.swaroopch.com/)

* [Official Python Docs FAQ](https://docs.python.org/2/faq/programming.html)
* [TutorialPoint - Defining a function](https://www.tutorialspoint.com/python/python_functions.htm)
* [VSCode for Python Development](https://medium.com/small-things-about-python/use-visual-studio-code-for-python-development-5d59c8479add)
* [Dan Bader - Code Review and useful tutorials](https://dbader.org/)
* [String Formatting Plain and Clear](https://pyformat.info/)
* [Python Module of the Week](http://pymotw.com/2/contents.html)
* [Python Tricks for Beginners](https://www.codementor.io/sumit12dec/python-tricks-for-beginners-du107t193)
* [First steps with Python Boto on AWS](https://linuxacademy.com/howtoguides/posts/show/topic/14209-automating-aws-with-python-and-boto3)
* [Python Boto - S3 File Handling](https://dzone.com/articles/file-handling-in-amazon-s3-with-python-boto-librar)
* [Python Click](http://click.pocoo.org/5/)
* [Python - Plotly (Graphs)](https://plot.ly/python/offline/)
* [Python Pandas - In-memory](http://pandas.pydata.org/)

**Windows only**

* [Bpython on Windows](https://gist.github.com/heitorlessa/20bb6b6826878f01b0c5cbb1e6bf0982)
* [Better Command Prompt for Windows - Cmder](http://cmder.net/)
* [Zsh/Bash with batteries included for Windows - Babuum](http://babun.github.io/)

## One liners

> Quick HTTP Server

```bash

# Python 2
python -m SimpleHTTPServer

# Python 3
python -m http.server

```

> Quick pretty print JSON parse

```bash

cat file.json | python -m json.tool

```

> Quick profiling  

```bash

python -m cProfile python_script.py

```

---

## Possible exercises

**Look up all EC2 Instances and get something**

Ideas: Print VPC ID, Private IP Address and Public IP Address if there's any
Why Not: Create instance with fake names

```python
# Dirty EC2 Catch all if anyone gets stuck

import boto3
ec2 = boto3.resource('ec2')
for instance in ec2.instances.all():
    print instance.id
```

**Launch an EC2 Instance and retrieve its ID**

Ideas: Look up for VPC, Subnet and Security Group before launching it. Create Key Pair before creating it. Ask user how many EC2 Instances should be launched
Why Not: Only print Instance Info when instance is ready

**Create S3 Bucket and initial structure**

Ideas: Read structure from somewhere (file, etc.), Enable versioning, Delete bucket
Why Not: Create folders/files with fake and random names programmatically

**Automate AWS Console Experience**

Ideas: Log in and check if credentials are valid
Why Not: Close an AWS Account

> NOTE: You need [chromedriver](https://sites.google.com/a/chromium.org/chromedriver/downloads) binary in the PATH or explicitly call out how to find it