# Code Explaination
This is a simplified explaination of the first practical of cloud computing, which involves spliting a c program into multiple modules and then executing it. The program explained in this is different from the one done in class for the exact implementation as mentioned in the lab manual check the folder named *firstprac*.

## Program Overview
This program is very simple - it just displays "Hello, world!" on the screen. But it's split into multiple files to demonstrate how larger programs are organized:

1. `main.c` - The starting point of our program
2. `module1.h` - A header file that announces what functions exist
3. `module1.c` - The actual implementation of those functions

## Let's Start with `main.c`

```c
// main.c
#include <stdio.h>
#include "module1.h"

int main() {
    hello();
    return 0;
}
```

### Line-by-Line Explanation:

- `#include <stdio.h>`: This brings in the Standard Input/Output library (think of it like borrowing a book from the library). The angle brackets `<>` tell the compiler to look in the standard system directories.

- `#include "module1.h"`: This includes our own custom header file. The quotes `""` tell the compiler to look in the current directory first.

- `int main() { ... }`: Every C program needs a main function. This is where your program starts running - like the entrance to a building.

- `hello();`: This calls the function named `hello()` that we defined elsewhere.

- `return 0;`: This tells the operating system that our program finished successfully (like giving a thumbs up).

## Now Let's Look at `module1.h`

```c
// module1.h
#ifndef MODULE1_H
#define MODULE1_H

void hello();

#endif
```

### Line-by-Line Explanation:

- `#ifndef MODULE1_H` and `#define MODULE1_H`: These lines are like putting up a sign that says "Only enter this room once!" This prevents the compiler from including this file multiple times, which could cause errors.

- `void hello();`: This is a function declaration. It's like telling everyone "Hey, there's going to be a function called `hello()` that doesn't take any inputs and doesn't return any value." It's a promise that this function will exist somewhere.

- `#endif`: This marks the end of our "only enter once" protection.

## Finally, `module1.c`

```c
// module1.c
#include <stdio.h>
#include "module1.h"

void hello() {
    printf("Hello, world!\n");
}
```

### Line-by-Line Explanation:

- `#include <stdio.h>`: We need this again because each source file is compiled separately, and this file needs access to the `printf` function.

- `#include "module1.h"`: This includes our own header file to ensure our function implementation matches our declaration.

- `void hello() { ... }`: This is the actual implementation of our `hello()` function - the code that will run when we call `hello()`.

- `printf("Hello, world!\n");`: This displays text on the screen. The `\n` creates a new line (like pressing Enter).

## How It All Works Together

1. When you compile this program:
   - Each `.c` file gets compiled separately into an "object file"
   - Then these object files get linked together to form your final program

2. When you run the program:
   - The computer starts at `main()`
   - It calls `hello()`
   - `hello()` prints "Hello, world!"
   - The program returns 0 (success) and ends

## Why Split Code Into Multiple Files?

Imagine if you had 10,000 lines of code in one file - it would be very hard to find anything! By splitting your code into logical pieces:

- It's easier to understand
- Multiple people can work on different files
- You can reuse parts in other programs
- You only need to recompile the files you change

This is an important skill for building larger programs, especially in cloud computing where you might be working with many interconnected components.
