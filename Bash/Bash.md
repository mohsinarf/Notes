
## Useful commands
```
tree <directory_name>  or tree                  //Print directory tree
Cat <FileName> -n
scp -r -P port# <FileName> Username@IPAddress:/directory/
histroy | grep ssh
ls -l                                           // Show file in list mode with all the option
ls -a                                           // Show all files including hidden file 
chmod +x filename                               // make the file executable
find . -name "*libQtSvg.do*"
ldd exectubale_file > log.txt                   // Write the dependency required by exectuable_file in to a log.txt file
rm -rf "directory"                              // Remove directory without asking for confirmation

 fgrep '_PB_INC1' -r                            // Search text in the files from current location


```
## Hello Bash Script
```
Which Bash                                      // To find the location of bash
touch shellScript.sh                            // Create a shell script
chmod +x shellScript.sh                         // make the file executable
#! /bin/bash                                    // Run the script only using bash, no matter in which environment you are
echo "Hello Bash Script"
```
## Redirect to file
```
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

