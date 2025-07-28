# Designing the Text Type's Functions
This defines the built-in functions that would be available on any Text (or String) variable in Zexus.
This includes:
| Function | Purpose | Example |
|---|---|---|
| .length() | Returns the number of characters in the text. | let len = "Hello".length() # len is 5 |
| .to_uppercase() | Converts the entire text to uppercase. | let shouting = "hello".to_uppercase() # "HELLO" |
| .to_lowercase() | Converts the entire text to lowercase. | let quiet = "HELLO".to_lowercase() # "hello" |
| .trim() | Removes whitespace from the beginning and end of the text. | let clean = "  some text  ".trim() # "some text" |
| .contains(substring) | Returns true if the text contains the given substring. | "Zexus".contains("exus") # true |
| .replace(find, with) | Finds and replaces all occurrences of a substring. | let new = "I like cats".replace("cats", "dogs") # "I like dogs" |
| .split(by:) | Splits the text into a List of strings using a delimiter. | let words = "one,two,three".split(by: ",") # ["one", "two", "three"] |
| .is_empty() | Returns true if the text has no characters. | let empty = "".is_empty() # true |

* Example in Action
Here’s how a developer could use these functions together to clean up user input:
# Imagine this is input from a user form
let rawComment = "  WOW, zexus is AWESOME!  "

# 1. Clean up the input
let trimmedComment = rawComment.trim() # "WOW, zexus is AWESOME!"

# 2. Make it consistent
let lowercaseComment = trimmedComment.to_lowercase() # "wow, zexus is awesome!"

# 3. Check for keywords
if lowercaseComment.contains("awesome"):
  print "User thinks Zexus is awesome! 🎉"
