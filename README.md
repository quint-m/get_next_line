# get_next_line

`get_next_line` is a C utility function that reads and returns the next line from a file descriptor. Designed for efficiency and simplicity, it allows developers to process files line by line in a memory-safe manner.

## Features

- Reads a single line at a time from a file descriptor.
- Handles files, standard input (stdin), and network sockets.
- Supports variable buffer sizes via the `BUFFER_SIZE` macro.
- Gracefully handles EOF and empty lines.

---

## How It Works

Each time `get_next_line` is called, it:
1. Reads from the file descriptor into a buffer.
2. Processes the buffer to extract the next complete line.
3. Returns the line as a dynamically allocated string.
4. Preserves any leftover data in the buffer for the next call.

If the end of the file is reached or an error occurs, it returns `NULL`.

---

## Installation

Clone this repository:

```bash
git clone https://github.com/your-username/get_next_line.git
cd get_next_line
```

To use it in your project, simply include the `get_next_line.c` and `get_next_line.h` files in your codebase.

---

## Usage

Here's an example usage:

```c
#include <fcntl.h>
#include "get_next_line.h"

int main(void)
{
    int fd = open("example.txt", O_RDONLY);

    char *line;
    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }

    close(fd);
    return (0);
}
```

Compile with:

```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 your_program.c get_next_line.c -o your_program
```

---

## Configuration

You can adjust the buffer size by defining `BUFFER_SIZE` during compilation:

```bash
gcc -D BUFFER_SIZE=64 ...
```

---

## Notes

- Be sure to `free` the memory allocated for each line after use.
- Undefined behavior may occur if `BUFFER_SIZE` is set to zero or a very large value.
- Only tested on Unix-like operating systems.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

Feel free to suggest improvements or report issues in the [issues](https://github.com/your-username/get_next_line/issues) section.

---

Let me know if you'd like to add or change anything!
