# ClangTidy

clang-tidy is a tool designed to perform static code analysis on C and C++ code. It checks your code for potential issues and suggests improvements based on a set of predefined rules. 

## How to use
`clang-tidy -p /path/to/build_directory /path/to/source_file.cpp`

The -p (or --project) option specifies the path to the directory containing the compile_commands.json file.

## Checks
Following checks are added to the .clang-tidy file.
```
Checks: "*,
        -abseil-*,
        -altera-*,
        -android-*,
        -fuchsia-*,
        -google-*,
        -llvm*,
        -modernize-use-trailing-return-type,
        -zircon-*,
        -readability-else-after-return,
        -readability-static-accessed-through-instance,
        -readability-avoid-const-params-in-decls,
        -cppcoreguidelines-non-private-member-variables-in-classes,
        -misc-non-private-member-variables-in-classes,
"
```