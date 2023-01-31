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
![Image](firstMessage)
**1**

**2**

**3**

**Image 2:**
![Image](secondImage)
**1**

**2**

**3**

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
