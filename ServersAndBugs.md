# Servers and Bugs Lab Report (2)

---

## Part 1

The code for my StringServer:

    import java.io.IOException;
    import java.net.URI;
    import java.util.*;
    
    class Handler implements URLHandler {
        StringBuilder result = new StringBuilder(); 
        ArrayList<String> str = new ArrayList<String>();

        public String handleRequest(URI url) {
            if (url.getPath().equals("/")) {
                return result.toString();
            }
            else if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    result.delete(0, result.length());
                    for (int i = 1; i < parameters.length; i++) {
                        str.add(parameters[i]);
                    }
                    for (int i = 0; i < str.size(); i++) {
                        result.append(str.get(i));
                        result.append("\n");
                    }
                    return result.toString();
                }
                else {
                    return "404 Not Found!";
                }
            }
            else {
                return "404 Not Found!";
            }
        }
    }

    public class StringServer {
        public static void main (String[] args) throws IOException{
            if(args.length == 0){
                System.out.println("Missing port number! Try any number between 1024 to 49151");
                return;
            }

            int port = Integer.parseInt(args[0]);

            Server.start(port, new Handler());
        }
    }

2 screenshots of using ```/add-message```:

<img width="565" alt="Screenshot 2023-01-28 at 8 38 40 AM" src="https://user-images.githubusercontent.com/122576781/215278682-b3b1d6ee-4ebc-4658-bc7e-77d2ade1bdba.png">

The method in my code that is called is handleRequest, after the main method in StringServer starts the server. The relevant argument to this method is the URI used. There are two other relevant fields of the class, an ArrayList of Strings and a StringBuilder, both of which are initialized with default values. These values are later changed with the call to handleRequest and, upon finding a path including ```/add-message``` in the given URI, alters the values of the ArrayList and the StringBuilder. In this case, the ArrayList temporarily holds the input (the String after the ```/add-message?s=```) (specifically, "15L Lab Report 2") from the URI before it then gets added to the end of the StringBuilder (with formatting included). The StringBuilder result that is returned as a String then had the value "15L Lab Report 2". The URI remains unchanged throughout this process.

<img width="608" alt="Screenshot 2023-01-28 at 8 39 14 AM" src="https://user-images.githubusercontent.com/122576781/215278701-4952ae90-2516-4e8b-9e83-49e0cfb9fe26.png">

The method in my code that is called is handleRequest, after the main method in StringServer starts the server. The relevant argument to this method is the URI used. There are two other relevant fields of the class, an ArrayList of Strings and a StringBuilder, both of which are initialized with default values. These values are later changed with the call to handleRequest and, upon finding a path including ```/add-message``` in the given URI, alters the values of the ArrayList and the StringBuilder. In this case, the ArrayList temporarily holds the input (the String after the ```/add-message?s=```) (specifically, "15L Lab Report 2") from the URI before it then gets added to the end of the StringBuilder (with formatting included). The StringBuilder result that is returned as a String then had the value "15L Lab Report 2". The URI remains unchanged throughout this process.






## Part 2


## Part 3
