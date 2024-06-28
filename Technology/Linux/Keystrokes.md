### end-of-file (EOF)
Typically **Ctrl**+**D**.
- When writing to [[stdin]] **Ctrl**+**D** can be used to signal the end of data transmission when the data originates from the keyboard.
- In Windows environments, the typical EOF keystroke is **Ctrl**+**Z**.

### [[Signals#SIGINT - interrupt|SIGINT]] - interrupt signal
Upon pressing **Ctrl**+**C**, the foreground process (the one you're currently interacting with) receives a [[Signals#SIGINT - interrupt|SIGINT]].
Ctrl+C primarily affects the foreground process. Background processes are not directly affected by Ctrl+C. You can use the [[jobs|bg]] and [[jobs|fg]] commands or the [[jobs]] command to manage background processes.