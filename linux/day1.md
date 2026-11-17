# Command Line Editors – Part 01

## 1. Introduction to Command Line Editors

### What is a Command Line Editor?
A command line editor is a text editor that runs inside a terminal and allows users to create and modify files without a graphical interface.

### Why do we need it?

Command line editors are particularly useful when:

1. Working on remote computers or supercomputers.
2. Connecting to systems with poor network bandwidth.
3. Editing files directly inside a terminal.
4. Preparing scripts and configuration files for job execution.
5. Working in environments where file transfer requires multiple network hops.
6. GUI-based editors are unavailable.

**Key point:** Knowing at least one or two terminal editors is important for working effectively in Linux and remote environments.

---

## 2. Types of Text Editors

There are different categories of text editors.

### A. Line Editors

- Work inside a terminal.
- Allow editing one line at a time.
- Do not provide a complete visual representation of the file.
- Commands are used to perform editing operations.

Examples:

| Editor | Description |
|---|---|
| ed | One of the oldest Unix line editors. |
| ex | A slightly improved and more user-friendly version of ed. |

**Important:** These editors originated during the early Unix days and are available across many Unix/Linux systems.

### B. Terminal / Visual Editors

- Work inside the terminal.
- Provide a visual interface for editing.
- Allow users to navigate and modify files more conveniently.

Examples:

| Editor | Description |
|---|---|
| Pico | Originally associated with the Pine email application. |
| Nano | Improved editor based on Pico; simple and user-friendly. |
| vi | One of the most popular and powerful terminal editors. |
| Emacs | A powerful alternative to vi. |

**Important facts:**
- Pico was associated with Pine.
- Additional features were added to Pico, resulting in Nano.
- vi and Emacs are two popular choices among programmers.
- The instructor prefers vi.

### C. GUI-Based Editors

These editors work in a graphical user interface.

| Editor | Environment / Purpose |
|---|---|
| KWrite | KDE desktop environment; similar to Windows Notepad. |
| gedit | GNOME desktop environment; used for plain text files. |
| Sublime Text | Feature-rich programming editor. |
| Atom | Popular among GitHub users. |
| Brackets | Popular among HTML developers. |

### D. Integrated Development Environments (IDEs)

An IDE combines several development tools in one environment.

Usually includes:

- Code editor
- Compiler
- Debugger
- Other development tools

Examples mentioned:

1. Eclipse
2. Bluefish
3. NetBeans (Apache)

### Important Practical Recommendation

Learn at least two terminal editors:

- **vi:** Powerful, feature-rich and widely used.
- **nano:** Simple and beginner-friendly.

Both are generally bundled with Linux systems, making them useful when additional installations are not possible.

---

## 3. Important Features of a Good Text Editor

A good editor should provide the following capabilities.

### A. Navigation Features

1. Scroll through the file.
2. View content page by page.
3. Display the current position.
4. Identify the current line number.
5. Navigate:
   - Character by character.
   - Word by word.
   - Line by line.
6. Search using patterns and regular expressions.

### B. Text Editing Features

1. Insert text.
2. Replace existing text.
3. Delete text.
4. Cut, copy and paste.
5. Search and replace text.
6. Apply changes to:
   - The entire file.
   - A specific portion of the file.

### C. Programming Features

**Syntax highlighting**

- Editor understands the programming language.
- Highlights keywords and syntax.
- Helps identify syntactical errors while writing code.

### D. Advanced Features

| Feature                | Purpose |

| Key mapping            | Assign key combinations to perform complex operations. |
| Initialization scripts | Load predefined settings and key mappings when the editor starts. |
| Macros                 | Record and replay repetitive operations. |
| Plugins                | Extend the editor's functionality. |

**Important:** vi and Emacs satisfy these advanced editor requirements.

---

# PART 2: ED LINE EDITOR

## 4. Introduction to ed

### What is ed?

`ed` is an old Unix line-oriented text editor.

Characteristics:

- Edits text one line at a time.
- Does not display the entire file visually.
- Uses short, mostly single-letter commands.
- Commands operate on specific lines or ranges.
- Supports regular expressions.
- Supports inserting, deleting, replacing, moving and joining lines.

