## Zexus Language Specification v1.0

This document provides the official language specification for Zexus Version 1.0. It serves as the definitive guide for developers, contributors, and implementers of the Zexus language.

* 1. Introduction
Zexus is a high-level, declarative programming language designed to unify modern application development. Its core philosophy is to make coding intuitive, readable, and powerful by allowing developers to state what they want to achieve, while the language handles the complex implementation details.

# 1.1. Core Principles
The design of Zexus is guided by four main principles:

 * Natural Language First: Syntax consists of readable words, not cryptic symbols, making code easy to write and understand.

 * Declarative & Intent-Based: Focus on the "what," not the "how." Describe your desired end state, and let the language handle the implementation.

 * Context is King: The compiler is smart. It understands whether you're defining UI, backend logic, security rules, or data, and adapts accordingly.

 * Everything is a Module: Every file, library, and component is a self-contained, pluggable module, promoting clean and organized code.

* 2. Language Syntax & Semantics

2.1. Comments
Comments are used to leave notes in the code and are ignored by the compiler.
 * Single-line comments start with #.
 * Multi-line comments or docstrings are enclosed in """ ... """.
<!-- end list -->
# This is a single-line comment.

"""
This is a multi-line docstring,
often used at the top of a file for documentation.
"""

* 2.2. Variables
Variables are declared using the let keyword.
let message = "Hello, Zexus!"
let userCount = 50

* 2.3. Control Flow
Zexus uses standard if/else blocks for conditional logic.
if user.isLoggedIn:
  print "Welcome back!"
else:
  print "Please log in."

Loops are handled with a readable for each syntax.
for each user in allUsers:
  print user.name

* 2.4. UI and Components
The user interface is defined using screen and component blocks.
 * A screen represents a full page or view and can contain different states.
 * A component is a reusable piece of UI.
<!-- end list -->
screen Login:
  initial_state: :form

  state :form {
    # ... form content ...
  }

* 2.5. Actions
Backend logic or complex frontend operations are defined in action blocks. Actions can be async and use await for operations that take time.
action fetchUserData(userId):
  let response = await http.get("/api/users/{userId}")
  return response.json()

* 2.6. Data and Databases
Data structures are defined using entity. A database schema is defined within a database block.
database UserDB:
  entity User:
    username: text
    email: email_string

* 3. Module System
The module system allows code to be organized into separate files via export and use.
 * export: Makes functions, components, etc., available to other files. Can be named or default.
 * use: Imports code from another file.
<!-- end list -->
# File: utils.zx
action doSomething: print "Done."
export { doSomething }

# File: main.zx
use { doSomething } from "./utils.zx"
doSomething()

* 4. Error Handling
Zexus uses a try/catch mechanism for robust error handling. The throw keyword is used to trigger custom errors.
entity MyError { message: text }

try:
  if someConditionIsBad:
    throw MyError(message: "Something went wrong!")
catch (error: MyError):
  print "Caught a specific error: {error.message}"

* 5. The Standard Library
The Zexus Standard Library provides a built-in toolkit for common tasks.

* 5.1. Data Structures (List & Map)
 * List: An ordered collection of items. ["a", "b", "c"]
 * Map: A collection of key-value pairs. {"name": "Zaidu", "level": 10}

* 5.2. Text Manipulation (Text)
Provides functions on text variables, such as .length(), .to_uppercase(), .trim(), and .split(by:).

* 5.3. Math (Math)
A module for common mathematical operations, accessed via the Math namespace (e.g., Math.sqrt(16)).

* 5.4. Date & Time (DateTime)
A module for handling dates and times. Get the current time with DateTime.now() or create a new date with DateTime.new(...).

* 5.5. Filesystem (filesystem)
A module for interacting with local files, providing functions like filesystem.read_text(path) and filesystem.write_text(path, content).

* 5.6. Networking (http)
A module for making web requests, such as http.get(url) and http.post(url, body). These are async operations and must be used with await.

* 6. Command-Line Tools
Interaction with the Zexus ecosystem is handled by two command-line tools.
 * zx: The Zexus runner, used to execute .zx files.
   zx main.zx

 * zpm: The Zexus Package Manager, used to install and manage libraries.
   zpm install CoolUI

* 7. Appendix: Formal Grammar (EBNF)
This section provides a formal, technical definition of the language syntax for compiler developers. The grammar will be fully detailed in future revisions.
Example Rule:
variable_declaration ::= "let" , identifier , "=" , expression ;