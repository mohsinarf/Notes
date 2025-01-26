## Smart pointers

```
class item
{
public:
	item() {
		std::cout << "Object is created" << std::endl;
	}
	~item() {
		std::cout << "Object is distroyed" << std::endl;
	}
	void print() {
		std::cout << "Sample Text." << std::endl;
	}
};
int main()
{
	std::shared_ptr<item> s_pointer = std::make_shared<item>();
	{
		std::shared_ptr<item> s_pointer2 = s_pointer;
	}
	s_pointer->print();
}
```
### Weak_ptr (To avoid dangling pointers)
```
    // OLD, problem with dangling pointer
    // PROBLEM: ref will point to undefined data!

    int* ptr = new int(10);
    int* ref = ptr;
    delete ptr;

    // empty definition
    std::shared_ptr<int> sptr;

    // takes ownership of pointer
    sptr.reset(new int);
    *sptr = 10;

    // get pointer to data without taking ownership
    std::weak_ptr<int> weak1 = sptr;

    // deletes managed object, acquires new pointer
    sptr.reset(new int);
    *sptr = 5;

    // get pointer to new data without taking ownership
    std::weak_ptr<int> weak2 = sptr;

    // weak1 is expired!
    if (auto tmp = weak1.lock())
        std::cout << *tmp << '\n';
    else
        std::cout << "weak1 is expired\n";

    // weak2 points to new data (5)
    if (auto tmp = weak2.lock())
        std::cout << *tmp << '\n';
    else
        std::cout << "weak2 is expired\n";
```

## Raw Pointers
```
int var = 8;
int* ptr = &var;  
*ptr = 10; 

char* buffer = new char[8];
memset(buffer, 0 , 8);  // Assign the value of 0 to 8 bytes from buffer address

char** ptr_a = &buffer; // Pointers to pointer

delete[] buffer;
```

## Deallocation Heap Memory
```
// Deallocating single element
if (item)
   delete item;
   
// Deallocating vector
for (it=Vector.begin(); it != Vector.end(); it++)
     delete *it;
Vector.erase(it.begin(), it.end());
```


## CONST keyword
```
	const int a = 5;
	a = 10; // Not allowed to change the contents of a
```
```
	int var = 10;
	const int* a = new int;
	*a = 10;  // Not allowed to change the contents of pointer a
	a = &var; // Okay! 
```
```
	int var = 10;
	int* const a = new int;
	*a = 10;  // Okay
	a = &var; // Not allowed to reassign the pointer a
```
```
class Player
{
private:
	int m_x, m_y;

public:
	int GetX() const
	{
		return m_x;
	}
};

void print(const Player& player)
{
	std::cout << player.GetX() << std::endl;
}
int main()
{
	Player player;
	print(player);
}
```

## Mutable keyword
```
class Player {
private:
	std::string name;
	mutable int debug_count;
public:
	const std::string& GetName() const
	{
		debug_count++;
		return name;
	}

};
```

## Algorithm
```
#include <algorithm>   
std::sort(vec.begin(), vec.end());
std::abs(x);
std::pow(2,3);
std::swap(arr[i], arr[j]);

// Convert string to Int
char str[] = "12345";
int n = atoi(str);

// Convert integer to string using string library
 std::string str = std::to_string(n);

// Convert string to lowercase
    std::transform(str.begin(), str.end(), str.begin(), ::tolower);

// Find alpha numeric characters 
if (std::isalnum(c)) {
    std::cout << "Alphanumeric character found: " << c << std::endl;
} else {
    std::cout << "Non-alphanumeric character found: " << c << std::endl;
}

#include <cctype> functions
std::isalnum  // Checks if a character is alphanumeric (letter or digit).
std::isalpha  // Checks if a character is an alphabetic letter.
std::isdigit  // Checks if a character is a digit.
std::isxdigit // Checks if a character is a hexadecimal digit.
std::islower  //Checks if a character is a lowercase letter.
std::isupper  // Checks if a character is an uppercase letter.
std::isspace  //Checks if a character is a whitespace character.

std::tolower // Converts a character to lowercase.
std::toupper // Converts a character to uppercase.
```

## std::array
~~~
#include <array>
int main()
{
    std::array<int, 10> arr;
    
    for(int iter=0;iter<arr.size(); ++iter)
        arr[iter] = iter;
    
    for(int iter=0;iter<arr.size(); ++iter)
        std::cout<<arr[iter]<<std::endl;
        
    return 0;
}
~~~
### Advantages over C style array
1) arr.size() (no need to manage the size of static array)
2) Bounce checking during the debug mode

## Template

