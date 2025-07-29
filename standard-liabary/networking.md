# Networking (http) Module

The Zexus `http` module provides tools to make web requests. Network requests are asynchronous and should be used with `await`.

## Functions

| Function | Purpose |
|---|---|
| `http.get(url, options?)` | Fetches data from a URL. Options can include `headers` and `timeout`. |
| `http.post(url, body, options?)`| Sends data to a URL. Options can include `headers` and `timeout`. |

## The `Response` Object
Both functions return a `Response` object with the following properties:

| Property | Type | Description |
|---|---|---|
| `.status_code` | `Integer` | The HTTP status code (e.g., 200 for OK). |
| `.body` | `Text` | The raw text content of the response. |
| `.json()` | `Map` | A helper function to parse the body as JSON. |
| **`.error`** | `Text?` | Contains an error message if the request failed (e.g., "Timeout"). |

## Example Usage
```zexus
action fetchUserData:
  let url = "[https://api.example.com/user/123](https://api.example.com/user/123)"
  
  let options = {
    "timeout": 5000, # Timeout in milliseconds
    "headers": {
      "Authorization": "Bearer YOUR_API_KEY"
    }
  }

  try:
    let response = await http.get(url, options: options)
    
    if response.status_code == 200:
      let userData = response.json()
      print "User name: {userData.get("name")}"
    else:
      print "API Error: {response.status_code}"
  catch (error):
    print "Network Error: {error.message}"

fetchUserData()
