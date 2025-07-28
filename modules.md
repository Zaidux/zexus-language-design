# The Zexus Module System

The Zexus module system allows you to organize your code into separate files and share code between them. This is done through `export` and `use` statements. Each file in Zexus is its own module.

## Exporting from a Module

You can make functions, components, entities, or variables available to other files using the `export` keyword.

### Named Exports
To export multiple specific items from a file, wrap them in curly braces `{}`.

```zexus
# File: utils.zx

action sayHello(name: text):
  print "Hello, {name}!"

action sayGoodbye(name: text):
  print "Goodbye, {name}!"

let appVersion = "1.0"

# Export specific actions and variables
export { sayHello, sayGoodbye, appVersion }

Default Export
A file can also have one default export. This is usually for the main thing the file provides, like a screen.
# File: home_screen.zx

screen HomeScreen:
  # ... screen content ...

# Export the screen as the default for this file
export default HomeScreen

Using Modules
To use code from another file, you use the use keyword.
Importing Named Exports
To import only specific items from a module, list them inside curly braces {}. This is your use.only idea in action!
# File: main.zx

# Import only 'sayHello' and 'appVersion' from utils.zx
use { sayHello, appVersion } from "./utils.zx"

sayHello("Zaidu") # "Hello, Zaidu!"
print "Version: {appVersion}" # "Version: 1.0"

Importing a Default Export
To import a default export, you just name it directly.
# File: main.zx

# Import the default export from home_screen.zx
use HomeScreen from "./screens/home_screen.zx"

# Now you can use HomeScreen
display: HomeScreen()