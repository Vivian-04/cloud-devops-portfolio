# Shell Scripting Notes

```
assigning variable
ANIMAL="penguin"
echo "My favorite animal is a $ANIMAL"
Another way to assign to a variable is to use the output of another command as the contents of the variable by enclosing the command in back ticks:
#!/bin/bash
CURRENT_DIRECTORY=`pwd`
echo "You are in $CURRENT_DIRECTORY"
nano test.sh = to edit a shell script using nano
vi editor has two modes called insert and command
The sed command is used to edit streams (STDIN) and the awk command is used for scripting.

Its possible to get input from the user and assign it to a variable through read command
A)#!/bin/bash

echo -n "What is your name? "
read NAME
echo "Hello $NAME!"

If you pass this script:
B)#!/bin/bash
echo "Hello $1"
A dollar $ sign followed by a number N corresponds to the Nth argument passed to the script. 
If you call the example above with ./test.sh World the output will be Hello World. The $0 variable contains the name of the script itself.

to know an exit code type echo $? and returns 0 if the string was found and 1 otherwise
BRANCHING is making the script do different functions based on tests

The test command gives you easy access to comparison and file test operators. For example:

Command	Description
test –f /dev/ttyS0	0 if the file exists
test ! –f /dev/ttyS0	0 if the file doesn’t exist
test –d /tmp	0 if the directory exists
test –x `which ls`	substitute the location of ls then test if the user can execute
test 1 –eq 1	0 if numeric comparison succeeds
test ! 1 –eq 1	NOT – 0 if the comparison fails
test 1 –ne 1	Easier, test for numeric inequality
test “a” = “a”	0 if the string comparison succeeds
test “a” != “a”	0 if the strings are different
test 1 –eq 1 –o 2 –eq 2	-o is OR: either can be the same
test 1 –eq 1 –a 2 –eq 2	-a is AND: both must be the same

C)#!/bin/bash

if grep -q root /etc/passwd; then
  echo root is in the password file
else
  echo root is missing from the password file
fi

test is fairly verbose for a command that gets used so frequently, so there is an alias for it called [ (left square bracket). If you enclose your conditions in square brackets, it’s the same as running test. So, these statements are identical.

if test –f /tmp/foo; then
if [ -f /tmp/foo]; then

D)#!/bin/bash

if [ "$1" = "hello" ]; then
  echo "hello yourself"
elif [ "$1" = "goodbye" ]; then
  echo "nice to have met you"
  echo "I hope to see you again"
else
  echo "I didn't understand that"
fi

E)#!/bin/bash

case "$1" in
hello|hi)
  echo "hello yourself"
  ;;
goodbye)
  echo "nice to have met you"
  echo "I hope to see you again"
  ;;
*)
  echo "I didn't understand that"
esac

Note that this example is the same as the D

There are two main loops in shell scripts: the for loop and the while loop.
F)#!/bin/bash

SERVERS="servera serverb serverc"
for S in $SERVERS; do
  echo "Doing something to $S"
done

G)#!/bin/bash

for NAME in Sean Jon Isaac David; do
  echo "Hello $NAME"
done

H)#!/bin/bash

for S in *; do
  echo "Doing something to $S"
done
The second loop uses a * which is a file glob. This gets expanded by the shell to all the files in the current directory.

J)#!/bin/bash

i=0
while [ $i -lt 10 ]; do
  echo $i
  i=$(( $i + 1))
done
echo “Done counting”


In command mode of the vi editor
Key	Function
j	Moves cursor down one line (same as down arrow)
k	Moves cursor up line (same as up arrow)
l	Moves cursor to the right one character (same as right arrow)
h	Moves cursor to the left one character (same as left arrow)
w	Moves cursor to beginning of next word
e	Moves cursor to end of word
b	Moves cursor to beginning of previous word
Keys	Function
$	Moves cursor to end of current line (same as End key)
0 (zero)	Moves cursor beginning of current line (same as Home key)
3G	Jumps to third line (nG jumps to the nth line)
1G	Jumps to first line
Shift+G	Jumps to the last line

commands to use while in command mode
u   undo
dw  delete word
2dw  delete 2 words
x    deletes a character
xxxx   deletes 4 characters
4u  undo last 4 operations and recover the deleted character
5X   deletes 5 characters to the left
dd    delete the current line
p     paste the deleted lines below
2dd   deletes two lines
4w     move to the fourth word
shift+D delete to the end
d$      deletes to the end of line
shift+J  join two lines
yw       copy the current word
shift+P  paste the copied word
1G       move to the first line
3J       join three lines
:%s/text //g   Search for and delete the word text
l	Lowercase ‘L’ moves forward one space
~	Shift+` changes letter to lower case
:w     save the file
a	Enter insert mode to Append text to the right of the cursor
o     open a blank line below the current line
O     Open a blank line above the current line

Command	Function/Keys
:x	Will save and close the file.
:wq	Will write to file and quit.
:wq!	Will write to a read-only file, if possible, and quit.
ZZ	Will save and close. Notice that no colon : is used in this case.
:q!	Exit without saving changes
:e!	Discard changes and reload file
:w!	Write to read-only, if possible.
/line   to search for an instance of line
n     to move to the next instance
?line   search backward for the word 'line'
cw      replace a word by writing over it
Insert modes include: i, I, a, A, o, and O.

to run shell files type bash "scriptname.sh" or ./sample.sh(use this if its been made executable)
to avoid typing bash make itt executable for all usrs using chmod a+x sample.sh

echo "Today is" `date +%A` = to output today is tuesday in scripting

K)#!/bin/bash                                                                   
echo "Please enter your age"                                                  
read age                                                                      
if test $age -lt 16                                                           
then                                                                          
   echo "You are not old enough to drive."                                    
else                                                                          
   echo "You can drive!"                                                      
fi                         

L)#!/bin/bash
echo "Enter a username to check: "
read name
if grep $name /etc/passwd > /dev/null
then
    echo "$name is on this system"
else
    echo "$name does not exist"
fi

M) #!/bin/bash                                                                   
echo "Please enter a number greater than 100"                                 
read num                                                                      
while [ $num -le 100 ]                                                        
do                                                                            
    echo "$num is NOT greater than 100."                                      
    echo "Please enter a number greater than 100."                            
    read num                                                                  
done                                                                          
echo "Finally, $num is greater than 100"

N)for name in /etc/passwd /etc/hosts /etc/group
do
          wc $name
done

O)ls
for num in `seq 1 12`
do
          touch test$num
done
ls



```