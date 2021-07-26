With control structures you can control the execution of Linux commands in a shell script. A control structure consists of two components: *a test and commands*. 
- **test**: you can compare strings, integers, and logical operations.
- **commands**: the commands for control structures can be while, for, case, if, and if/else statements.

The two different kinds of control structures are loops and conditional.
- **loops**: while, for, for-in
- **conditional**: is an expression that evaluates to a Boolean value - *true or false*; if and case statements are examples of a condition.

#### IF STATEMENT

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