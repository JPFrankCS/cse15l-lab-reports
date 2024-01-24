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
            if (params[0].split("=")[0] != "s"){
                return "ERROR - INCORRECT URL FORMAT";
            }
            String message = (params[0].split("="))[1];
            if (params[1].split("=")[0] != "user"){
                return "ERROR - INCORRECT URL FORMAT";
            }
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
