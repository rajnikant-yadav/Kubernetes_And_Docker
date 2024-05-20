# Shell Scripting Tutorial

## What is Shell Scripting?

A shell script is a text file that contains a sequence of commands for a Unix-based operating system. These commands are executed by the shell, which is a command-line interpreter.

## Getting Started

1. **Create a File**: Start by creating a new file. You can use any text editor like `nano`, `vim`, or `gedit`.

    ```sh
    nano myscript.sh
    ```

2. **Add Shebang**: At the top of your file, add the shebang line. This tells the system which interpreter to use.

    ```sh
    #!/bin/bash
    ```

3. **Write Commands**: Below the shebang, write your commands just like you would type them in the terminal.

    ```sh
    #!/bin/bash
    echo "Hello, World!"
    ```

4. **Save and Close**: Save your file and close the text editor.

## Making the Script Executable

Before you can run your script, you need to make it executable.

```sh
chmod +x myscript.sh
```

## Running the Script
To run your script, type:

```sh
./myscript.sh
```