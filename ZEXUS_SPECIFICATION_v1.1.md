 # Zexus Language Specification v1.1
This document provides the official language specification for Zexus Version 1.1. It serves as the definitive guide for developers, contributors, and implementers of the Zexus language.
1. Introduction
Zexus is a high-level, declarative programming language designed to unify modern application development. Its core philosophy is to make coding intuitive, readable, and powerful by allowing developers to state what they want to achieve, while the language handles the complex implementation details.
1.1. Core Principles
The design of Zexus is guided by four main principles:
 * Natural Language First: Syntax consists of readable words, not cryptic symbols, making code easy to write and understand.
 * Declarative & Intent-Based: Focus on the what, not the how. [cite_start]Describe your desired end state, and let the language handle the implementation.
 * Context is King: The compiler is smart. [cite_start]It understands whether you're defining UI, backend logic, security rules, or data, and adapts accordingly.
 * Everything is a Module: Every file, library, and component is a self-contained, pluggable module, promoting clean and organized code.
2. Language Syntax & Semantics
2.1. Comments
Single-line comments start with #. Multi-line docstrings are enclosed in """ ... """.
# This is a single-line comment.

"""
This is a multi-line docstring for documentation.
"""

2.2. Variables
Variables are declared using the let keyword.
let message = "Hello, Zexus!"
let userCount = 50

2.3. Control Flow
Zexus uses standard if/else blocks and a readable for each syntax for loops.
if user.isLoggedIn:
  print "Welcome back!"
else:
  print "Please log in."

for each user in allUsers:
  print user.name

2.4. UI and Components
The UI is defined using screen blocks, which can contain different states. A component is a reusable piece of UI.
screen Login:
  initial_state: :form
  state :form { # ... screen content ... }

2.5. Actions
Backend logic is defined in action blocks. Actions can be async and use await.
action fetchUserData(userId):
  let response = await http.get("/api/users/{userId}")
  return response.json()

2.6. Data and Databases
Data structures are defined using entity. Database schemas are defined in a database block.
database UserDB:
  entity User:
    username: text
    email: email_string

3. Module System
Zexus organizes code using export and use.
 * export: Makes items available to other files.
 * use: Imports items from another file.
<!-- end list -->
# File: utils.zx
action doSomething: print "Done."
export { doSomething }

# File: main.zx
use { doSomething } from "./utils.zx"
doSomething()

4. Error Handling
Zexus uses a try/catch mechanism. Use throw to trigger custom errors.
entity MyError { message: text }

try:
  if someConditionIsBad:
    throw MyError(message: "Something went wrong!")
catch (error: MyError):
  print "Caught a specific error: {error.message}"

5. The Standard Library
5.1. Data Structures
List
An ordered collection of items.
| Function | Purpose | Example |
|---|---|---|
| .add(item) | Adds an item to the end of the list. | names.add("Chris") |
| .remove(item) | Removes the first matching item. | scores.remove(88) |
| .count() | Returns the number of items. | let num = names.count() |
| .is_empty() | Returns true if the list has no items. | if users.is_empty(): ... |
| .find(where: ...) | Finds the first item that matches a condition. | names.find(where: it == "Gemini") |
| .map(transform: ...) | Creates a new list by applying a function to each item. | names.map(transform: it.to_uppercase()) |
| .filter(condition: ...) | [cite_start]Creates a new list with items that pass a condition. | scores.filter(condition: it > 90) |
| .reduce(initial, logic: ...) | [cite_start]Reduces the list to a single value. | scores.reduce(0, logic: acc + item)|
Map
A collection of key-value pairs.
| Function | Purpose | Example |
|---|---|---|
| .set(key, value) | Adds or updates a key-value pair. | userProfile.set("level", 11) |
| .get(key) | Retrieves the value for a given key. | userProfile.get("level") |
| .has(key) | Returns true if the map contains the key. | if userProfile.has("is_active"): ... |
| .remove(key) | Removes a key-value pair. | userProfile.remove("is_active") |
5.2. Text Manipulation
| Function | Purpose | Example |
|---|---|---|
| .length() | Returns the number of characters. | let len = "Hello".length() |
| .to_uppercase() | Converts the text to uppercase. | "hello".to_uppercase() |
| .to_lowercase() | Converts the text to lowercase. | "HELLO".to_lowercase() |
| .trim() | Removes whitespace from the start and end. | "  text  ".trim() |
| .contains(substring) | Returns true if the text contains the substring. | "Zexus".contains("exus") |
| .replace(find, with) | Replaces all occurrences of a substring. | "I like cats".replace("cats", "dogs") |
| .split(by:) | Splits the text into a List of strings. | "a,b,c".split(by: ",") |
| .match(regex) | [cite_start]Returns true if the text matches a regex pattern. | "a@b.com".match(email_regex) |
5.3. Math
Constants
| Constant | Purpose | Example |
|---|---|---|
| Math.PI | [cite_start]The value of Pi (π). | let circ = 2 * Math.PI * r |
Functions
| Function | Purpose | Example |
|---|---|---|
| Math.sqrt(number) | Calculates the square root. | Math.sqrt(16) |
| Math.pow(base, exp) | Raises a base to an exponent. | Math.pow(2, 3) |
| Math.random_int(min, max) | [cite_start]Returns a random integer in a range. | Math.random_int(1, 100) |
| Math.sin(angle) | [cite_start]Calculates the sine of an angle (in radians). | Math.sin(Math.PI / 2) |
| Math.cos(angle) | [cite_start]Calculates the cosine of an angle (in radians). | Math.cos(Math.PI) |
5.4. Date & Time
| Function | Purpose | Example |
|---|---|---|
| DateTime.now() | Gets the current date and time. | let now = DateTime.now() |
| DateTime.new(...) | Creates a specific date. | DateTime.new(year: 2025) |
| .format(as: ...) | [cite_start]Formats the date into a text string. | now.format(as: "YYYY-MM-DD") |
| .to_timezone(tz) | [cite_start]Converts to a different timezone. | tokyoTime.to_timezone("local") |
| (date1 - date2) | [cite_start]Creates a Duration object. | DateTime.now() - startDate |
5.5. Filesystem
[cite_start]These functions can throw errors and should be used in a try/catch block.
| Function | Purpose |
|---|---|
| filesystem.read_text(path) | Reads a text file. |
| filesystem.write_text(path, content) | Writes to a text file. |
| filesystem.exists(path) | Checks if a file or directory exists. |
5.6. Networking (http)
| Function | Purpose |
|---|---|
| http.get(url, options?) | Fetches data from a URL. |
| http.post(url, body, options?) | Sends data to a URL. |
| The options map can include headers and a timeout. The returned Response object includes .status_code, .body, .json(), and an .error property. |  |
6. Command-Line Tools
 * zx: The Zexus runner for executing .zx files.
 * zpm: The Zexus Package Manager for installing libraries.
 * 
7. Appendix: Formal Grammar (EBNF)
This section provides a simplified formal grammar for Zexus v1.0. It is a guide for building a parser for the language.
variable_declaration ::= "let" , identifier , "=" , expression ;
if_statement ::= "if" , expression , ":" , code_block , ("else" , ":" , code_block)? ;