### Why learn ed today?

Even though ed is not commonly used for everyday editing:

1. It helps understand the origin of vi commands.
2. Many ed commands are also used in vi.
3. It is useful in emergency situations when other editors are unavailable.
4. It is commonly available in Unix/Linux environments.

### ed vs ex

- `ed`: Original line editor.
- `ex`: Slightly improved and more user-friendly version of ed.
- Many commands are common to both.

---

## 5. Getting Help for ed

Two commands are used to access documentation:

| Command | Purpose |
|---|---|
| `man ed` | Opens the manual page for ed. |
| `info ed` | Opens the detailed information page for ed. |

The instructor uses `info ed` to explore:
- Overview.
- Introduction to line editing.
- Command formats.
- Different editing operations.

---

## 6. Opening a File Using ed

Syntax:

```bash
ed filename
```

Example:

```bash
ed test.txt
```

When ed opens a file:

- It reads the file into memory.
- It displays the number of bytes read.
- It does not automatically display all the file contents.
- There is no prompt by default.

### Displaying the prompt

```text
P
```

- Capital `P` enables the command prompt.
- The prompt appears as `*`.
- You can now enter editing commands.

### Understanding the byte count

If ed displays `117` after opening a file, it means that 117 bytes have been read.

You can verify the file size using:

```bash
ls -l test.txt
```

---

## 7. Understanding Addresses in ed

**This is one of the most important concepts in ed.**

An address specifies which line or range of lines an editing command should operate on.

General command format:

```text
[start_address],[end_address]command[parameters]
```

An address can represent:
- A particular line.
- The current line.
- The last line.
- A range of lines.
- A line matching a regular expression.

### 7.1 Address Symbols

| Address | Meaning | Example |
|---|---|---|
| `2` | Second line | `2p` |
| `.` | Current line | `.p` |
| `$` | Last line | `$p` |
| `%` | All lines | `%p` |
| `,` | Entire buffer | `,p` |
| `+` | Next line | `+p` |
| `-` | Previous line | `-p` |
| `;` | Current line to last line | `;p` |
| `/pattern/` | Line matching a pattern | `/hello/p` |

### 7.2 Important Address Explanations

**1. Line number**

```text
2
```
Refers to the second line.

**2. Current line (`.`)**

```text
.
```
Refers to the line where the editor is currently positioned.

**3. Last line (`$`)**

```text
$
```
Refers to the last line of the file.

**4. All lines (`%`)**

```text
%
```
Refers to the entire file.

**5. Comma (`,`)**

```text
,
```
Refers to the complete buffer, from the first line to the last line.

**6. Plus (`+`)**

Moves the address to the next line.

**7. Minus (`-`)**

Moves the address to the previous line.

**8. Semicolon (`;`)**

Refers to the range starting from the current line and continuing to the last line.

**9. Regular expression address**

```text
/hello/
```
Searches for a line containing the pattern `hello`.

### Quick Memory Trick

- `.` = Current
- `$` = Last
- `%` = All
- `,` = Entire buffer
- `+` = Next
- `-` = Previous
- `;` = Current to end
- `/pattern/` = Search

---

## 8. Important ed Commands

Most ed commands are single-letter commands.

| Command | Meaning | Purpose |
|---|---|---|
| `p` | Print | Display the current line or specified range. |
| `a` | Append | Insert text after the current line. |
| `i` | Insert | Insert text before the current line. |
| `c` | Change | Replace the addressed line(s) with new text. |
| `d` | Delete | Delete the addressed line(s). |
| `s` | Substitute | Search and replace text. |
| `j` | Join | Join two or more lines. |
| `m` | Move | Move lines to another position. |
| `t` | Transfer | Copy addressed lines to another position. |
| `u` | Undo | Reverse the previous editing operation. |
| `f` | File | Display the current filename. |
| `r` | Read | Read a file or command output into the buffer. |
| `w` | Write | Save the buffer to disk. |
| `q` | Quit | Exit the editor. |
| `P` | Prompt | Enable or disable the command prompt. |
| `!` | Shell escape | Execute a shell command. |

---

## 9. Printing and Navigating Through a File

