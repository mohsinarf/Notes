


### Variadic templates
Variadic templates are class or function templates, that can take any variable(zero or more) number of arguments. In C++, templates can have a fixed number of parameters only that have to be specified at the time of declaration. However, variadic templates help to overcome this issue. Douglas Gregor and Jaakko Järvi came up with this feature for C++.

Variadic arguments are very similar to arrays in C++. We can easily iterate through the arguments, find the size(length) of the template, can access the values by an index, and can slice the templates too. 

So basically, Variadic function templates are functions that can take multiple numbers of arguments.
~~~
#include <iostream>
#include <utility>


// A function template that prints a variable number of arguments
template <typename T>
void print(T t)
{
	std::cout << t << " ";
}

template <typename T, typename... Args>
void print(T t, Args... args)
{
	std::cout << t << " ";
	print(args...);
}

int main()
{

	print(1, 2, 3, 4, 5);  // Outputs "1 2 3 4 5"
	return 0;
}
~~~
### Rvalue references
C++11 introduces a new reference termed the rvalue reference. An rvalue reference to T, which is a non-template type parameter (such as int, or a user-defined type), is created with the syntax T&&. Rvalue references only bind to rvalues.

Type deduction with lvalues and rvalues:
~~~
int x = 0; // `x` is an lvalue of type `int`
int& xl = x; // `xl` is an lvalue of type `int&`
int&& xr = x; // compiler error -- `x` is an lvalue
int&& xr2 = 0; // `xr2` is an lvalue of type `int&&` -- binds to the rvalue temporary, `0`

void f(int& x) {}
void f(int&& x) {}

f(x);  // calls f(int&)
f(xl); // calls f(int&)
f(3);  // calls f(int&&)
f(std::move(x)); // calls f(int&&)

f(xr2);           // calls f(int&)
f(std::move(xr2)); // calls f(int&& x)
~~~

### move semantics
Moving an object means to transfer ownership of some resource it manages to another object.

The first benefit of move semantics is performance optimization. When an object is about to reach the end of its lifetime, either because it's a temporary or by explicitly calling std::move, a move is often a cheaper way to transfer resources. For example, moving a std::vector is just copying some pointers and internal state over to the new vector -- copying would involve having to copy every single contained element in the vector, which is expensive and unnecessary if the old vector will soon be destroyed.

### std::move
In C++, std::move is a function that is used to indicate that an object should be moved from one location to another. It is typically used to optimize the performance of code by allowing the object to be moved rather than copied
~~~
#include <utility>

void foo(std::string&& str) {
  // str is an rvalue reference and can be modified
  // without making a copy of the original string
}

int main() {
  std::string s = "Hello, world!";

  // s is an lvalue, so it cannot be passed directly to foo
  foo(std::move(s));  // s is now an rvalue and can be moved

  return 0;
}

~~~
In this example, the function foo takes an rvalue reference as an argument. An rvalue reference is a special type of reference that can only be bound to an rvalue, which is a temporary object or a value that is not associated with an identifier.

Since s is an lvalue (a value that is associated with an identifier), it cannot be passed directly to foo as an argument. However, by using std::move, we can convert s into an rvalue, allowing it to be passed to foo.

After the call to std::move, s is still a valid object, but it may be in an unspecified or "moved-from" state, meaning that its value may have been modified or destroyed. Therefore, it is generally a good idea to avoid using an object after it has been moved from, unless you are certain that the object is still in a valid state

### Forwarding references (universal references)
Also known (unofficially) as universal references. A forwarding reference is created with the syntax T&& where T is a template type parameter, or using auto&&. This enables perfect forwarding: the ability to pass arguments while maintaining their value category (e.g. lvalues stay as lvalues, temporaries are forwarded as rvalues).

Forwarding references allow a reference to bind to either an lvalue or rvalue depending on the type. Forwarding references follow the rules of reference collapsing:

