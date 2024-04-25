# Lab Report 1

## `cd` Command Usage

### Command with No Arguments
![cd with no arguments](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/20fb4c5e-226b-4af6-a899-dd1954ea196a)
- **Command:** `cd`
- **Working Directory Before Command:** `/home`
- **Explanation:** Running `cd` with no arguments defaults to changing the current working directory to the user's home directory. In this case, since the user was already in `/home`, there is no visible change.
- **Error:** No error.

### Command with a Path to a Directory as an Argument
![cd to a directory](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/86f5510f-ab3f-426f-966d-b125bceb99b2)
- **Command:** `cd lecture1`
- **Working Directory Before Command:** `/home`
- **Explanation:** This command changes the current working directory to the directory `lecture1` within `/home`.
- **Error:** No error.

### Command with a Path to a File as an Argument
![cd to a file error](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/b801b828-b1a6-4c29-877c-a019c372178b)
- **Command:** `cd lecture1/messages/en-us.txt`
- **Working Directory Before Command:** `/home/lecture1`
- **Explanation:** This command attempts to change the directory to a file, which is not possible. The `cd` command is intended only for changing directories.
- **Error:** Yes, an error because `cd` cannot navigate to a file.

## `ls` Command Usage

### Command with No Arguments
![ls with no arguments](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/cd70f0f5-ca27-471b-b338-cdf5659d6b92)
- **Command:** `ls`
- **Working Directory Before Command:** `/home`
- **Explanation:** Lists all contents of the current working directory, which is `/home`.
- **Error:** No error.

### Command with a Path to a Directory as an Argument
![ls a directory](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/764ac6c6-4c3b-4a25-8340-6a412d15b86f)
- **Command:** `ls lecture1`
- **Working Directory Before Command:** `/home`
- **Explanation:** Lists all contents within the specified directory `lecture1`.
- **Error:** No error.

### Command with a Path to a File as an Argument
![ls a file](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/e98bfba1-0902-4a2e-ae0b-4b52d683336c)
- **Command:** `ls messages/en-us.txt`
- **Working Directory Before Command:** `/home/lecture1/messages`
- **Explanation:** Lists the specified file `en-us.txt` showing its details within its directory.
- **Error:** No error.

## `cat` Command Usage

### Command with No Arguments
![cat with no arguments](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/f0f573fb-84e5-44b2-9710-d462f62ab3fc)
- **Command:** `cat`
- **Working Directory Before Command:** `/home`
- **Explanation:** The `cat` command without arguments waits for input from the terminal, expecting to concatenate from stdin.
- **Error:** No error, but requires user input to proceed.

### Command with a Path to a Directory as an Argument
![cat a directory error](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/392831b8-6ee6-4057-a973-3301a9a4cacd)
- **Command:** `cat Lecture1`
- **Working Directory Before Command:** `/home`
- **Explanation:** Attempting to use `cat` on a directory results in an error because `cat` is designed to read files, not directories.
- **Error:** Yes, an error because directories cannot be displayed using `cat`.

### Command with a Path to a File as an Argument
![cat a file](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/b35c5abc-e2d8-49ec-85ec-90f7521a629d)
- **Command:** `cat messages/en-us.txt`
- **Working Directory Before Command:** `/home`
- **Explanation:** This command displays the contents of the file `en-us.txt`. "Hello World!" is displayed, verifying that the file contains readable text.
- **Error:** No error.

h
h
h
h
h
h
h
h
hh
hh
h
h
h
h
h
h



# Lab Report 2

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
