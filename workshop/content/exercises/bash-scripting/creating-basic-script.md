Bash scripts can be very basic to extremely complex. The previous example was a basic script that ran a couple commands such as *echo* and *date*. More complex scripts can have many components and commands that display text, adding commands, reading input, and using regular expressions to manipulate data to the need of the script. 

#### The first line

Always specify the shell within the first line of the file as mentioned before.

```execute
vim mysecondscript.sh
```

copy the below command to your terminal window that has *mysecondscript.sh* open.

```copy
#!/bin/bash
```

```execute
cat mysecondscript.sh
```

#### Adding comments

It is good practice to add comments to your script to let others know what the script's purpose is.

```execute
echo "A script that adds varibles together" >> mysecondscript.sh
```

```execute
cat mysecondscript.sh
```

#### Adding commands

Next you will add the commands that you will want to execute within the shell. Order matters and will read line by line one at a time. 

```execute
echo "
echo "Enter a number: "
read NUM1
echo "Enter a second number: "
read NUM2
TOTAL=$NUM1+$NUM2
echo "The sum of these numbers is " $TOTAL
exit 0
" >> mysecondscript.sh
```

- First you will notice the echo commands simply displaying string text asking for a number and a second number.
- Next you will notice the read command. This command will ask input from the user and store it within a variable specified. In this case there is NUM1 and NUM2 variables. 
- Then there is another variable named TOTAL. With this variable we are using simple math operators to add the two variables together. You will notice the dollar signs ($). The $ calls that specific variable.
- The last echo command will display the string of text and also call the TOTAL variable using the $. 

We will need to chmod the file to allow executable permissions:

```execute
chmod +x mysecondscript.sh
```

Then run the script:

```execute
./mysecondscript.sh
```

You will be asked to input a couple numbers then the numbers will be added together and display the total to your terminal. 