### Functions
```
template<typename T>
void print(T value) 
{
	std::cout << value << std::endl;
}

int main()
{
	print(5);
	print(6.7f);
	print("Sample text");
}
```
### Classes
```
template<int N, typename T>
class Array
{
private:
	T array[N];
public:
	void print_size() {
		std::cout << N << std::endl;
	}
};

int main()
{
	Array<5, int> array;
	array.print_size();
}
```
## Threads
```
#include <iostream>
#include <thread>

static bool flag = true;

void print_to_console(int num)
{
    while(flag)
    {
        std::cout << "Working..."<< num << std::endl;
    }
}

int main()
{
    std::thread t1(print_to_console, 2);
    std::cin.get();
    flag = false;
    t1.join();
    return 0;
}
```
## Exceptions 
```
    try 
    {
        // throws std::length_error
        std::string("abc").substr(10);
    } 
    catch (const std::exception& e) { // reference to the base of a polymorphic object
         std::cout << e.what(); // information from length_error printed
    }
```
## Explicit keyword
```
struct A
{
    A(int) { }      // converting constructor
    A(int, int) { } // converting constructor (C++11)
    operator bool() const { return true; }
};
 
struct B
{
    explicit B(int) { }
    explicit B(int, int) { }
    explicit operator bool() const { return true; }
};
 
int main()
{
    A a1 = 1;      // OK: copy-initialization selects A::A(int)
    A a2(2);       // OK: direct-initialization selects A::A(int)
    A a3 {4, 5};   // OK: direct-list-initialization selects A::A(int, int)
    A a4 = {4, 5}; // OK: copy-list-initialization selects A::A(int, int)
    A a5 = (A)1;   // OK: explicit cast performs static_cast
    if (a1) ;      // OK: A::operator bool()
    bool na1 = a1; // OK: copy-initialization selects A::operator bool()
    bool na2 = static_cast<bool>(a1); // OK: static_cast performs direct-initialization
 
//  B b1 = 1;      // error: copy-initialization does not consider B::B(int)
    B b2(2);       // OK: direct-initialization selects B::B(int)
    B b3 {4, 5};   // OK: direct-list-initialization selects B::B(int, int)
//  B b4 = {4, 5}; // error: copy-list-initialization does not consider B::B(int,int)
    B b5 = (B)1;   // OK: explicit cast performs static_cast
    if (b2) ;      // OK: B::operator bool()
//  bool nb1 = b2; // error: copy-initialization does not consider B::operator bool()
    bool nb2 = static_cast<bool>(b2); // OK: static_cast performs direct-initialization
}
```
## std::any keyword
```
#include <any>
#include <iostream>
 
int main()
{
    std::cout << std::boolalpha;
 
    // any type
    std::any a = 1;
    std::cout << a.type().name() << ": " << std::any_cast<int>(a) << '\n';
    a = 3.14;
    std::cout << a.type().name() << ": " << std::any_cast<double>(a) << '\n';
    a = true;
    std::cout << a.type().name() << ": " << std::any_cast<bool>(a) << '\n';
 
    // bad cast
    try
    {
        a = 1;
        std::cout << std::any_cast<float>(a) << '\n';
    }
    catch (const std::bad_any_cast& e)
    {
        std::cout << e.what() << '\n';
    }
 
    // has value
    a = 2;
    if (a.has_value())
    {
        std::cout << a.type().name() << ": " << std::any_cast<int>(a) << '\n';
    }
 
    // reset
    a.reset();
    if (!a.has_value())
    {
        std::cout << "no value\n";
    }
 
    // pointer to contained data
    a = 3;
    int* i = std::any_cast<int>(&a);
    std::cout << *i << "\n";
}
```

## C++11 features
### constexpr
In C++11, the constexpr keyword can be used to declare variables or functions that must be evaluated at compile time. This means that the value of a constexpr variable or the result of a constexpr function can be used in any context where a constant expression is required, such as in the initialization of a const variable or as an array bound.

Using constexpr has several benefits:

It allows for more efficient code, as the value is computed at compile time rather than at runtime.
It can make the code easier to read and understand, as the value of a constexpr variable or the result of a constexpr function is known at compile time and does not depend on runtime conditions.
It can enable better optimization by the compiler, as it knows the value of a constexpr variable or the result of a constexpr function at compile time.
Here is an example of a simple constexpr function in C++11:

```
constexpr int factorial(int n)
{
    return (n <= 1) ? 1 : n * factorial(n - 1);
}

int main()
{
    // The value of 'x' will be computed at compile time
    constexpr int x = factorial(5);

    // The value of 'y' will be computed at runtime
    int y = factorial(5);

    return 0;
}

```
### Raw String Literals
C++11 introduces a new way to declare string literals as "raw string literals". Characters issued from an escape sequence (tabs, line feeds, single backslashes, etc.) can be inputted raw while preserving formatting. This is useful, for example, to write literary text, which might contain a lot of quotes or special formatting. This can make your string literals easier to read and maintain.

A raw string literal is declared using the following syntax:

```R"delimiter(raw_characters)delimiter"```
