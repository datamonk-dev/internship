<!-- markdownlint-disable MD024 TOP004 -->

# Introduction

Welcome to the command line, your new powerful interface to the Linux operating system! If you've primarily used graphical interfaces (like clicking icons and opening menus), the command line might feel a bit intimidating at first. Don't worry! This lesson will introduce you to the fundamental commands you'll use daily, transforming the terminal from a mysterious black box into a familiar and efficient tool.

Think of the command line as talking directly to your computer. Instead of pointing and clicking, you type commands, and the computer responds. This direct interaction offers incredible power, speed, and precision, essential skills for any aspiring developer.

### Lesson Overview

This section contains a general overview of topics that you will learn in this lesson.

* Understanding the core principles of Linux command-line interaction.
* Mastering essential commands for navigating your file system.
* Learning how to view, search, and manage files.
* Gaining insights into process management and system monitoring.
* Discovering how to get help and find information about commands.

### Assignment

<div class="lesson-content__panel" markdown="1">

1.  Read through each section carefully, paying close attention to the command explanations and examples.
2.  **Practice every command** in your terminal. There's no substitute for hands-on experience!
3.  Complete all the exercises provided at the end of each section. Verify your output matches the expected results.
4.  Explore the additional resources and videos to deepen your understanding.

</div>

### Linux and Bash Fundamentals

Now, let's dive into some useful commands and utilities we will be using on a daily basis when using Linux. Mastering these will significantly boost productivity and understanding of how your development environment works.

#### Why the Command Line?

The command line (often called the terminal, console, or shell) is a text-based interface used to operate software and operating systems. While it might seem old-fashioned, it offers several advantages for developers:

* **Efficiency:** Many tasks can be automated and performed much faster than with a GUI.
* **Power:** Access to advanced system functions and configurations not available through graphical tools.
* **Remote Access:** Crucial for managing servers, which typically have no GUI.
* **Version Control:** Git, a fundamental tool for developers, is primarily command-line driven.
* **Scripting:** Automate repetitive tasks using shell scripts.

## 1. Command-Line Navigation

Imagine your Linux system as a vast forest of files and folders. To find your way around, create new clearings, or prune old paths, you need a map and the right tools. Linux follows a strict convention for storing different kinds of files (such as system binaries, logs, configurations, and user files) in specific places. Understanding this structure is key to navigating efficiently.

The diagram below outlines some of the primary directories used by Linux for these purposes. Getting familiar with these will make it much easier to locate files and understand system organization.

![Linux Directories](./img/linux_directories.png)

