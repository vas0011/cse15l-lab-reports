#Code
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String messages  =  "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("&"); 
            String[] getMessage = parameters[0].split("=");
            String[] getUser = parameters[1].split("=");            
            String message = null;

            if (getMessage[0].equals("s")) {
                message = getMessage[1];
            }
            if(getUser[0].equals("user")){
                message = getUser[1] + ": " + message + "\n";
            }
            
            messages += message;
            return messages;
        } else {
            return "404 Not Found!";
        }
    }
}

class ChatServer{
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

![Image](addmessage1.png)
1. Which methods in your code are called?
   
2.  What are the relevant arguments to those methods, and the values of any relevant fields of the class?
  
3.  How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

![Image](addmessage2.png)
1. Which methods in your code are called?

2. What are the relevant arguments to those methods, and the values of any relevant fields of the class?

3. How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
