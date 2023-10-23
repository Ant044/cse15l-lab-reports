Andrew Tan\
10/21/2023\
CSE 15L Section A05

# **Lab 2 Lab report**
## **Part 1: StringServer**
For this part of the lab, I started by cloning the wavelet folder provided in week 2 as a foundation, and made edits to `NumberServer.java` (and also added an exception to `Server.java`)\
I created a blank text file `text.txt` in the `wavelet` folder, and used Buffered reader/writer to write to the file whenever someone used `add-message` and to read from to print the lines on the screen.\
The line numbers are not saved into the text file, but added when the `readFromFile()` method is called.
This is the code for my `StringServer.java`:
```
import java.io.IOException;
import java.net.URI;
import java.io.File;
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.BufferedReader;
import java.io.FileReader;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;

    public String readFromFile() throws Exception
    {
                String retString = "";
        String line;
        BufferedReader br = new BufferedReader(new FileReader("text.txt"));
        int lineCount = 1;
        while ((line = br.readLine()) != null) 
        {
            line = String.format("%d: ", lineCount) + line + "\n";
            retString += line;
            lineCount++;
        }
        //return String.format(parameters[1]);
        return String.format(retString);
    }

    public String handleRequest(URI url) throws Exception 
        {
            if (url.getPath().equals("/")) 
        {
            return readFromFile();
            //return String.format("Number: %d", num);
        } /*
        else if (url.getPath().equals("/increment")) 
        {
            num += 1;
            return String.format("Number incremented!");
        } */
        else 
        {
            if (url.getPath().contains("/add-message")) 
            {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) 
                {
                        {
                            FileWriter file = new FileWriter("text.txt", true);
                            BufferedWriter buffer = new BufferedWriter(file);
                            buffer.write(parameters[1]);
                            buffer.newLine();
                            buffer.close();
                        }/*
                    String retString = "";
                    String line;
                    BufferedReader br = new BufferedReader(new FileReader("text.txt"));
                    int lineCount = 1;
                    while ((line = br.readLine()) != null) 
                    {
                        line = "\n" + String.format("%d: ", lineCount) + line;
                        retString += line;
                        lineCount++;
                    }
                    //return String.format(parameters[1]);
                    return String.format(retString); */
                    return readFromFile();
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException 
    {
        if(args.length == 0)
        {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
\
This is the first use of `add-message`
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/385e9f5a-dfc5-4f9c-93f1-378630894a9c)
And this is my second usage
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/de1d27d5-79d6-4716-b1e8-b726c26cbd0e)



## **Part 2: SSH Key**
Path to the private key on my personal computer: `C:\Users\Andrew\.ssh\id_rsa` \
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/3a8682f5-632b-4703-bfd1-71b5f621472a)
\
Path to the public key within the ieng6 account: `/home/linux/ieng6/cs15lfa23/cs15lfa23ir/.ssh/authorized_keys` \
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/5f2317a0-f825-4ba9-af51-ccb7432d1c49)
\
Screenshot of logging in without having to enter a password (No idea why there are so many stale file handles)\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/1f957531-50ba-40f9-9e70-9e1648f384bc)


## **Part 3: Reflection**
I was not previously aware of the function or power of queries. I think servers being able to write stuff into text files based on what a user types into the URL is really cool.
