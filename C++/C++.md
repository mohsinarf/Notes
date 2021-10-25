## Pointers
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

## Casting

## Template

## Iterator
