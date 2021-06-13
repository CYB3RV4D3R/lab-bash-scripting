Bash scripts can be very basic to extremely complex. The previous example was a basic script that ran a couple commands such as *echo* and *date*. More complex scripts can have many components and commands that display text, adding commands, reading input, and using regular expressions to manipulate data to the need of the script. 

#### The first line

Always specify the shell within the first line of the file as mentioned before.

```execute
vim mysecondscript.sh
```

**copy the below command to your terminal window that has *mysecondscript.sh* open.**

```copy
#!/bin/bash
```
**Then type :wq to save your file and exit.**

```execute
cat mysecondscript.sh
```

#### Adding comments

It is good practice to add comments to your script to let others know what the script's purpose is.

```execute
echo "#A script that adds varibles together" >> mysecondscript.sh
```

```execute
cat mysecondscript.sh
```

#### Adding commands

Next you will add the commands that you will want to execute within the shell. Order matters and will read line by line one at a time. 

```execute
vim mysecondscript.sh
```
**first press i on your keyboard to get into insert mode within vim. This allows you to type, paste, and move to the next line. Put the cursor on the line below the comment which should be line 3 and paste the below contents.**

**copy the below contents within mysecondscript.sh right below the comment**

```copy
declare -i NUM1
declare -i NUM2
declare -i TOTAL
echo "Enter a number: "
read NUM1
echo "Enter a second number: "
read NUM2
TOTAL=$NUM1+$NUM2
echo "The sum of these numbers is " $TOTAL
exit 0
```
**very important now that you are in insert mode in vim you will need to press ESC to get out of insert mode so you can type in :wq to exit and save the file.**

- First you will notice the declare commands. This is needed as by not declaring the variables it will only print out the first and second number as a string and not as integers. 
- Next you will notice the echo commands simply displaying string text asking for a number and a second number.
- Next you will notice the read command. This command will ask input from the user and store it within a variable specified. In this case there is NUM1 and NUM2 variables. 
- Then there is another variable named TOTAL. With this variable we are using simple math operators to add the two variables together. You will notice the dollar signs ($). The $ calls that specific variable.
- The last echo command will display the string of text and also call the TOTAL variable using the $. 

Other interesting commands to know besides **:wq** is:

**:q!** to exit a file without saving it. Very useful when you did mistakes that you do not want to save and just want to quit the vim editor.

**:set paste** which allows you to disable automated indenting.

**:set nopaste** after you pasted the content with the previous set paste command.

**:set number** which allows you to set numbers along the side of the terminal. This allows you to quickly see which line a code snippit is on. This is greatly helpful for errors that occur specifying a line of code the error occured on. 

We will need to chmod the file to allow executable permissions:

```execute
chmod +x mysecondscript.sh
```

Then run the script:

```execute
./mysecondscript.sh
```

You will be asked to input a couple numbers then the numbers will be added together and display the total to your terminal. 