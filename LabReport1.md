 **Lab Report 1**

# 1. Downloading VSCode
First, open this link: [Link](https://code.visualstudio.com/)
 
You will see this page: 
![Image](first.png)

Then, press the download button and follow through all the steps.
There's no need to update anything, just click your way through until it downloads.
Then, you should see a page like this:
![Image](second.png)

# Downloading Git for Windows
Next, because you're on Windows you need to download Git at this link: [Link](https://gitforwindows.org/)

This will open up a screen that looks like this: 
![Image](third.png)
From here, press Download. There is one step you have to manually change, which is shown below.
![Image](fourth.png)

__Make sure you switch the program Git will be used with to VS Code as shown above, or the rest of the process won't work.__

# Setting up VSCode 
Now, we're going to open up a terminal in VS Code by pressing the Terminal option from the top menu bar and clicking on New Terminal from the dropdown.
From there, press `Ctrl` + `Shift` + `P` , which should get you looking at something like this:
![Image](fifth.png)
From here, type in `Select Default Profile` into the search and select that option when it comes up.
Now, select GitBash, as seen below.
![Image](sixth.png)

# Signing into your cse15l account in VSCode
Now you're going to connect your personal account made for 15L to the server.
Open a new terminal and enter the following: 
`ssh cs15lsp23ic@ieng6.ucsd.edu` (ic is my specific code, your two letter code is different)

I will attach an image and walk you through the next few steps of logging in.
![Image](seventh.png)
Once you get to the 'Are you sure...' prompt, you will type in yes. 
After that, it will prompt you for the password you created with your cse15l account, enter it now.

# Trying out some commands!
Lastly, you're gonna try inputting some commands now that you're logged in. 
You can try `cd` , `ls` , `pwd`, `ls /home/linux/ieng6/cs15lsp23` , `cat /home/linux/ieng6/cs15lsp23/public/hello.txt`

Attached are some images of how these commands will run: 
![Image](eighth.png)
![Image](ninth.png)
![Image](tenth.png)

And you're all done setting up VSCode and linking your account!
