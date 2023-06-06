# Lab Report 5
## Step 1: Student Reporting Bug

**What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?**

XPS 9305 Windows VS Code

**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.**

I'm seeing an error saying that the directory grading-area is not found, even though I specifically created the directory grading-area using mkdir grading area early on in the file. 
For some reason the directory cannot be found so I can not change my file path to grading-area directory using 'cd grading-area' as I expected
![Image](otro.png)
![Image](este.png)

**Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**

The failure-inducing input is the command I ran which is shown in the screenshot above, and is simply running the grade.sh file using one of the example repositories provided on the course website. The current directory is the list-examples-grader directory, which is shown to contain the grading-area directory when doing an ls command, so I'm not sure why the cd command isn't working. 

## Step 2: TA Response
Hi, thanks for the information. It looks like you may be confused on what directory you are actually in by the time you hit the line in your file which produces the bug, which is the `cd grading-area` line. Previously in your file you used the cd command to switch into the sub-directory student-submission, so that is the directory you are currently running in when you reach that line. This means you are trying to use cd from one subdirectory to another subdirectory, which is causing the error since the subdirectory student-submission cannot directly access the subdirectory grading-area. How can you change the syntax around your cd grading-area command so that you are checking in a place where it will be visible, and not in the subdirectory you are currently in? (Hint: you used the correct syntax earlier in the file)





