# Exploring Command-Line Options with 'Find' Command
Information on how exactly ChatGPT was used to help find commands for this lab report is included at the end of the report.

## -size
The first new command line option I found was the -size, which goes through a directory and any subdirectories and returns only the files/directories above or below a certain memory size, depending on how the command is set up. The command can also check for different units of storage such as kilabytes, megabytes, etc, each with their own letter representation. It can also be made to specifically search and return files, or directories, by prefacing the command -size with `-type f` for files or `-type d` for directories.
The command is shown being used below for two different directories, `plos` and `911report`.
![Image](uno.png)
Here, the find command takes a path to a directory `plos` and returns only the files/directories with size GREATER than 18 kilabytes, due to the use of `+` before the number. The kilabytes is signified by a lower case k, while b is for bytes, M is for megabytes, and G is for gigabytes.
![Image](dos.png)
Here, find is looking inside 911report directory for files or directories UNDER 50 kilabytes, due to the `-` in front of the number, and kilabytes again signified by a lowercase k. The seach returns the directory itself on this search, showing that unless specified by the `-type` function, it will search unambiguously, returning both files and directories. I found the original command `-size` on ChatGPT as well as how to implement it, and other options such as `-type`.

## -ok
The command-line option -ok for find takes a command which is placed after the `-ok`, in this case `-ok grep`, and searches and returns all the lines in each file in the directory that contain whatever string you place after the grep. The syntax I used in the first use of this -ok is `find plos -ok grep 'approach' {} \` , which is looking inside of the plos directory for each file and running the command grep 'approach'. The specific difference between the command `-ok` and similar commands such as `-exec` is that with `-ok` , the terminal will prompt you to enter yes/no for each file it encounters in the directory before it runs the given command, in this case grep.

![Image](tres.png)
Here, we see that if you try running the command on a directory it won't work, but this is only due to the nature of the command grep, which is specifically looking inside a file for a string. This means that the -ok command will attempt to run commands on both directories and files. When successful, the output is the lines which contain 'approach'. The terminal will continue to prompt you with every file and directory until there is no more left or you stop it with `Ctrl + c`.
![Image](cuatro.png)
It is worth noting that if you enter no when prompted in regards to a file or directory, it will simply be skipped over. Here, the find command is looking in the directory government and the -ok command inquires with regard to each file and directory in government before running the grep command and searching for the string 'problems' in said file. The information on this command -ok and its implementation is from the website [Link](https://man7.org/linux/man-pages/man1/find.1.html) . This website contains a description of the many command line options for find and outlines how to implement -ok and its use. 

## -type
The -type command-line option for `find` narrows down the search for find down to a specific type, file or directory. A file is signified by `-type f` and a directory by `-type d`.
![Image](cinco.png)
In this case, find is searching for and printing out all the files found in the plos directory. The `-print` command at the end is just to make all these files print out onto the terminal. 
![Image](seis.png)
Here, find searches the directory 911report for any directories or subdirectories, which it prints out into the terminal. 
This information was found on ChatGPT.
## -exec
The -exec command is similar to the -ok command, except that it doesn't prompt the user for input before running a given command on all the files/directories signified. 
![Image](siete.png)
Here, I used `find 911report -size -30k -exec cat {} \;` . So, find is looking inside the directory 911report for files/directories of size UNDER 30 kilabytes and running the command cat on them, which prints out their contents into the terminal. The cat command does not work for directories, which is shown in the first line of output where the terminal prints `cat: 911report: Is a directory` , signifying it could not run the command on it. 
![Image](ocho.png)
In this case find is looking in the directory biomed for files/directories under 10 kilabytes and cat'ing them to print their contents into the terminal. Just as before, the cat function won't work on directories, which the terminal will show. Otherwise, the files under 10k size have their contents printed onto the command line. This information regarding -exec is from ChatGPT.

## ChatGPT Use Explanation:
**The first question I asked ChatGPT is: 
what are some command line options for the command 'find' in java. 
ChatGPT outputted:**


The `find` command is not a built-in command in Java, but it is a common command line tool in Unix and Unix-like operating systems. The `find` command is used to search for files in a directory hierarchy based on different criteria. Here are some common command line options for the `find` command:

- `-name`: searches for files by name. For example, `find /home/user -name myfile.txt` will search for a file named `myfile.txt` in the `/home/user` directory.

- `-type`: searches for files by type. For example, `find /home/user -type d` will search for directories in the `/home/user` directory.

- `-mtime`: searches for files based on modification time. For example, `find /home/user -mtime +7` will search for files modified more than 7 days ago in the `/home/user` directory.

- `-size`: searches for files based on size. For example, `find /home/user -size +1M` will search for files larger than 1 megabyte in the `/home/user` directory.

- `-exec`: executes a command on each file found. For example, `find /home/user -name myfile.txt -exec grep 'pattern' {} \;` will search for the pattern `pattern` in the `myfile.txt` file.

- `-print`: prints the name of each file found. For example, `find /home/user -type f -name '*.txt' -print` will print the names of all text files in the `/home/user` directory.

These are just a few examples of the many command line options available for the `find` command. For more information, you can refer to the `man` pages or other documentation for your operating system.

**From here, I got the idea to use -type, -size, and -exec.
I then asked a follow up question, asking: how to use -size command for find,
to which ChatGPT outputted,**
```
The `-size` command in `find` is used to search for files based on their size. You can specify the file size in bytes, kilobytes, megabytes, or gigabytes using a number followed by a size indicator (`b` for bytes, `k` for kilobytes, `M` for megabytes, or `G` for gigabytes).

Here are some examples of how to use the `-size` command with `find`:

1. To find all files in the current directory and its subdirectories that are larger than 1 MB:

   ```
   find . -type f -size +1M
   ```

   In this command, `find` searches for all regular files (`-type f`) in the current directory (`.`) and its subdirectories that are larger than 1 megabyte (`-size +1M`).

2. To find all files in the `/home/user` directory that are smaller than 100 bytes:

   ```
   find /home/user -type f -size -100b
   ```

   In this command, `find` searches for all regular files (`-type f`) in the `/home/user` directory that are smaller than 100 bytes (`-size -100b`).

3. To find all directories in the current directory and its subdirectories that are exactly 1 GB in size:

   ```
   find . -type d -size 1G
   ```

   In this command, `find` searches for all directories (`-type d`) in the current directory (`.`) and its subdirectories that are exactly 1 gigabyte in size (`-size 1G`).

You can use the `-` and `+` operators with the `-size` command to search for files smaller or larger than a certain size, respectively. The `b`, `k`, `M`, and `G` size indicators can be used to specify the size of files in bytes, kilobytes, megabytes, or gigabytes, respectively.
```
**This gave me more information on specific possible implementations of the -size command and the meaning behind the b,k,M,G characters, which I was confused on and unsure of how to use it for anything other than megabytes since that is what the previous output had shown an example of.**