Want a more in-depth visual explanation? Watch this excellent video on Linux file system hierarchy:
[The Linux File System Explained (YouTube)](hhttps://youtu.be/42iQKuQodW4)

In this chapter, we will dig into commands related to folder structure and file navigation in a Linux operating system.

#### Command Explanations:

Here's a breakdown of the essential commands for moving around and managing your files and directories.

* `pwd`: **P**rints the **w**orking **d**irectory. This command tells you exactly where you are in the file system hierarchy. Think of it as "Where am I?"
* `ls`: **L**i**s**ts files and directories. This is like looking inside a folder.
    * `ls -l`: Provides a "long listing" format, showing more details like permissions, ownership, size, and modification date. 
    * `ls -a`: Shows "all" files, including hidden ones (those starting with a `.`).
* `cd`: **C**hanges the **d**irectory. This is how you move between folders. 
    * `cd ..`: Moves up one directory level.
    * `cd ~`: Moves to your home directory (the default starting point for your user).
    * `cd /path/to/directory`: Changes to an absolute path.
* `mkdir`: **M**a**k**e **dir**ectory. Used to create new folders.
* `cp`: **C**o**p**ies files or directories.
    * `cp file1.txt backup/`: Copies `file1.txt` into the `backup` directory.
    * `cp -r folder1/ folder2/`: Copies `folder1` and its contents recursively to `folder2`.
* `mv`: **M**o**v**es or renames files or directories. This command serves a dual purpose: moving a file to a new location or simply changing its name.
    * `mv old.txt archive/`: Moves `old.txt` into the `archive` directory.
    * `mv original.txt new_name.txt`: Renames `original.txt` to `new_name.txt`.
* `rm`: **R**e**m**oves files or directories. Use with caution, as deleted files are often unrecoverable from the command line!
    * `rm temp.txt`: Deletes the file `temp.txt`.
    * `rm -r temp_folder/`: Deletes the directory `temp_folder` and its contents recursively.
* `cat`: Con**cat**enates and displays file content. Useful for quickly viewing the entire content of small text files.
* `less`: Views file content one screen at a time. Ideal for larger files, allowing you to scroll, search, and navigate without loading the entire file into memory. Press <kbd>q</kbd> to quit `less`.
* `head`: Displays the beginning of a file. By default, it shows the first 10 lines.
    * `head -n 5 file.txt`: Displays the first 5 lines.
* `tail`: Displays the end of a file. By default, it shows the last 10 lines. Often used to monitor log files in real-time (`tail -f`).
    * `tail -n 5 file.txt`: Displays the last 5 lines.
* `touch`: Creates new empty files or updates the timestamp of existing files.
* `*`: **Wildcard** for multiple characters. Matches any sequence of characters. For example, `*.txt` matches all files ending in `.txt`.
* `?`: **Wildcard** for a single character. Matches any single character. For example, `doc?.md` matches `doc1.md`, `docA.md`, etc., but not `doc10.md`.
* `echo >>`: The `echo` command prints text to the terminal. `>>` is a redirection operator that appends the output to a file. For example, `echo "Hello" >> greeting.txt` will add "Hello" to the end of `greeting.txt`.

#### Examples

Practice these commands in your terminal to get a feel for how they work.

```bash
pwd                                 # Print current directory 
ls                                  # List contents of current directory 
ls -l                               # List contents in long format 
ls -a                               # List all contents, including hidden files
cd /etc                             # Change to the /etc directory (absolute path)
pwd                                 # Confirm new directory
cd ..                               # Change to the parent directory 
pwd                                 # Confirm parent directory
mkdir notes                         # Create a new directory named 'notes' 
touch file1.txt file2.txt           # Create two new empty files 
mkdir backup                        # Create a 'backup' directory
cp file1.txt backup/                # Copy file1.txt into the backup directory
mv file2.txt archive/file_two.txt   # Move file2.txt into 'archive' (if exists) and rename it 
rm temp.txt                         # Remove a file named temp.txt 
rm -r temp_folder/                  # Remove a folder named temp_folder and its contents (use with caution!)
cat file.txt                        # Display the entire content of file.txt
less file.txt                       # View file.txt content page by page (press 'q' to exit)
head -n 10 file.txt                 # Display the first 10 lines of file.txt
tail -n 10 file.txt                 # Display the last 10 lines of file.txt
echo "My first line" > my_file.txt  # Create or overwrite my_file.txt with "My first line"
echo "My second line" >> my_file.txt # Append "My second line" to my_file.txt
cat my_file.txt                     # View the content of my_file.txt
ls *.txt                            # List all files ending with .txt 
ls doc?.md                          # List files like doc1.md, docA.md, etc.
```
### Exercises
Work through these exercises to solidify your understanding of navigation and file management.

## 1. Create a directory and navigate into it:

Create a new directory named my_project, then navigate into it and verify your current location.

``` bash
mkdir my_project
cd my_project
pwd
```
**Expected output:** ```/home/yourusername/my_project``` (your username will replace yourusername)

**2. Create and copy files:**

Inside my_project, create two empty files: report.txt and data.csv. Then, create a new directory named archive and copy report.txt into it.

``` bash
touch report.txt data.csv
mkdir archive
cp report.txt archive/
```
**Verification:**
 Check if ```report.txt``` exists inside the ```archive/``` directory using ```ls archive/```

**3. View file permissions:**

From inside ```my_project```, list all files and directories in long format to see their permissions.

```bash
ls -la
```
**Expected output:** You should see lines similar to:

```-rw-r--r-- 1 yourusername yourusername 0 Jun 5 10:30 data.csv```
```drwxr-xr-x 2 yourusername yourusername 4096 Jun 5 10:30 archive``` (permissions may vary slightly)

**4. View file content with ```cat``` and ```less```:**

Add some text to ```data.csv``` (you can use ```echo "header1,header2" > data.csv``` and then ```echo "value1,value2" >> data.csv```). Then, view its contents using both ```cat``` and l```ess```.

```bash
echo "Name,Age" > data.csv
echo "Alice,30" >> data.csv
echo "Bob,24" >> data.csv
cat data.csv
less data.csv
```
**Expected output:** 
The content of ```data.csv``` should be displayed. When using ```less```, you'll need to press <kbd>&#x21B5; Enter</kbd>+<kbd>q</kbd> to exit.

**5. Practice wildcard matches:**

Create a few more files that will allow you to test the ```*``` and ```?``` wildcards. Then, use ```ls``` with wildcards to list specific groups of files.

```bash
touch document1.txt document2.md photo.jpg report_final.txt
ls *.txt
ls doc*.txt
ls *.md
ls report?.txt
```
**Expected output:**

```ls *.txt``` should list ```document1.txt```, ```report.txt```, ```report_final.txt``` (and ```data.csv``` if still ```.txt```)

```ls doc*.txt``` should list ```document1.txt```.

```ls *.md``` should list ```document2.md```.
```ls report?.txt``` should list ```report_final.txt``` (or similar if you named it differently).

---

## 2. Process Management & Environment
Every program running on your Linux machine spawns a process. Sometimes a single program will spawn multiple processes to handle different tasks concurrently. For example, each Chrome tab you open often creates a new process with its own allocated RAM and CPU threads. Similarly, each extension running within Chrome might have its own process(es). Optimizing resource allocation and understanding what's running on your system requires a good grasp of these processes.

In this section, we will look into some commands that allow us to view and manage processes running on the system. Think of this as the Linux alternative to Windows' Task Manager, but far more powerful and granular.

### Command Explanations:
These commands provide powerful tools for monitoring system activity, managing running programs, and understanding your shell's environment.

- ```top```: Table of processes. Displays real-time, dynamic information about system processes. It shows CPU usage, memory usage, swap space, and a list of the top consuming processes. Press <kbd>&#x21B5; Enter</kbd>+<kbd>q</kbd>  to quit top.
- ```htop```: An enhanced, interactive process viewer. ```htop``` provides a more user-friendly interface than ```top```, with color-coding, mouse support, and easier navigation. It's often not installed by default but is highly recommended. To install on Ubuntu/Xubuntu: ```sudo apt install htop```.
  
- ```ps aux```: Process status. Displays a snapshot of all currently running processes.
  - ```a```: Shows processes for all users.
  - ```u```: Displays user/owner.
  - ```x```: Shows processes not associated with a terminal.
  
- ```kill```: Terminates processes by their Process ID (PID). This is how you stop a misbehaving program.
  - ```kill 1234```: Sends a termination signal to the process with PID ```1234```.
  - ```kill -9 1234```: Sends a "force kill" signal (SIGKILL). Use this as a last resort, as it doesn't allow the program to clean up gracefully.
- ```pkill```: Terminates processes by name. More convenient than ```kill``` if you don't know the exact PID.
  - ```pkill chrome```: Attempts to kill all processes with "chrome" in their name.
  
- ```echo $PATH```: Displays the current ```PATH``` environment variable. The ```PATH``` variable tells your shell where to look for executable commands when you type them.
- ```export```: Sets environment variables. Environment variables are dynamic named values that can affect the way running processes behave.
  - ```export MY_VARIABLE="hello"```: Creates an environment variable ```MY_VARIABLE```.
  - ```export PATH=$PATH:~/bin```: Appends ```~/bin``` to your ```PATH```, allowing you to run executables in your bin directory from anywhere.

- ```history```: Shows your command history. This is incredibly useful for recalling previously typed commands.
- ```!100```: Re-executes the 100th command from your history. Use ```history``` to find command numbers.
- ```neofetch```: Displays system information in a clean, aesthetic way, often including your distribution logo. (May need to be installed: ```sudo apt install neofetch```).
- ```df -h```: Disk free. Shows disk space in human-readable form (```-h```). This lets you see how much space is left on your various disk partitions.
- ```du -sh```: Disk usage. Displays the size of a directory in human-readable form (```-h```), summarizing (```-s```) the total size.
  - ```du -sh ~```: Shows the size of your home directory.
- ```lscpu```: List CPU information. Displays detailed information about your CPU architecture.
- ```.bashrc```: A shell configuration file for the Bash shell, executed when you open an interactive shell (like your terminal). This is where you put custom aliases, functions, and environment variable settings that you want to apply to every new terminal session.
- ```.bash_profile```: A shell configuration file executed only during login shells (e.g., when you log in via SSH or some graphical terminal emulators at startup). For most regular terminal use, ```.bashrc``` is more commonly used.

**Examples**

Experiment with these commands to understand your system's activity and configuration.
```bash
top                                 # Display real-time process activity (press 'q' to quit)
htop                                # (Install if not present) Enhanced interactive process viewer
ps aux                              # Display a snapshot of all running processes
ps aux | grep bash                  # Find processes related to the 'bash' shell
kill 1234                           # Terminate process with PID 1234 (replace 1234 with an actual PID)
pkill firefox                       # Try to kill all processes named 'firefox'
echo $PATH                          # Display your current PATH environment variable
export MY_VAR="Hello DataMonk!"         # Create an environment variable
echo $MY_VAR                        # Display its value
export PATH=$PATH:~/bin             # Add your personal 'bin' directory to PATH
history                             # Show your command history
!100                                # Execute the 100th command in your history (replace 100 with a valid number)
neofetch                            # Display system information
df -h                               # Show disk space in human-readable form
du -sh ~                            # Display total size of your home directory
lscpu                               # Display CPU architecture information
```

**Exercises**

These exercises will help you apply process management and environment commands.

**1. Find your terminal's PID and identify a specific process:**

Open ```top```. Locate the process ID (PID) of your terminal application (e.g., ```gnome-terminal```, ```xfce4-terminal```). Observe its CPU and memory usage.

```bash
top
```
**Expected output:**
 A dynamic list of processes. Look for your terminal application's name and its associated PID in the list.

**2. Check Bash processes:**

Use ```ps aux``` and ```grep``` to filter for all processes related to your ```bash``` shell.

```bash
ps aux | grep bash
```
**Expected output:** A list of processes where bash appears in the command, showing details like user, PID, CPU, and memory usage.

**3. Add an alias to .bashrc and source it:**

An alias is a shortcut for a longer command. Add an alias ```ll``` that runs ```ls -la```. Then, "source" your ```.bashrc``` file to apply the changes without restarting your terminal, and finally, test your new alias.

```bash
echo "alias ll='ls -la'" >> ~/.bashrc
source ~/.bashrc
ll
```
**Expected output:** The ```ll``` command should now produce a detailed, long-format listing of the current directory's contents, similar to ```ls -la```.


<div class="lesson-note lesson-note--tip" markdown="1">

**What `source` does**  
*The `source` command (or `.` which is its shorthand) reads and executes commands from the file passed as its argument, in the current shell. This is crucial because if you just run `.bashrc` as a script, the changes would only apply to a new sub-shell created for that script, not your current interactive session. `source` makes the changes effective immediately.*

</div>

**4. Use command history:**

Display your entire command history. Then, pick a command from your history (e.g., the `mkdir my_project` command from earlier) and re-execute it using its history number (e.g., `!123` if it was command 123).

```bash
history
# Then, find a command number (e.g., 10) and run:
!10
```
**Expected output:** `history` will show a numbered list of all commands you've typed. `!NUM` will re-execute the command corresponding to `NUM` in that list.

**5. View disk and CPU information:**

Check your disk space usage in a human-readable format and then display detailed information about your CPU.
```bash
df -h
lscpu
```
**Expected output:** `df -h` will show a table of file system sizes, used space, available space, and mount points. `lscpu` will output detailed CPU specifications like architecture, cores, threads, and cache sizes.

### To be continued…
<!-- end list -->
