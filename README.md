This repo consists of basic linux setup. This could be a good starting point if someone uses WSL (windows subsystem for linux).

# CHEATS

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

