Shell expansion” (sometimes called _parameter expansion_ or more generally “word expansion”) in Linux (and Unix-like shells such as **bash**) is the process where the shell transforms parts of your command line _before_ executing the command.

for example 
`echo $(date)`
this command will not echo $(date) but instead it will transform the $(date) and display the current date 

## The Sequence of Expansions

The Bash Reference Manual describes several kinds of expansions. [GNU](https://www.gnu.org/s/bash/manual/html_node/Shell-Expansions.html?utm_source=chatgpt.com)  
A commonly used summary (from “Understanding Expansion in the Linux Shell”) lists **seven** distinct steps/types of expansion that the shell applies (in a particular order) to the words in a command. 

Here are the major ones, in roughly the order they are applied:

| Expansion Type                     | What It Does                                                                                  | Example                                                                |
| ---------------------------------- | --------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Brace expansion**                | Expands patterns with `{}` into multiple strings                                              | `echo file{1..3}` → `file1 file2 file3`                                |
| **Tilde expansion**                | Converts `~` (optionally with a username) into a home directory path                          | `cd ~` → `/home/username`                                              |
| **Parameter (variable) expansion** | Replaces `$VAR` or `${VAR}` with the value of the variable                                    | `echo $HOME` → `/home/username`                                        |
| **Command substitution**           | Runs a sub-command and replaces its placeholder with its output                               | `echo "Today is $(date)"`                                              |
| **Arithmetic expansion**           | Evaluates arithmetic expressions                                                              | `echo $((2+3))` → `5`                                                  |
| **Process substitution**           | Substitutes a process output (or input) in place of a filename reference                      | `diff <(ls dir1) <(ls dir2)`                                           |
| **Word splitting**                 | After expansions, the shell splits the expanded text into words (based on the `IFS` variable) | If `VAR="a b c"`, then `$VAR` may become three arguments unless quoted |
| **Pathname expansion (globbing)**  | Expands wildcards (`*`, `?`, `[ ]`) into matching filenames                                   | `ls *.txt` → list of `.txt` files                                      |
|                                    |                                                                                               |                                                                        |

Note: Some sources combine or re-categorize these (e.g. process substitution is sometimes grouped with command substitution)


**trace** of how the Linux shell performs **expansion** 
🧩 Expansion Order
1️⃣ Brace Expansion
2️⃣ Tilde Expansion
3️⃣ Parameter (Variable) Expansion
4️⃣ Command Substitution
5️⃣ Arithmetic Expansion 
6️⃣ Word Splitting
7️⃣ Pathname Expansion (Globbing)