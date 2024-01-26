The function malloc() in C++ is used to allocate the requested size of bytes and it returns a pointer to the first byte of allocated memory. A malloc() in C++ is a function that allocates memory at the runtime, hence, malloc() is a dynamic memory allocation technique. It returns a null pointer if fails.

free() function in C++ is used to dynamically de-allocate the memory.

```c++
pointer_name = (cast-type*) malloc(size);

int* int_ptr = (int*) malloc(sizeof(int));

free(int_ptr);
```

### Where Should Malloc be used?
-  Dynamic Memory allocation
- Heap memory
	- malloc() allocates the memory location on the heap and returns a pointer on the stack pointing to the starting address of the array type memory being allocated.
