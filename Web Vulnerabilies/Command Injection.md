
 1. Command injection`echo exec("whoami")`
 2.  `system("whoiam")`
 3. Blind Command Injection  `exec("whoami")`
 4. [Command Injection payloads](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Command%20Injection)
 5. Searching
            Regular expression security cheat sheet

**Command Injection  VS Code Injection**
- Command injection is **string to command**.
(**; ,|| , &&** are used to join command.The `exec()` function is for code execution.
 - Code injection is "string to code".("." is used to join code)(`eval("echo "....)` function).Using " , ' for testing.
