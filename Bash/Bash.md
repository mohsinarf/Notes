
## Useful commands
---

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

```
## Hello Bash Script
---
```
Which Bash                                      // To find the location of bash
touch shellScript.sh                            // Create a shell script
chmod +x shellScript.sh                         // make the file executable
#! /bin/bash                                    // Run the script only using bash, no matter in which environment you are
echo "Hello Bash Script"
```
## Redirect to file
---
```
echo "Sample text" > file.txt                   // Create file.txt and Write "Sample text" in it
cat > file.txt                                  // Write text in the file.txt file from the terminal
cat >> file.txt                                 // Append text in the file.txt file from the terminal
```
## Comments in Bash Script
---
```
#this is a one-line comment                     // Single line comments
: '                                             // Multiple line comments
this is a one-line comment
this is a one-line comment
this is a one-line comment'
```

