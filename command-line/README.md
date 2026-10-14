# Command-Line Fundamentals for Cybersecurity

## 1. What Is a Command-Line Interface (CLI)?

A Command-Line Interface (CLI) allows users to interact with an operating system or application by typing commands instead of using a graphical user interface (GUI).

CLIs are widely used in cybersecurity for system administration, log analysis, network troubleshooting, digital forensics, incident response, and automation.

Examples of command-line environments:
- **Windows:** Command Prompt (CMD), PowerShell
- **Linux:** Bash, Zsh
- **macOS:** Zsh, Bash

## 2. Anatomy of a Command

A typical command consists of a command name, options, and arguments.

**General syntax:**

```text
command [options] [arguments]
```

Example:

```bash
grep -i "failed" auth.log
```

Explanation:
- `grep` — searches text for matching patterns.
- `-i` — makes the search case-insensitive.
- `"failed"` — the search pattern.
- `auth.log` — the file being searched.

Note: Exact command syntax and available options depend on the operating system and shell.

## 3. Standard Input, Output, and Error

Command-line programs commonly use three standard data streams:

| Stream | File descriptor | Purpose |
|---|---:|---|
| Standard input (stdin) | 0 | Receives input |
| Standard output (stdout) | 1 | Displays normal output |
| Standard error (stderr) | 2 | Displays error messages |

These streams can be redirected or connected to other commands.

## 4. Pipes (`|`)

A pipe passes the standard output of one command to the standard input of another command.

**Example (Bash):**

```bash
cat auth.log | grep -i "failed"
```

This searches the contents of `auth.log` for lines containing "failed", ignoring case.

A simpler equivalent is:

```bash
grep -i "failed" auth.log
```

**Cybersecurity use cases:**
- Filtering authentication logs.
- Searching command output for suspicious indicators.
- Extracting relevant events from large text files.
- Combining small utilities to investigate incidents.

## 5. Output Redirection

Redirection sends command output to a file instead of displaying it in the terminal.

### Overwrite a file

```bash
command > output.txt
```

Writes standard output to `output.txt`, replacing its existing contents.

### Append to a file

```bash
command >> output.txt
```

Appends standard output to the end of the file.

### Redirect errors

```bash
command 2> errors.txt
```

Writes standard error to `errors.txt`.

### Redirect output and errors (Bash)

```bash
command > output.txt 2>&1
```

Writes both standard output and standard error to `output.txt`.

**Forensic caution:** Redirection can create or modify files. When investigating evidence, avoid writing into the original evidence location. Use an appropriate working copy and preserve the original evidence.

## 6. Command Chaining

Command chaining allows multiple commands to be executed in sequence.

### Semicolon (`;`) — Bash

```bash
command1; command2
```

Executes the second command after the first finishes, regardless of whether the first succeeds.

### AND operator (`&&`)

```bash
command1 && command2
```

Executes the second command only if the first succeeds.

### OR operator (`||`)

```bash
command1 || command2
```

Executes the second command only if the first fails.

These operators are useful for automating repetitive tasks and handling errors.

**Important:** Command-chaining syntax varies between shells. Check the documentation for the shell you are using.

## 7. Exit Codes

An exit code indicates whether a command completed successfully.

In Bash, the exit status of the most recently executed command is available through:

```bash
echo $?
```

Common interpretation:

- `0` — success.
- Non-zero — failure or another condition defined by the command.

Example:

```bash
grep "authentication failed" auth.log
echo $?
```

A result of `0` means at least one matching line was found. A result of `1` means no matching lines were found. Other errors can produce different exit codes.

Exit codes are useful when troubleshooting scripts, checking tool execution, and building automated security workflows.

## 8. Environment Variables

Environment variables store information that programs can use during execution.

Examples in Bash:

```bash
echo "$HOME"
echo "$PATH"
printenv
```

- `HOME` — commonly identifies the user's home directory.
- `PATH` — lists directories searched for executable commands.
- `printenv` — displays environment variables.

Environment variables are useful for configuring tools and writing scripts. Be careful not to expose credentials, tokens, or other secrets when displaying or sharing environment information.

## 9. Quoting and Special Characters

Quotation marks help the shell interpret arguments correctly.

Example:

```bash
cat "incident report.txt"
```

The quotation marks ensure that the filename is treated as one argument despite containing spaces.

In Bash:
- Single quotes (`'...'`) preserve the literal meaning of most enclosed characters.
- Double quotes (`"..."`) preserve most characters literally while allowing certain expansions, such as `$HOME`.
- The backslash (`\`) can escape special characters.

Understanding quoting is important because incorrect quoting can change a command's meaning or cause it to operate on unintended files.

## 10. Command-Line Applications in Cybersecurity

Command-line skills support many security activities:

| Activity | Example |
|---|---|
| Log analysis | Searching authentication logs |
| Network troubleshooting | Examining network configuration |
| Digital forensics | Searching files and reviewing metadata |
| Incident response | Collecting system information |
| Threat hunting | Filtering events for suspicious activity |
| Automation | Running repeatable scripts |
| Malware investigation | Extracting strings and examining artifacts in a controlled lab |

Always use appropriate authorization when examining systems, collecting information, or running security tools.

## 11. Safe Command-Line Practices

1. Read the command and understand its options before executing it.
2. Check the current directory and target path before modifying files.
3. Be especially careful with deletion commands, recursive operations, and commands run with administrator or root privileges.
4. Do not blindly copy commands from untrusted websites.
5. Avoid running unknown scripts on your main system.
6. Use an isolated virtual machine for potentially dangerous security experiments.
7. Preserve original forensic evidence and document investigative actions.
8. Never test security tools against systems without authorization.

## 12. Reliable References

- GNU Bash Reference Manual: https://www.gnu.org/software/bash/manual/bash.html
- GNU Bash Pipelines: https://www.gnu.org/software/bash/manual/html_node/Pipelines
- GNU Bash Redirections: https://www.gnu.org/software/bash/manual/html_node/Redirections.html
- GNU Bash Exit Status: https://www.gnu.org/software/bash/manual/html_node/Exit-Status.html
- Microsoft Command Prompt Reference: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/cmd

---

*Notes maintained for cybersecurity learning, command-line practice, and security investigation workflows.*
