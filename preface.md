# Preface

## Why plutr

First, we would like to find out the difference between console and shell.
A DOS console does with batches, but does within, or out, called a command?
The history of Unix console is started with sh, csh, tcsh, .., bash (shell family).
A shell is with comands and scripts.

The definition of a shell is the layer between an operating system and applications.
However, about a console, consoles begin with, as of, a monitor with keyboard for
a mainframe. What's the diff. between shell is still unknown yet. However, it was
the precidential multi-tasking system with the muti-user feather.

To analyze it, the first is that they need communication, such as the `whos` and
`finger`. Can we name these command, instruction, function or order? This console
only has the text-mode. Therefore, the applications for the console are also
always in the text-mode. The flow in-between goes, such as a pipe or redirect.
To compare with a morden shell; however, it remains the same for most application.

My idea becomes very clear now; a console looks for >_< while shell look for $_$.

Hence, I'm mad.

## Checkup test for the distinction of a console or a shell
```
shell$ command -o -p --option filename (clear)
shell$ command subcommand ($ git init)
dos console> function? filename /parameter
dos console> command? filename /parameter
dos console> instruction? filename /parameter
dos console> order? filename /parameter
```

## Data flow

1. pipe
```
  > a | b
  $ a | b
```
2. redirect
```
  > (not supported??)
  $ a > b; a 1> b; a 2> b; (correctness check needed..)
```
3. are there others?
To be investigated..








