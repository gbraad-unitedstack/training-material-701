# Training 701

### Python
Gerard Braad

gerard@unitedstack.com


## Coding style

  * PEP8


## Before submit

  * run unitests


## Debugging
Debugging is a the process of finding and resolving defects that prevent correct
operation of a computer process.

Many different techniques exist

  * synchronous
  * asynchronous (concurrency)


## pdb
`pdb` is an interactive source code debugger for Python programs, offered as a
module. 

  * breakpoints
  * single stepping
  * inspection of stack frames
  * source code listing
  * evaluation of code


## Run pdb
To run the python debugger you can call it on your scriptfile

```
$ pdb [scriptfile]
```

or

```
$ python -m pdb [scriptfile]
```

## Commands
Below are several `pdb` commands to deal with the inspection and execution of
the scriptfile.


| Command  | Shorthand | Description                                           |
|----------|-----------|-------------------------------------------------------|
| break	   | b	       | Set a breakpoint.                                     |
| continue | c	       | Continue with program execution.                      |
| exit     | q         | Abort the program.                                    |
| help     | h         | Print list of commands or help for a given command.   |
| list     | l         | Show source code around current line.                 |
| return   | r         | Continue execution until the current function returns.|
| step     | s         | Continue and break on next instruction.               |
| next     | n         | Similar to `step`, but does not enter function call)  |
|          | p         | Evaluate expression and print the result              |

Note: `print` will be evaluated by the interpreter. `pp` is pretty print.


## Breakpoints
There are different ways to specify a breakpoint

  * `break [scriptfile]:[linenumber]`
  * `break [module].[functionname]`
  * `break [location], [condition]`

You can `enable` and `disable` beakpoints using their identifier. `ignore` will
ignore the breakpoint at the next crossing, while `clear` will remove a
breakpoint entirely.


## More advanced options
You can also use `commands` to execute commands at the breakpoint and `jump` to
change the execution flow.

For more information: [pdb](https://pymotw.com/2/pdb/)


## Add pdb
A good way to start the debugger is to start the debugging session from the
script itself. For this you need to add a call to `set_trace()`.

Anywhere in your code you could do:

```
import pdb; pdb.set_trace()
```

and start the execution of the script from a terminal. You might have to check
the service file to see which command is started.
