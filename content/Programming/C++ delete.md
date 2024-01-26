Difference between delete and [[C++ malloc() & free() |free]]
The **delete** operator should only be used for deallocating the memory allocated either using the **new** operator or for a NULL pointer, and **free()** should only be used for deallocating the memory allocated either using malloc(), calloc(), realloc() or for a NULL pointer.

delete operator calls the **destructor** to ensure cleanup and resource deallocation for objects.

https://www.geeksforgeeks.org/delete-and-free-in-cpp/