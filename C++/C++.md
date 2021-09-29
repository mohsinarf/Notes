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


## CONST keyword

## Mutable keyword

## Template

## Iterator

## Algorithm
```
#include <algorithm>   
sort(vec.begin(), vec.end());
abs(x);
```
## Casting

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
