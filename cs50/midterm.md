# Data Structures
### arrays
``` ```
### structs
``` ``` 
### singly linked list
``` ```
### doubly linked list
``` ```
### Trie (prefix tree)
- a trie is a structure that can store values, words, etc, shaped as a tree:
    - example: storing all the names in a class; instesad of a linked list with each node representing a student, use a trie that maps out all possible combinations of letters to represent the names.

``` ```

### hash table
- Hashes can be formatted in a multitude of ways:
    1. Alphabetical: 26 buckets for each letter
    2. Alphabetical: 26^N buckets for lettter depth
    3. ALphabetical: Ranging number for sum of ASCII values of entier word or 4-5 letters
    - I implemented #2 in Speller

``` ```

### stacks/queues

# Memory
pointers: declaration, passing, and setting
- A pointer is denoted by a * or &.
    - &[variable] returns a pointer to the variable. It does NOT give the pointer to the value of the variable.
    - *[pointer variable] is used to dereference the pointer, and give you just the VALUE of the value. It'd be the same as using any non-pointer variable.
    - *[variable name] declares a variable and says that it is a pointer.
        - To declare a pointer, you need to initialize it to a valid memory location: this is where memory allocation comes into play. (see below for more)
``` 
int *p = malloc(sizeof(int));
*p = 5;
// p is a pointer, the value is 5

int q = 5;
int *ptr = &q;
*ptr += 5;
// q is 10
```

### Memory: malloc, free
- void* malloc(size_t size);
    - Size = the number of BYTES to allocate
    - Typically can just use ```sizeof()``` to pass in a certain data structure.  
    - Returns a pointer to that place in memory-- it is the BEGINNING of it. Needed to free the memory.
    - NOTE: One issue that may appear is that mallocing does not always work for structs. For anything that contains a char array field, that will have to be malloc'ed itself after the struct has been malloc'ed, because it's not posible to have predicted the amount of chars that were to be stored in that struct. 
- free()
    - Takes in a pointer, and frees the memory from heap. 

### Memory (conceptual): stack, heap
- stack: this is the automatic stuff that your code uses for local variables, etc. It is inflexible.
- heap: this is the stuff you malloc from and can be tricky to manage. It is flexible.

### Addressing and dereferencing memory
- Addressing memory
- Dereferencing memory
    - This is in the context of structs; you can use the ```->``` to dereference. 
    ``` 
    example

    typedef struct node_t {
        struct node_t next;
        int val;
    } node;

    // main
    node *first = malloc(sizeof(node));
    first->val = 10; // here, -> is used to dereference the pointer and access the integer variable and set it to 10. This can also be done across nodes themselves. Hypotehtically, you could do something like: 
    // first->next->next->next->next->val = 10;
    ```

# Debugging
-  help50: understand error messages
    - Usage: help50 make [program], help50 valgrind ./[program]
    - Ues by running it with  but before your compilation command.
-  debug50: debug each line
    - Usage: debug50 ./[program]
    - Use by running it with but before your execution command
-  valgrind: check memory usage
    - Usage: valgrind ./[program]
    - Use by running it with but before your execution command

# Alternative file types

### File Loading (including basics for reading .csv, txt, etc.)
Steps
``` 
// 1. File name
string fileName = "file.txt";

// 2. Open file
FILE *file = fopen(fileName, "r");


// Reading

// Close
``` 
### Images

### .WAV Files


# Coding Principles
Endian
- Big Endian: 
- Little Endian