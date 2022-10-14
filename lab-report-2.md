# The Second Lab Report

## Part 1: Simple Search Engine
    import java.io.IOException;
    import java.net.URI;
    import java.util.ArrayList;

    class Handler implements URLHandler {
        // The one bit of state on the server: a number that will be manipulated by
        // various requests.
        ArrayList<String> storage = new ArrayList<String>();
        int counter=0;
        public String handleRequest(URI url) {
            if (url.getPath().equals("/")) {
                return String.format("Invisible List");
            } else if (url.getPath().equals("/add")) {
                String[] parts = url.getQuery().split("=");
                storage.add(parts[1]);
                counter++;
                return String.format("String added!"+" Counter: "+Integer.toString(counter));
            } else {
                System.out.println("Path: " + url.getPath());
                if (url.getPath().contains("/search")) {
                    String[] parameters = url.getQuery().split("=");
                    String willReturn ="";
                    for(int i=0;i<storage.size();i++){ 
                        if (storage.get(i).contains(parameters[1])){ 
                            willReturn += storage.get(i)+" ";
                        }
                    }
                    return willReturn;
                }
                return "404 Not Found!";
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

Which methods in your code are called
What the values of the relevant arguments to those methods are, and the values of any relevant fields of the class
If those values change, how they change by the time the request is done processing

![First Added Word](PhotosLab2/markDownPhoto1.png)

This first photo 

