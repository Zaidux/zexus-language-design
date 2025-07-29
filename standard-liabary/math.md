# Math Module

The Zexus `Math` module provides a standard set of essential mathematical functions and constants. All functions are accessed through the `Math` namespace.

## Constants

| Constant  | Purpose             | Example              |
| --------- | ------------------- | -------------------- |
| `Math.PI` | The value of Pi (π). | `let circ = 2 * Math.PI * r` |

## Functions

| Function                          | Purpose                                                 | Example                                     |
| --------------------------------- | ------------------------------------------------------- | ------------------------------------------- |
| `Math.sqrt(number)`               | Calculates the square root of a number.                 | `Math.sqrt(16)` # Returns 4                 |
| `Math.pow(base, exponent)`        | Raises a base number to the power of an exponent.       | `Math.pow(2, 3)` # Returns 8                |
| `Math.random()`                   | Returns a random decimal number between 0.0 and 1.0.    | `Math.random()` # e.g., 0.734...            |
| `Math.random_int(min, max)`       | Returns a random integer within a specified range.      | `Math.random_int(1, 100)` # e.g., 42        |
| `Math.round(number)`              | Rounds a number to the nearest integer.                 | `Math.round(5.7)` # Returns 6               |
| `Math.abs(number)`                | Returns the absolute (non-negative) value of a number.  | `Math.abs(-15)` # Returns 15                |
| **`Math.sin(angle)`** | Calculates the sine of an angle (in radians).           | `Math.sin(Math.PI / 2)` # Returns 1.0       |
| **`Math.cos(angle)`** | Calculates the cosine of an angle (in radians).         | `Math.cos(Math.PI)` # Returns -1.0          |
| **`Math.tan(angle)`** | Calculates the tangent of an angle (in radians).        | `Math.tan(0)` # Returns 0.0                 |
