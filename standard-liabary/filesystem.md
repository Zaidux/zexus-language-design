# Filesystem Module

The Zexus `Filesystem` module provides a standard interface for interacting with the computer's file system. All functions are accessed through the `filesystem` namespace.

## Functions

| Function                          | Purpose                                                          |
| --------------------------------- | ---------------------------------------------------------------- |
| `filesystem.read_text(path)`      | Reads the entire content of a text file and returns it as `Text`.  |
| `filesystem.write_text(path, content)` | Writes text to a file. Overwrites the file if it exists.       |
| `filesystem.append_text(path, content)`| Adds text to the end of an existing file.                        |
| `filesystem.exists(path)`         | Returns `true` if a file or directory exists at the given path.  |
| `filesystem.delete(path)`         | Deletes the file or directory at the given path.                 |
| `filesystem.list_files(path)`     | Returns a `List` of file and directory names inside a given path. |

## Example Usage

```zexus
# Define paths
let configFile = "./config.txt"
let logFile = "./app.log"

# Check if a config file exists and read from it
if filesystem.exists(configFile):
  let configContent = filesystem.read_text(configFile)
  print "Configuration loaded."
  
  # Append a log message to the log file
  let now = DateTime.now().format(as: "YYYY-MM-DD HH:mm:ss")
  filesystem.append_text(logFile, "[{now}] Application started successfully.\n")
else:
  # Write a default log message if no config is found
  filesystem.write_text(logFile, "No config file found. Running with defaults.\n")
