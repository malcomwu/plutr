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


## Command list

1. Personal
1.1 Regular
- who
- finger user_name
- hi there_name   // respond: (my_name) hi there_name (touch of the contact)
- contact user_name messages  // one line
- share user_name topic   // enter a conversion session by share()
- block user_name_w_wildcard_w_regexp   // ~/blocked_users.list - --- --- -rw
                                        // ~/share_sessions
                                        // ~/share_sessions/John_001.log
- unblock user_name_w_wildcard_w_regexp
- login user_name
- logout
- exit (for console in v1.0 w/o net)

- how?
- where?   // ~~ pwd //

# For me and my friends in warm and in cold, avoid a cold fish.

1.2 Functional
- calc statement   // Enter a calculation session if statement := ''.

# For my tasks.

2. Compute routine
- which command_name
- pwd
- ls folder_name
- cd folder_name
- touch file_name

# So long..


### Session description

1. Share session
```session
Enter in a share session.
John> Hi Marry~
Marry> Hi John!
Marry> What's up!?
John> Okay, bye~
Marry> (^D) logout
```

2. Calculation session
2.1. Gramma
```session
Calc-Stmt ::= assign | expr
assign := expr
expr := the-js-features-for-number-without-Math-namespace
```
2.2 Feature add-on
**A function for the resolution of floating point and decimal number**
```es
const defaultEpsilon = 0.000001
export const near = (a, b, epsilon) => Math.abs(a - b) <= epsilon
// Usage:
const a = 1.23456
const b = 1.23457
near(a, b) === false
near(a, b, 0.0001) === true
```

2.3 Usage
Note that the usage in the command line is as below. The usage in the
session is about the same.
```shell
$ calc 1 + 2
ans = 3
$ calc a = 1 + 2
a = 3
$ touch dummy
$ pwd
$ // commands
$ calc a
a = 3
$ // commends
$ calc a + 3
a = 6
$ cal b = 4 + 5 + 6
b = 15
$ // commends
$ cal a + b
ans = 21
$ cal ans
ans = 21
$ cal c = a + b
c = 21
$ calc    // enter the described session
```
