# **CSE 15L Winter 2023 Lab Report 2**
### Eric Song, Wednesday B270 1 p.m.
### <br /> Part 1: StringServer

StringServer.java Code:
```
import java.io.IOException;
import java.net.URI;


/**
 * ServerString objects implement the handleRequest method; this lets it
 * respond to changes in the URL.
 */
class ServerString implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    
    private static final int INITIAL = 0;
    private static final int DEFAULT_END = 2;
    private static final int ADDED_STRING = 1;
    String overallMessage = "";
    boolean firstMessage = true;

    /**
     * Determines the different responses based on how the URL is changed in
     * the browser.
     * 
     * @param url the URL being processed
     */
    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String query = url.getQuery();
            //check for valid query
            try {
                if (query.substring(INITIAL, DEFAULT_END).equals("s=")) {
                    //valid query, add query string to overlal string
                    String message = query.split("=")[ADDED_STRING];
                    overallMessage += message + "\n";

                    //return overall string
                    return overallMessage;
                } else {
                    //invalid query
                    return "Invalid Query";
                }
            } catch (Exception E) {
                return "Invalid Query";
            }
        } else if (firstMessage == true) {
            firstMessage = false;
            return "Use Path /add-message?s=<string>";
        } else {
            return "Invalid URL\nCurrent Strings:\n" + overallMessage;
        }

    }
}

/**
 * Runs the StringServer.
 */
class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new ServerString());
    }
}
```
**<br /> `/add-message` demonstrations:**
<br />
<br /> C:\Users\19255\Documents\GitHub\cse15l-lab-reports\lab-reports\lab-report-two>java StringServer 4000
<br /> Server Started! Visit http://localhost:4000 to visit.
<br /> 
<br /> Initial State (before any strings are added)
<br /> 