### Print a particular line

```text
2p
```

Displays the second line.

### Print the current line

```text
.p
```

Displays the current line.

### Print the last line

```text
$p
```

Displays the last line.

### Print the entire file

```text
,p
```

Or:

```text
%p
```

### Print a range of lines

```text
2,3p
```

Displays lines 2 and 3.

### Move to the next line

```text
+
```

### Move to the previous line

```text
-
```

### Print from the current line to the end

```text
;p
```

### Search for a pattern

```text
/hello/
```

Searches for the first occurrence of `hello` and moves to the matching line.

Example:

```text
/oldest/
```

If the word occurs in line 3, the editor moves to line 3.

---

## 10. Executing Shell Commands Inside ed

The exclamation mark `!` allows you to execute shell commands without leaving the editor.

Syntax:

```text
!command
```

Example:

```text
!date
```

- Executes the `date` command in the shell.
- Displays its output.
- Does not automatically insert the output into the current file.

### Reading command output into the buffer

Syntax:

```text
r !command
```

Example:

```text
r !date
```

This reads the output of the date command into the current buffer.

**Difference:**

| Command | Action |
|---|---|
| `!date` | Executes date and displays output. |
| `r !date` | Executes date and inserts output into the buffer. |

---

## 11. Reading and Writing Files

### Read another file into the current buffer

Syntax:

```text
r filename
```

Reads the contents of another file into the current buffer.

### Save the file

```text
w
```

Writes the current buffer to disk.

### Exit the editor

```text
q
```

Quits the editor and returns to the shell.

### Typical workflow

```bash
ed test.txt
```

Inside ed:

```text
P
,p
w
q
```

Meaning:
1. Open the prompt.
2. Display the entire file.
3. Save the file.
4. Quit.

**Remember:** Editing the buffer and saving it to disk are separate operations. Use `w` to save your changes.

---

# PART 3: PRACTICAL EDITING OPERATIONS

## 12. Creating a Test File

The instructor creates a test file instead of modifying important files in the home directory.

Example:

```bash
echo "Hello world" > test.txt
```

Append additional lines:

```bash
echo "Welcome to line editor" >> test.txt
echo "ed is perhaps the oldest editor out there" >> test.txt
echo "End of file" >> test.txt
```

Display the file:

```bash
cat test.txt
```

The initial test file contains four lines.

---

## 13. Deleting Lines

Command:

```text
d
```

Deletes the current line.

### Delete the last line

```text
$d
```

Explanation:

- `$` identifies the last line.
- `d` deletes the addressed line.

### Delete a specific line

```text
2d
```

Deletes line 2.

### Delete a range

```text
2,4d
```

Deletes lines 2 through 4.

**Example from the demonstration:**

```text
$d
w
q
```

The last line is deleted, the file is saved, and the editor is closed.

---

## 14. Appending Text

Command:

```text
a
```

Appends text after the current line.

### Example

```text
1a
Appended this line after the first line
.
```

Explanation:

1. `1` selects the first line.
2. `a` starts appending text after that line.
3. Enter the new text.
4. Enter a single `.` on an empty line to finish the append operation.

**Important:** The standalone dot terminates the text-input mode. It is not part of the inserted text.

### Append at the end of the file

```text
$a
New line at the end
.
```

---

## 15. Inserting Text

Command:

```text
i
```

Inserts text before the current line.

Example:

```text
3i
Inserted before line 3
.
```

This inserts the new text before the original third line.

### Append vs Insert

| Append (`a`) | Insert (`i`) |
|---|---|
| Adds text after the current line. | Adds text before the current line. |
| `2a` adds after line 2. | `2i` adds before line 2. |

---

## 16. Substituting / Replacing Text

The `s` command is used to search for and replace text.

Syntax:

```text
s/old/new/
```

Where:
- `s` = Substitute.
- First expression = Text to search for.
- Second expression = Replacement text.

### Example

```text
2s/welcome/WELCOME/
```

Replaces `welcome` with `WELCOME` in line 2.

### Changing the first word

The instructor demonstrates replacing a word in a specific line with a capitalized version.

General syntax:

```text
2s/old/A/
```

