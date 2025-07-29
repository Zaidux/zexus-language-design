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

## Error Handling
Filesystem operations can often fail due to issues like a file not being found or a lack of permissions. All functions that can fail (like `read_text`, `write_text`, etc.) will **throw an error**. It is best practice to wrap these calls in a `try/catch` block.

### Example Usage

```zexus
let configFile = "./config.txt"

# Use a try/catch block to handle potential errors
try:
  let configContent = filesystem.read_text(configFile)
  print "Configuration loaded successfully."
catch (error: FileNotFoundError):
  print "Error: The config file was not found. Using default settings."
catch (error: PermissionError):
  print "Error: Do not have permission to read the config file."
