# Data Structures
### arrays
``` ```
### structs
``` ``` 
### singly linked list
```
typedef struct temp_ll { // singly linked list
    struct temp_ll next;
    char *name;
} linked_list;
```
### doubly linked list
```
typedef struct temp_dll { // doubly linked list
    struct temp_dll previous;
    struct temp_dll next;
    char *name;
    int value;
} doubly_linked_list;
```
### Trie (prefix tree)
- a trie is a structure that can store values, words, etc, shaped as a tree:
    - example: storing all the names in a class; instesad of a linked list with each node representing a student, use a trie that maps out all possible combinations of letters to represent the names.

```
typedef struct temp_trie { // trie; example is alphabetically made
    struct temp_trie *letters[]; // this holds the entire alphabet. this does NOT denote which letter this is; rather, what demonstrates which letter it is is based on where it was originally referenced in memory (previous letter's array slot)
    boolean end; // denote whether or not the path we have gone down is a valid path.
} trie;
```

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
    // More info below.

// Close
fclose(file)
``` 

There are two (main) ways to read files:
<br><br>
**fread**
- read RAW DATA, stopping at the specified data size
- Used for:
    - Reading image (bitmap) files
```
size_t fread(void *ptr, size_t size, size_t nmemb, FILE *stream); 
```
- ptr: buffer memory block to store data
- size: SPECIFIED size for each element to be read (BYTE size)
- nmemb: NUMBER of elements (of specified size) to read
- stream: file, terminal input (stdin)

<br>**fgets**
- read LINES of TEXT, stopping at \n
- Used for:
    - .txt
    - .csv
```
char *fgets(char *s, int n, FILE *stream);
```
- s: pointer that is made, buffer for where data is stored. 
- n: maximum char number to read
- stream: file, terminal input (stdin)

### Images
- Image (bitmaps) are formatted as such:
    - HEADER: 54 bytes
        - file header (): 14 bytes
        - image-specific information header (): 40 bytes 
    
    - DIMENSIONS
        - Padding is determined by if pixels are in a multiple of 4. If not, they will be padded.
            - 3 bytes * 3 pixels = 9 bytes, meaning 3 padding bytes are added.
            - 3 bytes * 12 pixels = 36 bytes, meaning no padding added.
        - Colors are encoded in BGR.
        - Width: encoded as a positive number in hexidecimal
        <br>
        ``` width of 0000001a = 26 pixels wide```
        - Height: can be encoded as either positive or negative.
            - negative: "top-down" image, meaning the first row of file = first row of at top of image
            <br>
            ``` height of ffffffe0 = 15 pixels tall```
            - positive: "bottom-up" image, meaning the first row of file = bottommost row of image

    - IMAGE INFORMATION
        - 24 bits/pixel; 1 byte per color, encoded in B,G,R order.
            

### .WAV Files
- Audio calculations
    - Bytes needed for 1 second of a song
    - Samples needed to encode 1 second of song
    Given a CD-quality audio (44,100 hz sampling rate at 16-bit quality) with 2 channels

    - Hz, 1 cycle per second
    44,100 samples/second * 16 bits / 8 = 88,200 bytes/second
    88,200 bytes/second * 2 = 176,400 bytes/second for 2 channels 


- HEADER
    - 44 bytes long
    - utilizes uint8_t (unsigned 8-bit integer)

```
// Create an array of bytes to store each line from the WAV header
uint8_header[HEADER_SIZE]; // given in Volume pset code
fread(header, HEADER_SIZE, 1, input);
fwrite(header, HEADER_SIZE, 1, output);
```

- SAMPLES AND WRITING 
    - 1 sample is measured in 16-bit integers

```
// Create a buffer for 1 sample, read, and write it in
int16_t buffer;
fread(&buffer, sizeof(int16+t), 1, input); // input is presumably the input file
fwrite(&buffer, sizeof(int16_t), 1, output);
```

# Coding Principles
### Endian
- Big Endian: where the most significant byte is stored at the lowest memory address. Big end first.
    - example: 365 in binary in Big Endian is:
    <br>
    ```0000 0001 0110 1101```
- Little Endian: where the least significant byte is stored at the lowest memory address. Little end first.
    - example: 365 in binary in Little Endian is:
    <br>
    ```1011 0110 1000 0000```

### Unsigned/Signed Data Types
- Unsigned: can only be positive, doubling upper limit of values that can be stored
- Signed: can be either positive or negative
    - The most significant bit indicates the sign of the number (0 = pos, 1 = neg)
    ```01111111 = +127```
    <br>
    ```10000000 = -128```