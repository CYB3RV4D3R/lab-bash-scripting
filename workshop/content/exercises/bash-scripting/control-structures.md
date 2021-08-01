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
cat << 'EOF' >> case_example.sh
#!/bin/bash
# a simple script for a case statement

echo "What month where you born in?"
read MONTH

case $MONTH in
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
Execute the command and be mindful it is case sensitive when you type your response:
```execute
./case_example.sh
```

## LOOPING STRUCTURES

There are three looping structures variants: *while loop*, *until loop*, and *for loop*.

- **while loop** executes over and over until a specified condition is no longer *true* and evaluates to *false*.

The structure of a while condition:
```
while condition
do
    list of commands
done
```

- **until loop** works in the opposite manner as the while loop, an until loop runs over and over as long as the condition is *false*. Once the condition evaluates to *true*, the until loop will end. 

The structure of a until condition:
```
until condition
do
    list of commands
done
```

- **for loop** loops only for a specific amount of times rather that the *while* and *until* loops loop indefinitely until a specified condition is met. A very common command that is used in *for* loops is the **seq** command to create a sequence of numbers to determine how many times it will loop. 

A for loop structure example:
```execute
cat << 'EOF' >> for_loop1.sh
#!/bin/bash
for i in `seq 15`
    do
        echo "The current number is $i."
    done
exit 0
EOF
```
```execute
chmod +x for_loop1.sh
```
```execute
./for_loop1.sh
```

**NOTE**: The greatest danger with looping structures is that it is possible to get stuck in the infinite loop. The condition never changes to a value that will break the loop. The only way to break out of an infinite loop is by pressing *CTRL+C*. 

Lets create a basic script with control structures!

Another *for loop* example:
```execute-2
cat << 'EOF' >> for_loop2.sh
#!/bin/bash
for i in $( ls ); do
    echo item: $i
done
exit 0
EOF
```
```execute-2
chmod +x for_loop2.sh
```
```execute-2
./for_loop2.sh
```

A *while loop* example:
```execute
cat << 'EOF' >> while_loop.sh
#!/bin/bash 
COUNTER=0
while [  $COUNTER -lt 10 ]; do
   echo The counter is $COUNTER
   let COUNTER=COUNTER+1 
done
EOF
```
```execute
chmod +x while_loop.sh
```
```execute
./while_loop.sh
```

A *until loop* example:
```execute
cat << 'EOF' >> until_loop.sh
#!/bin/bash 
COUNTER=20
until [  $COUNTER -lt 10 ]; do
   echo COUNTER $COUNTER
   let COUNTER-=1
done
EOF
```
```execute
chmod +x until_loop.sh
```
```execute
./until_loop.sh
```

## Now get to practicing your own control structures using the ones provided as guides to creating loop statements within your own bash scripts!