T& & becomes T&
T& && becomes T&
T&& & becomes T&
T&& && becomes T&&

~~~
// Since C++14 or later:
void f(auto&& t) {
  // ...
}

// Since C++11 or later:
template <typename T>
void f(T&& t) {
  // ...
}

int x = 0;
f(0); // T is int, deduces as f(int &&) => f(int&&)
f(x); // T is int&, deduces as f(int& &&) => f(int&)

int& y = x;
f(y); // T is int&, deduces as f(int& &&) => f(int&)

int&& z = 0; // NOTE: `z` is an lvalue with type `int&&`.
f(z); // T is int&, deduces as f(int& &&) => f(int&)
f(std::move(z)); // T is int, deduces as f(int &&) => f(int&&)
~~~

### std::forward
In C++, std::forward is a function template that is used to perfectly forward a value from one function to another. It is typically used in conjunction with forwarding references, which are a type of reference that can bind to both lvalues and rvalues.

Here is an example of how std::forward might be used:
~~~
#include <utility>

template <typename T>
void foo(T&& x) {
  // x is a forwarding reference
  bar(std::forward<T>(x));  // Perfectly forward x to bar
}

int main() {
  int n = 42;
  foo(n);  // n is an lvalue, so x is an lvalue reference
  foo(42);  // 42 is an rvalue, so x is an rvalue reference

  return 0;
}

~~~
In this example, the function foo takes a forwarding reference as an argument. When foo is called with an lvalue (such as the variable n), x becomes an lvalue reference and binds to the lvalue. When foo is called with an rvalue (such as the integer literal 42), x becomes an rvalue reference and binds to the rvalue.

The std::forward function is then used to perfectly forward the value of x to the function bar. This allows foo to accept any type of argument and pass it along to bar without making any copies.

The std::forward function is implemented using template type deduction and reference collapsing, which are advanced C++ concepts that can be difficult to understand at first. However, if you are familiar with these concepts, std::forward can be a very powerful tool for implementing generic and efficient functions in C++.

### Raw String Literals
C++11 introduces a new way to declare string literals as "raw string literals". Characters issued from an escape sequence (tabs, line feeds, single backslashes, etc.) can be inputted raw while preserving formatting. This is useful, for example, to write literary text, which might contain a lot of quotes or special formatting. This can make your string literals easier to read and maintain.

A raw string literal is declared using the following syntax:

~~~
R"delimiter(raw_characters)delimiter"
~~~

### Static_assertions
In C++, static assertions are a way to perform compile-time checks on values that are known at compile time. They are often used to ensure that certain conditions are met, such as checking the sizes of types or checking that a template parameter is of a certain type.
Static assertions are implemented using the static_assert macro, which is defined in the <cassert> header. The static_assert macro takes a boolean expression as its first argument and a string literal as its second argument. If the boolean expression is true, the program will continue to compile as normal. If the boolean expression is false, the program will fail to compile and the string literal will be used as the error message.
~~~
#include<cassert>
#include<iostream>

int main()
{
	 constexpr int x = 0;
	 constexpr int y = 1;
	static_assert(x == y, "x != y");

	return 0;
}
~~~

### Intiailizer list
In C++, an initializer list is a list of values used to initialize an object of a class type. Initializer lists are a feature of the C++ language that allow objects to be initialized with a list of values, rather than with a single value or with a sequence of assignment statements.

Initializer lists are typically used to initialize data members of a class, but they can also be used to initialize other objects. Initializer lists are denoted by enclosing a comma-separated list of values in curly braces {}.
~~~
#include <iostream>
#include <vector>

class MyClass
{
public:
    MyClass(std::initializer_list<int> il)
    {
        for (int i : il)
        {
            std::cout << i << " ";
        }
        std::cout << std::endl;
    }
};

