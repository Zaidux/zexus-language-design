# Core Data Structures

This document defines the core data structures available in the Zexus Standard Library.

## List
A **`List`** is an ordered collection of items. It is the most common way to store a sequence of values.

### Creation
```zexus
# A list of strings
let names = ["Zaidu", "Gemini", "Alex"]

# A list of numbers
let scores = [95, 88, 100]

# An empty list that will hold User entities
let users: List<User> = []

Functions
| Function | Purpose | Example |
|---|---|---|
| .add(item) | Adds an item to the end of the list. | names.add("Chris") |
| .remove(item) | Removes the first matching item from the list. | scores.remove(88) |
| .count() | Returns the number of items in the list. | let numUsers = names.count() |
| .is_empty() | Returns true if the list has no items. | if users.is_empty(): print "No users yet." |
| .find(where: ...) | Finds the first item that matches a condition. | let gemini = names.find(where: it == "Gemini") |
| .sort() | Sorts the list. | scores.sort() |
| .map(transform: ...) | [cite_start]Creates a new list by applying a function to each item. [cite: 33] | let upper = names.map(transform: it.to_uppercase()) |
| .filter(condition: ...) | [cite_start]Creates a new list with only the items that pass a condition. [cite: 33] | let highScores = scores.filter(condition: it > 90) |
| .reduce(initial, logic: ...) | [cite_start]Reduces the list to a single value by combining items. [cite: 33] | let total = scores.reduce(0, logic: accumulator + item) |
Map
A Map is a collection of key-value pairs. It is used to store associated data, where each value is linked to a unique key.
Creation
# A map representing a user's profile
let userProfile = {
  "name": "Zaidu",
  "level": 10,
  "is_active": true
}

# An empty map that will hold scores
let playerScores: Map<String, Integer> = {}

Functions
| Function | Purpose | Example |
|---|---|---|
| .set(key, value) | Adds or updates a key-value pair. | userProfile.set("level", 11) |
| .get(key) | Retrieves the value for a given key. | let currentLevel = userProfile.get("level") |
| .has(key) | Returns true if the map contains the key. | if userProfile.has("is_active"): ... |
| .remove(key) | Removes a key-value pair from the map. | userProfile.remove("is_active") |
| .keys() | Returns a List of all the keys in the map. | let profileKeys = userProfile.keys() |
| .values() | Returns a List of all the values in the map. | let profileValues = userProfile.values() |