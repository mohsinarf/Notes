## How delete[] Knows How Much To Deallocate In C++?
1. When you allocate memory using `new[]` in C++, the memory allocator actually allocates a bit more memory than just the array itself. 
2. In this extra memory, the allocator stores information about the size of the array that was allocated. This is typically stored just before the start of the array. [2](https://stackoverflow.com/questions/197675/how-does-delete-know-the-size-of-the-operand-array)[3](https://www.reddit.com/r/cpp_questions/comments/o5gkqy/how_does_delete_know_how_long_the_array_is/)
3. When you call `delete[]` on a pointer to the array, the C++ runtime is able to access this size information and use it to properly deallocate the entire array, including calling the destructors on each element. 
4. The exact implementation details of how this size information is stored are not standardized and can vary between different C++ compilers and memory allocators. But the general approach is to store the array size in the extra memory allocated. [2](https://stackoverflow.com/questions/197675/how-does-delete-know-the-size-of-the-operand-array)[3](https://www.reddit.com/r/cpp_questions/comments/o5gkqy/how_does_delete_know_how_long_the_array_is/)
5. This is why it's important to always use `delete[]` when deallocating memory allocated with `new[]`, rather than trying to manually keep track of the array size yourself. The C++ runtime handles this for you behind the scenes. [4](https://www.geeksforgeeks.org/delete-and-free-in-cpp/

In summary, the `delete[]` operator is able to determine the size of the array to deallocate by accessing metadata stored by the memory allocator when the array was originally created with `new[]`. This allows `delete[]` to properly clean up the entire allocated memory block.

## What is a Virtual Destructor in C++?

A virtual destructor in C++ is a destructor that has the 'virtual' keyword in its declaration. This allows the correct destructor to be called when deleting an object through a base class pointer, ensuring that the destructors of both the base and derived classes are called.[1](https://en.cppreference.com/w/cpp/language/destructor)[2](https://favtutor.com/blogs/virtual-destructor-cpp)[3](https://www.scaler.com/topics/virtual-destructor-in-cpp/)
## Why Use a Virtual Destructor?

Without a virtual destructor, when an object of a derived class is deleted through a base class pointer, only the base class destructor is called. This can lead to memory leaks, as the derived class destructor is not called to free up the resources allocated by the derived class object.[2](https://favtutor.com/blogs/virtual-destructor-cpp)[3](https://www.scaler.com/topics/virtual-destructor-in-cpp/)[5](https://www.javatpoint.com/virtual-destructor-in-cpp)By making the base class destructor virtual, the correct destructor (derived class destructor first, then base class destructor) will be called when deleting the object, preventing memory leaks.[1](https://en.cppreference.com/w/cpp/language/destructor)[2](https://favtutor.com/blogs/virtual-destructor-cpp)[3](https://www.scaler.com/topics/virtual-destructor-in-cpp/)

## What Is Name Mangling In C++?
Name mangling in C++ is a compiler technique to encode function or variable signatures into unique names. It facilitates function overloading, namespaces, and function templates by distinguishing entities with the same name. The mangled name typically includes information about parameters, return type, and sometimes namespaces. It ensures correct linkage during compilation and linking phases. Understanding name mangling is crucial for interfacing with external libraries and low-level development tasks.

## What Is Explicit Constructor In C++?
an explicit constructor is a constructor that is declared with the `explicit` keyword. When a constructor is declared explicit, it means that it cannot be called with implicit type conversion. This helps prevent unintended implicit conversions during object initialization.

Here's an example:

```
class MyClass {
public:   
explicit MyClass(int x) : value(x) {} 
private:    
int value; 
};  

void func(MyClass obj) {     
// Do something with obj
}  

int main() {     
MyClass obj1 = 10; // Error: Cannot convert int to MyClass implicitly     
MyClass obj2(10); // OK: Explicit constructor call     
func(10); // Error: Cannot convert int to MyClass implicitly     func(MyClass(10)); // OK: Explicit constructor call     return 0; 
}
```

In this example, `MyClass` has an explicit constructor that takes an integer. The `func` function expects a `MyClass` object. Without the `explicit` keyword, `func(10)` would implicitly create a `MyClass` object, which could be undesirable. However, with the `explicit` keyword, such implicit conversions are not allowed, and you must explicitly create the `MyClass` object as `func(MyClass(10))`.

## What Is The Use Of extern 'C' In C++?
The `extern "C"` syntax in C++ is used to declare functions or objects with C linkage. It tells the compiler to use C linkage for the named entities, which means that the names of those entities will be exposed to the outside world without any C++ name mangling. This is typically used when interfacing with C code from C++, as C++ has different name mangling rules than C.

Here's an example:

```
	extern "C" { 
	void c_function(); // Declaration of a C function 
	}  
	int main() {  
	c_function(); // Calling a C function    
	return 0; }
```



In this example, `c_function` is declared with C linkage, meaning its name will not undergo C++ name mangling. This allows the function to be called from C++ code without any issues, even if it's implemented in a separate C file.

## Compiler works for C++ and C

Compilation in C and C++ involves several stages, including preprocessing, compilation, assembly, and linking. Let me explain each stage in detail:

1. Preprocessing: The preprocessor stage handles directives, such as `#include` and `#define`, and performs textual substitutions. It processes header files, expands macros, and removes comments. The output of this stage is a modified source code file, often with a .i or .ii extension.
    
2. Compilation: The compilation stage takes the preprocessed source code and translates it into assembly language. It involves lexical analysis, syntax analysis, and semantic analysis. The output of this stage is an assembly file (often with a .s extension) that contains low-level instructions specific to the target architecture.
    
3. Assembly: The assembly stage takes the assembly code and translates it into machine code specific to the target architecture. It involves converting mnemonic instructions into binary representations. The output of this stage is an object file (often with a .o extension) that contains machine code and additional information like symbols, relocation information, and debugging symbols.
    
4. Linking: The linking stage combines multiple object files and resolves references between them. It resolves function calls and variable references to their actual memory locations. The output of this stage is an executable file, a shared library, or a dynamically linked library, depending on the type of the project.
    

During the linking stage, the linker performs several tasks, including:

- Symbol resolution: The linker resolves symbols (functions and variables) by matching their references to their definitions in the object files or libraries. If a symbol is defined multiple times or is missing, it raises an error.
    
- Relocation: The linker adjusts addresses in the object code to reflect the final memory layout of the executable. It resolves relative addresses and updates them to absolute addresses.
    
- Library linking: The linker can link external libraries into the executable. It searches for symbols in the libraries and resolves references to them.
    
- Final executable creation: The linker combines all the object files and libraries into a single executable file, which can be run by the operating system.
    

It's worth noting that the compilation process can vary depending on the specific compiler and build system used. Different compilers may have additional optimization steps or variations in the stages described above. However, the overall concepts and stages remain similar across different implementations.

## How Static Variable Behaves In Template Class And Template Functions?

- A template class is a generic class that can be used with different data types. When the template class is instantiated with a specific type, a separate version of the class is created for that type.
- Any static variables declared within the template class are also instantiated separately for each type the class is used with. [1](https://www.reddit.com/r/cpp_questions/comments/jn1ftx/static_variables_in_template_classes/?rdt=34824)[2](https://www.fayewilliams.com/2014/12/23/static-variables-in-template-classes-and-methods/)
- This means that if you create multiple objects of the same template class type (e.g. `TestStatic<int>`), they will all share the same static variable. However, objects of different template class types (e.g. `TestStatic<int>` and `TestStatic<double>`) will have their own separate static variables. [1](https://www.reddit.com/r/cpp_questions/comments/jn1ftx/static_variables_in_template_classes/?rdt=34824)[2](https://www.fayewilliams.com/2014/12/23/static-variables-in-template-classes-and-methods/)
- To properly define the static variable, you need two lines of code - the declaration inside the class, and the definition outside the class. This is because static variables are not part of the class itself, but rather part of the scope controlled by the class. [1](https://www.reddit.com/r/cpp_questions/comments/jn1ftx/static_variables_in_template_classes/?rdt=34824)[2](https://www.fayewilliams.com/2014/12/23/static-variables-in-template-classes-and-methods/)
- More recently, the `inline` keyword can be used to simplify the definition of static variables in template classes. [1](https://www.reddit.com/r/cpp_questions/comments/jn1ftx/static_variables_in_template_classes/?rdt=34824)

In summary, static variables in template classes behave similarly to static variables in regular classes, but a separate static variable is created for each unique template type instantiation. This allows sharing of the static variable within the same template type, but isolation between different template types

## What is the `override` Keyword in C++?

The `override` keyword in C++ is used to indicate that a member function in a derived class is intended to override a virtual function of the same name in the base class. It serves two main purposes:

1. **Clarity for the reader**: The `override` keyword makes it clear that the function is meant to be an override of a virtual function in the base class. This helps other developers understand the code better.
2. **Compile-time checking**: When the `override` keyword is used, the compiler will check that the function in the derived class does indeed override a virtual function in the base class. If the signatures do not match, the compiler will generate an error. This helps catch mistakes where the programmer thinks they are overriding a function, but accidentally change the signature instead.

Here's an example:

```
class Base {
public:     
virtual void foo(float x) {
	/* implementation */ 
	} 
};  
class Derived : public Base 
{
public:   

// Correct override     
void foo(float x) override { 
	/* implementation */ 
	}
	      
// Error: signature does not match     
int foo(int x) override { 
	/* implementation */ 
	} 
};
```


In the example above, the first override of `foo()` in the `Derived` class is correct, as it matches the signature of the virtual function in the `Base` class. However, the second override is incorrect, as it changes the return type, and the compiler will generate an error.The `override` keyword was introduced in C++11 to help catch these kinds of mistakes at compile-time, making the code more robust and easier to maintain.

VTable?
In C++, a vtable (virtual table) is a mechanism used in object-oriented programming to implement dynamic dispatch, particularly for polymorphic behavior. It is a table of function pointers associated with a class hierarchy where each entry in the table points to the most derived function implementation for that method. Vtables are used to support runtime polymorphism through virtual functions.

Compilation Phase:

During compilation, the compiler creates a vtable for each class that has at least one virtual function.
The vtable is essentially an array of function pointers.
Each virtual function in the class corresponds to an entry in the vtable.
Construction of Objects:

When an object of a class with virtual functions is created, a hidden pointer called the vptr (virtual pointer) is added to the object.
This vptr points to the vtable of the class.
Function Calls:

When a virtual function is called through a base class pointer or reference, the compiler looks up the vptr of the object to determine the appropriate vtable.
It then uses the vtable to find the correct function pointer for the virtual function being called.
The function pointed to by the vtable entry is invoked.
Dynamic Dispatch:

This process is called dynamic dispatch because the actual function to be called is determined at runtime based on the type of the object, rather than at compile time.
This enables polymorphic behavior, where the correct function implementation is called based on the runtime type of the object.
Here's a more detailed example illustrating the steps:

```
#include <iostream>

class Animal {
public:
    virtual void makeSound() {
        std::cout << "Animal makes a sound" << std::endl;
    }
};

class Dog : public Animal {
public:
    void makeSound() override {
        std::cout << "Dog barks" << std::endl;
    }
};

int main() {
    Animal* animalPtr;

    Dog dog;

    animalPtr = &dog;

    // Step 1: Object creation:
    // - Object of type Dog is created
    // - vptr is added to the object, pointing to Dog's vtable

    // Step 2: Function call through base class pointer:
    // - Compiler checks the vptr of the object pointed to by animalPtr
    // - It finds Dog's vtable
    // - It looks up the entry for makeSound() in Dog's vtable
    // - It calls the function pointed to by that entry, which is Dog::makeSound()
    animalPtr->makeSound(); // Output: "Dog barks"

    return 0;
}
```
Understanding vtables is crucial for leveraging the power of runtime polymorphism in C++.
