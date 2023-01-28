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

The method in my code that is called is handleRequest, after the main method in StringServer starts the server. The relevant argument to this method is the URI used. There are two other relevant fields of the class, an ArrayList of Strings and a StringBuilder, both of which are initialized with default values. These values are later changed with the call to handleRequest and, upon finding a path including ```/add-message``` in the given URI, alters the values of the ArrayList and the StringBuilder. In this case, the ArrayList temporarily holds the input (the String after the ```/add-message?s=```) (specifically, "StringServer.java is running") from the URI before it then gets added to the end of the StringBuilder (with formatting included). The StringBuilder result that is returned as a String then had the value "15L Lab Report 2\nStringServer.java is running". The URI remains unchanged throughout this process.

## Part 2

I chose the bug from the averageWithoutLowest method in ArrayExamples.java. 

A failure-inducing input for the buggy program:

    @Test
    public void testAverageWithoutLowest1() {
        double[] input1 = {2.0, 2.0, 6.0, 2.0, 6.0, 2.0};
        assertEquals(6.0, ArrayExamples.averageWithoutLowest(input1), 0.0);
    }


An input that doesn't induce a failure:

    @Test 
    public void testAverageWithoutLowest2() {
        double[] input1 = {1.0, 4.0, 8.0, 6.0};
        assertEquals(6.0, ArrayExamples.averageWithoutLowest(input1), 0.0);
    }

The symptom, as the output of running the above tests:

<img width="783" alt="Screenshot 2023-01-28 at 9 35 05 AM" src="https://user-images.githubusercontent.com/122576781/215282136-c44880f7-8ab9-4174-9684-14fa774e8f7e.png">

The bug:

Before fixing (what caused the symptoms seen):

    static double averageWithoutLowest(double[] arr) {
        if(arr.length < 2) { return 0.0; }
        double lowest = arr[0];
        for(double num: arr) {
          if(num < lowest) { lowest = num; }
        }
        double sum = 0;
        for(double num: arr) {
          if(num != lowest) { sum += num; }
        }
        return sum / (arr.length - 1);
      }

After fixing:

    static double averageWithoutLowest(double[] arr) {
        if(arr.length < 2) { return 0.0; }
        double lowest = arr[0];
        for(double num: arr) {
          if(num < lowest) { lowest = num; }
        }
        double sum = 0;
        int checker = 0;
        for(double num: arr) {
          if(num != lowest) { sum += num; }
          else { checker++; }
        }
        return sum / (arr.length - checker);
      }
    }

The bug was that the code assumed only one of the lowest number in the double array input would be taken out of account when calculating the average. However, it can be seen that all instances of the lowest number were removed from adding together the values of the double array, so dividing by the length of the array minus one wouldn't divide by the number of elements added together (which needs to be done to find the average). To compensate for this, I included a variable to keep track of how many elements were not counted (and are thus the lowest), and instead of subtracting 1 from the length of the array, I subtracted the counter from the length of the array. This works as intended because now the result of the addition of the elements of the double array while not including all occurrences of the lowest number is divided by the number of elements that were summed, thus giving the average of those elements. 

## Part 3

I didn't know how to use GitHub desktop to record changes to a project/code, what with committing changes and pushing to GitHub. I also learned how to set up a locally hosted server (I previously didn't know this was possible) and how to better understand the processes of urls. 
