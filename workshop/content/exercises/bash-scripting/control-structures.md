With control structures you can control the execution of Linux commands in a shell script. A control structure consists of two components: *a test and commands*. 
- **test**: you can compare strings, integers, and logical operations.
- **commands**: the commands for control structures can be while, for, case, if, and if/else statements.

The two different kinds of control structures are loops and conditional.
- **loops**: while, for, for-in
- **conditional**: is an expression that evaluates to a Boolean value - *true or false*; if and case statements are examples of a condition.

## IF STATEMENT

IF statement allows you to make a decision in the program based on conditions specified. If the condition is met then the program will execute the lines of code specified otherwise, the program will execute the other tasks specified. As you see in the example below for the structure of an *if statement* **NOTE**: that you finish off the block of code with *fi* 

A single decision:
```
if <condition>
  then
    # lines of code goes here
  fi 
```

A double decision:
```
if <condition>
  then
    # lines of code if condition is met
  else
    # lines of code if condition is not met
  fi
```

Multiple conditions:
```
if <condition1>
  then
    # lines of code for conditon 1
  elif <condition2>
  then
    # lines of code for condition 2
  else
    # lines of code if condition is not met
  fi
```

Lets try a simple if/then statement within a bash script that will check if a file exists or not. 

```execute
cat << EOF >> simplescript.sh
#!/bin/bash
cd
  ls
  if [ -e simplescript.sh ]
  then
    echo "file exists!"
  else
    echo "file does not exist!"
  fi
EOF
```
Once this code is copied into the terminal and saved as *simplescript.sh* then you can change the permissions to execute the script. 

```execute
chmod +x simplescript.sh 
```
check to see the file is executable:
```execute
ll
```

execute the script:
```execute
./simplescript.sh 
```

In this example script, the `[ -e simplescript.sh ]` condition calls a utility called test and checks to see if the file called "simplescript" exists ( **note:** the -e option checks for regular files). If the test returns a value of `TRUE` the block of code immediately below is executed. If the test returns a value of `FALSE` then the statement under the else portion is executed. 

#### **if/then/else options:**
- -d checks to see if the specified file exists and is a directory
- -e checks to see if the specified file exists
- -f checks to see if the specified file exists and is a regular file
- -G checks to see if the specified file exists and is owned by a group
- -L checks to see if the specified file exists and if it is a symbolic link
- -r checks to see if the specified file exists and if the read permission is granted
- -w checks to see if the specified file exists and if the write permission is granted
- -x checks to see if the specified file exists and if the execute permission is granted

## CASE STRUCTURES

The case structure really is an enhanced version of the if/then statement. The if/then statement works if we have a condition that can be evaluated in one of two ways (true or false). However, in cases with conditions that could be evaluated in many different ways you would want to use the case statement. 

#### The syntax for a case structure:
```
case <variable> in 
  response_1 ) commands
  ;;
  response_2 ) commands
  ;;
  response_3 ) commands
  ;;
  response_4 ) commands
  ;;
esac
```

Essentially the case statement compares the value of the variable to the list of responses within the case statement. 

For example, we could create a script that asks users what month they were born in. Depending on the response that is given, we give the script to provide a custom response using the case statement. Here is an example:

```execute 
cat << EOF >> case_example.sh
#!/bin/bash
# a simple script for a case statement

echo "What month where you born in?"
read MONTH

case "$MONTH" in
    January | February | March ) echo "Being born in" $MONTH" you were born in the first quarter."
    ;;
    April | May | June ) echo "Being born in" $MONTH" you were born in the second quarter."
    ;;
    July | August | September ) echo "Being born in" $MONTH" you were born in the third quarter."
    ;;
    October | November | December ) echo "Being born in" $MONTH" you were born in the last quarter."
    ;;
    * ) echo "Sorry, that month is invalid."
    ;;
esac
exit 0
EOF
```
```execute
chmod +x case_example.sh
```
```execute
ll
```
```execute
./case_example.sh
```