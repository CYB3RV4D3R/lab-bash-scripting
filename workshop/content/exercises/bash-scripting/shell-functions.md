The bash shell allows you to define functions that can be used from the shell prompt. When you define a function, you essentially define a new `command` that you can call and use as if it were a standard command. The function contains a list of commands you want to run. Functions is not saved in a file, it only exists in memory. This means it will go away when you close the current shll session. You can of course add a function to your bash script files to make it persistent. 

The syntax for a function:
```
function_name()
{
    command1
    command2
    command3
}
```

A simple function demostration:
```execute
show ()
{
ls -l $1    
}
```
```execute
show /home
```

You will notice the **$1** variable that was passed to the ls -l command. That means it will pass in the first argument I specified on the command line (i.e /home directory). You can pass in more arguments and add in more variables such as $2, $3, $4, and so on). 

Now there will be times that we need to use the same function multiple times and that is where a shell script comes in handy. We can create a shell script with a function that displays how functions work with arguments. 

```execute
cat << 'EOF' >> function_script.sh
#!/bin/bash
ARG=$1

function mimic {
  if [[ -z $ARG ]]; then
    ARG='world'
  fi
  echo "hello $ARG"
}

mimic $ARG
EOF
```

```execute
chmod +x function_script.sh
```

Now we will run it with no arguments. If no arguments it will have the ARG variable default to *world*:
```execute
./function_script.sh
```

Now we will run with an argument. This will take the argument you provide it:
```execute
./function_script.sh bash-scripter
```

This concludes our 101 class of basic bash scripting! Have fun creating and testing your own scripts within the terminal window.