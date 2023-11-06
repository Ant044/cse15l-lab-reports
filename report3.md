Andrew Tan\
10/31/2023\
CSE 15L Section A05

# **Lab 3 Lab report**

## **Bugs**
This was a failure inducing input test for the `reverseInPlace()` function in the initial `ArrayExamples.java` file provided to us. The input was `{3,4}`
```
  @Test // My ReverseInPlace test
	public void testReverseInPlace2()
  {
    int[] input1 = { 3, 4 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 4, 3 }, input1);
  }
```
(I took out the other test before compiling)
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/70b09053-e142-4036-9cf3-39f7e1c896a4)


An input that didn't cause a failure was `{ 3 }`, which was the input that was initially given to us in the test. 
```
    @Test 
    public void testReverseInPlace() {
        int[] input1 = { 3 };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[]{ 3 }, input1);
    }
```

![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/51b8e5e1-1853-448f-b36e-6114665fa652)


the symptom for failing in this case was JUnit explicitly telling us that it failed. It expected a 3, but got a 4 for the second element of the resulting array.

This is the initial code:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

And this is the fixed code:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```
the bug was that instead of swapping elements simultaneously, one was being set to the other, thus permenantly deleting one of the values. After making a temp value and swapping them at the same time, we then had to change the for loop to only iterate through the first half of the array as to not reverse it twice. 

## **Researching Commands**
I decided to research command line options for `grep`. For the following examples, my working directory is the `technical` folder. I used an article from Geeks for Geeks to find options to try ( https://www.geeksforgeeks.org/grep-command-in-unixlinux/ )

### -w
The first option is `-w`, which means that the whole word has to match for the line to be returned. 
`grep -w United plos/journal.pbio.0020001.txt` returned many lines:
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/07b7cc10-7c04-4f08-aa1e-d2d0e63c6a5b)\
This returned every line that had "United" as its own, standalone word
while `grep -w Uni plos/journal.pbio.0020001.txt` (removed the second half of United) returned nothing, as "Uni" doesn't appear as a standalone word in the file. 
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/6604cc30-e95d-4098-a7ed-fced6da99721)\

### -o
The second option is `-o`, which prints only the matching portion of the line. 
`grep -o United plos/journal.pbio.0020001.txt` gave me 
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/f90dbc52-3e55-484a-8651-481d7e3aa7ca)\
which is about what I would expect from the description. The next question was whether it literally returned the same thing for however many lines it appears on no matter what, or if it can return something larger. I again tried it with only `Uni` to see if it would return the entire word.
`grep -o Uni plos/journal.pbio.0020001.txt` gave me 
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/c61da540-31e2-4efd-be0b-5f686cedea43)\
I question the use cases of this option.

### -v
The third option is `-v`, which prints lines that *don't* match what our input.
`grep -v United plos/journal.pbio.0020001.txt`
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/d608cb99-2a04-44a3-8013-a94c3a82676c)\
This printed most of the file, but most notably, the first line which has "United" in it is omitted. 
I tried doing this again but using the most common letter, `e`.
`grep -v e plos/journal.pbio.0020001.txt`
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/40b96425-0e11-46e9-8305-1314cf6c8eac)\
The result was pretty funny, consisting mostly of blank lines, and actually got through the entire output on one screen.

### -n
The last command `-n` is used to print the line number alongside of the line.
`grep -n United plos/journal.pbio.0020001.txt` gave me 
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/c8c84a9e-4664-47de-9f69-935665b10ec5)\
The result is quite self-explanatory. It prepends the number of the respective line in the file to the output.
I combined this with the `-v` command to see which lines had no 'e's in it
`grep -v -n e plos/journal.pbio.0020001.txt`
![image](https://github.com/Ant044/cse15l-lab-reports/assets/146861585/92004a22-7a1e-4e13-98c4-0932fd174310)\
Now I know `            Canada?` was on line 96.       



