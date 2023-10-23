# Lab Report 2: Servers and SSH Keys

### StringServer Code:
This program consists of two primary classes: `StringHandler` and `StringServer`.

## StringHandler

- `StringHandler` is an implementation of the `URLHandler` interface
- Its primary function is to handle URI requests with the path "/add-message"
- Then build a message string using the query parameter

```java
class StringHandler implements URLHandler {
    // StringBuilder builds and stores messages
    private StringBuilder messageBuilder = new StringBuilder();
    
    // counter to keep track of the number of messages added
    private int messageCounter = 0;

    public String handleRequest(URI url) {
        // Check if the path is "/add-message"
        if (url.getPath().equals("/add-message")) {
            // Extract the query from the URI
            String query = url.getQuery();
            
            // Check if the query starts with "s="
            if (query != null && query.startsWith("s=")) {
                // Extract the message after "s=" from the query
                String message = query.substring(2);
                
                messageCounter++;
                
                // Append the message to the builder with its order number
                messageBuilder.append(messageCounter).append(". ").append(message).append("\n");
                
                return messageBuilder.toString();
            }
        }
        // Return a 404 error message if the path doesn't match or the query is invalid
        return "404 Not Found!";
    }
}
```

## StringServer
- StringServer is the main entry point of the application. It takes a port number as an argument and then starts the server on the provided port using the StringHandler to process requests. 


  ```java
  class StringServer {
    public static void main(String[] args) throws IOException {
        // Check if a port number is provided
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        // Parse the port number from the arguments
        int port = Integer.parseInt(args[0]);

        // Start the server on the specified port with a `StringHandler` instance
        Server.start(port, new StringHandler());
    }

``` 
