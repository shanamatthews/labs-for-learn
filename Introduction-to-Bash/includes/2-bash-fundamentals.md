# Bash fundamentals

An understanding of Bash starts with an understanding of Bash syntax. Once you know the syntax, you can apply it to every Bash command that you execute.

The full syntax for a Bash command is:

```
command [options] [arguments]
```

Bash treats the first string it encounters as a command. The following command uses Bash's `ls` (for "list") command to display the contents of the pwd — shorthand for the current working directory: 

```bash
ls
```
 
Bash commands are often accompanied by arguments. For example, you can include a path name in an `ls` command to list the contents of another directory:

```bash
ls /etc
```

Most Bash commands have options for modifying how they work. Options, also called *flags*, give a command more specific instructions. As an example, files and directories whose names begin with a period are hidden from the user and are not displayed by `ls`. However, you can include a `-a` (for "all") flag in an `ls` command and see everything in the target directory:

```bash
ls -a /etc
```

You can even combine flags for brevity. For example, rather than type `ls -a -l /etc` to show all files and directories in Linux's "/etc" directory in long form, you can type this instead:

```bash
ls -al /etc
```

Bash is nothing if not concise. In fact, it is sometimes remarkable (and a point of pride among Bash aficionados) how much can be accomplished with a single command.

## Getting help

Which options and arguments can be used, or must be used, varies from command to command. Fortunately, Bash documentation is built into the operating system. Help is never more than a command away. To learn about the options for a command, use the `man` (for "manual") command. For instance, to see all the options for the `mkdir` ("make directory") command, do this:

```bash
man mkdir
```

`man` will be your best friend as you learn Bash. `man` is how you find the information you need to understand how any command works.

Most Bash and Linux commands support the `--help` option. This shows a description of the command's syntax and options. To demonstrate, type `mkdir --help`. The output will look something like this:

```
Usage: mkdir [OPTION]... DIRECTORY...
Create the DIRECTORY(ies), if they do not already exist.

Mandatory arguments to long options are mandatory for short options too.
  -m, --mode=MODE   set file mode (as in chmod), not a=rwx - umask
  -p, --parents     no error if existing, make parent directories as needed
  -v, --verbose     print a message for each created directory
  -Z                   set SELinux security context of each created directory
                         to the default type
      --context[=CTX]  like -Z, or if CTX is specified then set the SELinux
                         or SMACK security context to CTX
      --help     display this help and exit
      --version  output version information and exit

GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
Report mkdir translation bugs to <http://translationproject.org/team/>
Full documentation at: <http://www.gnu.org/software/coreutils/mkdir>
or available locally via: info '(coreutils) mkdir invocation'
```

Help obtained this way is typically more concise than help obtained with `man`. 

## Using wildcards

Wildcards are symbols that represent one or more characters in Bash commands. The most frequently used wildcard is the asterisk. It represents zero characters or a sequence of characters. Suppose the pwd contains hundreds of image files, but you only want to see the PNG files — the ones whose file names end with **.png**. Here's the command to list only those files:

```bash
ls *.png
```
> Linux has no formal concept of a file-name extension as other operating systems do. This doesn't mean that PNG files won't have a **.png** extension. It simply means that Linux attaches no special significance to the fact that the file names end with **.png**.

Now let's say the pwd also contains JPEG files, and some end in **.jpg** while others end in **.jpeg.** Here's one way to list all the JPEG files:

```bash
ls *.jpg *.jpeg
```

And here is another:

```bash
ls *.jp*g
```

The \* wildcard matches on zero or more characters, but the ? wildcard represents a single character. If the current directory contains files named **0001.jpg**, **0002.jpg**, and so on though **0009.jpg**, the following command lists them all:

```bash
ls 000?.jpg
```

Yet another way to use wildcards to filter output is to use square brackets, which denote groups of characters. The following command lists all the files in the pwd whose names contain a period immediately followed a lowercase J or P, which means it lists all the **.jpg**, **.jpeg**, and **.png** files, but not **.gif** files:

```bash
ls *.[jp]*
```

In Linux, file names and the commands that operate upon them are case-sensitive. So to list all the files in the pwd whose names contain periods followed by an uppercase *or* lowercase J or P, you could type this:

```bash
ls *.[jpJP]*
```

Expressions in square brackets can represent ranges of characters. For example, the following command lists all the files in the current directory whose names begin with a lowercase letter:

```bash
ls [a-z]*
```

This command, by contrast, lists all the files in the current directory whose names begin with an uppercase letter:

```bash
ls [A-Z]*
```

And this one lists all the files in the current directory whose names begin with a lowercase *or* uppercase letter:

```bash
ls [a-zA-Z]*
```

Based on this, can you guess what the following commands will do?

```bash
ls [0-9]*
ls *[0-9]*
ls *[0-9]
```

If you need to use one of the wildcard characters as an ordinary character, you make it literal or "escape it" by prefacing it with a backslash. So, if for some reason you had an asterisk as part of a file name — something you should never do intentionally — you could search for it with a command such as:

```bash
$ ls *\**
```

Armed with this information about Bash syntax, you're ready to start learning the key Bash commands that every sysadmin should know.