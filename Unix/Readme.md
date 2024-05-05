
## Useful commands
```
tree <directory_name>  or tree                  //Print directory tree
Cat <FileName> -n
scp -r -P port# <FileName> Username@IPAddress:/directory/
histroy | grep ssh
ls -l                                          // Show file in list mode with all the option
ls -a                                          // Show all files including hidden file 
chmod +x filename                              // make the file executable
find . -name "*libQtSvg.do*"
ldd exectubale_file > log.txt                  // Write the dependency required by exectuable_file in to a log.txt file
rm -rf "directory"                             // Remove directory without asking for confirmation
ldd app.exec                                   // find all the dependencies to run the application
fgrep '_PB_INC1' -r                            // Search text in the files from current location
rm -r ./*                                      // Remove all files at the existing location


```
## Grep Commands
```
grep '_PB_INC1' -r .                           // Search text in the files from the current location
grep "search_word" file.txt                    // Search for a specific word in a file
grep -r "pattern" /path/to/directory           // Recursive search in directories for a pattern
grep -i "pattern" file.txt                     // Case-insensitive search for a pattern
grep -c "pattern" file.txt                     // Count the number of occurrences of a pattern in a file
grep -n "pattern" file.txt                     // Display line numbers where the pattern matches occur
grep -v "exclude_this" file.txt                // Invert the match and show lines that do not contain the pattern
grep "^[A-Za-z]+ing$" file.txt                 // Use regular expressions for complex pattern matching
grep "pattern" -f file_list.txt                // Search for a pattern from a list of files

```
## Vim Commands
```
vim filename
vimdiff file1 file2

/                                               // to start the search
n                                               // to find the next instance
N                                               // to find the previous instance
/\<gnu\>                                        // to search the whole word
```
## Hello Bash Script
```
Which Bash                                      // To find the location of bash
touch shellScript.sh                            // Create a shell script
chmod +x shellScript.sh                         // make the file executable
#! /bin/bash                                    // Run the script only using bash, no matter in which environment you are
echo "Hello Bash Script"
```

## Managing files
```
cat file.txt                                    // Display all the contents of file.txt
tail -f file.txt                                // Display the last few lines of a file in real-time as new lines are added to the file

echo "Sample text" > file.txt                   // Create file.txt and Write "Sample text" in it
cat > file.txt                                  // Write text in the file.txt file from the terminal
cat >> file.txt                                 // Append text in the file.txt file from the terminal
```
## Comments in Bash Script
```
#this is a one-line comment                     // Single line comments
: '                                             // Multiple line comments
this is a one-line comment
this is a one-line comment
this is a one-line comment'
```

## Tmux Commands
```
yum install tmux                               // Install the tmux on CentOS 6
tmux                                           // Open the tmux

ctrl + b  %                                    // Open the pane on the right side
ctrl + b  "                                    // Open the pane on the bottom side
ctrl + b  ->                                   // Select the right pane
ctrl + b  <-                                   // Select the left pane
exit                                           // Close the current pane

ctrl + b  c                                    // Create a new window in the tmux session
ctrl + b  ,                                    // Rename the window
ctrl + b  1                                    // Select the window 1
ctrl + b  0                                    // Select the window 0
exit                                           // Close the current window

ctrl + b  d                                    // Detach the tmux session
tmux ls                                        // Display the current running tmux session
tmux attach -t "session_name"                  // Attach the current running session
tmux rename-session -t "current name" "New name"  // Rename the existing tmux session
tmux new -s "session name"                     // Create a new session with the specified name
tmux kill-session -t "session_name"            // Close the session

```

## DNS Query
```
dig google.com
```

## Running process
```
ps -ef                                        // Display information about the currently running processes
```

## Android Commands
```
adb devices
adb intall package

adb pair 192.168.0.7:45247
adb connect 192.168.0.7:45247 
adb -s 192.168.0.7:45247 shell
adb shell
```

## Managing Process

```
ps aux
kill <PID>
top // maximum memory using programs
```
