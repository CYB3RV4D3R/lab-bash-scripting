When you are piping output to the shell or processing text streams within a script there will be times you want to filter the output of one command so that only a specific portion is processed along to the stdin of the next command. Several examples of these tools to process text are the following:
- cut
- fmt
- join/paste
- nl
- sed/awk
- sort
- split
- tr
- uniq
- wc

### CUT command

The *cut* command is used to print columns or fields that you specify from a file to the standard output. *by default, the tab character is used as a delimiter*. 

Some of the following are options that can be used with cut:
- **blist** select only these bytes
- **clist** select only these characters
- **flist** select only the specified fields
- **-s** do not print lines that do not contain delimiters

The following example is using the cut command to display all group names from the */etc/group* file. You will notice the delimiter within this file is **:** between fields. 

```execute
cut -d: -f1 /etc/group
```

### FMT command

The *fmt* command is to reformat a text file. Most commonly use the fmt command to change the wrapping of long lines within a file to a more readable width. 
The fmt syntax: **fmt *option filename***.
Example: **fmt -w 80 *filename*** 

You can conjure up a file that has more than 100 characters and practice using the fmt command to make the file more manageable. 

### JOIN & PASTE commands

The *join* command prints a line from each of the two specified input files. The first field is the default join field delimited by white space. You can use different join fields by using the **-j *field*** option.

The first file:
```execute
echo "1 Chris
2 Richie
3 Mason" > firstnames.txt
```

The second file:
```execute
echo "1 Polly
2 Groto
3 Smitty" > lastnames.txt
```

Now execute the join command by the number field:
```execute
join -j 1 firstnames.txt lastnames.txt
```

The *paste* command works in the same manner as the join command but pastes together corresponding lines from one or more files into columns. 

Example of the paste command:
```execute
paste firstnames.txt lastnames.txt
```

Another example of paste with delimiter of a colon:
```execute
paste -d: firstnames.txt lastnames.txt
```

### NL command

The *nl* command determines the number of lines in a file printed off to the left side of the output.

Example 1:
```execute
nl sample.txt
```

Example 2:
```execute
nl firstnames.txt
```

### SED & AWK commands

