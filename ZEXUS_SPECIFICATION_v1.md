# Zexus Language Specification v1.0

This document provides the official language specification for **Zexus Version 1.0**. It serves as the definitive guide for developers, contributors, and implementers of the Zexus language.

---

## 1. Introduction

Zexus is a high-level, declarative programming language designed to unify modern application development. Its core philosophy is to make coding intuitive, readable, and powerful by allowing developers to state what they want to achieve, while the language handles the complex implementation details.

---

### 1.1 Core Principles

The design of Zexus is guided by four main principles:

- **Natural Language First**  
  Syntax consists of readable words, not cryptic symbols, making code easy to write and understand.

- **Declarative & Intent-Based**  
  Focus on the *what*, not the *how*. Describe your desired end state, and let the language handle the implementation.

- **Context is King**  
  The compiler is smart. It understands whether you're defining UI, backend logic, security rules, or data, and adapts accordingly.

- **Everything is a Module**  
  Every file, library, and component is a self-contained, pluggable module, promoting clean and organized code.

---

## 2. Language Syntax & Semantics

### 2.1 Comments

Comments are used to leave notes in the code and are ignored by the compiler.

- Single-line comments start with `#`.
- Multi-line comments (docstrings) are enclosed in `""" ... """`.

```zexus
# This is a single-line comment.

"""
This is a multi-line docstring,
often used at the top of a file for documentation.
"""


---

2.2 Variables

Variables are declared using the let keyword.

let message = "Hello, Zexus!"
let userCount = 50


---

2.3 Control Flow

Zexus uses standard if/else blocks for conditional logic:

if user.isLoggedIn:
  print "Welcome back!"
else:
  print "Please log in."

Loops are handled with a readable for each syntax:

for each user in allUsers:
  print user.name


---

2.4 UI and Components

The user interface is defined using screen and component blocks.

A screen represents a full page or view and can contain different states.

A component is a reusable piece of UI.


screen Login:
  initial_state: :form

  state :form {
    # ... form content ...
  }


---

2.5 Actions

Backend logic or complex frontend operations are defined in action blocks. Actions can be async and use await.

action fetchUserData(userId):
  let response = await http.get("/api/users/{userId}")
  return response.json()


---

2.6 Data and Databases

Data structures are defined using entity. Database schemas are defined in a database block.

database UserDB:
  entity User:
    username: text
    email: email_string


---

3. Module System

Zexus organizes code into separate files using export and use.

export: Makes functions, components, etc., available to other files.

use: Imports code from another file.


# File: utils.zx
action doSomething: print "Done."
export { doSomething }

# File: main.zx
use { doSomething } from "./utils.zx"
doSomething()


---

4. Error Handling

Zexus uses a try/catch mechanism for robust error handling. Use throw to trigger custom errors.

entity MyError { message: text }

try:
  if someConditionIsBad:
    throw MyError(message: "Something went wrong!")
catch (error: MyError):
  print "Caught a specific error: {error.message}"


---

5. The Standard Library

The Zexus Standard Library includes core utilities for various tasks.

5.1 Data Structures (List & Map)

List: An ordered collection of items.

Map: A key-value collection.


["a", "b", "c"]
{"name": "Zaidu", "level": 10}

5.2 Text Manipulation (Text)

Text utilities available on text values:

text.length()
text.to_uppercase()
text.trim()
text.split(by: ",")

5.3 Math (Math)

Common math operations via the Math namespace:

Math.sqrt(16)

5.4 Date & Time (DateTime)

Handle dates and time easily:

DateTime.now()
DateTime.new("2025-07-29T12:00:00Z")

5.5 Filesystem (filesystem)

Read/write local files:

filesystem.read_text("/data/file.txt")
filesystem.write_text("/data/file.txt", "Hello Zexus")

5.6 Networking (http)

Make web requests. These are async and require await.

let result = await http.get("https://api.example.com/data")


---

6. Command-Line Tools

Interaction with the Zexus ecosystem is handled via:

zx — The Zexus runner for executing .zx files.


zx main.zx

zpm — The Zexus Package Manager for installing and managing libraries.


zpm install CoolUI


---

# 7. Appendix: Formal Grammar (EBNF)
This section provides a simplified formal grammar for Zexus v1.0. It is intended as a guide for building a parser for the language.
Notation:
 * ::= means "is defined as".
 * | means "or".
 * * means "zero or more times".
 * ? means "optional" (zero or one time).
 * Items in quotes (e.g., "let") are literal keywords.
Core Structure
program ::= statement*
statement ::= declaration | control_flow | expression | comment

Declarations
declaration ::= variable_declaration | screen_declaration | action_declaration

variable_declaration ::= "let" , identifier , "=" , expression
screen_declaration ::= "screen" , identifier , ":" , screen_body
action_declaration ::= "async"? , "action" , identifier , "(" , parameter_list? , ")" , ":" , code_block

Control Flow
control_flow ::= if_statement | for_loop

if_statement ::= "if" , expression , ":" , code_block , ("else" , ":" , code_block)?
for_loop ::= "for" , "each" , identifier , "in" , identifier , ":" , code_block

Module System
module_statement ::= use_statement | export_statement

use_statement ::= "use" , (identifier | "{" , identifier_list , "}") , "from" , string_literal
export_statement ::= "export" , ("default" , identifier | "{" , identifier_list , "}")

Error Handling
error_statement ::= try_catch_statement | throw_statement

try_catch_statement ::= "try" , ":" , code_block , "catch" , "(" , identifier , ")" , ":" , code_block
throw_statement ::= "throw" , expression

Basic Expressions & Literals
expression ::= literal | identifier | function_call | arithmetic_expression

literal ::= string_literal | number_literal | boolean_literal
identifier ::= (letter | "_") , (letter | number | "_")*