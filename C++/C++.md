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
sort(vec.begin(), vec.end());
abs(x);
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
