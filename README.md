Here is a revised version of your `README.md` with improved formatting, clearer writing, and a more professional structure.

---

# Advanced Operating Systems: A POSIX Shell Implementation

## Overview

This project is a custom POSIX-compliant shell, built for an Advanced Operating Systems curriculum. It features a core loop that parses and executes user commands, supporting essential shell functionalities like I/O redirection, command pipelines, background processes, and signal handling.

## ✨ Features

-   **Dynamic Prompt:** Displays the `username`, `system name`, and the `current working directory` (with `~` representing the home directory).
-   **Core Built-in Commands:**
    -   `cd`: Change directory.
    -   `echo`: Print arguments to standard output.
    -   `pwd`: Print the current working directory.
-   **Command Implementation:**
    -   `ls`: Lists directory contents, with support for `-a` and `-l` flags.
    -   `pinfo`: Displays detailed process information for the shell itself.
    -   `search`: A built-in command to locate files and directories within a given path.
-   **Process Management:**
    -   **Foreground & Background:** Execute commands in the foreground (blocking) or background (non-blocking) using the `&` operator.
    -   **Signal Handling:** Gracefully handles `SIGINT` (Ctrl+C), `SIGTSTP` (Ctrl+Z), and `EOF` (Ctrl+D).
-   **I/O and Pipelines:**
    -   **Redirection:** Supports input (`<`), output (`>`), and append (`>>`) redirection.
    -   **Pipes:** Allows chaining multiple commands together using the pipe (`|`) operator.
-   **User Experience:**
    -   **Command History:** Persists the last 20 commands, navigable using the up-arrow key.
    -   **Tab Completion:** Provides auto-completion for file and directory names.

## 🚀 Getting Started

### Compilation

To compile the shell, use the provided `MakeFile`.

```bash
# This will generate the executable 'mainStar'
make -f MakeFile
```

### Usage

Run the compiled executable to start the shell session.

```bash
./mainStar
```

### Cleaning the Project

To remove all generated object files and the executable:

```bash
make -f MakeFile clean
```

## 📁 Project Structure

-   `mainStar.cpp`: The core shell loop, command parser, and execution coordinator.
-   `background.cpp`: Manages the execution of foreground and background jobs.
-   `cd.cpp`: Implements the built-in `cd` command.
-   `echo.cpp`: Implements the built-in `echo` command.
-   `history.cpp`: Manages loading, saving, and navigating the command history.
-   `ls.cpp`: Implements the `ls` command and its flags.
-   `pinfo.cpp`: Implements the custom `pinfo` command.
-   `pipe.cpp`: Handles the setup and execution of command pipelines.
-   `redirect.cpp`: Manages I/O redirection for `<`, `>`, and `>>`.
-   `search.cpp`: Implements the built-in `search` functionality.
-   `signal_handling.cpp`: Configures all signal handlers for the shell.

## 📝 Assumptions and Limitations

### Assumptions

1.  **Space Delimitation:** All commands, flags, and arguments must be separated by spaces.
2.  **Grep Patterns:** When using `grep`, patterns should be provided without surrounding quotes (e.g., `grep pattern file.txt` instead of `grep "pattern" file.txt`).
3.  **Execvp Handling:** Redirection and pipe commands are managed using the `execvp` system call.
4.  **Pinfo Scope:** The `pinfo` command displays information about the shell's own running process.

### Limitations

-   **Environment Variables:** The `OLDPWD` and `PWD` environment variables are not updated or used by the shell.
-   **Filesystem Library:** The project does not use the C++ filesystem library.
-   **Advanced Redirection:** Complex redirection operators (e.g., `2>&1`, `&>`, `>&`, `2>`) are not implemented.
-   **History Cap:** The command history is limited to the 20 most recent commands.
