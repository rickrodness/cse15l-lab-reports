# Lab Report 2: Servers and SSH Keys
### StringServer Code

```java
import java.io.IOException;
import java.net.URI;

class StringHandler implements URLHandler {
    private StringBuilder messageBuilder = new StringBuilder();
    private int messageCounter = 0;

    public synchronized String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String query = url.getQuery();
            if (query != null && query.startsWith("s=")) {
                String message = query.substring(2); // Extract the message after "s="
                messageCounter++;
                messageBuilder.append(messageCounter).append(". ").append(message).append("\n");
                return messageBuilder.toString();
            }
        }
        return "404 Not Found!";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new StringHandler());
    }
}


```


