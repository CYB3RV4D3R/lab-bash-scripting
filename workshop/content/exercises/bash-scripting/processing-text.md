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

The **sed** command is a *stream* text editor. Unlike, vi or vim, a stream editor takes a stream of text as its stdin and then performs operations on it that you specify. Then, sed sends the results to stdout.

sed command example:
```
sed s/word1/word2/
```

The *s* command syntax is used to specify a text string to replace with another text string with the *s* meaning substitute. In the above example you are searching for *word1* then replacing it with *word2*. Another option is to used **d** which deletes the specified text. for example you would type *sed /word3/d* which would search for the word3 and delete it. 

First lets cat some text strings into a file:
```execute
echo "This is a lovely bash scripting exercise!" > sed_example.txt
```

Next lets use the sed command againt this file:
```execute
cat sed_example.txt | sed s/exercise/course/
```

You will notice that it does not save the changes:
```execute
cat sed_example.txt
```

To save the changes you have to redirect into a new file:
```execute
cat sed_example.txt | sed s/exercise/course/ > new_sed_example.txt
```
```execute
cat new_sed_example.txt
```

As you can see the word *exercise* was replaced by *course*. If there is more than one of the same word and want to replace all of them you simply add the *g* at the end i.e **sed s/word1/word2/g**. **the g in this example stands for global which means all matching occurances in the line would be replaced**. This format also works when your using the text editor such as vim. You will just type **:%s/word1/word2/g** while in the editor. *If you are in **insert** mode in vim you will need to hit **esc** to get out of insert mode to run the search and replace feature* The sed tool is very powerful and useful in DevSecOps and any system administrator role. You will find yourself searching and replacing terms within files quite often. 

The next command we will discuss is the *awk* command. Like sed, awk can be used to receive output from another command as its stdin and manipulate it in a manner you specify. However, awk treats each line of text it receives as a record. Each word in the line, seperated by a space or tab character, is treated as a seperated field within the record. 

Consider this file:
```execute
echo "This is line 1
This is line 2
This is line 3
This is line 4
This is line 5
This is line 6" > awk_example.txt
```
```execute
cat awk_example.txt
```

You can see this file, in the view of *awk* has 6 "records" because there is 6 lines of seperated text. Also, awk delimits *fields* by whitespace so each "record" carries four *fields*. Each field is referenced by **$field_number**. For example, the first field would be **$1**, and the second field **$2**, and so on. 

The awk syntax:
```
awk 'pattern {manipulation}'
```

An awk example to only print the 3rd and 4th fields from a file:
```execute
cat awk_example.txt | awk '{print $3,$4}'
```

An awk example to include a pattern that prints a record with a pattern of *line* and also print the 1st, 2nd, and 4th field in those records:
```execute
cat awk_example.txt | awk '/line/ {print $1,$2,$4}'
```

Then another example like the one above but to match a pattern of *4*:
```execute
cat awk_example.txt | awk '/4/ {print $1,$2,$4}'
```

You can also add your own text to the output and control characters to the output by using the following:
- **\t** inserts a tab character
- **\n** adds a newline character
- **\f** adds a form feed character
- **\r** adds a carriage return character
  
For example:
```execute
cat awk_example.txt | awk '/line/ {print "Field 1: "$1"\t", "Field 2: "$2"\t", "Field 4: "$4"\t"}'
```

This searches for the pattern *line* and then prints the strings "Field 1", "Field 2", and "Field 4". The corresponding *$field_number* is referenced and the *\t* option is used to insert a tab character in between each field. 