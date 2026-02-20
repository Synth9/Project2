# Project X README

Student 1: Partner1 Name (123456789)

Student 2: Partner2 Name (123456987)

## Project Status
This the current status of the project ...

## Known Issues
The project fails to function properly in ...

## Code References
* [Different ways to initialize variables](https://stackoverflow.com/questions/22543875/different-ways-to-initialize-variables)
* [Some other link](https://stackoverflow.com)

## Generative AI Use
I used ChatGPT for Prompt 1, and ZZZZZ for Prompt 2....

### Prompt 1
How do I iterate over all characters in a string in C++17?

### Response 1
In C++17, you can iterate over all characters in a string using a range-based for loop. Here's an example:
```cpp
#include <iostream>
#include <string>

int main() {
    std::string myString = "Hello, World!";

    // Using range-based for loop to iterate over characters in the string
    for (char c : myString) {
        std::cout << c << " ";
    }

    return 0;
}
```
In this example, the `for (char c : myString)` loop iterates over each character in the string `myString`, and the variable `c` takes on the value of each character in turn. The loop body prints each character followed by a space.

This is a concise and readable way to iterate over the characters in a string in C++17.

### Chagnes 1
I only needed the `for` loop part, and my string was named `bar` so I changed it to just:
```cpp
// AI Generated
for (char c : bar) {
```

### Prompt 2
in a makefile how do I make a generic rule for compilation

### Response 2
In a Makefile, you usually create a generic (pattern) rule to compile source files into object files. This avoids writing one rule per file.
Basic generic compilation rule (C)
CC      := gcc
CFLAGS  := -Wall -Wextra -O2

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

How this works:


%.o: %.c → any .o depends on the matching .c


$< → the first prerequisite (the .c file)


$@ → the target (the .o file)


Example usage
OBJS = main.o util.o math.o

myprog: $(OBJS)
	$(CC) $(OBJS) -o myprog

Make will automatically use the generic rule to build each .o.

C++ version
CXX     := g++
CXXFLAGS := -Wall -Wextra -O2

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@


Using built-in rules (often enough)
Make already has implicit rules for common languages, so this may work without writing your own rule:
CFLAGS += -Wall -Wextra -O2

Then just list your objects and targets.

Generic rule with headers (optional improvement)
%.o: %.c %.h
	$(CC) $(CFLAGS) -c $< -o $@

⚠️ This only works if every .c has a matching .h. For real projects, use dependency generation:
CFLAGS += -MMD -MP
-include $(OBJS:.o=.d)


Summary


Use pattern rules: %.o: %.c


Use automatic variables: $@, $<


Let Make’s implicit rules work when possible


If you want, tell me:


C, C++, or another language


single directory or subdirectories


simple project or large codebase


I can tailor the Makefile exactly to your setup.

### Changes 2
Changed some of the flags for what I needed.

### Prompt 3
how to make a library from one object file in linux

### Response 3
You can do this in a couple of common ways on Linux, depending on whether you want a static or a shared library. I’ll walk through both, starting simple.

1️⃣ Static library (.a) from one object file
This is the most straightforward case.
Step 1: compile your source into an object file
gcc -c foo.c -o foo.o

Step 2: create a static library from the object file
ar rcs libfoo.a foo.o

That’s it.
You now have libfoo.a.
Using it later
gcc main.c -L. -lfoo


Naming matters: libfoo.a is found with -lfoo.


2️⃣ Shared library (.so) from one object file
For shared libraries, the object file must be position-independent code (PIC).
Step 1: compile with -fPIC
gcc -fPIC -c foo.c -o foo.o

Step 2: create the shared library
gcc -shared -o libfoo.so foo.o

Using it later
gcc main.c -L. -lfoo

At runtime, the loader must find it:
export LD_LIBRARY_PATH=.
./a.out

(or install it into /usr/lib, /usr/local/lib, etc.)

3️⃣ Verifying what’s inside
Static library contents
ar t libfoo.a

Symbols exported
nm libfoo.a
# or
nm -D libfoo.so


4️⃣ Minimal example recap
# static
gcc -c foo.c
ar rcs libfoo.a foo.o

# shared
gcc -fPIC -c foo.c
gcc -shared -o libfoo.so foo.o


If you want, tell me:


which compiler (gcc / clang),


whether this is for C or C++,


or if you’re hitting a specific error,


and I’ll tailor it exactly to your case.

### Changes 3
Changed to match my filenames.