int main()
{
    MyClass obj{1, 2, 3, 4, 5};  // Outputs "1 2 3 4 5"

    int arr[5] = {6, 7, 8, 9, 10};  // Initializes arr with {6, 7, 8, 9, 10}

    std::vector<int> vec{11, 12, 13};  // Initializes vec with {11, 12, 13}

    return 0;
}

~~~
~~~
int sum(const std::initializer_list<int>& list) {
  int total = 0;
  for (auto& e : list) {
    total += e;
  }

  return total;
}

auto list = {1, 2, 3};
sum(list); // == 6
sum({1, 2, 3}); // == 6
sum({}); // == 0
~~~

### Right angle brackets
C++11 is now able to infer when a series of right angle brackets is used as an operator or as a closing statement of typedef, without having to add whitespace.
~~~
typedef std::map<int, std::map <int, std::map <int, int> > > cpp98LongTypedef;
typedef std::map<int, std::map <int, std::map <int, int>>>   cpp11LongTypedef;
~~~
### Non-static data member initializers
Allows non-static data members to be initialized where they are declared, potentially cleaning up constructors of default initializations.
~~~
// Default initialization prior to C++11
class Human {
    Human() : age{0} {}
  private:
    unsigned age;
};
// Default initialization on C++11
class Human {
  private:
    unsigned age {0};
};
~~~

### Inline namespaces
All members of an inline namespace are treated as if they were part of its parent namespace, allowing specialization of functions and easing the process of versioning. This is a transitive property, if A contains B, which in turn contains C and both B and C are inline namespaces, C's members can be used as if they were on A.
~~~
namespace Program {
  namespace Version1 {
    int getVersion() { return 1; }
    bool isFirstVersion() { return true; }
  }
  inline namespace Version2 {
    int getVersion() { return 2; }
  }
}

int version {Program::getVersion()};              // Uses getVersion() from Version2
int oldVersion {Program::Version1::getVersion()}; // Uses getVersion() from Version1
bool firstVersion {Program::isFirstVersion()};    // Does not compile when Version2 is added
~~~

### Range-based for loops
Syntactic sugar for iterating over a container's elements.
~~~
std::array<int, 5> a {1, 2, 3, 4, 5};
for (int& x : a) x *= 2;
// a == { 2, 4, 6, 8, 10 }
Note the difference when using int as opposed to int&:

std::array<int, 5> a {1, 2, 3, 4, 5};
for (int x : a) x *= 2;
// a == { 1, 2, 3, 4, 5 }
~~~

### Deleted functions
A more elegant, efficient way to provide a deleted implementation of a function. Useful for preventing copies on objects.
~~~
class A {
  int x;

public:
  A(int x) : x{x} {};
  A(const A&) = delete;
  A& operator=(const A&) = delete;
};

A x {123};
A y = x; // error -- call to deleted copy constructor
y = x; // error -- operator= deleted
~~~
### Final specifier
Specifies that a virtual function cannot be overridden in a derived class or that a class cannot be inherited from.
~~~
struct A {
  virtual void foo();
};

struct B : A {
  virtual void foo() final;
};

struct C : B {
  virtual void foo(); // error -- declaration of 'foo' overrides a 'final' function
};
~~~
Class cannot be inherited from.
~~~
struct A final {};
struct B : A {}; // error -- base 'A' is marked 'final'
~~~

### Default functions
A more elegant, efficient way to provide a default implementation of a function, such as a constructor.
~~~
struct A {
  A() = default;
  A(int x) : x{x} {}
  int x {1};
};
A a; // a.x == 1
A a2 {123}; // a.x == 123
With inheritance:

struct B {
  B() : x{1} {}
  int x;
};

struct C : B {
  // Calls B::B
  C() = default;
};

C c; // c.x == 1
~~~

