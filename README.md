This repo consists of basic linux setup. This could be a good starting point if someone uses WSL (windows subsystem for linux).

# Helpful commands

## 1. Screen:
### Why use it?
1. If user runs multiple tasks simultaneously.
2. If user wants to keep a task running while the machine closes or logs out etc. (Safe way to run long tasks)
3. Monitor a task while running other tasks.

### Basic operation 

| Description 				| Command 				|
|---------------------------------------|---------------------------------------|
| Start a new session with session name (recommended) | `screen -S <session_name>`		|
| List running sessions / screens	| `screen -ls`				|
| Attach to a running session		| `screen -x`				|
| Attach to a running session with name	| `screen -r <session_name>`		|
| Detach a running session		| `screen -d <session_name>`		|

## 2. tmux:
### Why use it?
1. More functional alternative to SCREEN

### Basic operation

| Description 				| Command 				|
|---------------------------------------|---------------------------------------|
| Create a new window (with shell) | `Ctrl+b c`		|
| Choose window from a list	| `Ctrl+b w`				|
| Switch to window 0 (by number )		| `Ctrl+b 0`				|
| Rename the current window	| `Ctrl+b ,`		|
| Split current pane horizontally into two panes		| `Ctrl+b %`		|
| Split current pane vertically into two panes| `Ctrl+b "`				|
|  Go to the next pane		| `Ctrl+b o`				|
| Toggle between the current and previous pane	| `Ctrl+b ;`		|
| Close the current pane		| `Ctrl+b x`		|

# Basic commands with helpful usage

## 1. ls

| Description 				| Command 				|
|---------------------------------------|---------------------------------------|
| List file names and edit them | `ls -1 select_certain_files_using_wildcards \| sed -e 's/pattern_to_remove//'`		|

## 2. find

| Description 				| Command 				|
|---------------------------------------|---------------------------------------|
| Find last modified file in a folder | `find folder_to_find -type f -printf "%T@ %p\n" \| sort -n \| cut -d' ' -f 2- \| tail -n 1`		|

