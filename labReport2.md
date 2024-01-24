Today's post will be covering servers and ssh keys. Lets start by looking at an interesting Server I coded.
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    ArrayList<String> database = new ArrayList<>();
    
    public String handleRequest(URI url){
        if (url.getPath().equals("/")){
            return "Please Alter the Path to Start a Conversation";
        }
        else if (url.getPath().equals("/add-message")){
            String[] params = url.getQuery().split("&");
            String message = (params[0].split("="))[1];
            String name = (params[1].split("="))[1];
            database.add(name + ": " + message);
        }
        String result = "";
        for (int i = 0; i<database.size();i++){
            result+=database.get(i) + "\n";
        }
        return result;
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if (args.length==0){
            System.out.println("Please Enter a Port Number");
            return;
        }
        
        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}
```
Now Heres the output:
![String Server Screenshot 1](StringServerScreenshot1.png)
Which methods in your code are called?
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

---
![String Server Screenshot 2](StringServerScreenshot2.png)
Which methods in your code are called?
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
