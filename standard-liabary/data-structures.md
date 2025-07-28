# Core Data Structures

This document defines the core data structures available in the Zexus Standard Library.

## List
A **`List`** is an ordered collection of items. It is the most common way to store a sequence of values.

### Creation
```zexus

A list of strings
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
| .find(where: ...) | Finds the first item that matches a condition. | let gemini = names.find(where: it == "Gemini") |
| .sort() | Sorts the list. | scores.sort() |
| .is_empty() | Returns true if the list has no items. | if users.is_empty(): print "No users yet." |
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