Here, `A` is the replacement text.

### Replace text in a specific line

```text
3s/welcome/WELCOME/
```

Changes `welcome` to `WELCOME` only in line 3.

### Important

By default, the substitution command replaces the first matching occurrence in the addressed line.

---

## 17. Regular Expressions in ed

Regular expressions (regex) help identify text patterns instead of searching only for fixed words.

They can be used for:
- Finding specific words.
- Matching characters.
- Replacing text.
- Modifying multiple lines.
- Adding prefixes or suffixes.
- Performing bulk editing operations.

### Important regex symbols

| Symbol | Meaning |
|---|---|
| `.` | Matches any single character. |
| `*` | Matches zero or more repetitions of the preceding expression. |
| `.*` | Matches any sequence of characters. |
| `\(...\)` | Groups an expression in basic regular expressions. |
| `\1` | Refers to the first captured group in the replacement. |
| `/.../` | Delimits a search pattern. |

### Example: Adding a prefix to every line

Suppose the file contains:

```text
Hello world
Welcome to line editor
ed is the oldest editor
End of file
```

We want to add `prefix` at the beginning of every line.

Concept:

1. Select all lines using `%`.
2. Match the complete content using a regular expression.
3. Add the required prefix.
4. Use back-reference `\1` to retain the original content.

Command:

```text
%s/\(.*\)/prefix \1/
```

Explanation:

| Part | Meaning |
|---|---|
| `%` | Apply to all lines. |
| `s` | Substitute. |
| `\(.*\)` | Capture the complete line. |
| `prefix ` | Text to insert at the beginning. |
| `\1` | Restore the original captured content. |

Result:

```text
prefix Hello world
prefix Welcome to line editor
prefix ed is the oldest editor
prefix End of file
```

**Important:** `\1` is called a back-reference. It inserts the text captured by the first group.

### Example: Replacing text only in selected lines

```text
3,5s/PREFIX/prefix/
```

This changes `PREFIX` to `prefix` only in lines 3 through 5.

### Important concept

The same substitution operation can be applied to:
- One particular line.
- A selected range.
- The entire file.

Only the address range needs to change.

---

## 18. Joining Lines

Command:

```text
j
```

Joins two or more lines into one line.

### Example

```text
5,6j
```

Joins lines 5 and 6.

Explanation:
- `5,6` selects lines 5 and 6.
- `j` joins the selected lines.

The resulting line contains the combined text.

**Use case:** When two separate lines need to become one continuous line.

---

## 19. Moving Lines

Command:

```text
m
```

Moves a line or range of lines to another position.

Syntax:

```text
[address]m destination
```

### Example: Move line 5 after line 1

```text
5m1
```

Moves line 5 to the position after line 1.

### Example: Move line 2 to the beginning

```text
2m0
```

Moves line 2 to the beginning of the file.

### Understanding destination addresses

| Destination | Meaning |
|---|---|
| `m0` | Move to the beginning of the file. |
| `m1` | Move after line 1. |
| `m2` | Move after line 2. |

**Important:** `m` changes the position of the original line; it does not create a copy.

---

## 20. Undoing Changes

Command:

```text
u
```

Undo reverses the previous editing operation.

Example:

```text
u
```

The instructor uses this after moving a line to restore the previous arrangement.

**Use case:** When an unwanted editing operation has been performed.

---

## 21. Finding the Current Filename

Command:

```text
f
```

Displays the name of the file currently being edited.

Example:

```text
f
```

Useful when working with multiple files or when you need to confirm which file is open.

---

## 22. Displaying the Current Line

Command:

```text
p
```

Prints the current line.

Example:

```text
.p
```

Displays the contents of the current line.

---

# PART 4: COMPLETE COMMAND REFERENCE

## 23. ed Command Cheat Sheet