### auto
auto-typed variables are deduced by the compiler according to the type of their initializer.
~~~
auto a = 3.14; // double
auto b = 1; // int
auto& c = b; // int&
auto d = { 0 }; // std::initializer_list<int>
auto&& e = 1; // int&&
auto&& f = b; // int&
auto g = new auto(123); // int*
const auto h = 1; // const int
auto i = 1, j = 2, k = 3; // int, int, int
auto l = 1, m = true, n = 1.61; // error -- `l` deduced to be int, `m` is bool
auto o; // error -- `o` requires initializer
~~~
Extremely useful for readability, especially for complicated types:
~~~
std::vector<int> v = ...;
std::vector<int>::const_iterator cit = v.cbegin();
// vs.
auto cit = v.cbegin();
~~~
Functions can also deduce the return type using auto. In C++11, a return type must be specified either explicitly, or using decltype like so:
~~~
template <typename X, typename Y>
auto add(X x, Y y) -> decltype(x + y) {
  return x + y;
}
add(1, 2); // == 3
add(1, 2.0); // == 3.0
add(1.5, 1.5); // == 3.0
~~~
The trailing return type in the above example is the declared type (see section on decltype) of the expression x + y. For example, if x is an integer and y is a double, decltype(x + y) is a double. Therefore, the above function will deduce the type depending on what type the expression x + y yields. Notice that the trailing return type has access to its parameters, and this when appropriate.

### Lambda expressions
A lambda is an unnamed function object capable of capturing variables in scope. It features: a capture list; an optional set of parameters with an optional trailing return type; and a body. Examples of capture lists:

[] - captures nothing.
[=] - capture local objects (local variables, parameters) in scope by value.
[&] - capture local objects (local variables, parameters) in scope by reference.
[this] - capture this by reference.
[a, &b] - capture objects a by value, b by reference.
~~~
int x = 1;

auto getX = [=] { return x; };
getX(); // == 1

auto addX = [=](int y) { return x + y; };
addX(1); // == 2

auto getXRef = [&]() -> int& { return x; };
getXRef(); // int& to `x`
~~~
By default, value-captures cannot be modified inside the lambda because the compiler-generated method is marked as const. The mutable keyword allows modifying captured variables. The keyword is placed after the parameter-list (which must be present even if it is empty).
~~~
int x = 1;

auto f1 = [&x] { x = 2; }; // OK: x is a reference and modifies the original

auto f2 = [x] { x = 2; }; // ERROR: the lambda can only perform const-operations on the captured value
// vs.
auto f3 = [x]() mutable { x = 2; }; // OK: the lambda can perform any operations on the captured value
~~~
### decltype
decltype is an operator which returns the declared type of an expression passed to it. cv-qualifiers and references are maintained if they are part of the expression. Examples of decltype:
~~~
int a = 1; // `a` is declared as type `int`
decltype(a) b = a; // `decltype(a)` is `int`
const int& c = a; // `c` is declared as type `const int&`
decltype(c) d = a; // `decltype(c)` is `const int&`
decltype(123) e = 123; // `decltype(123)` is `int`
int&& f = 1; // `f` is declared as type `int&&`
decltype(f) g = 1; // `decltype(f) is `int&&`
decltype((a)) h = g; // `decltype((a))` is int&
template <typename X, typename Y>
auto add(X x, Y y) -> decltype(x + y) {
  return x + y;
}
add(1, 2.0); // `decltype(x + y)` => `decltype(3.0)` => `double`
~~~

### Type aliases
Semantically similar to using a typedef however, type aliases with using are easier to read and are compatible with templates.
~~~
template <typename T>
using Vec = std::vector<T>;
Vec<int> v; // std::vector<int>

using String = std::string;
String s {"foo"};
~~~

### nullptr
C++11 introduces a new null pointer type designed to replace C's NULL macro. nullptr itself is of type std::nullptr_t and can be implicitly converted into pointer types, and unlike NULL, not convertible to integral types except bool.
~~~
void foo(int);
void foo(char*);
foo(NULL); // error -- ambiguous
foo(nullptr); // calls foo(char*)
~~~

