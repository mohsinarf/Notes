# Clang-format
`clang-format` is a tool that can automatically format C, C++, and other supported code according to a set of style rules.

## Create a .clang-format file (optional)
You can create a configuration file to specify the coding style you want. If you don't create a configuration file, clang-format will use default style settings.

Here's a simple example of a .clang-format file:
```
BasedOnStyle: LLVM
IndentWidth: 4
```

## Run clang-format
### Formatting a Single File
To format a single file, run:
```
clang-format -i source_file.cpp
```
The -i flag stands for "in-place," meaning it will modify the file directly.

### Formatting Multiple Files
To format multiple files, you can specify them all in the command:
```
clang-format -i file1.cpp file2.cpp file3.cpp
```