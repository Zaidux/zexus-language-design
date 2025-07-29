# Text Manipulation Module

This document defines the built-in functions available on any `Text` (or `String`) variable in Zexus.

## Functions

| Function | Purpose | Example |
|---|---|---|
| `.length()` | Returns the number of characters. | `let len = "Hello".length()` |
| `.to_uppercase()` | Converts the text to uppercase. | `let shouting = "hello".to_uppercase()`|
| `.to_lowercase()` | Converts the text to lowercase. | `let quiet = "HELLO".to_lowercase()` |
| `.trim()` | Removes whitespace from the start and end. | `let clean = "  text  ".trim()` |
| `.contains(substring)` | Returns `true` if the text contains the substring. | `"Zexus".contains("exus")` |
| `.replace(find, with)` | Replaces all occurrences of a substring. | `"I like cats".replace("cats", "dogs")` |
| `.split(by:)` | Splits the text into a `List` of strings. | `"a,b,c".split(by: ",")` |
| **`.match(regex)`** | Returns `true` if the text matches a regex pattern. | `"user@a.com".match(email_regex)` |

## Example Usage
```zexus
let rawComment = "  Contact me at zaidu@example.com for more info. "

# 1. Clean up the input
let cleanComment = rawComment.trim()

# 2. Use a regex to find an email address
let emailRegex = "/\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b/"
if cleanComment.match(emailRegex):
  print "Email address found in comment."