### Strongly-typed enums
Type-safe enums that solve a variety of problems with C-style enums including: implicit conversions, inability to specify the underlying type, scope pollution.
~~~
// Specifying underlying type as `unsigned int`
enum class Color : unsigned int { Red = 0xff0000, Green = 0xff00, Blue = 0xff };
// `Red`/`Green` in `Alert` don't conflict with `Color`
enum class Alert : bool { Red, Green };
Color c = Color::Red;
~~~
### Explicit virtual overrides
Specifies that a virtual function overrides another virtual function. If the virtual function does not override a parent's virtual function, throws a compiler error.
~~~
struct A {
  virtual void foo();
  void bar();
};

struct B : A {
  void foo() override; // correct -- B::foo overrides A::foo
  void bar() override; // error -- A::bar is not virtual
  void baz() override; // error -- B::baz does not override A::baz
};
~~~
### Converting constructors
Converting constructors will convert values of braced list syntax into constructor arguments.
~~~
struct A {
  A(int) {}
  A(int, int) {}
  A(int, int, int) {}
};

A a {0, 0}; // calls A::A(int, int)
A b(0, 0); // calls A::A(int, int)
A c = {0, 0}; // calls A::A(int, int)
A d {0, 0, 0}; // calls A::A(int, int, int)
~~~
Note that the braced list syntax does not allow narrowing:
~~~
struct A {
  A(int) {}
};

A a(1.1); // OK
A b {1.1}; // Error narrowing conversion from double to int
~~~
Note that if a constructor accepts a std::initializer_list, it will be called instead:
~~~
struct A {
  A(int) {}
  A(int, int) {}
  A(int, int, int) {}
  A(std::initializer_list<int>) {}
};

A a {0, 0}; // calls A::A(std::initializer_list<int>)
A b(0, 0); // calls A::A(int, int)
A c = {0, 0}; // calls A::A(std::initializer_list<int>)
A d {0, 0, 0}; // calls A::A(std::initializer_list<int>)
~~~

### Ref-qualified member functions
Member functions can now be qualified depending on whether *this is an lvalue or rvalue reference.
~~~
struct Bar {
  // ...
};

struct Foo {
  Bar getBar() & { return bar; }
  Bar getBar() const& { return bar; }
  Bar getBar() && { return std::move(bar); }
private:
  Bar bar;
};

Foo foo{};
Bar bar = foo.getBar(); // calls `Bar getBar() &`

const Foo foo2{};
Bar bar2 = foo2.getBar(); // calls `Bar Foo::getBar() const&`

Foo{}.getBar(); // calls `Bar Foo::getBar() &&`
std::move(foo).getBar(); // calls `Bar Foo::getBar() &&`

std::move(foo2).getBar(); // calls `Bar Foo::getBar() const&&`
~~~

### Trailing return types
C++11 allows functions and lambdas an alternative syntax for specifying their return types.
~~~
int f() {
  return 123;
}
// vs.
auto f() -> int {
  return 123;
}
auto g = []() -> int {
  return 123;
};
~~~
This feature is especially useful when certain return types cannot be resolved:
~~~
// NOTE: This does not compile!
template <typename T, typename U>
decltype(a + b) add(T a, U b) {
    return a + b;
}

// Trailing return types allows this:
template <typename T, typename U>
auto add(T a, U b) -> decltype(a + b) {
    return a + b;
}
~~~
In C++14, decltype(auto) (C++14) can be used instead.

### Noexcept specifier
The noexcept specifier specifies whether a function could throw exceptions. It is an improved version of throw().
~~~
void func1() noexcept;        // does not throw
void func2() noexcept(true);  // does not throw
void func3() throw();         // does not throw

