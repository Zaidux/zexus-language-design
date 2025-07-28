# Error Handling in Zexus

Zexus provides a robust error handling mechanism using `try/catch` blocks and custom, definable error types. This allows developers to build resilient applications that can gracefully handle unexpected situations without crashing.

## The `try/catch` Block

The primary way to handle potential errors is to wrap fallible code in a `try` block. If an error occurs within that block, the program immediately jumps to the corresponding `catch` block.

```zexus
try:
  # Attempt an operation that might fail
  let data = filesystem.read_text("./non_existent_file.txt")
catch (error):
  # Handle the failure
  print "Failed to read file: {error.message}"

Custom Errors and throw
To cover all possible error cases in detail, Zexus allows you to define and throw your own custom errors. This is useful for enforcing business logic and creating specific failure conditions.
You can define a custom error using an entity and use the throw keyword to trigger it.
# Define a custom error type
entity InvalidAgeError {
  message: text
}

# An action that can throw our custom error
action registerUser(age: integer):
  if age < 18:
    # Throw a new instance of our custom error
    throw InvalidAgeError(message: "User must be 18 or older to register.")
  
  # ... continue with registration
  print "User registration successful!"


# Now, handle that specific error
try:
  registerUser(age: 16)
catch (error: InvalidAgeError):
  # This block specifically catches our custom error
  print "Registration Failed! {error.message}"
catch (error):
  # A general catch-all for any other unexpected errors
  print "An unknown error occurred."