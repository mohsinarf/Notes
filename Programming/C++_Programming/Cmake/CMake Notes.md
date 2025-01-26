## Targets
In CMake, targets are the fundamental units that define what gets built. They represent the end products of the build process, such as executable files (programs), libraries, or custom commands. These targets are created using commands like `add_executable`, `add_library`, and `add_custom_target`.

Here's a breakdown of the different types of targets in CMake:

- **Executables:** These are the final programs that you can run after building the project. You create them using the `add_executable` command, specifying the name of the executable and the source files that make it up.
    
- **Libraries:** These are reusable blocks of code that can be linked into other executables. You create libraries using the `add_library` command, specifying the type of library (static or shared) and the source files.
    
- **Custom Targets:** These are targets that allow you to run arbitrary commands during the build process. They are useful for tasks that aren't directly related to building executables or libraries, such as running tests, generating documentation, or packaging the project. You create custom targets using the `add_custom_target` command.

```
cmake_minimum_required(VERSION 3.0.0)  
  
project(Calculator_Proj VERSION 1.0.0)  
  
add_library(my_math addition.cpp multiply.cpp)  
add_library(my_print print.cpp)  
add_executable(calculator main.cpp)  
  
target_link_libraries(calculator PRIVATE my_math my_print)

```


## add_subdirectory

The `add_subdirectory` command in CMake is used to incorporate another directory containing a CMakeLists.txt file into your project's build process. It essentially instructs CMake to navigate to that subdirectory, locate the CMakeLists.txt file, and then process it as if it were part of the current project's build system.

Here's a detailed explanation of how `add_subdirectory` works:

- **Specifying the Subdirectory:** You provide the path to the subdirectory that contains the CMakeLists.txt file you want to include. This path can be relative to the current directory (e.g., `src/mySubdirectory`) or an absolute path.
    
- **Building the Subdirectory:** When CMake encounters `add_subdirectory`, it changes directories to the specified subdirectory and executes the commands within the subdirectory's CMakeLists.txt file. This allows you to define targets (executables, libraries) specific to that subdirectory.
    
- **Variable Scope:** An important concept to understand is variable scope. Each call to `add_subdirectory` creates a new scope for variables. Variables defined in the parent directory (where the `add_subdirectory` is called) are visible within the subdirectory's CMakeLists.txt. However, variables defined within the subdirectory's CMakeLists.txt are not accessible in the parent directory.
    
- **Optional Arguments:** `add_subdirectory` offers some optional arguments that provide more control:
    
    - **Binary Directory:** By default, the build products (executables, libraries) generated in the subdirectory are placed in a subdirectory within the main project's build directory, mirroring the source directory structure. You can specify a custom binary directory using the `BINARY_DIR` argument.
    - **CONFIGURE_COMMAND:** This argument allows you to execute a custom command before configuring the subdirectory's build process. This might be useful for specific setup tasks needed for that subdirectory.
- **Benefits of Using `add_subdirectory`:**
    
    - **Modularization:** It promotes modular code organization by allowing you to break down your project into smaller, self-contained directories with their own build logic.
    - **Reusability:** Subdirectories can house reusable libraries or components that can be easily integrated into other parts of your project or even into other projects.
    - **Maintainability:** It improves code maintainability by separating concerns and allowing you to manage different parts of the project independently.

By effectively using `add_subdirectory`, you can create a well-structured and organized build system for complex projects, making them easier to build, manage, and maintain.
## target_include_directories

The `target_include_directories` command in CMake is used to specify the locations where the compiler should look for header files when building a specific target (executable, library, etc.).

Here's a breakdown of what the command does:

- **Specifying the Target:** You provide the name of the target you want to modify. This target should be previously created using commands like `add_executable` or `add_library`.

- **Include Directories:** Following the target name, you list the directories containing the header files you want the compiler to consider. These can be absolute paths (like `/usr/include`) or relative paths within your project structure.

- **Scope (PUBLIC, PRIVATE, INTERFACE):** An important aspect of `target_include_directories` is the scope you define for the include directories. This is specified using keywords like `PUBLIC`, `PRIVATE`, or `INTERFACE`.

- **PUBLIC:** Directories listed under `PUBLIC` are propagated to any target that links against this target. This means the dependent target can also find headers from these directories.
- **PRIVATE:** Directories listed under `PRIVATE` are only visible to the target itself and not to any targets linking against it.
 - **INTERFACE:** This is used for header files that are part of the target's public interface. These headers are meant to be used by other targets, but their location might be specific to this target's build system. The actual location isn't propagated, but dependent targets are informed about the existence of these headers.
   

By effectively using `target_include_directories` with different scopes, you can control which headers are visible to different parts of your project and ensure the compiler finds the necessary files for successful compilation.

## target_link_libraries

The `target_link_libraries` command in CMake is crucial for linking your project's targets (executables, libraries) with the necessary libraries during the build process. It essentially tells the linker which libraries your target depends on to resolve external symbols and function calls.

**Here's a breakdown of what it does:**

1. **Specifying the Target:** You provide the name of the target you want to link libraries with. This target should be previously created using commands like `add_executable` or `add_library`.
    
2. **Listing Libraries:** Following the target name, you list the libraries your target depends on. These can be:
    
    - **Library Names:** The actual names of the libraries you want to link against (e.g., `pthread`, `OpenGL`).
    - **`<TARGET_NAME>`:** This refers to another target created within your project.
    - **`<IMPORTED_TARGET>`:** This refers to an external library you've imported using `find_package`.
3. **Scope (PUBLIC, PRIVATE, INTERFACE):** An important aspect of `target_link_libraries` is the scope you define for the libraries:
    
    - **PUBLIC:** Libraries listed under `PUBLIC` become part of the target's public interface. This means any target linking against this target will also be linked with these public libraries.
    - **PRIVATE:** Libraries listed under `PRIVATE` are only linked with the current target and are not propagated to dependent targets.
    - **INTERFACE:** This is used for libraries that your target depends on but are not necessarily part of your project's build system. The linker is informed about the need for these libraries, but their location might be resolved during final linking stages.
4. **Optional Flags:** You can optionally use flags like `debug` or `optimized` to specify which version of the library (debug or optimized) to link with, depending on your build configuration.
    

**By effectively using `target_link_libraries` with different scopes, you achieve several benefits:**

- **Resolving Dependencies:** Ensures your target has access to the necessary libraries to function correctly.
- **Modular Linking:** Controls which libraries are exposed to dependent targets, promoting modularity and avoiding unnecessary dependencies.
- **Finding Libraries:** CMake helps locate system libraries or imported libraries based on their names or using `find_package`.

**Remember:** Always link with the appropriate libraries to avoid linker errors and ensure your target functions as intended.