void func4() noexcept(false); // may throw
~~~
Non-throwing functions are permitted to call potentially-throwing functions. Whenever an exception is thrown and the search for a handler encounters the outermost block of a non-throwing function, the function std::terminate is called.
~~~
extern void f();  // potentially-throwing
void g() noexcept {
    f();          // valid, even if f throws
    throw 42;     // valid, effectively a call to std::terminate
}
~~~
### char32_t and char16_t
Provides standard types for representing UTF-8 strings.
~~~
char32_t utf8_str[] = U"\u0123";
char16_t utf8_str[] = u"\u0123";
~~~

### Special member functions for move semantics
The copy constructor and copy assignment operator are called when copies are made, and with C++11's introduction of move semantics, there is now a move constructor and move assignment operator for moves.
~~~
struct A {
  std::string s;
  A() : s{"test"} {}
  A(const A& o) : s{o.s} {}
  A(A&& o) : s{std::move(o.s)} {}
  A& operator=(A&& o) {
   s = std::move(o.s);
   return *this;
  }
};

A f(A a) {
  return a;
}

A a1 = f(A{}); // move-constructed from rvalue temporary
A a2 = std::move(a1); // move-constructed using std::move
A a3 = A{};
a2 = std::move(a3); // move-assignment using std::move
a1 = f(A{}); // move-assignment from rvalue temporary
~~~


### Explicit conversion functions
Conversion functions can now be made explicit using the explicit specifier.
~~~
struct A {
  operator bool() const { return true; }
};

struct B {
  explicit operator bool() const { return true; }
};

A a;
if (a); // OK calls A::operator bool()
bool ba = a; // OK copy-initialization selects A::operator bool()

B b;
if (b); // OK calls B::operator bool()
bool bb = b; // error copy-initialization does not consider B::operator bool()
~~~

### Attributes
Attributes provide a universal syntax over __attribute__(...), __declspec, etc.
~~~
// `noreturn` attribute indicates `f` doesn't return.
[[ noreturn ]] void f() {
  throw "error";
}
~~~
### constexpr
Constant expressions are expressions evaluated by the compiler at compile-time. Only non-complex computations can be carried out in a constant expression. Use the constexpr specifier to indicate the variable, function, etc. is a constant expression.
~~~
constexpr int square(int x) {
  return x * x;
}

int square2(int x) {
  return x * x;
}

int a = square(2);  // mov DWORD PTR [rbp-4], 4

int b = square2(2); // mov edi, 2
                    // call square2(int)
                    // mov DWORD PTR [rbp-8], eax
constexpr values are those that the compiler can evaluate at compile-time:

const int x = 123;
constexpr const int& y = x; // error -- constexpr variable `y` must be initialized by a constant expression
~~~
Constant expressions with classes:
~~~
struct Complex {
  constexpr Complex(double r, double i) : re{r}, im{i} { }
  constexpr double real() { return re; }
  constexpr double imag() { return im; }

private:
  double re;
  double im;
};

constexpr Complex I(0, 1);
~~~
### Delegating constructors
Constructors can now call other constructors in the same class using an initializer list.
~~~
struct Foo {
  int foo;
  Foo(int foo) : foo{foo} {}
  Foo() : Foo(0) {}
};

Foo foo;
foo.foo; // == 0
~~~
### User-defined literals
User-defined literals allow you to extend the language and add your own syntax. To create a literal, define a T operator "" X(...) { ... } function that returns a type T, with a name X. Note that the name of this function defines the name of the literal. Any literal names not starting with an underscore are reserved and won't be invoked. There are rules on what parameters a user-defined literal function should accept, according to what type the literal is called on.

Converting Celsius to Fahrenheit:
~~~
// `unsigned long long` parameter required for integer literal.
long long operator "" _celsius(unsigned long long tempCelsius) {
  return std::llround(tempCelsius * 1.8 + 32);
}
24_celsius; // == 75
~~~
String to integer conversion:
~~~
// `const char*` and `std::size_t` required as parameters.
int operator "" _int(const char* str, std::size_t) {
  return std::stoi(str);
}

"123"_int; // == 123, with type `int`
~~~
