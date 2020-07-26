# Prelude

## Table of Conent
```
  I. Why plutr

  II. Methodology

  III. Data flow
    III-1. Pipe
    III-2. Redirect
    III-3. Socket
      III-3.1. Definition of socket operators
      III-3.2. Usage
      III-3.3. What the =>, <= and <=> is

  IV. Command list (Working draft)
    IV-1. Console commands
    IV-2. Shell commands
    IV-3. Common commands
    IV-4. Routine commands

  V. Session description
    V-1. Share session
      V-1.1. Gramma
      V-1.2. Usage
    V-2. Calculator (calc) session
      V-2.1. Gramma
      V-2.2. Feature add-on
      V-2.3. Usage
```

## I. Why plutr

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


## II. Methodology

Checkup test for the distinction of a console or a shell
```
shell$ command -o -p --option filename (clear)
shell$ command subcommand ($ git init)
dos console> function? filename /parameter
dos console> command? filename /parameter
dos console> instruction? filename /parameter
dos console> order? filename /parameter
```

## III. Data flow

### III-1. Pipe

A pipe is a one way distribution (FIFO).
```sh
1> a | b
2$ a | b
```

### III-2. Redirect

A redirection is a one way dispatch.
The features are only partially supported in 1> console.
```sh
2$ a > b; a 1> b; a 2> b; (forward redirection)
2$ a < b; a <1 b; a <2 b; (reverse redirection)
2$ a <> b                 (assertion test => yes|no)
2$ a <-> d                (diff a b; a feature for vedors to follow)
```

### III-3. Socket

#### III-3.1. Definition of socket operators
Some socket operators are sketched as follows:

```sh
3? a <= b
3? a => b
3? a <=> b
```
in which the function is mainly for the 3?-layer for either network
server-app or in-OS communication. For example, the former the
socket transmission via the http(s) application layer; aonther, the
remote desktop applications. For the later, the xterm-xwin model.
Currently, all the windows in Linux distributions have very low
efficiency in the sysop or developers do not care, because it's enough
for you. It is not described for the details. Say, 'no' games can
be developed in Linux.

#### III-3.2. Usage
Can multiple sockets do in the illustation below?

                                <======>
                            //===========\\
               (((kernel)graphica.so)<=>application.o)
                             \\==========//
                                ========>
                                  <====

in which it is applicable to the remote desktop with a certain level
of security. The interace is clean.

The `2$ b => a <1` and `2$ a <=> b <1`are not supported in v1.0.
The `1> a => b $2 are supported, but the difinition is unclear at the
point for your reading.`

#### III-3.3. What the =>, <= and <=> is
The the function of the three operators are briefly described in the
following draft table:

```
              Table 1. Functions of socket operators (Draft)
  ==================================================================
         Operator                 Fuction
  ------------------------------------------------------------------

      i)    =>               ==.-----^ ...>-(o)==>
                               v-----. ....>/

     ii)    <=               as above in the other direction

    iii)    <=>              <==.-----^ ...>-(o)==>
                               v-----. ....>/

  ==================================================================
   The dot (.) denotes the signal while the (^) and (v) the sluts.
```


## IV. Command list (Working draft)

### IV-1. Console commands

```sh
dir directory_name
```


### IV-2. Shell commands

**1 Personal**

**1.1. Regular**

**1.1.1. Privilage commands**

The following commands are only for SysOp only,

```sh
- add user                    #                                    (SysOp)
- add group default_group     # /root/path/to/default_groups.list - -rw --- ---
- add group group_name        # /root/path/to/groups.list
- grant group_name leader_name
```

The others for the group leaders who are granted,

```sh
  add greeting greeting_name  # ~/greetings.list      - -rw -rw ---
  add regard reard_name       # ~/regards.list        - -rw -rw ---
-                                                       (Group leader)
```

**1.1.2. Descirption of commands between privilage and normal users**

The only default group is with your supervisor or may be two, in which
the mangers are optional; only your major manger in the up-stream should be
there. The second default for you is those who is supervised by you. You can
do `who` and `finger`; say default `hi`, `hello` `hoi` and others defined by
someone who has the privilage to do it. Another command is  `contact` to
message all members in the group.

However, we only share to the friends in the
`share marklee Do you have time?` command. Who is my friends? We can add one
by one such as `add friend marklee`. The friends can also be edited in
`~/friends.list` to either add many at once or comment someone out in a line
of `# marklee`. To delete it is anoter option, but it can be added in again.
The comment is your helper or you want to remove it.


**1.1.3. Regular commands for the users and their friends**

**Group**
```sh
- who
- finger user_name

- hi there_name    // respond: (my_name) hi there_name (touch of the contact)
- hello there_name
- hoi there_name
- defined-greeting there_name

- contact user_name messages  // one line
```

**Friend**
```sh
- add friend user_name                 # ~/friends.list - --- --- -rw
- share user_name topic                # enter a conversion session by share()
- block user_name_w_wildcard_w_regexp  # ~/blocked_users.list - --- --- -rw
                                       # ~/share_sessions
                                       # ~/share_sessions/John_001.log
- unblock user_name_w_wildcard_w_regexp
- login user_name
- logout
- exit (for console in v1.0 w/o net)

- how?
- where?   // ~~ pwd //
```


### IV-3. Common commands

The common commands for both console (1>) and shell (2>) terminals.
```sh
- echo log_messages_to_user   # typically used in *.bat in 1> and *.sh in 2$
                              # echo $enviromnet-variable
- mkdir folder_name           # with default `1> md` alias
- rmdir folder_name           # with defualt `1> rd` alias
- calc statement              # enter a calculation session if statement := ''
  calc env                    # sub-command to review variabls including ans
```


**IV-4. Routine comands**
```sh
- which command_name
- pwd                         # 2$ present working directory
  cd                          # 1> same as about; it does cd '' signature
- cd folder_name              # change direcory
- ls folder_name              # list directory
- touch file_name             # results in <fs type-"abcfs">
                              #              <file_name>new String('') EOF</file_name>
                              #            </fs>
```


## V. Session descriptions

### V-1. Share session

#### V-1.1. Gramma
```bnf
regards = /^bye~?$' | /^Good bye[\.!]$/ | sysop-defined  # it trigger the session closing
```

#### V-1.2. Usage
```session
Enter in a share session.
John> Hi Marry~
Marry> Hi John!
Marry> What's up!?
John> Okay, bye~
Marry> bye
session logout.
```


### V-2. Calculator (calc) session

#### V-2.1. Gramma
```bnf
statement := assign | expr
assign := expr
expr := the-js-features-for-number-without-Math-namespace
```

#### V-2.2 Feature add-on

**i)** `near(a,b, epsilon) => true|false`

A function for the resolution of floating point and decimal number
```es
const defaultEpsilon = 0.000001
export const near = (a, b, epsilon) => Math.abs(a - b) <= epsilon
// Usage:
const a = 1.23456
const b = 1.23457
near(a, b) === false
near(a, b, 0.0001) === true
```

#### V-2.3 Usage
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
