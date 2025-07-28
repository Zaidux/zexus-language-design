# Networking (http) Module

The Zexus `http` module provides tools to make web requests, allowing applications to communicate with APIs and websites over the internet. Network requests are asynchronous, meaning they don't block the rest of your program while waiting for a response.

## Functions

| Function                          | Purpose                                                                 |
| --------------------------------- | ----------------------------------------------------------------------- |
| `http.get(url)`                   | Fetches data from a URL using an HTTP GET request.                      |
| `http.post(url, body)`            | Sends data to a URL using an HTTP POST request. The body can be a `Map`. |

## The `Response` Object
Both functions return a `Response` object, which has the following properties:

| Property             | Type      | Description                                     |
| -------------------- | --------- | ----------------------------------------------- |
| `.status_code`       | `Integer` | The HTTP status code (e.g., 200 for OK).        |
| `.body`              | `Text`    | The raw text content of the response.           |
| `.json()`            | `Map`     | A helper function to parse the body as JSON.    |

## Example Usage

```zexus
# An asynchronous action to fetch a random joke from a public API
action fetchRandomJoke:
  let url = "[https://official-joke-api.appspot.com/random_joke](https://official-joke-api.appspot.com/random_joke)"
  
  # 'await' pauses the action until the network request is complete
  let response = await http.get(url)
  
  # Check if the request was successful
  if response.status_code == 200:
    # Parse the JSON response into a Map
    let jokeData = response.json()
    
    print "Setup: {jokeData.get("setup")}"
    print "Punchline: {jokeData.get("punchline")}"
  else:
    print "Failed to fetch joke. Status: {response.status_code}"

# Run the action
fetchRandomJoke()