| Command | Function | Example |
|---|---|---|
| `P` | Enable prompt | `P` |
| `p` | Print current line | `.p` |
| `,p` | Print entire file | `,p` |
| `%p` | Print all lines | `%p` |
| `2p` | Print line 2 | `2p` |
| `2,4p` | Print lines 2–4 | `2,4p` |
| `a` | Append after current line | `2a` |
| `i` | Insert before current line | `2i` |
| `c` | Change addressed lines | `2c` |
| `d` | Delete current line | `.d` |
| `$d` | Delete last line | `$d` |
| `s` | Substitute text | `2s/old/new/` |
| `j` | Join lines | `2,3j` |
| `m` | Move lines | `5m1` |
| `t` | Copy lines | `2t5` |
| `u` | Undo previous operation | `u` |
| `f` | Display filename | `f` |
| `r` | Read a file | `r other.txt` |
| `r !` | Read command output | `r !date` |
| `w` | Save file | `w` |
| `q` | Quit editor | `q` |
| `!` | Execute shell command | `!date` |

---

## 24. Important Differences to Remember

### 1. ed vs vi

| ed | vi |
|---|---|
| Line-oriented editor. | Visual terminal editor. |
| Works one line at a time. | Displays a larger portion of the file. |
| No full visual navigation. | Supports visual navigation. |
| Older Unix editor. | More convenient for modern terminal editing. |
| Uses short commands. | Also uses many commands originating from ed/ex. |

### 2. Append vs Insert

| Append (`a`) | Insert (`i`) |
|---|---|
| Adds text after the addressed line. | Adds text before the addressed line. |

### 3. Read vs Write

| Read (`r`) | Write (`w`) |
|---|---|
| Reads content into the buffer. | Saves buffer contents to disk. |

### 4. Shell command vs Reading shell output

| `!command` | `r !command` |
|---|---|
| Executes a shell command. | Executes a shell command and reads its output into the buffer. |

### 5. Move vs Transfer

| Move (`m`) | Transfer (`t`) |
|---|---|
| Moves the original lines. | Copies the addressed lines to another location. |

### 6. Delete vs Change

| Delete (`d`) | Change (`c`) |
|---|---|
| Removes the addressed lines. | Replaces the addressed lines with newly entered text. |

---

## 25. Important Concepts Demonstrated in the Practical Session

The instructor demonstrated the following operations on `test.txt`:

1. Created a test file using the `echo` command.
2. Opened the file using `ed`.
3. Checked the file size using `ls -l`.
4. Enabled the prompt using capital `P`.
5. Navigated to the first and last lines.
6. Printed the entire buffer.
7. Printed a selected range of lines.
8. Searched for words such as `hello` and `oldest`.
9. Moved forward and backward between lines.
10. Displayed the current line.
11. Executed the `date` shell command.
12. Read the output of `date` into the buffer.
13. Saved changes using `w`.
14. Deleted the last line.
15. Appended a new line after the first line.
16. Used regular expressions to replace words.
17. Changed the case of selected words.
18. Displayed the filename using `f`.
19. Appended a line at the end of the file.
20. Joined two lines using `j`.
21. Moved a line using `m`.
22. Moved a line to the beginning using `m0`.
23. Undid the previous operation using `u`.
24. Added a prefix to every line using regular expressions and back-references.
25. Applied substitutions to a selected range of lines.
26. Saved the final buffer and exited.

---

## 26. Final Takeaways

1. Command line editors are essential when working with remote Linux systems.
2. Nano is simple, while vi is powerful and widely used.
3. ed is a historical line editor and helps explain the origin of vi commands.
4. Addresses determine which lines an editing command operates on.
5. `%` and `,` represent the entire buffer.
6. `.` represents the current line and `$` represents the last line.
7. `a`, `i`, `d`, `s`, `j` and `m` are important editing commands.
8. Regular expressions enable powerful bulk editing.
9. Back-references such as `\1` help retain matched text during replacement.
10. `r` reads content into the buffer, while `w` saves it to disk.
11. `!` executes shell commands.
12. `u` reverses the previous editing operation.
13. Understanding ed commands makes learning vi/ex easier.

**Most important commands to memorize:**

```text
p  - Print
a  - Append
i  - Insert
c  - Change
d  - Delete
s  - Substitute
j  - Join
m  - Move
t  - Transfer
u  - Undo
f  - Filename
r  - Read
w  - Write
q  - Quit
!  - Shell command
P  - Prompt
```

**End of Command Line Editors – Part 01.**