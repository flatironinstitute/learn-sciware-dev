# Sciware

## Tools to make programming easier
### Intro to code editors and debugging

https://github.com/flatironinstitute/learn-sciware-dev/tree/master/16_EditorsVSCode


## Rules of Engagement

### Goal:

Activities where participants all actively work to foster an environment which encourages participation across experience levels, coding language fluency, *technology choices*\*, and scientific disciplines.

<small>\*though sometimes we try to expand your options</small>


## Rules of Engagement

- Avoid discussions between a few people on a narrow topic
- Provide time for people who haven't spoken to speak/ask questions
- Provide time for experts to share wisdom and discuss
- Work together to make discussions accessible to novices

<small>
(These will always be a work in progress and will be updated, clarified, or expanded as needed.)
</small>


## Zoom Specific

- If comfortable, please keep video on so we can all see each other's faces.
- Ok to break in for quick, clarifying questions.
- Use Raise Hand feature for new topics or for more in-depth questions.
- Please stay muted if not speaking. (Host may mute you.)
- We are recording. Link will be posted on #sciware Slack.


## Future Sessions

- Suggest topics and vote on options in #sciware Slack


## Today's Agenda



# Intro to IDEs



# Quick reference guides



# Workspaces

Workspaces are a quality of life feature of vscode that let you:

- Save which folders you are using.
- Configure settings that only apply to said folders.
- Set tasks (compiling/running) and debugging configurations.
- Store and restore UI state associated with that workspace (opened files, tab order, ...)
- Enable or disable extensions only for that workspace.


## Creating a workspace

### Open the folder(s) you will use
<img height=80% width=80% src="./assets/gifs/open_folder.gif">


## Save workspace
<img height=80% width=80% src="./assets/gifs/save_workspace.gif">


## Load workspace
<img height=80% width=80% src="./assets/gifs/open_workspace.gif">



# Integrated execution

Execute python codes without a terminal!


## Select your python interpreter
<img height=80% width=80% src="./assets/gifs/select_interpreter.gif">


## Run your code!
<img height=80% width=80% src="./assets/gifs/integrated_execution.gif">



# Compile and Debug c++ code



## Create a task file

### It tells VSCode how to compile your code
<img height=80% width=80% src="./assets/gifs/create_task.gif">


## Examples

### Compiling with g++
```yml
{
 "version": "2.0.0",
 "tasks": [
  {
   "type": "cppbuild",
   "label": "Build .cpp file", //Remember this label!
   "command": "/usr/bin/g++", //Compiler
   "args": [
    "-g",
    "${workspaceFolder}/simple_addition.cpp",
    "-o",
    "${workspaceFolder}/simple_addition.out"
   ],
   "options": {
    "cwd": "${fileDirname}"
   },
   "problemMatcher": [
    "$gcc"
   ],
   "group": {
    "kind": "build",
    "isDefault": true
   },
   "detail": "compiler: /usr/bin/g++"
	 }
 ]
}
```


## Compiling with make
```yml
{
 "version": "2.0.0",
 "tasks": [
  {
   "type": "shell",
   "label": "Build .cpp file", //Remember this name!
   "command": "make",
   "group": {
    "kind": "build",
    "isDefault": true
   }
  }
 ]
}
```


## Create a launch file

### Defines how the debugging goes
<img height=80% width=80% src="./assets/gifs/create_launch.gif">


## Examples

### For c++

```yml
{
 "version": "0.2.0",
 "configurations": [        
   {
    "name": "(gdb) g++ buld and debug",
    "type": "cppdbg",
    "request": "launch",
    "program": "${workspaceFolder}/simple_addition.out",
    "args": [],
    "stopAtEntry": false,
    "cwd": "${workspaceFolder}",
    "environment": [],
    "externalConsole": false,
    "MIMode": "gdb",
    "setupCommands": [
     {
      "description": "Enable pretty-printing for gdb",
      "text": "-enable-pretty-printing",
      "ignoreFailures": true
     }
    ],
    "preLaunchTask": "Build .cpp file"
   }
 ]
}
```


## For python

```yml
{
 "version": "0.2.0",
 "configurations": [
  {
   "name": "Python: Specific file",
   "type": "python",
   "request": "launch",
   "program": "${workspaceFolder}/simple_addition.py",
   "console": "integratedTerminal"
  }
 ]
}
```


## Debugging options

### Breakpoints
<img height=80% width=80% src="./assets/gifs/create_breakpoint.gif">


## Types of breakpoints

- Normal breakpoints: "Breaks" the execution of the code when it is hit.
- Conditional breakpoints:
    - Expression condition: The breakpoint will "break" execution whenever the expression evaluates to True
    - Hit count: "Breaks" execution only if it has been hit a particular number of times
- Inline breakpoints: Only are hit when the execution reaches a specific line and column.


## Debugging Actions

- Continue/Pause (F5)
- Step Over (F10)
- Step Into (F11)
- Restart (Ctrl+Shift+F5)
- Stop (Shift+F5)


## Step Over
<img height=80% width=80% src="./assets/gifs/step_over.gif">


## Step Into
<img height=80% width=80% src="./assets/gifs/step_into.gif">


## Step Out
<img height=80% width=80% src="./assets/gifs/step_out.gif">


## Watch Variables
<img height=80% width=80% src="./assets/gifs/watch_variables.gif">



# Working on Remote Clusters

All of the cool features you've seen so far, can be used when editing _remote_ files, i.e. on a cluster!!


## How It Works

<img height=80% src="./assets/vscode_remote_setup.png">


## What You Can Do

- View, move, and reorganize directories
- Edit files
- Debug
- Static linting
- Formatting
- View figures


## Bonus: Setup

1. Get OpenSSH compatible SSH client
2. Download the [Remote SSH extension](https://code.visualstudio.com/docs/remote/ssh) for VSCode
3. Enable key-based authentication, see the [VSCode docs](https://code.visualstudio.com/docs/remote/troubleshooting#_configuring-key-based-authentication) for details
4. From the VSCode command palette search for `Remote-SSH: Connect to Host`
5. Enter your username and host info, e.g. `jasm3285@login.colorado.edu`

See the official instructions [here](https://code.visualstudio.com/docs/remote/ssh-tutorial)