
# Lab Report 3

## Part 1
### Code Explanation

The `ChatServer` includes a main server loop that listens for incoming connections and processes each connection individually. The main method of interest in our code is `handleRequest`, which handles the parsing of the URL and the addition of new chat messages to the chat history.

Here's the critical part of the implementation:

```java
public String handleRequest(URI url) {
    if (url.getPath().equals("/")) {
        return chatHistory.toString().isEmpty() ? "No messages yet." : chatHistory.toString();
    } else if (url.getPath().equals("/add-message")) {
        String message = "", user = "";
        String query = url.getQuery();
        String[] parameters = query.split("&");
        for (String param : parameters) {
            String[] pair = param.split("=");
            if (pair.length > 1) {
                String key = pair[0];
                String value = URLDecoder.decode(pair[1], StandardCharsets.UTF_8);
                if ("s".equals(key)) {
                    message = value;
                } else if ("user".equals(key)) {
                    user = value;
                }
            }
        }

        if (!message.isEmpty() && !user.isEmpty()) {
            chatHistory.append(user).append(": ").append(message).append("\n");
            return chatHistory.toString();
        } else {
            return "Invalid request: Missing 's' or 'user' parameters!";
        }
    } else {
        return "404 Not Found!";
    }
}
```

### Screenshots Analysis

#### First Screenshot Analysis 
![First Request Screenshot](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/222f36b8-cc5e-45c1-925b-5f5946c8a68d)

- **Methods Called**: `handleRequest`
- **Arguments and Values**:
  - `URI url`: A `URI` object representing the URL accessed by the user. For the first request (`/add-message?s=Hello&user=jpolitz`), the path is `/add-message` and the query is `s=Hello&user=jpolitz`.
  - `chatHistory`: Initially empty, this `StringBuilder` accumulates the chat messages.
- **Field Changes**:
  - `chatHistory` changes from an empty string to "jpolitz: Hello\n".

#### Second Screenshot Analysis
![Second Request Screenshot](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/2f451fa9-2d29-4708-9543-18cd562ebaf6)
- **Methods Called**: `handleRequest`
- **Arguments and Values**:
  - `URI url`: For the second request (`/add-message?s=How%20are%20you&user=yash`), the path and query reflect the new message addition.
- **Field Changes**:
  - `chatHistory` updates from "jpolitz: Hello\n" to "jpolitz: Hello\nyash: How are you\n".

### Conclusion

Each HTTP request to add a message triggers the `handleRequest` method, which updates the `chatHistory` field of the class based on the parsed URL query parameters. The server dynamically builds and displays a chat history based on user interactions.

## Part 2

1. ![Private Key Listing](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/2d7a73c1-f698-41d6-b82c-7dc9b786d42f)
2. ![Public Key Listing](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/14b4dca9-8e9b-4a2c-998e-7591915c0c5f)
3. ![SSH Login Without Password](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/28452b36-2d9d-4a3e-81b7-9ebfae2ba65a)

## Part 3

In the labs from weeks 2 and 3, I gained practical skills in managing remote server connections using SSH keys, which eliminated the need for password entry, enhancing both convenience and security. Additionally, I learned how to customize a web server's HTTP responses by implementing a chat server that dynamically modifies its response payload with query parameters
