# Linux Essentials Notes

```
Release cycle dictates how often software is updated
maintenance cycle describes how long a version of software will be supported

Environment variables are also called global variables and examples are PATH,HOME and HITSIZE(defines how many previous commands to store in the history list)
env = outputs a list of the environment variables
export = turn a local variable into an environment variable
variable1=$variable1' '$variable2  ....this changes the value of variable to the content of variable1 and variable2
unset = to remove exported variables
PATH variable = contains a list that defines which directories the shell looks in to find commands
In the output of the PATH variable eavh directory is separated by a colon
paths are directory addresses which include step by step navigation directions to a filesystem
PATH=/usr/bin/custom:$PATH .....adds and verifies the /usr/bin/custom directory to the PATH variable
$PATH= represents the vale of the variable PATH
type = determine where it comes from
Internal commands are built into the shell itself
External commands are binary executables stored in directories that are searched by the shell
which = displays the full path to the command in question by searching the PATH variable
type -a echo = displays all locations that contain the command echo
alias name=command.....to create new aliases
The type command can identify aliases to other commands
Functions can be used to execute mutliple commands
e.g   my_report () {                                            
> ls Documents                                                                  
> date                                                                          
> echo "Document directory report"                                              
> }                             ..this function named my_report would do the things inside the {}
Double quotes stop the shell from interpreting some metacharacters (special characters), including glob characters.
Glob characters include *,? and [].
Double quotes still allow for command substitution, variable substitution, and permit some other shell metacharacters
Single quotes prevent the shell from doing any interpreting of special characters, including globs, variables, command substitution and other metacharacters
echo 'The car costs $100'                        
The car costs $100
echo "The path is $PATH"                          
The path is /usr/bin/custom:/home/sysadmin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
echo The service costs \$1 and the path is $PATH(here the backlash character stops the $1 from being interpreted as a variable
The service costs $1 and the path is /usr/bin/custom:/home/sysadmin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
Backquotes, or backticks, are used to specify a command within a command, a process called command substitution.
e.g  echo Today is `date`                         
Today is Mon Nov 4 03:40:04 UTC 2018
Control statements allow you to use multiple commands at once or run additional commands, depending on the success of a previous command
The ; character can be used to run multiple commands irrespective of the other one
The double ampersand && acts as a logical "and"; if the first command is successful, then the second command will also run. If the first command fails, then the second command will not run.
The double pipe || is a logical "or". i.e either run this first command or the second one
whoami- gives info about who the user is
uname = info about the kernel
pwd = print working directory
history 5 = displays the last five commands from your history
!9 = executes the 9th command in your history list
man = displays the manual page for a command and to exit use the Q page and use H to display a help page
Sections of a MAN page include: name, synopsis, description, options,files,author, reporting bugs, copyright and see also
while searching a MAN page type the /(for forward search) and ?(backward search)character followed by a search term and to move to the next match press n and press shift N to return to the previous match
press h to see list of movement commands  and q to get back to the document
By default, there are nine sections of man pages:

General Commands
System Calls
Library Calls
Special Files
File Formats and Conventions
Games
Miscellaneous
System Administration Commands
Kernel Routines

To search for man pages by name, use the -f option to the man command(note whatis command does the same)
The -k option to the man command searches both the names and descriptions of the man pages for a keyword.(note that the apropos command does the same thing)
man -k password = displays summary of all man pages that have tje keyword password in the description
whereis command is to find commands and man pages
locate is used to find any file or directory
locate -c will show how many files match e.g locate -b "\crontab"
note that locate command wont show files created today unless the database is manually updated by the root user by running updatedb
Another option is to use find command which searches the live filesystem rather than the static database
locate -b includes listings that have the search yerm in the basename of the filename..tthe basename is the portion of the filename not included in the directory names.
To limit the output even further, place a \ character in front of the search term. This character limits the output to filenames that exactly match the term.
Another advantage of info over man pages is that the writing style of info documents is typically more conducive to learning a topic. Consider man pages to be more of a reference resource and info documents to be more of a learning guide.
a listing of movement commands is available by hitting the Shift+H key while reading the info documentation, to close the help screen type the L key which brings back the current document. To quit entirely, use the Q key.
cat --help = learn the basic usage of a command quickly
There's additional documentation called readme files and usually found on the /usr/share/doc and /usr/doc.

note that which and whereis is primarily to find commands and their associated files while find is used to locate any file or directory

~ represents  users home directory
Absolute paths allows the user to specify the exact location of a directory
Relative paths start from the current directory
 two period .. characters always represents one directory higher relative to the current directory, sometimes referred to as the parent directory.
the .bashrc file in the home directory customizes features of the shell, such as creating or modifying variables and aliases.
ls -l outputs the contents of a file with its metadata and add h to put it in a redable human format
ls- S ouptuts based on size from largest to smallest
ls -t sorts files based on the time they were modified 
add full time to display the complete timestamp
ls - r this displays it in reverse
ls -d displays info about the directories itself rather than the contents
ls –d /etc/[abcd]* will display files that begin w the letter a,b,c,d
ls -d /etc/???? will display files in /etc directory that are exactly 4 characters long
ls -R (recursive)this displays all the files in directory and all the files in all subdirectories
d	directory	A file used to store other files.
-	regular file	Includes readable files, images files, binary files, and compressed files.
l	symbolic link	Points to another file.
s	socket	Allows for communication between processes.
p	pipe	Allows for communication between processes.
b	block file	Used to communicate with hardware.
c	character file	Used to communicate with hardware.


Black or White	Regular file
Blue	Directory file
Cyan	Symbolic link file (a file that points to another file)
Green	Executable file (a program)
The character standard used for Linux is the UTF-8 standard which is based on the ASCII (American Standard Code for Information Interchange). To learn more about ASCII, execute the man -s 7 ascii command.
Glob characters are often referred to as wild cards. These are symbol characters that have special meaning to the shell.
The asterisk * character is used to represent zero or more of any character in a filename.
The question mark ? character represents any single character.
The bracket [] characters are used to match a single character by representing a range of characters that are possible match characters.
the pattern /etc/[!DP]* matches any file that does not begin with a D or P.
always use the -d option with globs, which tells the ls command to display the name of directories, instead of their contents:
cp source destination
The -v option causes the cp command to produce output if successful. The -v option stands for verbose:
cp /etc/hosts ~/hosts.copy  = gives the hosts a new name called hosts.copy
while copying files use -i(interactive option/0 to safeguard against overwriting
To answer n to each prompt automatically, use the -n option. It stands for no clobber, or no overwrite.
cp -r means copy recursively (both files and directories
To copy all files in a directory, use the -R option
The first copy with the -p option preserved the original timestamp.
-n	No Clobber: Do not overwrite a destination file's contents.
mv source destination
mv example.txt Videos/newexample.txt  = move example.txt to videos under a new name
mv newexample.txt myfile.txt = renames the newexample.txt file to myfile.txt
touch comand = creates a new file
rm = deletes files
rm -r =deletes directory (i=interactive option) or use rmdir but only if the directory is empty
mkdir = make directories
Archiving is combining multiple files into one and in linus its of value when making a large number of files available such as the source code to an application, when storing log files, when backing up directories, some streaming devices perform bettter when sending stream of data and its faster
Compression reduces the amount of data needed to store or transmit a file while storing it in a way that it can be restored..there are two types of compression namely
Lossless: no information is removed from the file
Lossy:information might be removed from the file 
JPEG's use lossy compression while GIF's and PNGs are compressed but lossless 
compressing an already compressed file will not make it smaller
with lossless comression the multiple compression isnt a problem
gzip = to compress files..using the option -l shows information about the compression
gunzip or gzip -d will decompress the file
there are other compression commands namely
gzip ...uses lempel-Ziv data compression algorithm
bzip ....uses Burrows-wheeler block sorting which compresses smaller at expense of more CPU time
xz and unxz ..uses lempel-ziv-markov(LZMA) chain algorithm which can result in lower decompression CPU times that are on par with gzip while providing the better compression ratios typically associated with the bzip2 tools
tar is short form to TApe aRchive..used to stream many files to a tape for bavkups or file transfer
the tar command has three modes namely:
create- make a new archive out of a series of files
extract - pull one or more files out of an archive
list - show the contnets of the archive without extracting

tar -c = create an archive
tar -f = use archive file
tar -cf alpha_files.tar alpha* = creates the archive alpha_files.tar and the wildcard * is to include all the files beginning with alpha
tar -z = compress an archive using the gzip command
tar -j = compress or decompress an archive using the bzip2 command
tar -x = extract files from an archive
tar -v = verbose output
tar -t = list the contents of the archive
tar -tjf folders.tbz = list the files in an archve, decompress with an bzip2 command and operate on a given archive
bunzip2 -c folders.tbz | tar -t = the first part is to decompress the file but the -c option sends the output to the screen and the output is redirected to tar -t
if you don't specify a file with -f then the tar will read from the standard input which in this case is the uncompressed file
if you want to extract the archive, copy it into a different directory and then slam the command tar -xjf folders.tbz
note the -f has to be at the end so tar wont assume its a filename

zip alpha_files.zip alpha* = creates the compressed archive called zipfile and then adds the list of alpha files
unlike tar command zip command doesnt recurse into subdirectories by default and so you use the zip  command with -r
zip -r udev.zip /etc/udev
to view the contents of a zip archive use The –l option with the unzip command ...unzip -l udev.zip
tar -xvf udev.tar.gz = extract the contents of an archive
tar -rvf udev.tar /etc/hosts = adds a file to an existing archive
tar -tvf udev.tar  = lists files in the archive
bzip2 words = compress the file
bunzip2 words.bz2 = decompress the file
xz words = compress the file
unxz words.xz = decompress the file
zip words.zip words = where zip is the command, words.zip is the file name tobe created and the words is the name of the files to be placed in the compressed file
to extract the zip archive, use the unzip command
to view the contents of a zip archive use the -l option with unzip command

cat command is for creating and displaying text files as well as combining copies of text files
While using more and less commands..use the following keys for movement

Key	Movement
Spacebar	Window forward
B	Window backward
Enter	Line forward
Q	Exit
H	Help

To start a search to look forward from your current position, use the command less(more) /etc/passwd then use the slash / key.
To search backward from your current position, press the question mark ? key, then type the text or pattern to match and press the Enter key. 
use the n key to move the next match and use the Shift+N key combination to go to a previous match.
The search terms actually use patterns called regular expressions
By default, the head and tail commands display ten lines of the file
tail -5 /etc/sysctl.conf = outputs the last 5 lines of the files
head -n 3 /etc/sysctl.conf = outputs the first three lines of the file
For the tail command, either -3 or -n -3 still means show three lines.
head command recognizes -n -3 as show all but the last three lines, and yet the head command still recognizes the option -3 as show the first three lines.
head -n -20 /etc/passwd = will display the file excluding the last 20 lines
tail -n +25 /etc/passwd will output from line 25 to the end of the file
tail -f = useful to see changes to a File as theyre happening
nl = adds line number to the output
Standard input, or STDIN, is information entered normally by the user via the keyboard. 
Standard output, or STDOUT, is the normal output of commands.STDOUT is also known as stream or channel #1.
Standard error, or STDERR, is error messages generated by commands.STDERR is also known as stream or channel #2.
echo "New line 1" > example.txt = overwrites any content of the file which is called clobbering
echo "New line 1" >> example.txt = will add to the file content
Thus, stream #2 must be specified when redirecting STDERR by placing the number 2 preceding the arrow > character.....ls /fake 2> error.txt
If only the STDOUT is sent to a file, STDERR is still printed to the screen:
If only the STDERR is sent to a file, STDOUT is still printed to the screen e.g ls /fake /etc/ppp 2> error.txt = this will output the ls /etc/ppp and redirect the error text to the file
Both STDOUT and STDERR can be sent to a file by using the ampersand & character in front of the arrow > character. The &> character set means both 1> and 2> e.g find /etc -name hosts > find.out 2>&1
ls /fake /etc/ppp > example.txt 2> error.txt = This would output stdout to example.txt and will output stderr to error.txt
find ~ -name "*bash*" = find words containing bash in your home directory
find /etc -name hosts = find words containing hosts in /etc directory
find /etc -name hosts 2> err.txt = output the stderr to the error.txt file
tr = takes a set of charactes and translates them into another set of characters
tr 'a-z' 'A-Z' = this command will translate whatever you input into a string of capital letters and use ctrl D to stop(note that the command wont work directly on a file but will have to be used like this below)
tr 'a-z' 'A-Z' < example.txt = it'll take input from the example.txt file
tr 'a-z' 'A-Z' < example.txt > newexample.txt = takes input from the first file and redirects the output to the next file
sort mypasswd = sorts in alphabetical order
Option	Function
-t,	Specifies the comma character as the field delimiter
-k2	Sort by field #2
-k1n	Numerically sort by field #1
-k3	Sort by field #3
-r      reverse sort
cut -d: -f1 /etc/passwd = cuts the first field knowing that the delimiter is :
cut -d: -f1,5-7 mypasswd = cuts the 5th to 7th field
ls -l | cut -c1-11,50- = will display just the file type (character 1), permissions (characters 2-10), a space (character 11), and filename (characters 50+):

egrep - uses extended regular expression and fgrep is used to match literal characters 
grep sshd passwd used to search for the keyword sshd in the passwd file
the caret ^ character can be used to match a pattern at the beginning of a line
grep '^root' passwd = find lines begining with root in the passwd file
Use the $ symbol to match the pattern sync at the end of a line:
grep 'sync$' passwd = find lines ending with sync in the passwd file
grep -c = provides a count of how many lines match
grep -n = displays the original line numbers 
grep -v = inverts the match otputting lines that don't contain the patters
grep -i = ignores the case distinctions i.e either lowercase or uppercase
grep -w = returns lines which contain matches that form whole words
grep '....' red.txt = to find all words that have at least four characters
grep '[0-9]' profile.txt = to find all the lines in profile.txt which have a number in them
grep '[^0-9]' profile.txt = actually matches lines which contain non-numbers. not to match lines that do not contain numbers
grep 'sshd|root|operator' passwd......in this case it'll only work if you include option -E or use egrep(i.e using it in extended mode)
grep 're\*' newhome.txt = to look for an actual asterisk character ..put a backlash character
wc = this outputs no of lines, no of words , no of bytes and file name
wc -l = tells the number of lines
The asterisk * character is used to match zero or more occurrences of a character or pattern preceding it. For example, e* would match zero or more occurrences of the letter e:
grep -E 'colou?r' spelling.txt = To match colo followed by zero or one u character followed by an r character:
grep -E 'e+' red.txt = To match one or more e characters
grep -E 'gray|grey' spelling.txt = To match either gray or grey
grep -E '[0-9]{3}' passwd =  to search for a pattern containing a sequence of three digits

A central processing unit (CPU or processor) is the brain of the computer, where the execution of code takes place and where most calculations are done and is directly connected to the motherboard
If a hardware system has more than one processor, the system is referred to as a multiprocessor. If more than one processor is combined into a single overall processor chip, then it is called multi-core.
On an x86 system, the system processes data 32 bits at a time; on an x86_64 the system processes data 64 bits at a time. An x86_64 system is also capable of processing data 32 bits at a time in a backward compatible mode. 
One of the main advantages of a 64-bit system is the ability to work with more memory, while other advantages include increased efficiency of processing and increased security.
x86 processors. These processors include the 80386 (i386), 80486 (i486), the Pentium series (i586) and the Pentium Pro series (i686)
In linux, arch command is used to see whuch family the CPU of the system belongs to
For more information about the CPU, use the lscpu command
programs are loaded in RAM along with any data they need to store, while instructions are sent to the processor when they execute.
When the system is running low on RAM, virtualized memory called swap space is used to temporarily store data to disk. Data stored in RAM that has not been used recently is moved over to the section of the hard drive designated as swap, freeing up more RAM for use by currently active programs
free = view the amount of RAM
free -m = forces the output rounded to the nearest megabyte
free -g = forces the output rounded to the nearest gigabyte

A bus is a high-speed connection that allows communication between computers or the components inside a computer.
The motherboard has buses that allow for multiple devices to connect to the system, including the Peripheral Component Interconnect (PCI) and Universal Serial Bus (USB).
The PCI  bus is usualyy used for soumd and network cards
lspci = to view all the devices connected by the PCI bus
lspci -k = show devices along with the kernel driver and modules
lsmod = view the currently loaded modules

Devices connected internally are usually cold-plug, meaning the system must be shut down in order to connect or disconnect a device. USB devices are hot-plug, meaning they can be connected or disconnected while the system is running.
lsusb = to display the devices connected to the system via USB 
Hard drives are divided into one or more partitions. A partition is a logical division of a hard drive, designed to take a large amount of available storage space and break it up into smaller areas
Some hard drives make use of a partitioning technology called Master Boot Record (MBR) while others make use of a partitioning type called GUID Partitioning Table (GPT).
GPT is a newer technology  allowing having partitions larger than two terabytes which MBR does not have
Tools for managing MBR is fdisk, cfdisk and sfdisk commands
Tools for managing GPT are gdisk, cgdisk and sgdisk
there are tools that support MBR and GPT type disks which include parted and graphical gparted tool.
The file name is prefixed based on the different types of hard drives. IDE (Intelligent Drive Electronics) hard drives begin with hd, while USB, SATA (Serial Advanced Technology Attachment) and SCSI (Small Computer System Interface) hard drives begin with sd.
the drives would be arranged as /dev/hda and the second would be /dev/hdb
the partitions on a disk would be given as /dev/sda1 and /dev/sda2
 
fdisk -l /dev/sda = to display further information about the partitions(the l option non-interactively lists block devices which include disks and logical volumes)


Optical drives are mounted in a filesystem under the /media folder while older distributions used the /mnt folder

There are three types of video cables commonly used:

the older but still used analog 15-pin Video Graphics Array (VGA) cable
the more recent 29-pin Digital Visual Interface (DVI) interface
the very widely-used High-Definition Multimedia Interface (HDMI) which supports resolutions up to the 4K or Ultra HD range, and has either 19 or 29 pins
the newest digital display interface, the 20-pin DisplayPort (DP). Also its miniaturized counterpart, the Mini DisplayPort, used mainly for Apple products.

Power supplies are the devices that convert alternating current (120v, 240v) into direct current, which the computer uses at various voltages (3.3v, 5v, 12v). 

head -n 20 /proc/cpuinfo = view first 20 lines of the cpu information

GNU is the free software that surrounds the kernel and provides open source equivalents of many common UNIX commands. The Linux part of this combination is the Linux kernel, which is the core of the operating system.
Key functions of the Linux kernel include a system call interface, process management, memory management, virtual filesystems, networking, and device drivers.

/proc = info about active processes through a pseudo filesystem and info about system hardware and kernel configuration
/dev = hardware devices are made available under this file
/sys = info about the devices are stored here
pseudo filesystems appear to be real files on disk but exist only in memory

To make changes permanent (persistent even after rebooting), entries can be added to the appropriate section of the /etc/sysctl.conf file.
init process has a PID of 1
On a system V based system, the init process would be the /sbin/init program 
on a systemd based system, the /bin/systemd file is typically executed
the information about the process can be found in the /proc/1 directory
maximum PID value, which can be viewed and configured through the /proc/sys/kernel/pid_max file. 
pstree = shows the processes that can be maped into a family tree
ps = to view current processes in the current shell
ps - forest = shows processes in a map form
ps -ef or ps aux = view all processes
ps -u root = view root's active processes
top = regularly updates the output of running processes
Pressing the K key while the top command is running will prompt the user to provide the PID and then a signal number. Sending the default signal requests the process terminate, but sending signal number 9, the KILL signal, forces the process to terminate.
Pressing the R key while the top command is running will prompt the user for the process to renice, and then for a niceness value. Niceness values can range from -20 to 19, and affect priority. Only the root user can use a niceness value that is a lower number than the current one, or a negative niceness value, which causes the process to run with an increased priority. Any user can provide a niceness value that is higher than the current niceness value, which causes the process to run with a lowered priority.
uptime = load avergaes during the last 1,5,15 minutes or by displaying the contents of the /proc/loadavg file which display the 5 values, the first 3 being the 1,5,15 minutes load avergaes and the 4th value is a fraction which shows no of processes currently executing code on the CPU and the total no of processes and the last value is the last PID value
On a single-core CPU, a value of one (1) would mean that the system is fully-loaded. On a four core CPU, a value of 1 would mean that the system is only 1/4 or 25% loaded.
The hardware memory on the system is shared by all the processes on the system, through a method called virtual addressing.
kernel space and user space communicate with each through system call APIs that act as intermediaries

free = provides a snapshot of the memory being used at the moment
free -s = same thing above but with how often to update and specify the number of seconds
free -m = output in megabytes

syslog is the term used to describe logging
logging daemons include syslogd and klogd combined but is now replaced by rsysylogd which is a single service
those based on systemd, the logging daemon is named journald, and the logs are designed to allow for mainly text output, but also binary.
The standard method for viewing journald-based logs is to use the journalctl command.

the log files are stored in the /var/log
boot.log	Messages generated as services are started during the startup of the system.
cron	Messages generated by the crond daemon for jobs to be executed on a recurring basis.
dmesg	Messages generated by the kernel during system boot up.
maillog	Messages produced by the mail daemon for e-mail messages sent or received.
messages	Messages from the kernel and other processes that don't belong elsewhere. Sometimes named syslog instead of messages after the daemon that writes this file.
secure	Messages from processes that required authorization or authentication (such as the login process).
journal	Messages from the default configuration of the systemd-journald.service; can be configured in the /etc/journald.conf file amongst other places.
Xorg.0.log	Messages from the X Windows (GUI) server.

file = users can check the file content type before they view it to make sure that it is safe to view.
lastb and last commands can be used to view the /var/log/btmp and /var/log/wtmp files respectively.
dmesg | grep -i usb = issues regarding usb using i option to ignore case

              Not Shareable	Shareable 
Variable	/var/lock	/var/mail
Static	/etc	/opt
 

Directory	Contents
/	The base of the structure, or root of the filesystem, this directory unifies all directories regardless of whether they are local partitions, removable devices or network shares
/bin	Essential binaries like the ls, cp, and rm commands, and be a part of the root filesystem
/boot	Files necessary to boot the system, such as the Linux kernel and associated configuration files
/dev	Files that represent hardware devices and other special files, such as the /dev/null and /dev/zero files
/etc	Essential host configurations files such as the /etc/hosts or /etc/passwd files
/home	User home directories
/lib	Essential libraries to support the executable files in the /bin and /sbin directories
/lib64	Essential libraries built for a specific architecture. For example, the /lib64 directory for 64-bit AMD/Intel x86 compatible processors
/media	Mount point for removable media mounted automatically
/mnt	Mount point for temporarily mounting filesystems manually
/opt	Optional third-party software installation location
/proc	Virtual filesystem for the kernel to report process information, as well as other information
/root	Home directory of the root user
/sbin	Essential system binaries primarily used by the root user
/sys	Virtual filesystem for information about hardware devices connected to the system
/srv	Location where site-specific services may be hosted
/tmp	Directory where all users are allowed to create temporary files and that is supposed to be cleared at boot time (but often is not)
/usr	
Second hierarchy

Non-essential files for multi-user use
/usr/local	
Third hierarchy

Files for software not originating from distribution
/var	
Fourth hierarchy

Files that change over time
/var/cache	Files used for caching application data
/var/log	Most log files
/var/lock	Lock files for shared resources
/var/spool	Spool files for printing and mail
/var/tmp	Temporary files to be preserved between reboots

The first process is always /sbin/init, so the directory /proc/1
cat /proc/1/cmdline; echo 

ping localhost > /dev/null     
ping localhost > /dev/null &    = the difference is that this has the process running in the background while the first has it runing in the foreground

jobs = to see which commands are running
fg %1 = to bring the first command to the foreground
bg %1 = to bring the first command to the background
ctrl Z to stop process
Using the job number, stop the last ping command with the kill command 
killall = stops all commands
ps = shows running commands and their PID's
ps -e = so all processes are displayed
ps -o = to specify which columns to output
ps -o pid,tty,time,%mem,cmd --sort %mem = sort the output by %mem( adding + in front of the column name is ascending while - is descending)

after using top command, type K to start inputting command
The sleep command is typically used to pause a program (shell script) for a specific period of time
pkill -15 sleep = to terminate the remaining sleep command
The main log file that is written to by syslogd is /var/log/messages.
On CentOS systems, the syslogd is called rsyslogd.


A network packet is used to send network comunication between hosts by breaking down communication into smaller packets
An Ip address is a unique number assigned to a host on a network
Netmask, subnet mask or network mask is a number system that can be used to define whuch IP addresses are considered to be within a single network
A Uniform Resource Locator (URL), also commonly called a web address, is used to locate a resource, like a web page, on the internet. It’s what you type into your web browser to access a web page. For example, http://www.netdevgroup.com. It includes the protocol http:// and the hostname www.netdevgroup.com.
DHCP(Dynamic Host Configuaration Protocol) server defines how network information is assigned to client hosts
A Domain Name System (DNS) provides the service of translating domain names into IP addresses.
Ethernet has common speeds of 100Mbps and 1Gbps

IPv6 hasnt been embraced because there's NAT
Net Address Translation (NAT) used a technique to provide more hosts access to the Internet.a group of hosts is placed into a private network with no direct access to the Internet; a special router provides Internet access, and only this one router needs an IP address to communicate on the Internet.
On a CentOS system, the primary configuration file for an IPv4 network interface is the /etc/sysconfig/network-scripts/ifcfg-eth0 file.
cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE="eth0"
BOOTPROTO=none
NM_CONTROLLED="yes"
ONBOOT=yes
TYPE="Ethernet"
UUID="98cf38bf-d91c-49b3-bb1b-f48ae7f2d3b5"
DEFROUTE=yes
IPV4 _FAILURE_FATAL=yes
IPV6INOT=no
NAME="System eth0"
IPADDR=192.168.1.1
PREFIX=24
GATEWAY=192.168.1.1
DNS1=192.168.1.2
HWADDR=00:50:56:90:18:18
LAST_CONNECT=1376319928

If you want to have your system have a static IPv6 address, add the following to the configuration file:

IPV6INIT=yes
IPV6ADDR=<IPv6 IP Address>
IPV6_DEFAULTGW=<IPv6 IP Gateway Address>

If you want your system to be a DHCP IPv6 client, then add the following setting:

DHCPV6C=yes

The accepted method of making changes to a network interface is to take the interface down using a command such as ifdown eth0, make the desired changes to the configuration file, and then bring the interface back up and into service with a command such as ifup eth0.
Another less specific method is to restart the system’s networking entirely, with a command such as service network restart
The address of the DNS server is stored in the /etc/resolv.conf file
The nameserver setting is often set to the IP address of the DNS server
host example.com = which works with DNS to associate a hostname with an IP address.
host -a example.com = comprehensive list of DNS information
host -t = to query an aspect of a DNS

/etc/hosts	This file contains a table of hostnames to IP addresses. It can be used to supplement a DNS server.
/etc/resolv.conf	This file contains the IP addresses of the name servers the system should consult in any attempt to resolve names to IP addresses.
/etc/nsswitch.conf	This file can be used to modify where hostname lookups occur. It contains a particular entry that describes in what order name resolution sources are consulted.

ifconfig or ip addr show = interface configuration and is used to display network configuration information
route = to view a table that describes where network packages are sent 
route -n = to view a table w numbers
"ip route show" can be used in placed of route
ping = continues sending packages to determine if a network is reachable
ping -c =to ping limiting to a particular no of iterations
denial of service attack. In this sort of attack, a server is overwhelmed by a massive number of network packets
netstat -i = display statistics regarding network traffic
netstat -r = display routing information
A port is a unique number that is associated with a service provided by a host. If the port is open, then the service is available for other hosts.
netstat -tln = to see a list of all open ports(-t stands for TCP, -l stands for listening and  -n stands for show numbers, not names)
ss = designed to show socket statistics and supports all the major packet and socket types
Netid	The socket type and transport protocol
State	Connected or Unconnected, depending on protocol
Recv-Q	Amount of data queued up for being processed having been received
Send-Q	Amount of data queued up for being sent to another host
Local Address	The address and port of the local host’s portion of the connection
Peer Address	The address and port of the remote host’s portion of the connection
dig = performs queries on the DNS server to determine if the information needed is available on the server.
dig -x = o resolve the IP address 192.168.1.2 to a hostname
ssh = connects you to another machine across the network
ssh bob@test = to sssh inot the test machine usingbob as the username

If your system is connected to a network with DNS servers, then the nameserver entry in the /etc/resolv.conf file configures your system to use these servers to resolve hostnames into IP addresses.
A fully-qualified domain name (FQDN) includes not just the hostname, but also the domain that the hostname is "in". For the FQDN cserver.example.com, cserver is the hostname and example.com is the domain.

sudo = to be used when the root account is disabled and can carry out root commands
su - or su -root = can be used to switch to the root account
/etc/passwd = defines some of the account information for user accounts
in the /etc/passwd file it looks like this - sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash
first field is the name, second is password placeholder, third/fourth is user/group ID, fifth is the comment, 6th is homedirectory and the last is the location of the user's login shell
/etc/shadow = contains account information related to the user's pasword
sysadmin:$6$c75ekQWF$.GpiZpFnIXLzkALjDpZXmjxZcIll14OvL2mFSIfnc1aU2cQ/221QL5AX5RjKXpXPJRQ0uVN35TY3/..c7v0.n0:16874:5:30:7:60:15050:
The representationis username:password:lastchange:minimum(no of days between password changes):maximum:warn(no of days before password expiry that the system warns the user):inactive(graceperiod):expire;reserved
getent passwd sysadmin = retrieves account information for the sysadmin from the /etc/passwd#
user accounts have UID values of greater than 500 and root account has a UID of 0 and there are additional account called system accounts that have from 1 to 499
system accounts have asterisk in the password part in the /etc/shadow
primary group membership is in the /etc/passwd and secondary group membership is in the /etc/group
grep mail /etc/group = to display mail group account information
getent group mail = to display mail group account information
id = print user and group information for a specified user.
id -g = print only the user's primary group
id -G = verify the user's secondary group memberships
who = displays users currently logged into the system and also displaus info such as the current runlevel( a functional state of the computer) and the time that the system was booted
root     	tty2        2013-10-11 10:00    ..this means the user logged in via a local command line process
sysadmin	tty1        2013-10-11 09:58 (:0) ....this indicates they have performed a local graphical login
sysadmin 	pts/0       2013-10-11 09:59 (:0.0)
sysadmin 	pts/1       2013-10-11 10:00 (example.com)....this means the user has logged in remotely

w = more detailed list about users on the system
The JCPU column in the w command represents total cpu time used by all processes run since login.
The PCPU column in the w command represents total cpu time used by all processes run since login.
last =  reads the entire login history from the /var/log/wtmp file and displays all logins and reboot records by default
lastb = it shows bad or failed login attempts
uptime = how long the system has been running
/var/log/wtmp file keeps a log of all users who have logged in and out the system.
The who command reads from the /var/log/utmp file which logs current users, while the last command reads from the /var/log/wtmp file, which keeps a history of all user logins.
he getent command has the advantage over the grep command as it is also able to access user accounts that are not defined locally
getent passwd sysadmin = displays from the /etc/passwd file
The “Epoch” began on January 1, 1970.
getent database record = this is how its used
groupadd = to create a new group
groupadd -g = to create anew group specifying its group ID
groupadd -r = assigns a new group a GID that is less than the lowest standard GID
groupmod -n = change the name
groupmod -g = change the GID for a group
if you change the GID, the files in it would no longer be associated with any group name, theud only be owned by a GID only and theyre orphaned files
find / -nogroup = To search for all files that are owned by just a GID (not associated with a group name) use the -nogroup option of the find command:
groupdel = delete a group
useradd -D =allows you to view or change some of the default values
useradd -u = allows you specify the UID number
useradd -g = allows use a diff primary group than the defaukt when creating a new user account
useradd -G = allows you add a no of supplementary groups
useradd -M = specify that it shouldnt create the home directory
useradd -m = specify that it should create a home directory
useradd -c = specifies for a command
useradd -d = allows you specify either an existing directory or a new home directory to create for the user
useradd -b = you to use a different base directory group than the default when creating a new user account.
useradd -f = allows you to use a different INACTIVE value than the default when creating a new user account.
useradd -e =allows you to use a different EXPIRE value than the default when creating a new user account.
useradd -s =allows you to use a different login shell than the default when creating a new user account.
Skeleton directory has its contents copied into the new user's home directory
useradd -k =allows you to use a different SKEL directory than the default when creating a new user account.
To modify one of the useradd default values, the /etc/default/useradd file could be edited with a text editor. Another (safer) technique is to use the useradd -D command.
grep -Ev '^#|^$' /etc/login.defs = to filter out the comments and blank lines
The /etc/login.defs file also contains values that are applied by default to new users you create with the useradd command. Unlike the /etc/default/useradd file, the /etc/login.defs file is usually edited directly by the administrator to alter its values.

One system account that is an exception to this rule is the user nfsnobody, which has a UID of 65534.
It is common to specify the /sbin/nologin shell for accounts to be used as system accounts.

passwd jane = set or change the password for the user jane
The chage command provides many options for managing the password aging information found in the /etc/shadow file.

Here's a summary of the chage options:

Short Option	Long Option	Description
-l	--list	List the account aging information
-d LAST_DAY	--lastday LAST_DAY	Set the date of the last password change to LAST_DAY
-E EXPIRE_DATE	--expiredate EXPIRE_DATE	Set account to expire on EXPIRE_DATE
-h	--help	Show the help for the chage command
-I INACTIVE	--inactive INACTIVE	Set account to permit login for INACTIVE days after password expires
-m MIN_DAYS	--mindays MIN_DAYS	Set the minimum number of days before the password can be changed to MIN_DAYS
-M MAX_DAYS	--maxdays MAX_DAYS	Set the maximum number of days before a password should be changed to MAX_DAYS
-W WARN_DAYS	--warndays WARN_DAYS	Set the number of days before a password expires to start displaying a warning to WARN_DAYS



USERMOD OPTIONS
Short Option	Long Option	Description
-c	COMMENT	Sets the value of the GECOS or comment field to COMMENT.
-d HOME_DIR	--home HOME_DIR	Sets HOME_DIR as a new home directory for the user.
-e EXPIRE_DATE	--expiredate EXPIRE_DATE	Set account expiration date to EXPIRE_DATE.
-f INACTIVE	--inactive INACTIVE	Set account to permit login for INACTIVE days after password expires.
-g GROUP	--gid GROUP	Set GROUP as the primary group.
-G GROUPS	--groups GROUPS	Set supplementary groups to a list specified in GROUPS.
-a	--append	Append the user's supplemental groups with those specified by the -G option.
-h	--help	Show the help for the usermod command.
-l NEW_LOGIN	--login NEW_LOGIN	Change the user's login name.
-L	--lock	Lock the user account.
-s SHELL	--shell SHELL	Specify the login shell for the account.
-u NEW_UID	--uid NEW_UID	Specify the user's UID to be NEW_UID.
-U	--unlock	Unlock the user account.

If you use the -G option without the -a option, then you must list all the groups to which the user would belong.
if youre using the a and G option then only list the group you would like to add
userdel jane = to delete the user jane without the user's home directory
userdel -r jane = to delete the user, home and mailspool

you can also make changes to a user by editing the /etc/default/useradd file

groups = to know which groups i belong to
newgrp research = to change my current primary group to research temporarily
usermod -g groupname username = to change group permanently
chgrpn newname filename = to hcnage the group owner of a file to another group
To change the group ownership of all of the files of a directory structure, use the recursive -R option to the chgrp command
stat = displays detailed info about a file
chown jane /tmp/filetest1 = changes user ownership to the user jane
chown jane:users /tmp/filetest2 = changes user and group ownership to jane and user(note that : can be replaced by .)
chown .users /tmp/filetest1 = changes group owner of a file if the user doesnt have root ownerhsip
The w permission allows a user to delete files from a directory, but only if the user also has x permission on the directory.
The x permission is required to "get into" a directory, but the r permission on the directory is not necessary unless you want to list the directory's contents.
chmod u=rx abc.txt = to give user only read and execute commands
The umask command is a feature that is used to determine default permissions that are set when a file or directory is created. Default permissions are determined when the umask value is subtracted from the maximum allowable default permissions.
The stat command displays more detailed information about a file, including providing the group ownership both by group name and GID number. 
stat test.sh = verify the octal value for the permissions to test.sh
The chown command can only be executed by the root user and it can change both the user and group that owns a file.

The chgrp command can be used by either the user who owns a file or by the root user.

The chgrp command only changes the group that owns a file.

When the setuid permission is set on an executable binary file (a program) the binary file is run as the owner of the file, not as the user who executed it. 
The passwd command has the special setuid permission set. When the passwd command is run, and the command accesses the /etc/shadow file, the system acts as if the user accessing the file is the owner of the passwd command (the root user), not the user who is running the command.
the setuid permission is represented by the s in the owner permissions where the execute permission would normally be represented.
A lowercase s means that both the setuid and execute permission are set, while an uppercase S means that only setuid and not the user execute permission is set.
chmod u+s file = to add the setuid permission symbolically(you can also add 4000 to add setuid permission)
chmod 0775 file = to remove the setuid permission numerically
The setgid permission is similar to setuid, but it makes use of the group owner permissions.
it allows a user to run an executable binary file in a manner that provides them additional (temporary) group access

setuid → executable runs as the file owner (common: passwd).

setgid → executable runs as the file’s group; directories make new files inherit the group.
chmod g+s <file|directory> = to add the setgid permission( or use chmod 2775 <file|directory>)
chmod g-s <file|directory> = to remove the setgid permission (or use  chmod 0775 <file|directory>)

The sticky bit permission is used to prevent other users from deleting files that they do not own in a shared directory
e.g of sticky bit directories are /tmp and /var/tmp directories
A lowercase t means that both the sticky bit and execute permissions are set for others. An uppercase T means that only the sticky bit permission is set.
chmod o+t <directory> = to set the sticky bit permission (chmod 1775 <file|directory>)
chmod o-t <directory> = to remove the sticky bit permission (chmod 0775 <directory>)

For every file created, there is a block of data on the file system that stores the metadata of the file.This metadata is called the file's inode table.
ls -i = displays inode number of a file
File Name	Inode Number
passwd	123
shadow	175
group	144
gshadow	897

Hard links are two file names that point to the same inode.
ln target link_name = to create a hardlink
A symbolic link, also called a soft link, is simply a file that points to another file.
ln -s target link_name = To create a symbolic link,
find / -inum 278772 2> /dev/null = t finds all files linked to inode 278772 anywhere on the system.

To make changes permanent for kernel parameter files found under /proc/sys, the following file can have entries added to it: /etc/sysctl.conf





```