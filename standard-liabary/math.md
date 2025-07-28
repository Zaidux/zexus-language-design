# Math Module

The Zexus `Math` module provides a standard set of essential mathematical functions. All functions are accessed through the `Math` namespace.

## Functions

| Function                          | Purpose                                                 | Example                                     |
| --------------------------------- | ------------------------------------------------------- | ------------------------------------------- |
| `Math.sqrt(number)`               | Calculates the square root of a number.                 | `Math.sqrt(16)` # Returns 4                 |
| `Math.pow(base, exponent)`        | Raises a base number to the power of an exponent.       | `Math.pow(2, 3)` # Returns 8                |
| `Math.random()`                   | Returns a random decimal number between 0.0 and 1.0.    | `Math.random()` # e.g., 0.734...            |
| `Math.random_int(min, max)`       | Returns a random integer within a specified range.      | `Math.random_int(1, 100)` # e.g., 42        |
| `Math.round(number)`              | Rounds a number to the nearest integer.                 | `Math.round(5.7)` # Returns 6               |
| `Math.floor(number)`              | Rounds a number down to the nearest integer.            | `Math.floor(5.7)` # Returns 5               |
| `Math.ceil(number)`               | Rounds a number up to the nearest integer.              | `Math.ceil(5.2)` # Returns 6                |
| `Math.abs(number)`                | Returns the absolute (non-negative) value of a number.  | `Math.abs(-15)` # Returns 15                |

## Example Usage

```zexus
# Simulate a dice roll for a game
let diceRoll = Math.random_int(1, 6)
print "You rolled a {diceRoll}!"

# Calculate damage with a random critical hit chance
let baseDamage = 50
let criticalHit = Math.random() > 0.8 # 20% chance for a critical hit

if criticalHit:
  let totalDamage = Math.round(baseDamage * 1.5)
  print "Critical Hit! Damage: {totalDamage}"
else:
  print "Normal Hit. Damage: {baseDamage}"
