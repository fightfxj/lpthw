Notes for Learn Python the Hard Way
====

## 2013.1.30

### Set enviroment: 

    [Environment]::SetEnvironmentVariable("Path", "$env:Path;C:\Python27", "User")

### Set coding for Python scripts

    # -*- coding: utf-8 -*-

## 2013.2.20

### format sequences:

e.g:

    my_teeth = 'White'
    my_hair = 'Brown'
    print "He's got %s eyes and %s hair." % (my_eyes, my_hair)

What is the difference between %r and %s?:

Use the %r for debugging, since it displays the "raw" data of the variable.
e.g:
    
    x = "There are %d types of people." % 10
    binary = "binary"
    do_not = "don't"
    y = "Those who know %s and those who %s." % (binary, do_not)
    print "I said: %r." % x
    print "I also said: '%s'." % y
        
### Comma can break the code into two lines

e.g, the following outpout will appear on the same line

    print "First",
    print "second"
    
### Use raw_input():

    print "How old are you?",
    age = raw_input()
    print "So, you're %r old." % (age)

or

    age = int(raw_input("How old are you? "))
    print "So, you're %r old." % (age)
    
### Check documents:

    python -m pydoc raw_input

## 2013.2.24

### input from the command line:

  
    from sys import argv

    script, first, second, third = argv

    print "The script is called:", script
    print "Your first variable is:", first
    print "Your second variable is:", second
    print "Your third variable is:", third
  
### read file:

    from sys import argv
    
    script, filename = argv
    
    txt = open(filename)
    
    print "Here's your file %r:" % filename
    print txt.read()

### comments related with file:

* close -- Closes the file. Like File->Save.. in your editor.
* read -- Reads the contents of the file, you can assign the result to a variable.
* readline -- Reads just one line of a text file.
* truncate -- Empties the file, watch out if you care about the file.
* write(stuff) -- Writes stuff to the file.

e.g open a file to write:

    from sys import argv
    from os.path import exists
    
    script, from_file, to_file = argv
    
    print "Copying from %s to %s" % (from_file, to_file)
    
    in_file = open(from_file).read()  
    
    print "The input file is %d bytes long" % len(indata)    
    print "Does the output file exist? %r" % exists(to_file)

    out_file = open(to_file, 'w')
    out_file.write(indata)
        
    out_file.close()
    in_file.close()

### functions definition:

Arguments can be integrated:

    def print_two(*args):
        arg1, arg2 = args
        print "arg1: %r, arg2: %r" % (arg1, arg2)
    
    # ok, that *args is actually pointless, we can just do this
    def print_two_again(arg1, arg2):
        print "arg1: %r, arg2: %r" % (arg1, arg2)

## 2013.2.25

### if, elif, else

    if cars > people:
        print "We should take the cars."
    elif cars < people:
        print "We should not take the cars."
    else:
        print "We can't decide."
        
### list and for-loop

    change = [1, 'pennies', 2, 'dimes', 3, 'quarters']
    for i in change:
        print "I got %r" % i
    
    elements = []
    for i in range(0, 6):
        print "Adding %d to the list." % i
        # append is a function that lists understand
        elements.append(i)
        
### while-loop

    i = 0
    numbers = []
    
    while i < 6:
        print "At the top i is %d" % i
        numbers.append(i)
    
        i = i + 1
        print "Numbers now: ", numbers
        
### Rules For If-Statements

1. Every if-statement must have an else.
2. If this else should never be run because it doesn't make sense, then you must use a die function in the else that prints out an error message and dies, just like we did in the last exercise. This will find many errors.
3. Never nest if-statements more than 2 deep and always try to do them 1 deep. This means if you put an if in an if then you should be looking to move that second if into another function.

### Rules For Loops

1. Use a while-loop only to loop forever, and that means probably never. This only applies to Python, other languages are different.
2. Use a for-loop for all other kinds of looping, especially if there is a fixed or limited number of things to loop over.

### dictionary

    stuff = {'name': 'Zed', 'age': 36, 'height': 6*12+2}
    print stuff['name']
    stuff[1] = "Wow"
    print stuff
    del stuff[1]
    print stuff

### for-loop over dictionary

    states = {
        'Oregon': 'OR',
        'Florida': 'FL',
        'California': 'CA',
        'New York': 'NY',
        'Michigan': 'MI'
    }
    for state, abbrev in states.items():
        print "%s is abbreviated %s" % (state, abbrev)
    
    # get a state with a default value
    state = states.get('Texas', None)
    if not state:
        print "Sorry, no Texas."
    
### ordered dic

collections.OrderedDict

### get things from things

    # dict style
    mystuff['apples']
    
    # module style
    mystuff.apples()
    print mystuff.tangerine
    
    # class style
    thing = MyStuff()   # "instantiate" operation
    thing.apples()
    print thing.tangerine
    
### phases in class

* class X(Y)

    "Make a class named X that is-a Y."
* class X(object): def __init__(self, J)

    "class X has-a __init__ that takes self and J parameters."
* class X(object): def M(self, J)

    "class X has-a function named M that takes self and J parameters."
* foo = X()

    "Set foo to an instance of class X."
* foo.M(J)

    "From foo get the M function, and call it with parameters self, J."
* foo.K = Q

    "From foo get the K attribute and set it to Q."
    
### example of is-a

    ## Person is-a object
    class Person(object):
    
        def __init__(self, name):
            ## Person has-a name
            self.name = name
    
            ## Person has-a pet of some kind
            self.pet = None
    
    ## Employee is-a Person
    class Employee(Person):
    
        def __init__(self, name, salary):
            ## The name of the Employee is the same as the Person
            super(Employee, self).__init__(name)
            ## Employee has-a salary
            self.salary = salary

### the process of designing objects

1. Write or draw about the problem.
2. Extract key concepts from #1 and research them.
3. Create a class hierarchy and object map for the concepts.
4. Code the classes and a test to run them.
5. Repeat and refine.

### When To Use Inheritance Or Composition

1. Avoid multiple inheritance at all costs, as it's too complex to be useful reliably. If you're stuck with it, then be prepared to know the class hierarchy and spend time finding where everything is coming from.
2. Use composition to package up code into modules that is used in many different unrelated places and situations.
3. Use inheritance only when there are clearly related reusable pieces of code that fit under a single common concept, or if you have to because of something you're using.

