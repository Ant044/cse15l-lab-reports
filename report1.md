Andrew Tan
10/3/2023
CSE 15L Section A05

# **Lab 1 Lab report**

## **the `cd` command**
Using `cd` with no arguments from the working directory `/home` produces no output. This is because without any arguments, `cd` can't 
enter any folder.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/c55d080c-2ddc-4719-9ab0-0d1e823888dd)

Using `cd` with a path to a directory/folder also printed no output, however in the terminal prompt for the next command, the `~` representing home changes to `~/lecture1`, reflecting that it is working form that directory.\
 ![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/90070819-bb9e-4233-9452-760f52167534)

 Using `cd` with a path to a file returns an error reflecting that the file was not a directory. This happened because the argument given was an invalid type for this command.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/7eff8feb-d6db-48ec-a461-5319a74d0163)

## **The `ls` command**
Using `ls` without any arguments from the home directory printed the files/folders in that directory. This is because, without being given any path, `ls` works on the working directory itself. This is not an error as that is the intended function\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/8766f30e-cec0-47de-8ef6-94712ee80d50)

Given a directory as an argument, `ls` prints the contents of that directory instead of the working directory. This is not an error as that is also the intended function.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/9f5f48f7-0031-4a4e-8667-dbc91b57e001)

Given a file as an argument, `ls` simply prints the name of the file.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/0e974e7f-a7fc-4e79-ac91-3ecdbb9e0ac7)

## **The `cat` command**
Using `cat` without any arguments from the home directory seemed to glitch out the terminal. The user/directory thing was removed and I was able to just free type, and if I pressed enter it would duplicate the text. I had to use `ctrl+d` to exit the command. I'm not sure if this is an error or not.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/f30c076c-f190-4c35-a7fc-0e6ef8d0155d)

Using the command with a directory as an argument produced text that confirmed that, indeed, the directory was a directory. The output is not an error.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/fb4c4ea4-a236-4c9e-aca1-d58104a95f62)

Using the command with a file as an argument produced the text inside of that file (or files if there are multiple arguments). The output is not an error, as this is its intended purpose.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/de724f65-72cf-4c6b-b1d4-02375050716f)

