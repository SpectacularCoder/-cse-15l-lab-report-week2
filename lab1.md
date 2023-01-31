# -cse-15l-lab-report-week2
## Lab Report 2
### Part 1
Code for StringServer;
```
# code block
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
ArrayList<String> strings = new ArrayList<String>();


public String handleRequest(URI url) {
    String string = "";
    if (url.getPath().equals("/add-message"))
    {
        String[] parameters = url.getQuery().split("=");
        strings.add(parameters[1]);
        
        for (int i = 0; i < strings.size(); i++)
        {
    
           string += strings.get(i) + "\n";
        }
        return string;
    }
    return "Error";
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
}
```
**Image 1:**
![Image](firstMessage.jpg)
**1.** The server must be started first by the class StringServer, this is necessary for starting the server with a proper port. The next class is public StringHandleRequest, within this class several methods are used to find the desired string value to display on the server. We first use .getpath() to check if within the path there exist a "add-message" through the equals method. If this is true, we would then call the split method to split the query by the regex, in this case it 
is the "=". The add method is used to add the strings after the regex into the arrayList. A for loop runs thru this arrayList and we use .get to pull the
string values from the arrayList to display on the server.

**2.** The relevant field to the class is the url, we must first take a url to break down. For the path, we needed to have a path to first extract from and for this if condition to fall thru this path must have the string "add-message". For the next method, we need to make sure that there exist a regex of "=", this is the delimeter for isolating the string value we need. In the strings add method, we must have a argument of a string to add to the arrayList. This is done by adding the 1st value of the string parameter. After all values are added within our arrayList, we simply use the forloop and .get method to iterate through our arrayList and return each element within it.

**3.**

**Image 2:**
![Image](secondImage.jpg)
**1.**

**2.**

**3.**

### Part 2
### Part 3
Something I learned in Week 3 was how to essentially check the entirety of the actual output. 

The default code that was given was;
```
# code block
assertArrayEquals(new int[]{ 2, 3 }, input1);
```
Although this code works and does tell you if the expected output and the actual output is equal,
it only shows the indexes of where the difference occurs. This is not very helpful, since it does
not cover the broader view of where the bugs or errors could have occured at. However, if you used
toString() it can help show the entire actual output so you can see in the broader sense of where
the code could have occured.

Instead using this code;
```
# code block
assertEquals(Arrays.toString(new int[]{2,3}), Arrays.toString(input1));
```
The entire actual output is displayed, the toString method basically converts both expected output
and actual output to a string. This way when comparing the two, the entirety of the actual output 
is revealed.
