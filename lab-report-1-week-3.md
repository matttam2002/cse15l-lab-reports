# Week 3 Lab Report

# Part 1
- Simple Search Engine
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList; 
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> list = new ArrayList <String> () ;

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                list.add(parameters[1]);
            }
            return parameters[1]+ " added"; 
        }
        else if (url.getPath().contains("/search")){
            String[] parameters = url.getQuery().split("=");
            String result = ""; 
            if (parameters[0].equals("s")){
                for(int i=0; i<list.size(); i++){                   
                    if (list.get(i).contains(parameters[1])){
                        result = result +" " +list.get(i);
                    }
                }
            }
            return result;
        }
        else if ( url.getPath().equals("/")) {
            return ("Please add elements !"); 
        }
        else {
            return  "404 Not Found!"; 
        }
    }
}

class SearchEngine {
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
- Using add
