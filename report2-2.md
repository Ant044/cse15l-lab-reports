Andrew Tan\
10/22/2023\
CSE 15L Section A05

# **Lab 2 Lab report**
## **Part 1: StringServer**
For this part of the lab, I started by cloning the wavelet folder provided in week 2 as a foundation, and made edits to `NumberServer.java` (renamed it to `StringServer.java`)\
This is the code for `StringServer.java`:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler 
{
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String text = "";
    int lineNum = 1;

    public String handleRequest(URI url) 
    {
        if (url.getPath().equals("/")) 
        {
            return text;
        }
        else 
        {
            if (url.getPath().contains("/add-message")) 
            {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) 
                {
                    text += lineNum + ": " + parameters[1] + '\n';
                    lineNum++;
                    return text;
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer 
{
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
This is the first use of `add-message`:
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/4bca3331-f0ad-4982-862e-c7548b8664a7)\
For this run, the `.equals()` method was called a couple times to check the path of the URL.\
After determining that `/add-message` was part of the path, it called `getQuery().split("=")` on the url to get the 2 values `parameters[0]`, and `parameters[1]` from the query. `'s'` is the value in parameter[0] and `"Hello"` is parameter[1].\
The running string is named `text`, and is currently empty. After using `.equals` to confirm that the first split value is 's', it concatenates the `lineNumber` (which is set to `1` initially), the string (`"Hello"`) from parameter[1], and a new line to the string. \
`lineNumber` is then incremented from `1` to `2`, and finally `text` is returned.

And this is my second usage
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/e2010e27-82cb-49ca-a2a5-f61d68957236)\
The method calls in this run are largely the same. The difference as far as inputs go is that instead of `Hello`, I put `"Farewell"` into the URL after `s=`.\
Again, it `.equals()` is used to check the query, splitting it at the `=` and checking that the first split value is `s`. 
This time, `text` already has text in it when `lineNum`, `Farewell`, and `\n` are concatenated, so when `text` is returned, the page shows displays the current input *and* the previous input. `lineNum` is also incremented again from `2` to `3` before text is returned.


## **Part 2: SSH Key**
Path to the private key on my personal computer: `C:\Users\Andrew\.ssh\id_rsa` \
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/3a8682f5-632b-4703-bfd1-71b5f621472a)\
\
Path to the public key within the ieng6 account: `/home/linux/ieng6/cs15lfa23/cs15lfa23ir/.ssh/authorized_keys` \
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/5f2317a0-f825-4ba9-af51-ccb7432d1c49)\
\
Screenshot of logging in without having to enter a password (No idea why there are so many stale file handles)\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/1f957531-50ba-40f9-9e70-9e1648f384bc)\


## **Part 3: Reflection**
I was not previously aware of the function or power of queries. I think servers being able to write stuff into text files based on what a user types into the URL is really cool.
