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
    
### Use row_input():

    print "How old are you?",
    age = raw_input()
    print "So, you're %r old." % (age)

or

    age = raw_input("How old are you? ")
    print "So, you're %r old." % (age)
    
### Check documents:

    python -m pydoc raw_input