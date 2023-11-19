Andrew Tan\
11/19/2023\
CSE 15L Section A05

# **Lab 4 Lab report**
### **Step 4**
I typed `ssh cs15lfa23ir@ieng6.ucsd.edu<enter>` to log into my ieng6 account. I didn't have to type a password because I had previously generated and authorized a key.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/58650e07-686c-4dc8-900a-9cd5784e2a35)


### **Step 5**
`git clone git@github.com:Ant044/lab7.git<enter>` I cloned my forked repository into my ieng6 account using the link given by the SSH option instead of the HTML option\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/bc892772-feaa-4286-bec4-765a8a5e1263)


### **Step 6**
`cd lab7<enter>` to enter the `lab7` folder\
`bash test.sh<enter>` to run the bash script that is included in the git repository that runs the tests.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/8919a87d-74f8-4cbd-91d0-77175f5c9d97)

### **Step 7**
`vim ListExamples.java<enter>` to enter into the file using vim.\
`43jer2:wq<enter>` to make the needed change to the file\
`43j` was to jump down 43 lines\
`e` was to get to the cursor onto the `1` that needed to be swapped to a `2`\
`r2` replaced the `1` with a `2`\
`:wq<enter>` allowed me to save and exit\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/08e9f711-8632-48c9-a78f-471db6a994f8)


### **Step 8**
`<up><up><enter>` to rerun the bash script.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/b7a4c750-faf4-4005-b654-bd655efebd8b)


### **Step 9**
`git add ListExamples.java<enter>` to add the changed file to be committed\
`git status<enter>` just to double check\
`git commit -m "Fixed ListExamples.java"<enter>` to create a local commit, and\
`git push<enter>` to push it to Github.\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/8dbdcdc0-ac6e-4d9b-bd27-128de276a690)

After refreshing my repository on github, I could see that it went through when this message showed up\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/8060079e-cd26-41db-a030-f44daee1b2ff)\
And looking in to the file itself, I saw that the bug was indeed fixed\
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/4042f40e-3d81-4e09-837f-6203e2754efc)\

