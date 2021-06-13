In Linux you can create yourself some very powerful shell scripts that can run from your shell prompt. A shell script  is just a text file that contains a series of commands that are executed by the shell. This allows you to run multiple commands all at once and even be used to read input from the end user and make decisions based on that input. 

#### A basic script format

```copy
#!/bin/bash
#A simple script that displays the date and time
echo "The current time and date: "
date
exit 0
```

#### The components 

You notice there are several components within the basic script above. 

**#!/bin/bash** is the first line of a bash script that specifies which shell the script is to run. In this case, the */bin/bash* is specified so the shell that needs to be used is a bash shell while there are others such as */bin/sh*. You will specify to the needs of your environment. 

**#** is a comment that describes what the script does. Authors of bash scripts will utilize comments within their scripts to either remind themselves or others what the purpose behind the overall script and/or what a specific line of code does. 

**echo** this command displays a string that you specify within the double qoutes(" ") within the terminal window. 

**date** this commmand will display the date and time. This command will be displayed after the previous echo command.

**exit 0** lastly, this tells what the script should do when it is at the end of the script. The exit command with 0 simply tells the shell to exit the script.

#### Running the script

You will need to have the file permission of execute to run the script. With the execute permission assigned, the file can be allowed to execute from the shell prompt. First lets create the simple bash script in a text file. We append the **.sh** extension at the end of the file name to denote that it is a shell script. 

```execute
echo "
#!/bin/bash
#A simple script that displays the date and time
echo "The current time and date: "
date
exit 0
" >> myscript.sh
```

You can use the *cat* command to display the contents of that file to ensure the script contents were copied correctly. 

```execute
cat myscript.sh
```
#### The chmod command

Next we need to change the file permissions to allow execute so we can run the bash script within the shell prompt. You will use the *chmod* command with the *+x* option to allow execute. Other options include *r* for read permissions and *w* for write permissions. You also can specify you want the permission to only be available for the user. The *u* would be used for user for example `chmod u+x myscript.sh`.

```execute
chmod +x myscript.sh
```

Run the *ls -l* command to view the permissions of the bash script. Two things you will notice. The first, you will notice the file color will appear as green to let you know that file is executable. The second is you will notice the *x* displayed under owner and everyone permissions letting you know the file has the executable permission. 

```execute
ls -l
```

You now can run the script with the *./* prefix before the file name. You will also need to run the executable within the directory the file is saved. If you are in another directory you need to specify the full path to the file. 

```execute
./myscript.sh
```

When dealing with many end users that need to use the bash script you will want to add it within their PATH or within the ~/bin of each user. Notice with the command below you can see that the user has /bin specified in their PATH. 

```execute
echo $PATH
```
