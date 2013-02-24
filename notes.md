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

### 